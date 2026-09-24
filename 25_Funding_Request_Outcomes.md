---
title: Funding Request Outcomes
description: >-
  All possible outcomes after a funding request is reviewed — approval, rejection, changes requested, and cancellation
---

# Funding Request Outcomes

## Summary

| Outcome | Status | Final? | Funding notice created? | Capacity impact |
|---|---|---|---|---|
| **Approved** | Approved | No — settlement follows | Yes, automatically | Amount becomes **used** |
| **Rejected** | Rejected | Yes | No | Amount **released** |
| **Changes Requested** | Changes Requested | No — edit and resubmit | No | Amount stays **held** |
| **Cancelled** | Cancelled | Yes | No | Amount **released** |

![Funding Request Review - FA](<.gitbook/assets/review_funding_request_FAReview (1).png>)

## What Happens for Each Outcome

### Approved

1. Funding notice created with status **Pending Token Generation**
2. Facility agent approves notice → tokens created
3. Facility agent e-signs for each lender (**E-sign 0/n → n/n**)
4. Each lender sees notice after their signature is done
5. Lenders send funds and click **Confirm and Settle** → notice moves to **Settled**

### Rejected

- Status → **Rejected** (final); rejection reason saved
- Cannot be edited or resubmitted
- **Next:** Read the reason → create a new funding request addressing the issue

### Changes Requested

- Status → **Changes Requested**; facility agent's comments saved
- Edit the request (amount, date, purpose, documents) → resubmit → back to **In review**
- Cycle can repeat until approved or rejected

### Cancelled

Can cancel when status is **Draft** or **Changes Requested** (before resubmission).

- Status → **Cancelled** (final); cannot be reopened
- **Next:** Create a new funding request if still needed

## Capacity Flow

```
Submitted → amount held
Approved → amount becomes used
Rejected / Cancelled → amount released back to available capacity
```

**Available capacity = total commitment − used − held**

→ See [Funding Request Review (Facility Agent)](54_Funding_Request_Review_MM.md) for the reviewer's perspective.
→ See [Token Approval](45_Token_Approval.md) for what happens after approval.
