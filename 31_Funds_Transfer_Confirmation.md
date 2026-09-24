---
title: Funds Transfer Confirmation
description: Step-by-step guide for lenders to confirm fund transfers and finish a draw
---

# Funds Transfer Confirmation

## Overview

This is the last step in a credit facility draw. After the facility agent approves a funding notice and signs for each lender, you review your portion, send the funds by bank wire, and click **Confirm and Settle**.

That click records your transfer and completes token settlement for your share. Each lender confirms on their own. The notice moves from partly settled to fully settled as lenders finish.

## Who Can Use This

Lenders who were assigned a portion of a funding notice and have sent that amount to the borrower.

## When This Is Used

Use this when:

- A funding notice exists for an approved funding request
- The facility agent has finished the e-signature for your portion
- You have checked the draw amount, your share, and the borrower’s wire instructions
- You have sent the bank wire
- You are ready to record the transfer on the platform

## Step-by-Step Process

### Step 1: Access the Funding Notice

1. Open **Credit Facility** from the left menu.
2. Find the funding notice that needs your action.
3. You see it only after the facility agent has signed for your portion.
4. Click **Review Funding Notice**.

### Step 2: Review Funding Notice Details

Check:

- **Deal Name** — The credit facility
- **Funding Request Reference** — The borrower’s original request
- **Total Drawdown Amount** — The full draw across all lenders
- **Your Allocation Amount** — Your share of the draw
- **Allocation Percentage** — Your percentage of the draw
- **Purpose of Funds** — Why the borrower requested the funds
- **Borrower Wire Transfer Details** — Bank name, account number, routing or SWIFT details, and any wire instructions
- **Payment Deadline** — Any date by which the transfer should be sent

### Step 3: Transfer Funds

1. Send a bank wire for your allocated amount, using the details on the notice.
2. Match the amount to your allocation.
3. Keep the wire reference from your bank.
4. Keep the bank’s confirmation or receipt.

### Step 4: Enter Wire Confirmation Details

1. **Payment Method** — Choose one:
   - **Bank Wire**
   - **ACH**
   - **Other**
2. **Wire Reference** — Enter the reference from your bank. This is required.
3. **Wire Confirmation Document** — Upload the bank receipt.
4. **Transfer Amount** — Confirm it matches your allocation. It may already be filled in.
5. **Transfer Date** — Enter the date you sent the transfer.

### Step 5: Click Confirm and Settle

1. Click **Confirm and Settle**.
2. Confirm if a dialog appears.
3. The platform then:
   - Changes your transfer status from **pending** to **confirmed**
   - Transfers tokens that record your participation
   - Saves a record of that transfer
   - Marks your part of the draw as finished

![Confirm and Settle - Lender](images/60-funds-transfer-confirmation-investor/ConfirmAndSettleInvestor.png)

### Step 6: Verify Settlement Completion

1. Your transfer status shows **Confirmed**.
2. A record of the transfer is shown.
3. Your portion of the draw is complete.

## Settlement Progress Tracking

| Transfer Status | Meaning |
|----------------|---------|
| **Pending** | You have not confirmed the transfer |
| **Confirmed** | You confirmed, and token settlement for your share is complete |
| **Failed** | Confirmation did not complete |

| Funding Notice Status | Meaning |
|----------------------|---------|
| **LenderReview** | Lenders can review the notice and send funds |
| **SettlementInProgress** | At least one lender has started confirmation |
| **PartiallySettled** | Some lenders have confirmed |
| **Settled** | Every lender has confirmed |

## Rules & Validations

- Click **Confirm and Settle** only after the bank wire has been sent. The click is your confirmation of that transfer.
- A wire reference is required.
- The bank confirmation document is required.
- The amount must match your allocation.
- You can open the notice only after the facility agent has signed for you.
- Your confirmation does not wait for other lenders.
- **Confirm and Settle** cannot be undone. The token transfer stays on the record.
- Each lender’s status, wire details, and transfer record are kept separately.

## What Happens Next

**After you confirm**

- Your part of the draw is complete
- Tokens that record your participation are transferred
- The borrower is notified that your funds are confirmed

**After every lender confirms**

- The funding notice becomes **Settled**
- The draw is complete
- Facility use updates to include the new draw
- The settlement stays on the record

![Confirmfundstransfer](images/31-funds-transfer-confirmation/confirmfundstransfer.png)
