---
title: Feedback vs Rejection
description: Understand the fundamental difference between change requests (feedback) and rejections across all review workflows in Intain Markets
---

# Feedback vs Rejection

## Overview

During any review workflow in Intain Markets — whether it involves term sheets, funding requests, pool mandates, or loan-level comments — reviewers have the ability to either request changes or reject the item outright. These two actions look similar on the surface, but they have fundamentally different consequences for the item's lifecycle, editability, and the submitter's available next steps. Understanding this distinction is critical for both reviewers (who must choose the right action) and submitters (who must respond appropriately).

## Frequently Asked Questions

### Q: What is the core difference between a change request and a rejection?

**A:** A **change request** (also called feedback) keeps the workflow alive. The item returns to an editable state, the submitter can modify it to address the reviewer's comments, and they can resubmit it for another review cycle. A **rejection** permanently closes the workflow for that specific item. The item becomes read-only, cannot be edited or resubmitted, and the submitter must create an entirely new item to try again.

Think of it this way: a change request says "this needs adjustments before I can approve it," while a rejection says "this cannot be approved — start over."

### Q: How do I know which action was taken on my item?

**A:** The item's status field tells you exactly what happened:

| Status | Meaning | Your Options |
|--------|---------|--------------|
| `CHANGES_REQUESTED` | Reviewer asked for modifications | Edit and resubmit |
| `Rejected` / `REJECTED` | Reviewer permanently declined | Create a new item |

Both actions include comments or a reason from the reviewer. Always read these carefully — for change requests, the comments tell you what to fix; for rejections, the comments explain why and help you avoid the same issues in a new submission.

### Q: Where does feedback vs rejection apply in the platform?

**A:** The pattern applies across multiple modules:

**Term Sheets (Facility Agent Review)**

When a borrower submits a term sheet and it reaches `PENDING_REVIEW` status, the facility agent has three options:

- **Approve** → Status changes to `APPROVED`, master commitment is auto-created
- **Request Changes** → Status changes to `CHANGES_REQUESTED`. The system generates a change request record with a unique ID in the format `CR-{termSheetId}-{sequenceNumber}`. The current term sheet state is captured as a version snapshot (including `revisionNumber`, `signerStatus`, `signedPdf`, and all documents). The borrower's signing status is reset (`signerStatus: 'Pending'`, `docusignStatus: 'Reset - Must Re-sign'`), meaning the borrower must re-sign after making changes. The borrower can edit the term sheet and resubmit it, returning it to `PENDING_REVIEW`.
- **Reject** → Status changes to `Rejected`. The `rejectedAt`, `rejectedBy`, and `rejectionComments` fields are recorded. The term sheet is permanently closed — the borrower must create a new term sheet. No master commitment is created.

**Funding Requests (Facility Agent Review)**

When a borrower submits a funding request and it reaches `FAReview` status, the facility agent has three options:

- **Approve** → Status changes to `APPROVED`, funding notice auto-generated
- **Request Changes** → Status changes to `CHANGES_REQUESTED`. A change request is created with ID format `CR-{fundingRequestId}-{sequenceNumber}`. A version snapshot is preserved. The borrower can edit and resubmit the funding request, which returns to `FAReview`.
- **Reject** → Status changes to `REJECTED`. The `rejectedAt`, `rejectedBy`, and `rejectionReason` fields are recorded. The funding request is permanently closed with an audit event noting "rejected and closed; no further changes allowed." The borrower must create a new funding request. No funding notice is created.

**Pool Mandates (Market Maker / Investor)**

Pool-level feedback works differently from the term sheet and funding request patterns:

- **Feedback** — Market makers and investors can use the **Feedback** module to add comments on pools, loans, batches, and data room documents. This is a cross-entity messaging system (`/api/v2/feedback`) with full CRUD operations (create, read, update, delete), unread tracking, and bulk mark-as-read capability. Comments are visible to the issuer who can view and respond. The pool continues in its workflow.
- **Mandate Rejection** — When a market maker rejects a mandate, the pool can be submitted to another market maker, or the issuer can make improvements and resubmit.

**Loan-Level Feedback**

At the loan level within a pool review:

- **Loan Comments** — Market makers and investors can add feedback on individual loans using the chat/comment functionality. These comments are stored via the feedback module and support unread tracking. The loan remains in the pool.
- **Loan Removal Request** — A market maker or investor can request removal of a specific loan. The issuer sees the request and can accept (tick icon — loan status changes to `Removed`) or reject (cross icon — loan stays in the pool and remains in calculations).

### Q: What happens to the data when changes are requested vs when an item is rejected?

**A:**

| Aspect | Change Request | Rejection |
|--------|---------------|-----------|
| **Item editability** | Yes — status allows editing | No — item becomes read-only |
| **Can resubmit same item?** | Yes — submitter modifies and resubmits | No — must create a new item |
| **Status** | `CHANGES_REQUESTED` | `Rejected` / `REJECTED` |
| **Reviewer comments** | Stored as part of the change request record with a versioned snapshot | Stored as `rejectionReason` or `rejectionComments` |
| **Version history** | Each change request creates a numbered snapshot (version, timestamp, documents, status) | No versioning — single final state |
| **Workflow continuation** | Returns to reviewer after resubmission (e.g., back to `FAReview` or `PENDING_REVIEW`) | Workflow terminates for this item |
| **Audit trail** | `actionHistory` and `statusHistory` updated with change request details | `actionHistory` and `statusHistory` updated with rejection details |
| **E-signature impact** | For term sheets: signer status is reset — must re-sign after changes | Not applicable — no further signing |

### Q: Can a rejection be appealed or reversed?

**A:** No. Rejection is a final, irreversible decision in Intain Markets. There is no appeal mechanism, undo button, or administrative override. The rejected item remains in the system as a read-only record for reference, but it cannot be reactivated. The submitter's only option is to create a new item that addresses the issues identified in the rejection reason.

### Q: How should I respond when changes are requested?

**A:**

1. **Read the reviewer's comments carefully** — The change request record includes specific comments from the reviewer about what needs to be modified
2. **Review the version snapshot** — The system preserves a snapshot of your item's state at the time the change request was made, so you can see exactly what the reviewer saw
3. **Make all requested changes** — Edit the item to address every point raised by the reviewer
4. **Re-sign if required** — For term sheets, your signer status is reset to `Pending`, so you must re-sign the updated document before resubmitting
5. **Resubmit** — Submit the updated item, which returns to the review queue (e.g., `FAReview` or `PENDING_REVIEW`)
6. **Be prepared for iteration** — The reviewer may request additional changes if the modifications are not satisfactory, creating another change request with an incremented sequence number

### Q: How should I respond when my item is rejected?

**A:**

1. **Read the rejection reason** — Stored in `rejectionReason` (funding requests) or `rejectionComments` (term sheets)
2. **Understand the root cause** — Determine whether the rejection was due to eligibility, terms, documentation, or capacity issues
3. **Create a new item** — Start fresh with a new term sheet, funding request, or other applicable item
4. **Address all issues** — Incorporate the feedback from the rejection into your new submission
5. **Submit the new item** — Follow the standard submission process; the new item goes through the same review workflow independently

### Q: How does loan removal feedback differ from other feedback?

**A:** Loan removal is a special case. Unlike change requests on term sheets or funding requests, a loan removal request does not change the loan's status to `CHANGES_REQUESTED`. Instead, the issuer receives a binary accept/reject decision:

- **Accept removal (tick)** — The loan is marked as `Removed` and excluded from pool calculations going forward
- **Reject removal (cross)** — The loan remains in the pool and continues to be included in all calculations

This mechanism exists to give market makers and investors the ability to flag specific loans they find unsuitable, while preserving the issuer's authority over the final pool composition.

### Q: Is there a limit to how many times changes can be requested?

**A:** There is no hard limit on the number of change request cycles. Each change request increments the sequence number (`CR-{id}-1`, `CR-{id}-2`, `CR-{id}-3`, etc.) and creates a new version snapshot. However, repeated change request cycles should be a signal to both parties that a more substantive conversation may be needed before resubmission.
