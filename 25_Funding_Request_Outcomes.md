---
title: Funding Request Outcomes
description: Understand all possible outcomes after a funding request is reviewed, including approval, rejection, changes requested, and cancellation
---

# Funding Request Outcomes

## Overview

When a borrower submits a funding request, the facility agent reviews it and makes a decision. That decision sets the next step for the borrower and for the funding notice. This guide explains each outcome, the status you will see, and what you can do next.

The facility agent can **Approve**, **Reject**, or **Request Changes**. The borrower can also **Cancel** a request before a decision is made.

## Possible Outcomes

After a funding request is in review, these outcomes are possible:

| Outcome | Status | Final? | Funding Notice Created? |
|---------|--------|--------|-------------------------|
| **Approved** | **Approved**, then a funding notice is created | No. Settlement still follows. | Yes. It is created automatically. |
| **Rejected** | **Rejected** | Yes | No |
| **Changes Requested** | **Changes Requested** | No. The borrower can edit and resubmit. | No |
| **Cancelled** | **Cancelled** | Yes | No |

![Funding Request Review - FA](images/25-funding-request-outcomes/review_funding_request_FAReview.png)

## What Each Outcome Means

### Approved

**What it means:**
The facility agent has accepted the drawdown. The funding process continues from here.

**Status change:**
The funding request status changes to **Approved**. A funding notice is created right away.

**What happens next:**

1. **Funding notice created** — The notice lists each lender's share, based on that lender's commitment. The notice starts as **Pending token generation**.

2. **Facility agent approves the funding notice** — The facility agent reviews the notice and clicks **Approve**.

3. **Facility agent signs for each lender** — The action shows **E-sign (0/n)**. The number n is the count of lenders. It updates as each signature is completed, through **E-sign (n/n)**.

4. **Lenders see the notice** — A lender can open the funding notice after the signature for that lender is done. They do not wait for every other lender.

5. **Lenders send funds** — Each lender checks the amount and their share, sends the funds by bank wire, and clicks **Confirm and Settle** with the wire reference and confirmation document.

6. **Settlement completes** — As lenders confirm, the notice moves through **Partially Settled** to **Settled**. The borrower receives the funds.

**What you can see after approval:**
- Who approved the request, and when
- Any approval comments
- The funding notice and how far settlement has progressed

### Rejected

**What it means:**
The facility agent has declined the request and must give a reason.

**Status change:**
The status changes to **Rejected**. You cannot edit, resubmit, or reopen this request.

**What happens next:**

1. **Read the reason** — See which requirement was not met.

2. **Capacity is released** — Amount that was held for this request returns to the amount you can still borrow.

3. **Create a new request** — Start a new funding request that addresses the reason. The rejected request stays in your history so you can refer to it.

**What you can see after rejection:**
- Who rejected the request, and when
- The rejection reason
- The original request details

### Changes Requested

**What it means:**
The facility agent needs changes before they can approve. This is not a rejection. They describe what to update.

**Status change:**
The status changes to **Changes Requested**. You can edit the request and submit it again.

**What happens next:**

1. **Read the comments** — They may ask you to change the amount, the documents, the purpose, or another field.

2. **Edit the request** — You can change the amount, purpose of funds, funding date, and supporting documents.

3. **Resubmit** — Submit the update. The status returns to **In review (facility agent)**.

4. **Wait for a new decision** — The facility agent may approve, reject, or ask for more changes. The cycle can repeat.

**What you can see after changes are requested:**
- Who asked for the changes, and when
- The comments that describe the changes
- The request fields, which you can edit again

### Cancelled

**What it means:**
The borrower cancelled the request before a decision. This is used when the draw is no longer needed, or when you want to start again with different details.

**Status change:**
The status changes to **Cancelled**. You cannot reopen it.

**When you can cancel:**
- The request is still **Draft** and has not been submitted
- The request is **Changes Requested** and you have not resubmitted it

**What happens after cancellation:**
- Any held capacity returns to the amount you can still borrow
- The cancelled request stays in your history
- You can create a new funding request if you still need funds

## Complete Status Flow

```
Draft → Submit → In review (facility agent) → Approved → funding notice created → Partially Settled → Settled
                                               ↘ Rejected (final)
                                               ↘ Changes Requested → Edit → Resubmit → In review (facility agent)

Draft → Cancel → Cancelled (final)
Changes Requested → Cancel → Cancelled (final)
```

## Capacity Tracking Across Outcomes

The facility tracks how much you can still borrow:

| Event | Capacity impact |
|-------|-----------------|
| Funding request submitted | The amount is **held** and set aside |
| Approved | The held amount becomes **used** |
| Rejected | The held amount is **released** |
| Cancelled | The held amount is **released** |
| Changes Requested | The amount stays **held** while you edit |

**Available capacity** is the total commitment, minus the amount already used, minus the amount currently held.

## Summary

| Outcome | Status | Funding Notice | Capacity | Next Steps |
|---------|--------|----------------|----------|------------|
| Approved | **Approved**, then a funding notice is created | Created automatically | Becomes used | Facility agent signs for each lender. Lenders send funds. |
| Rejected | **Rejected** | Not created | Released | Create a new request |
| Changes Requested | **Changes Requested** | Not created | Stays held | Edit and resubmit |
| Cancelled | **Cancelled** | Not created | Released | Create a new request if you still need funds |

## Next Steps for Users

**For approved requests:**
- Follow the funding notice through signatures and lender settlement
- Funds are paid after the lenders click **Confirm and Settle**

**For rejected requests:**
- Read the rejection reason
- Create a new request that fixes the issues
- Check capacity and documents before you submit again

**For change requests:**
- Address every comment
- Check the edited fields before you resubmit
- The review can repeat if something is still missing

**For cancelled requests:**
- Confirm that you meant to cancel. You cannot undo it.
- Create a new request if you still need the funds
