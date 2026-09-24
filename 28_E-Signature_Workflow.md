---
title: E-Signature Workflow
description: >-
  Understand how electronic signatures work across credit facility workflows,
  including provider integration, per-lender tracking, and document lifecycle
---

# E-Signature Workflow

## Overview

E-signatures are used throughout the credit facility workflow to digitally sign legally binding documents. The Intain Markets platform integrates with professional e-signature providers to ensure that all signed documents are legally enforceable, fully traceable, and securely stored. Every signature is recorded with complete audit details — who signed, when they signed, and what document was signed.

The platform supports two e-signature providers: **Adobe Sign** and **ZohoSign**. A **mock signing** mode is also available in test and UAT environments for development and testing purposes. All three options use a shared e-signature architecture with consistent workflows across all signing points, ensuring that the signing experience is uniform regardless of which provider is configured.

## Workflow Overview

E-signatures are required at three key points in the credit facility lifecycle. Each signing point serves a different purpose, involves a different signer, and triggers a different status transition:

| Signing Point                 | Who Signs                   | What Is Signed                 | When It Happens                         | Status After Signing             |
| ----------------------------- | --------------------------- | ------------------------------ | --------------------------------------- | -------------------------------- |
| **Term Sheet Signing**        | Borrower                    | Term sheet document            | After borrower clicks **Create Draft**  | Draft → BorrowerSigned           |
| **Master Commitment Signing** | Lender                      | Master commitment document     | When lender clicks **Approve & E-Sign** | PendingLenderApproval → Active   |
| **Funding Notice Signing**    | Facility Agent (per lender) | Funding notice for each lender | After FA approves the funding notice    | Per-lender: E-sign (0/n) → (n/n) |

## Key Stages

### Stage 1: Term Sheet E-Signature (Borrower)

**When It Happens:** After the borrower completes a term sheet and clicks **Create Draft**, the e-signature process begins automatically.

**How It Works:**

1. The borrower clicks **Create Draft** on a term sheet
2. The platform generates a PDF of the term sheet document
3. The PDF is uploaded to the configured e-signature provider (Adobe Sign or ZohoSign) as a transient document
4. The provider creates a signing agreement and returns a signing URL
5. The e-signature popup opens automatically in the borrower's browser
6. The borrower reviews the term sheet document within the provider's signing interface
7. The borrower completes the electronic signature
8. The provider notifies the platform of the completed signature
9. The signed document is downloaded from the provider and stored on the platform
10. The term sheet status changes from **Draft** to **BorrowerSigned**

**What This Means:**

* The term sheet is formally signed by the borrower
* The borrower can now submit the term sheet to the facility agent for review
* The signed document is permanently stored and available for download by authorized users
* Without the borrower's signature, the term sheet cannot be submitted to the facility agent

**E-Sign Details Tracked:**

* `agreementId` — The provider's unique agreement identifier
* `signingUrl` — The URL used for the signing session
* `status` — Current e-sign status
* `signProvider` — Which provider was used (Adobe Sign or ZohoSign)
* `signedDocumentUrl` — URL to the stored signed document

### Stage 2: Master Commitment E-Signature (Lender)

**When It Happens:** When a lender reviews a master commitment in their Opportunities section and clicks **Approve & E-Sign** to formally approve and commit to the credit facility.

**How It Works:**

1. The lender navigates to their **Opportunities** section in Credit Facility
2. The lender clicks **Review & Approve** on the master commitment
3. The lender reviews all facility configuration details — basic information, parties, conditions, pricing, covenants
4. The lender clicks **Approve & E-Sign**
5. The platform generates a PDF of the master commitment document
6. The PDF is uploaded to the e-signature provider
7. The e-signature popup opens for the lender
8. The lender reviews and signs the document
9. The signed document is downloaded and stored
10. The lender's individual `approvalStatus` changes to **approved** with a timestamp
11. The master commitment status changes to **Active** — even if only one lender out of multiple has approved

**What This Means:**

* The lender formally approves and commits to the credit facility
* **Any single lender's approval activates the entire facility** — all lenders do not need to approve for the facility to become active
* Each lender's approval is tracked independently — one lender's decision does not affect another's
* The facility agent can proceed with deal modelling once the commitment is active
* The signed commitment document is legally binding

**Per-Lender Tracking:** Each lender in the master commitment has individual e-sign tracking:

* `approvalStatus` — `pending` → `approved` or `rejected`
* `esignStatus` — Tracks the e-sign completion status
* `esignDetails` — Provider-specific details (agreement ID, signing URL, signed timestamp)
* `approvedAt` — Timestamp of when the lender approved

### Stage 3: Funding Notice E-Signature (Facility Agent)

**When It Happens:** After a funding request is approved and a funding notice is automatically generated, the facility agent must individually e-sign the notice for each participating lender.

**How It Works:**

1. A funding request is approved → A funding notice is auto-generated with status **PendingTokenGenerated**
2. The facility agent clicks **Approve** on the funding notice
3. The action button displays **E-sign (0/n)** where n is the total number of participating lenders
4. The facility agent clicks the E-sign action
5. The e-signature popup opens for the first unsigned lender
6. The facility agent signs the funding notice for that specific lender
7. The counter updates — **E-sign (1/n)**
8. The facility agent repeats the process for each remaining lender: (2/n), (3/n), and so on
9. Each lender can see and act on the funding notice **immediately after their individual e-sign is complete** — they do not need to wait for all lenders to be signed
10. When all lenders are signed — **E-sign (n/n)** — the overall e-sign process is complete

**What This Means:**

* The facility agent formally signs the funding notice for each lender individually
* Each lender has a separate e-sign record with their own agreement ID, signing URL, and completion timestamp
* Lenders can begin reviewing and acting on the funding notice as soon as their individual e-sign is done
* The per-lender signing ensures each lender receives a legally valid, individually signed document

**E-Sign Progress Tracking:** The E-sign counter provides real-time visibility into the signing progress:

| Counter          | Meaning                                                  |
| ---------------- | -------------------------------------------------------- |
| **E-sign (0/3)** | No lenders signed yet (3 total lenders in this notice)   |
| **E-sign (1/3)** | Signed for 1 lender — that lender can now see the notice |
| **E-sign (2/3)** | Signed for 2 lenders — both can now see the notice       |
| **E-sign (3/3)** | All lenders signed — e-sign process complete             |

**Per-Lender E-Sign Fields:**

* `lenderId` — Which lender this e-sign is for
* `esignStatus` — `pending` or `signed`
* `agreementId` — Provider agreement ID for this lender's signing
* `signingUrl` — Signing URL for this lender's document
* `signedAt` — Timestamp when the signing was completed

## How the Workflow Progresses

### E-Signature Provider Architecture

The platform uses a provider abstraction layer that allows seamless switching between e-signature providers. The configured provider is set at the platform level, and all signing points use the same provider consistently.

**Adobe Sign Integration:**

1. The platform uploads the document as a "transient document" to Adobe Sign
2. Adobe Sign creates an agreement with the transient document
3. The signer's email and a signing redirect URL are configured
4. Adobe Sign returns an agreement ID and a signing URL
5. The platform polls for agreement completion status (checking for the `SIGNED` status)
6. On completion, the signed document is downloaded and stored

**ZohoSign Integration:**

1. The platform uploads the document to ZohoSign
2. ZohoSign creates a sign request with signer details
3. A redirect URL is configured for post-signing
4. ZohoSign returns a request ID and signing URL
5. The platform checks for completion status
6. On completion, the signed document is downloaded and stored

**Mock Signing (Test/UAT):**

* Mock signing is available for test and UAT environments
* When enabled, the signing completes instantly without calling any external provider
* The document is immediately marked as signed
* A mock signed document is generated
* This allows rapid testing of workflows without requiring real e-signature accounts

### Document Lifecycle

Every signed document follows this lifecycle:

```
Document Generated (PDF) → Uploaded to Provider → Signing Agreement Created → Signer Completes Signature → Platform Notified → Signed Document Downloaded → Stored in Platform → Available for Download
```

## Important Points to Know

**Legally Binding** — All electronic signatures completed through Adobe Sign or ZohoSign are legally binding and enforceable. They comply with electronic signature regulations.

**Required for Progression** — Documents cannot progress through the workflow without the required signatures:

* Term sheets cannot be submitted to the facility agent without the borrower's signature
* Master commitments cannot become active without at least one lender's signature
* Lenders cannot see or act on funding notices without the facility agent's per-lender e-sign

**Per-Lender Tracking** — For funding notices, each lender has their own independent e-signature status. The facility agent signs individually for each lender, and each lender gains access to the notice as soon as their signature is complete.

**Provider Flexibility** — The platform supports both Adobe Sign and ZohoSign. The active provider is configured at the platform level. DocuSign has been retired and is no longer supported.

**Complete Audit Trail** — Every e-signature action is recorded with full audit details: who signed, when they signed, which provider was used, the agreement ID, and a reference to the stored signed document. This audit trail is immutable and available for compliance review.

**Callback and Polling** — The platform uses both callback notifications and status polling to detect when a signing session is completed, ensuring reliable status updates regardless of how the signer completes the process.

**Signed Document Storage** — All signed documents are downloaded from the provider and stored permanently on the platform. Authorized users can download signed documents at any time for reference, compliance, or legal purposes.
