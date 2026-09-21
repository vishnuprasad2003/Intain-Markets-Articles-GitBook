---
title: What Happens After Rejection
description: Detailed guide to understanding rejection outcomes, their implications, and how to proceed after an item is rejected in Intain Markets
---

# What Happens After Rejection

## Overview

Rejection is a final, irreversible decision in Intain Markets that permanently closes the workflow for the rejected item. Unlike a change request (which allows editing and resubmission), a rejection means the specific term sheet, funding request, or mandate cannot be modified, resubmitted, or appealed. However, rejection is not a dead end — submitters can always create a new item that addresses the issues identified in the rejection. This article explains exactly what happens when each type of item is rejected, what data is preserved, and what steps are available to move forward.

## Possible Outcomes

Rejection can occur on several item types across the platform. Each rejection follows a consistent pattern — the item becomes read-only, the rejection reason is recorded, and the submitter is notified — but the specific implications differ based on what was rejected and where it sits in the workflow.

## What Each Outcome Means

### Term Sheet Rejected

**Trigger:** The facility agent clicks **Reject** while reviewing a term sheet in `PENDING_REVIEW` status.

**What the System Does:**
- Status changes to **Rejected** (displayed as "Rejected by Facility Agent")
- The `rejectedAt` timestamp is recorded using `DateUtils.nowUTC()`
- The `rejectedBy` field stores the facility agent's user ID
- The `rejectionComments` field stores the facility agent's explanation (defaults to "No comments provided" if left blank)
- A status history entry is appended: `{ status: 'Rejected', updatedAt: timestamp, updatedBy: userId }`
- An action history entry is appended: `{ action: 'Reject', comments: 'Term sheet rejected by facility agent', metadata: { newStatus: 'Rejected' } }`
- An audit event `credit_facility.term_sheet.rejected` is emitted

**What Is Preserved:**
- The complete term sheet record remains in the database as a read-only reference
- All previously uploaded documents (collateral profile, financial statements, KYC documents, collateral data, funding sheet) remain accessible
- The full status history and action history, including all prior change request cycles (if any), are preserved
- Any signed PDF from a previous signing attempt remains stored

**What Is NOT Created:**
- No master commitment is generated
- No facility is created
- No lender groups are assembled

**What the Borrower Can Do:**
- View the rejected term sheet and its documents
- Read the rejection comments to understand why it was declined
- Create a **new term sheet** with a fresh `termSheetId` (format: `TS-MMDDYYYY-xxxx`)
- Address the issues identified in the rejection comments
- Submit the new term sheet through the standard workflow

**What the Borrower Cannot Do:**
- Edit the rejected term sheet
- Resubmit the rejected term sheet
- Appeal or reverse the rejection

### Funding Request Rejected

**Trigger:** The facility agent clicks **Reject** while reviewing a funding request in `FAReview` status.

**What the System Does:**
- Status changes to **REJECTED**
- The `rejectedAt` timestamp is recorded
- The `rejectedBy` field stores the facility agent's user ID
- The `rejectionReason` field stores the facility agent's explanation
- A status history entry is appended: `{ status: 'REJECTED', updatedAt: timestamp, updatedBy: userId }`
- An action history entry is appended: `{ action: 'Reject', comments: rejectionReason || 'Funding request rejected by market maker', metadata: { newStatus: 'REJECTED', rejectionReason: rejectionReason } }`
- An audit event `credit_facility.funding_request.rejected` is emitted with summary: "Funding request {id} rejected and closed; no further changes allowed"
- A notification is sent to the borrower's organization confirming the rejection

**Status Validation:**
The system enforces that only funding requests in `FAReview` status can be rejected. If the request is already `REJECTED`, the system returns an informational response with the existing rejection details (status, `rejectedAt`, `rejectedBy`, `rejectionReason`) instead of re-processing.

**What Is Preserved:**
- The complete funding request record, including `preFilledData`, `userData`, `collateralAddendum`, and `collateralAddendumHistory`
- The full `actionHistory` and `statusHistory` arrays
- The `fundingRequestId` for reference

**What Is NOT Created:**
- No funding notice is generated
- No tokens are minted
- No e-signatures are initiated

**What the Borrower Can Do:**
- View the rejected funding request and its documents
- Read the rejection reason
- Create a **new funding request** with a fresh `fundingRequestId` (format: `FR-MMDDYYYY-xxxx`)
- Adjust the draw amount, documentation, or other parameters
- Submit the new request through the standard workflow

**What the Borrower Cannot Do:**
- Edit the rejected funding request
- Resubmit the rejected funding request
- Appeal the rejection

### Pool Mandate Rejected

**Trigger:** A market maker declines to structure the deal during the pool mandate review process.

**What Happens:**
- The market maker indicates they will not take on the mandate
- The pool remains in the system and is not deleted or archived

**What the Issuer Can Do:**
- View the pool and all associated loans
- Submit the pool to a **different market maker** for mandate consideration
- Make improvements to the pool (add or remove loans, update documentation, address the market maker's feedback) before resubmitting
- Share the pool directly with investors if the issuer has that capability

**What the Issuer Cannot Do:**
- Force the original market maker to reconsider
- Automatically transfer the mandate rejection feedback to a new market maker

### Loan Removal Request Rejected (by Issuer)

**Trigger:** A market maker or investor requests removal of a specific loan from a pool, and the issuer clicks the **cross icon** (reject removal).

**What Happens:**
- The loan remains in the pool
- The loan continues to be included in all pool calculations (amortization, collateral, etc.)
- The loan retains its current status (it is not marked as "Removed")

**What This Means:**
This is the only "rejection" scenario in Intain Markets where rejection is not a negative outcome for the submitter of the original item. Here, the issuer is rejecting the removal request, which means the loan stays in the pool — the issuer's preferred outcome. The market maker or investor who requested the removal can continue to provide feedback through the feedback module but cannot force the removal.

### Lender Approval Status Rejected (Funding Notice)

**Trigger:** A lender's approval status on a funding notice token distribution entry is set to `REJECTED`.

**What Happens:**
- The specific lender's `lenderApprovalStatus` in the `tokenDistribution` array is updated to `REJECTED`
- The `lenderApprovalStatusAt` and `lenderApprovalStatusBy` fields are recorded
- An action history entry with `action: 'LENDER_STATUS_UPDATED'` is appended
- A status history entry for the specific `lenderOrgId` is recorded

**What This Means:**
This rejection is scoped to a single lender's participation in a specific funding notice. It does not affect other lenders in the same funding notice or the overall funding notice status.

## Rejection vs Change Request — Summary

| Aspect | Rejection | Change Request |
|--------|-----------|----------------|
| **Final?** | Yes — cannot be undone | No — item returns to submitter |
| **Editable?** | No — becomes read-only | Yes — submitter can modify |
| **Resubmit same item?** | No — must create new item | Yes — edit and resubmit |
| **Status** | `Rejected` / `REJECTED` | `CHANGES_REQUESTED` |
| **Version snapshot?** | No — single final state | Yes — snapshot preserved per change request |
| **Audit trail** | Recorded with rejection reason/comments | Recorded with change request details |
| **Downstream items created?** | No (no master commitment, no funding notice, no tokens) | Not yet — created only upon eventual approval |

## Next Steps for Users

### For Borrowers (Term Sheets)

1. **Review the rejection comments** — Open the rejected term sheet and read the `rejectionComments` field. These comments explain what was unacceptable about the proposal.
2. **Assess feasibility** — Determine whether the issues can be addressed. If the rejection was due to eligibility or structural concerns, consult with the facility agent before creating a new term sheet.
3. **Create a new term sheet** — Navigate to Credit Facility and initiate a new term sheet. The system generates a fresh `termSheetId`. Fill in the facility terms, addressing the issues from the rejection.
4. **Upload updated documentation** — Provide updated collateral profiles, financial statements, and KYC documents if the rejection was documentation-related.
5. **Sign and submit** — Complete the e-signature (Create Draft → Adobe Sign) and submit for facility agent review.

### For Borrowers (Funding Requests)

1. **Review the rejection reason** — Open the rejected funding request and read the `rejectionReason` field.
2. **Adjust parameters** — If the rejection was due to the draw amount exceeding capacity, reduce the amount. If it was due to timing, adjust the funding date. If documentation was insufficient, prepare additional collateral.
3. **Create a new funding request** — Navigate to the master commitment and create a new funding request with a fresh `fundingRequestId`.
4. **Verify before submitting** — Ensure the request fits within the available borrowing capacity and all required documents are attached.
5. **Submit for review** — The new request will enter `FAReview` status for the facility agent.

### For Issuers (Pool Mandates)

1. **Review market maker feedback** — Read any comments or feedback the market maker provided via the feedback module.
2. **Evaluate alternatives** — Decide whether to submit to a different market maker or to improve the pool first.
3. **Improve the pool** — If needed, add stronger loans, remove problematic loans, or update supporting documentation.
4. **Resubmit or share** — Share the improved pool with a new market maker for mandate consideration.

## Key Points

- **Rejection is final and irreversible** for the specific item — there is no appeal process, undo capability, or administrative override
- **Create new items to try again** — the platform always allows submitters to create fresh items
- **Rejection reasons are permanently recorded** — they serve as a learning tool and are part of the audit trail
- **Rejected items remain visible** as read-only records, ensuring full traceability and reference for future submissions
- **Notifications are sent** — borrowers and issuers receive real-time (SSE) and/or email notifications when rejections occur
- **Status history is preserved** — even if an item went through multiple change request cycles before being rejected, the entire history is maintained
