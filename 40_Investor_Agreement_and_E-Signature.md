---
title: Investor Agreement and E-Signature
description: Complete workflow for investor agreement generation, Adobe Sign e-signature integration, manual upload, and per-investor tracking in asset sale deals
---

# Investor Agreement & E-Signature

## Overview

Investor agreements are legally binding documents that formalize the terms between the issuer and each investor in an asset sale deal. The Intain Markets platform supports electronic signature workflows via Adobe Sign (or Zoho Sign), allowing agreements to be created, distributed, signed, and tracked entirely within the platform. This workflow covers the complete agreement process from document preparation to fully executed signatures, including both the e-sign path and the manual upload alternative.

## Workflow Overview

The investor agreement workflow ensures that all legal documentation is properly executed before settlement can proceed. Agreements are managed per investor, and each investor's signature status is tracked independently.

**Document Preparation** — The issuer prepares the sale agreement document and uploads it to the deal, typically during deal creation (Step 3 of the wizard) or later from the deal details page.

**Agreement Status Initialization** — When a deal reaches the **Invest** stage and an investor is allocated, the platform initializes an investor agreement record with a status of **Not Signed** for each investor.

**Signature Routing** — The platform routes the document for electronic signature via Adobe Sign, creating individual signing requests for each allocated investor.

**Investor Signing** — Each investor receives their agreement, reviews the terms, and signs electronically through the Adobe Sign interface embedded within the platform.

**Tracking and Verification** — The platform tracks each investor's signing status and stores the executed documents securely.

## Key Stages

### Stage 1: Sale Agreement Upload

The issuer prepares the investor agreement document and uploads it to the deal. This happens in one of two places:

- **During deal creation**: On the Sale Terms tab (Step 3 of the wizard), the footer area provides an **Upload** button to attach a sale agreement PDF before submitting the deal.
- **From deal details**: After deal creation, the issuer can upload or replace the sale agreement from the deal's document management section.

The uploaded document serves as the template for all investor agreements in this deal. Accepted formats are PDF documents.

### Stage 2: Agreement Record Creation

When the deal is created, the platform initializes an investor agreement record on the deal with a default status of **Not Signed**. Once the underwriter finalizes allocation and confirms the winning buyer (the selected investor), the agreement becomes actionable for that investor.

- **Status**: `Not Signed`
- The agreement applies to the **selected investor** (winning buyer) on the deal — not all allocated investors

> **Important**: In the current workflow, there is one agreement per deal, tied to the selected investor. The selected investor is the party who signs the agreement.

### Stage 3: Electronic Signature via Adobe Sign

Once the deal reaches the **Invest** status, the e-signature process becomes available. The platform's integration with Adobe Sign works as follows:

1. **Initiation**: The platform creates an Adobe Sign agreement for each investor, embedding the sale agreement document and the investor's signing fields.
2. **Notification**: Each investor receives a notification (via the platform and/or email) that their agreement is ready for signing.
3. **Embedded Signing**: The investor accesses the deal details page and opens their agreement. The Adobe Sign interface is embedded within the platform — no separate Adobe Sign account is needed.
4. **Signing**: The investor reviews the terms and signs electronically within the embedded interface.
5. **Completion**: Upon signing, the platform receives a webhook callback from Adobe Sign. The signed PDF is downloaded and stored in blob storage. The agreement record is updated, and the deal status automatically advances to **Settlement In Progress**.

The updated agreement record contains:
- **Status**: `Signed`
- **Agreement ID**: The Adobe Sign agreement identifier
- **Blob Pointer**: Storage reference (container, stored path, version ID) for the signed document
- **Signed By Org ID**: The organization that signed
- **Signed Via**: `adobeSign`
- **Signed At**: UTC timestamp of when the signature was completed

> **Important**: Investor agreement signing is only allowed when the deal status is **Invest**. If the deal is in any other status, the signing action is blocked with an error message.

### Stage 4: Manual Agreement Upload (Alternative)

For cases where electronic signing is not used — such as when agreements are signed physically or through an external process — the issuer can upload manually signed agreements:

1. The issuer obtains the physically signed agreement from the investor
2. From the deal details page, the issuer uploads the signed document for the specific investor
3. The system records the manually uploaded agreement with:
   - **Status**: `Signed`
   - **Signed Via**: `upload`
   - **Blob Pointer**: Storage reference for the uploaded document
   - **Signed At**: UTC timestamp of the upload

Both paths — Adobe Sign and manual upload — result in the same `Signed` status and both automatically advance the deal to **Settlement In Progress**. They provide equivalent tracking capabilities.

### Stage 5: Agreement Completion and Settlement Gate

Once all investor agreements are signed or uploaded, the deal is ready to proceed to settlement:

- All investor agreements show **Signed** status
- The platform validates that all required agreements are in place
- The deal can proceed to the settlement phase
- If any investor's agreement remains **Not Signed**, settlement cannot begin

## How the Workflow Progresses

The agreement workflow runs in sequence with the commitment and allocation process. The typical sequence is:

1. Issuer uploads sale agreement during deal creation or before the deal reaches Invest status
2. Investors commit to the deal and the underwriter finalizes allocation, confirming the winning buyer
3. Deal status moves to **Invest**
4. The selected investor signs their agreement (via Adobe Sign or manual upload)
5. Upon signing, the deal automatically advances to **Settlement In Progress**

Each investor's agreement is independent — one investor signing does not affect another's process. The deal details page shows a summary of all investor agreement statuses, providing visibility into which investors have signed and which are still pending.

## Important Points to Know

**Adobe Sign Integration** — The platform uses Adobe Sign as the primary electronic signature provider. The signing experience is embedded directly within the platform interface. Investors do not need a separate Adobe Sign account to sign.

**Zoho Sign Support** — The platform also supports Zoho Sign as an alternative e-signature provider. The flow is functionally equivalent to Adobe Sign.

**Per-Investor Tracking** — Each investor has their own agreement instance with independent status tracking. The two statuses are:
- **Not Signed** — agreement created but not yet executed
- **Signed** — agreement fully executed (via e-sign or manual upload)

**Pre-Settlement Gate** — Settlement cannot begin until all investor agreements are executed. This ensures legal documentation is complete before any financial transfer occurs.

**Document Storage** — Signed agreements are stored securely in blob storage with versioning. Each agreement record maintains a full storage reference (container, stored path, version ID) linked to the deal for audit and compliance purposes.

**Dual Path Support** — The platform supports both electronic signing (Adobe Sign / Zoho Sign) and manual upload of pre-signed documents, providing flexibility for different operational preferences.

**Audit Trail** — Every signature event is logged with timestamps, the signing organization, and the signing method. The agreement record permanently captures who signed, when, and how — providing a complete audit trail for compliance and legal review.

**Status Gate Enforcement** — The backend enforces that investor agreement signing is only permitted when the deal is in **Invest** status. Attempts to sign at any other stage are rejected with a clear error message.
