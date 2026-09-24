---
title: Funding Request Review (Facility Agent)
description: >-
  How facility agents review, evaluate, and decide on funding requests submitted by borrowers
---

# Funding Request Review (Facility Agent)

Review a funding request when status is **In review (facility agent)**.

## Access the Request

1. **Credit Facility → Active Facilities** → open master commitment
2. Find the funding request with status **In review (facility agent)**
3. Click **Review Funding Request**

## What to Check

| Area | What to verify |
|---|---|
| **Draw amount** | Fits available borrowing capacity |
| **Funding date** | Matches facility terms |
| **Purpose of funds** | Stated and acceptable |
| **Advance rate** | Draw stays within approved rate |
| **Documents** | Collateral addendum, supporting files, funding sheet provided |
| **Lenders** | Participating lenders and their shares look correct |
| **History** | If resubmitted, confirm borrower addressed earlier comments |

## Decisions

### Approve

**Outcome:** Status → **Approved**; funding notice created automatically with status **Pending Token Generation**; borrower notified.

**What happens next:**
1. Click **Approve** on the funding notice → tokens generated
2. Borrower approves token transfer
3. Facility agent signs for each lender (**E-sign 0/n → n/n**)
4. Each lender confirms payment and settles

### Reject

**Outcome:** Status → **Rejected** (final); rejection reason saved; borrower must create a new funding request.

- Enter a rejection reason (required)
- Rejected requests are view-only and cannot be resubmitted

### Request Changes

**Outcome:** Status → **Changes Requested**; borrower edits and resubmits; returns to **In review (facility agent)** after resubmission.

- Enter comments describing what must change
- Each round is saved in the request history

## Key Rules

- Only facility agents can approve, reject, or request changes
- You can only act while status is **In review (facility agent)**
- Rejection is final — borrower must create a new request
- Approving does not require a signature (signatures happen on the funding notice)
- The funding notice is created automatically on approval; you do not create it manually

→ See [Funding Requests](44_Funding_Requests.md) for the borrower's submission process.
→ See [Feedback vs Rejection](73_Feedback_vs_rejection.md) for the difference between changes requested and rejection.
