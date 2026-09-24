---
title: Signature Visibility
description: >-
  Comprehensive guide to understanding when and where electronic signatures are
  visible across roles and workflows in Intain Markets
---

# Signature Visibility

## Overview

Electronic signatures are used throughout Intain Markets for term sheets, master commitments, funding notices, and batch self-certification. The platform supports two e-signature providers — **Adobe Sign** and **ZohoSign** — and manages signature visibility carefully based on the user's role and the item's workflow status. This guide explains who can see signatures, when they become visible, where to find signed documents, and how the platform tracks signature status across all e-signature workflows.

## How to Navigate Signature Information

Signature information appears in several locations within the platform, depending on the type of item and your role. Here is how to find signature details:

**For Term Sheets:**

* Navigate to **Credit Facility** → locate the term sheet
* Open the term sheet details
* Check the **Documents** section for the signed PDF
* The `signerStatus` field shows the signing state; after the borrower signs, the status changes to **BorrowerSigned**

**For Master Commitments:**

* Navigate to **Credit Facility** → **Active Facilities**
* Open the master commitment details
* Check the **Documents** section for signed commitment documents
* Each lender's `lenderStatus` in the `lenderGroups` array shows their individual signature status

**For Funding Notices:**

* Navigate to **Credit Facility** → locate the funding notice under its master commitment
* The action button shows **E-sign (0/n)** progressing to **(n/n)**
* Each lender's entry in `tokenDistribution` shows their `esignatureStatus`

**For Batch Self-Certification:**

* Navigate to the **Batches** section
* Self-certified batches show the signed certificate
* The `verificationSource` field shows `Self Certified (Data Only)`

## What You Will See

### Term Sheet Signatures

**Who Signs:** The Borrower

**How It Works:**

1. The borrower clicks **Create Draft**, which opens an Adobe Sign (or ZohoSign) popup
2. The borrower reviews the generated term sheet document (created from a template that includes all facility terms, collateral details, and financial data)
3. The borrower completes the signature in the provider's signing interface
4. Upon completion, the signed PDF is downloaded, stored in Azure Blob Storage, and linked to the term sheet record
5. The term sheet `signerStatus` changes from `Pending` to a signed state
6. The term sheet status advances to **BorrowerSigned**

**Signature Visibility by Role:**

| Party              | Can See Signed Document? | When                                                                                     |
| ------------------ | ------------------------ | ---------------------------------------------------------------------------------------- |
| **Borrower**       | Yes                      | Immediately after completing the signature                                               |
| **Facility Agent** | Yes                      | When the term sheet is submitted and reaches `PENDING_REVIEW` or `BorrowerSigned` status |

**What Is Stored:**

* The signed PDF is stored as a Blob pointer in the term sheet's `signedPdf` field
* The e-signature provider's envelope ID is recorded (`agreementId` for Adobe Sign, `requestId` for ZohoSign)
* The envelope status is tracked (e.g., `agreementStatus` for Adobe Sign, `requestStatus` for ZohoSign)
* The signing completion timestamp (`signingCompletedAt`) is recorded
* The full signing event is logged in the e-signature provider's collection (`adobesign_requests` or `zohosign_requests`)

**Change Request Impact:** If the facility agent requests changes on a signed term sheet, the signing status is **reset**:

* `signerStatus` returns to `Pending`
* `docusignStatus` shows `Reset - Must Re-sign`
* The borrower must re-sign the updated term sheet after making changes

### Master Commitment Signatures (Lender E-Sign)

**Who Signs:** Each Lender

**How It Works:**

1. After the facility agent approves a term sheet and a master commitment is auto-created, lenders are invited to sign
2. Each lender clicks **Approve & E-Sign** in their **Opportunities** section
3. An Adobe Sign (or ZohoSign) popup opens
4. The lender completes the signature
5. The signed document is downloaded, stored, and linked to the lender's group entry in the master commitment

**Lender Status Progression:**

| `lenderStatus` Value   | Meaning                                                     |
| ---------------------- | ----------------------------------------------------------- |
| `pending_approval`     | Lender has not yet acted                                    |
| `approved`             | Lender has approved (may precede e-signature in some flows) |
| `esignature_completed` | Lender has completed the e-signature — fully committed      |

**Signature Visibility by Role:**

| Party              | Can See Signed Document?    | When                                                                         |
| ------------------ | --------------------------- | ---------------------------------------------------------------------------- |
| **Lender**         | Yes — their own signature   | Immediately after completing their e-sign                                    |
| **Facility Agent** | Yes — all lender signatures | As each lender completes their e-sign                                        |
| **Borrower**       | Yes — all signatures        | After the facility becomes **ACTIVE** (at least one lender completes e-sign) |

**Activation Rule:** The master commitment status changes to **ACTIVE** when at least one lender in the `lenderGroups` array reaches `esignature_completed` status. The system filters lenders by this status when assembling token distributions for funding notices: `lenderGroups.filter(lender => lender.lenderStatus === 'esignature_completed')`.

**What Is Stored:**

* A signed PDF is generated per lender and stored as a Blob pointer in the lender's group entry
* The e-signature details (`agreementId`/`requestId`, `agreementStatus`/`requestStatus`, `envelopeStatus`) are recorded at the lender group level
* The signing event is appended to the master commitment's `actionHistory` and `statusHistory`
* If the master commitment has sub-commitments, the signing status is stamped on both the parent and sub-commitment records

### Funding Notice Signatures (FA Signs for Each Lender)

**Who Signs:** The Facility Agent (on behalf of each lender)

**How It Works:**

1. After the borrower approves the token transfer, the funding notice action shows **E-sign (0/n)**
2. The facility agent clicks the E-sign action, which opens an Adobe Sign (or ZohoSign) window
3. The facility agent signs on behalf of the first lender
4. The e-sign count updates to **(1/n)**
5. The facility agent repeats for each remaining lender
6. When all lenders are signed, the count shows **(n/n)**

**E-Sign Progress Tracking:**

| Status Display | Meaning                       |
| -------------- | ----------------------------- |
| E-sign (0/3)   | No lenders signed yet         |
| E-sign (1/3)   | FA signed for 1 of 3 lenders  |
| E-sign (2/3)   | FA signed for 2 of 3 lenders  |
| E-sign (3/3)   | All lenders signed — complete |

The platform tracks three aggregate fields on the funding notice:

* `eSignatureTotalCount` — total number of lenders requiring e-sign
* `eSignaturePendingCount` — how many lenders still need e-sign
* `eSignatureStatus` — overall e-sign status (`pending` → `completed`)

Each lender's individual status is tracked in the `tokenDistribution` array:

* `esignatureStatus`: `pending` → `ESIGN_COMPLETED`

**Signature Visibility by Role:**

| Party              | Can See Signed Document? | When                                                    |
| ------------------ | ------------------------ | ------------------------------------------------------- |
| **Facility Agent** | Yes — all signatures     | Immediately after signing for each lender               |
| **Lender**         | Yes — their own          | Only after FA completes e-sign for that specific lender |
| **Borrower**       | Yes — all signatures     | After FA completes e-signs for all lenders              |

**Critical Per-Lender Visibility Rule:** Each lender gains visibility into the funding notice **only after** the facility agent completes the e-sign for that specific lender. A lender whose `esignatureStatus` is still `pending` cannot see or act on the funding notice. This ensures that each lender only receives the funding notice when their legal documentation (the signed agreement) is in place.

### Batch Self-Certification Signatures

**Who Signs:** The Issuer

**How It Works:**

1. The issuer initiates batch self-certification via the `batchSelfCertify` e-signature request
2. The system generates a certificate document from the batch data
3. An Adobe Sign (or ZohoSign) window opens for the issuer to sign
4. Upon completion, the signed certificate is stored
5. All loans in the batch are stamped with `verificationSource: 'Self Certified (Data Only)'`
6. The batch status updates to `Reviewed`

**What Is Stored:**

* The signed certificate document is stored and linked to the batch record
* Each loan's metadata is updated with the verification source
* A notification is sent to the relevant organizations

## Helpful Tips

**Check the Status Field First** — Before looking for signed documents, check the item's status field. If a term sheet is still in `DRAFT`, there is no signature to view. If a funding notice shows `E-sign (0/3)`, no lender signatures exist yet.

**Signed Documents Are Permanent** — Once a document is signed via Adobe Sign or ZohoSign, the signed PDF is stored in Azure Blob Storage and cannot be modified, deleted, or replaced. This ensures the integrity of the signed agreement.

**Provider-Agnostic Tracking** — The platform uses a unified e-signature helper that works identically with both Adobe Sign and ZohoSign. The provider is determined by configuration, not by the user. Regardless of which provider is used, the signing experience, status tracking, and document storage follow the same patterns.

**Webhook-Driven Completion** — Signature completion is detected via webhooks from Adobe Sign or ZohoSign (registered at `/adobesign` or `/zohosign` webhook endpoints). The platform processes these webhooks to download the signed document, update the item's status, and trigger notifications. This means there may be a brief delay (typically seconds) between completing a signature in the provider's interface and seeing the updated status in Intain Markets.

**Multi-Channel Notifications** — When a signature is completed, the platform sends notifications via SSE (for real-time in-app updates) and email (for asynchronous notification). Both the signer and relevant counterparties receive notifications.

**Audit Trail Completeness** — Every signature event is recorded in multiple places: the item's `actionHistory`, the item's `statusHistory`, the e-signature provider's collection, and the platform's audit log. This provides a comprehensive, cross-referenced trail for compliance and dispute resolution.
