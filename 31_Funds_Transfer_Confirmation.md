---
title: Funds Transfer Confirmation
description: How lenders confirm fund transfers and complete a draw
---

# Funds Transfer Confirmation

After the facility agent signs for your portion of a funding notice, send the bank wire and click **Confirm and Settle** to complete your share of the draw.

## Steps

1. **Credit Facility** → find the funding notice → **Review Funding Notice**
   (visible only after the facility agent has signed for your portion)
2. Check notice details:
   - Your **Allocation Amount** and **Allocation Percentage**
   - **Borrower Wire Transfer Details** (bank, account, SWIFT/routing)
   - **Purpose of Funds**, **Payment Deadline**
3. **Send the bank wire** for your allocated amount
4. Fill in:
   - **Payment Method** — Bank Wire / ACH / Other
   - **Wire Reference** (required)
   - **Wire Confirmation Document** (upload bank receipt)
   - **Transfer Amount** — must match your allocation
   - **Transfer Date**
5. Click **Confirm and Settle** → confirm if prompted → token settlement for your share is recorded

![Confirm and Settle - Lender](.gitbook/assets/ConfirmAndSettleInvestor.png)
![Confirmfundstransfer](.gitbook/assets/confirmfundstransfer.png)

## Settlement Statuses

| Your transfer status | Meaning |
|---|---|
| **Pending** | Not yet confirmed |
| **Confirmed** | Transfer recorded; your tokens settled |
| **Failed** | Confirmation did not complete |

| Funding notice status | Meaning |
|---|---|
| **LenderReview** | Lenders reviewing; funds not yet sent |
| **SettlementInProgress** | At least one lender started confirmation |
| **PartiallySettled** | Some lenders confirmed |
| **Settled** | All lenders confirmed; draw complete |

## Key Rules

- Click **Confirm and Settle** only after the wire has been sent — it records an irrevocable confirmation
- Wire reference and bank confirmation document are both required
- Each lender's confirmation is independent — you do not wait for other lenders
- The action cannot be undone
