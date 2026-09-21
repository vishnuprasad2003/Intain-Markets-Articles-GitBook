---
title: Funding Request Outcomes
description: Understand all possible outcomes after a funding request is reviewed, including approval, rejection, changes requested, and cancellation
---

# Funding Request Outcomes

## Overview

When a borrower submits a funding request in a credit facility, the facility agent reviews it and makes a decision. This decision determines the next steps for the borrower and the overall funding workflow. Understanding each possible outcome — what it means, what status it produces, and what actions are available afterward — is essential for all credit facility participants.

The facility agent has three decision options: **Approve**, **Reject**, or **Request Changes**. In addition, borrowers can **Cancel** a request before a decision is made. Each outcome triggers different status transitions, notifications, and follow-up actions. This guide explains every outcome in detail so you know exactly what to expect and what to do next.

## Possible Outcomes

After a funding request enters the review stage, the following outcomes are possible:

| Outcome | Status | Terminal? | Funding Notice Created? |
|---------|--------|-----------|------------------------|
| **Approved** | `APPROVED` → `FundingNoticeGenerated` | No (continues to settlement) | Yes — auto-generated |
| **Rejected** | `REJECTED` | Yes — final state | No |
| **Changes Requested** | `CHANGES_REQUESTED` | No — borrower can edit and resubmit | No |
| **Cancelled** | `CANCELLED` | Yes — final state | No |

![Funding Request Review - FA](images/25-funding-request-outcomes/review_funding_request_FAReview.png)

## What Each Outcome Means

### Approved

**What It Means:**
The facility agent has determined that your funding request meets all requirements and has approved the drawdown. The funding process proceeds automatically from this point.

**Status Change:**
Your funding request status changes to **APPROVED**, and the system immediately auto-generates a funding notice, moving the status to **FundingNoticeGenerated**.

**What Happens Next:**

1. **Funding Notice Auto-Generated** — The system automatically creates a funding notice based on your approved request. The funding notice includes lender allocations calculated from each lender's commitment percentage. The notice status starts as **PendingTokenGenerated**.

2. **Facility Agent Approves the Funding Notice** — The facility agent reviews the generated funding notice and clicks **Approve** to advance it.

3. **Facility Agent E-Signs for Each Lender** — The facility agent must individually e-sign the funding notice for each participating lender. The action displays as **E-sign (0/n)**, where n is the total number of lenders. As each lender's e-sign is completed, the counter updates: (1/n), (2/n), and so on until (n/n).

4. **Lenders See the Funding Notice** — Each lender can see and act on the funding notice only after the facility agent has completed their individual e-sign. A lender signed at step 1/3 can begin their process before lender 3/3 is signed.

5. **Lenders Transfer Funds** — Each lender reviews the funding notice, verifies the drawdown amount and their allocation, transfers funds to the borrower via bank wire, and clicks **Confirm and Settle** with their wire reference and confirmation document.

6. **Settlement Complete** — Tokens are transferred on-chain for each lender, the funding notice progresses through **PartiallySettled** to **Settled** as all lenders confirm, and the borrower receives the funds.

**Key Fields Visible After Approval:**
- Reviewer name and timestamp
- Approval comments (if any)
- Link to the generated funding notice
- Funding notice progress tracking

### Rejected

**What It Means:**
The facility agent has determined that your funding request does not meet requirements and has declined it. The facility agent must provide a rejection reason explaining why the request was not approved.

**Status Change:**
Your funding request status changes to **REJECTED**. This is a **terminal state** — the request cannot be edited, resubmitted, or reopened.

**What Happens Next:**

1. **Review the Rejection Reason** — Read the reason provided by the facility agent. Understand specifically what requirements were not met or what issues were identified.

2. **Capacity Released** — Any facility capacity that was held when the request was submitted is released back to the available pool. This means the committed amount is once again available for future requests.

3. **Create a New Request** — You must create an entirely new funding request to try again. The new request should address the issues identified in the rejection reason.

**Important:** You cannot edit or resubmit a rejected funding request. You must start fresh with a new request. The rejected request remains visible in your history for reference.

**Key Fields Visible After Rejection:**
- Reviewer name and timestamp
- Rejection reason (required, provided by facility agent)
- Original request details (preserved for reference)

### Changes Requested

**What It Means:**
The facility agent has reviewed your request and determined that it needs modifications before it can be approved. This is not a rejection — it is a request for you to update specific aspects of your submission. The facility agent provides details about what changes are needed.

**Status Change:**
Your funding request status changes to **CHANGES_REQUESTED**. This is not a terminal state — you can edit and resubmit.

**What Happens Next:**

1. **Review the Change Request Details** — Read the comments and details provided by the facility agent. Understand exactly what modifications are needed — this may include adjusting the request amount, updating documentation, changing the purpose description, or correcting other fields.

2. **Edit Your Request** — Your funding request becomes editable again. You can modify the request amount, purpose of funds, drawdown date, maturity date, supporting documents, and other fields as needed.

3. **Resubmit** — After making the requested changes, submit the updated request. The status changes back to **FAReview** and the facility agent reviews your updated submission.

4. **Await New Decision** — The facility agent reviews your resubmitted request and may:
   - **Approve** — Funding notice is auto-generated and the process proceeds
   - **Reject** — Request is declined (you must create a new one)
   - **Request More Changes** — The cycle repeats until the request is approved or rejected

**Key Fields Visible After Changes Requested:**
- Reviewer name and timestamp
- Change request details/comments (what the FA wants changed)
- Editable request fields

### Cancelled

**What It Means:**
The borrower has voluntarily cancelled the funding request before a decision was made. This can happen when the borrower no longer needs the drawdown or wants to start over with different parameters.

**Status Change:**
Your funding request status changes to **CANCELLED**. This is a **terminal state** — the request cannot be reopened.

**When Cancellation Is Available:**
- When the request is still in **Draft** status (not yet submitted)
- When the request is in **ChangesRequested** status (returned by FA but not yet resubmitted)

**What Happens After Cancellation:**
- Any held facility capacity is released back to the available pool
- The cancelled request remains in your history for reference
- You can create a new funding request if needed

## Complete Status Flow

```
Draft → Submit → FAReview → Approved → FundingNoticeGenerated → PartiallySettled → Settled
                          ↘ Rejected (terminal)
                          ↘ ChangesRequested → Edit → Resubmit → FAReview (cycle repeats)

Draft → Cancel → Cancelled (terminal)
ChangesRequested → Cancel → Cancelled (terminal)
```

## Capacity Tracking Across Outcomes

The platform tracks facility capacity throughout the funding request lifecycle:

| Event | Capacity Impact |
|-------|----------------|
| Funding request submitted | Capacity **held** (reserved from available pool) |
| Approved | Held capacity becomes **utilized** |
| Rejected | Held capacity **released** (returned to available pool) |
| Cancelled | Held capacity **released** (returned to available pool) |
| Changes Requested | Capacity remains **held** while borrower edits |

**Available Capacity** = Total Commitment − Utilized Capacity − Held Capacity

## Summary

| Outcome | Status | Funding Notice | Capacity | Next Steps |
|---------|--------|----------------|----------|------------|
| Approved | APPROVED → FundingNoticeGenerated | Auto-generated | Becomes utilized | FA e-signs per lender, lenders transfer funds |
| Rejected | REJECTED | Not created | Released | Create new request |
| Changes Requested | CHANGES_REQUESTED | Not created | Remains held | Edit and resubmit |
| Cancelled | CANCELLED | Not created | Released | Create new request if needed |

## Next Steps for Users

**For Approved Requests:**
- Monitor the funding notice progress through e-signature and lender settlement
- Track lender confirmations as they complete their fund transfers
- Funds will be disbursed after all lenders click Confirm and Settle

**For Rejected Requests:**
- Carefully read the rejection reason provided by the facility agent
- Ensure your new funding request addresses all identified issues
- Verify capacity, documentation, and request parameters before submitting again

**For Change Requests:**
- Address every change requested by the facility agent
- Double-check all modified fields before resubmitting
- The review cycle may repeat — provide thorough and complete information to minimize back-and-forth

**For Cancelled Requests:**
- Review whether a new request is needed
- Verify that cancellation was intentional, as it cannot be undone
