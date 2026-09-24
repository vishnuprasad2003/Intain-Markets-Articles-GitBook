---
title: Funds Transfer Confirmation
description: >-
  Step-by-step guide for lenders to confirm fund transfers, complete settlement,
  and finalize drawdown participation
---

# Funds Transfer Confirmation

## Overview

Funds transfer confirmation is the final step in the credit facility drawdown process where lenders confirm they have transferred funds to the borrower. After the facility agent has approved a funding notice and completed e-signatures for each lender, each lender reviews the notice, transfers their allocated portion via bank wire, and clicks **Confirm and Settle** to finalize their participation. This action triggers a blockchain token transfer that records the lender's commitment on-chain, completing the settlement for that lender.

Each lender confirms their transfer independently — one lender's confirmation does not affect or depend on other lenders. The funding notice tracks settlement progress across all participating lenders, moving from partially settled to fully settled as each lender completes their confirmation.

## Who Can Use This

* **Lenders** who have been assigned a portion of a funding notice and have completed their fund transfer to the borrower

## When This Is Used

Use fund transfer confirmation when:

* A funding notice has been generated from an approved funding request
* The facility agent has completed the e-signature for your portion of the funding notice (your e-sign status shows as signed)
* You have reviewed the funding notice details and verified the drawdown amount, your allocation, and the borrower's wire instructions
* You have completed the off-chain bank wire transfer to the borrower
* You are ready to finalize your participation in the drawdown by recording the transfer on the platform

## Step-by-Step Process

### Step 1: Access the Funding Notice

1. Navigate to **Credit Facility** from the left sidebar menu
2. Locate the funding notice that requires your action
3. The funding notice becomes visible to you only after the facility agent has completed the e-signature for your portion
4. Click **Review Funding Notice** to open the funding notice details

### Step 2: Review Funding Notice Details

Before transferring funds, carefully review all the details presented in the funding notice:

* **Deal Name** — The name of the credit facility deal
* **Funding Request Reference** — Reference to the original funding request from the borrower
* **Total Drawdown Amount** — The total amount being drawn down across all lenders
* **Your Allocation Amount** — Your specific portion of the drawdown, calculated based on your commitment percentage
* **Allocation Percentage** — Your percentage share of the total drawdown
* **Purpose of Funds** — The stated purpose for which the borrower is requesting funds
* **Borrower Wire Transfer Details** — The borrower's bank information for the wire transfer, including:
  * Bank name
  * Account number
  * Routing/SWIFT details
  * Any specific wire instructions
* **Payment Deadline** — Any applicable timeline for completing the transfer

### Step 3: Transfer Funds Off-Chain

1. Using the borrower's wire transfer details from the funding notice, initiate a bank wire transfer for your allocated amount
2. Ensure the transfer amount matches your allocation exactly
3. Record the wire reference number from your bank — you will need this in the next step
4. Retain the wire confirmation document from your bank (transfer receipt or confirmation)

### Step 4: Enter Wire Confirmation Details

After completing the bank wire transfer, return to the platform to record the transfer details:

1. **Payment Method** — Select your payment method. The platform supports the following options:
   * **Bank Wire** — Standard bank wire transfer (most common)
   * **ACH** — Automated Clearing House transfer
   * **Other** — Other payment methods as applicable
2. **Wire Reference** — Enter the wire transfer reference number from your bank. This is a required field that uniquely identifies your transfer.
3. **Wire Confirmation Document** — Upload your bank's wire confirmation document (transfer receipt). This serves as proof of transfer.
4. **Transfer Amount** — Verify the transfer amount matches your allocation. This field may be pre-filled with your allocation amount.
5. **Transfer Date** — Enter or confirm the date the transfer was completed.

### Step 5: Click Confirm and Settle

1. After entering all wire confirmation details, click **Confirm and Settle**
2. A confirmation dialog may appear — confirm your action
3. The platform records your confirmation and initiates the following:
   * Your **transfer status** changes from **pending** to **confirmed**
   * A **blockchain token transfer** is initiated — Fungible Tokens (FT) representing your participation are transferred on-chain
   * The **blockchain transaction hash** is recorded for your transfer
   * Your participation in the drawdown is officially finalized

![Confirm and Settle - Lender](.gitbook/assets/ConfirmAndSettleInvestor.png)

### Step 6: Verify Settlement Completion

After confirming:

1. Your transfer status shows as **Confirmed** in the funding notice
2. The blockchain transaction hash is displayed, providing an immutable record of the settlement
3. Your portion of the drawdown is complete

## Settlement Progress Tracking

The funding notice tracks overall settlement progress across all participating lenders:

| Transfer Status | Meaning                                                            |
| --------------- | ------------------------------------------------------------------ |
| **Pending**     | Lender has not yet confirmed their fund transfer                   |
| **Confirmed**   | Lender has confirmed the transfer and token settlement is complete |
| **Failed**      | Transfer confirmation encountered an issue                         |

### Funding Notice Status Progression

As lenders confirm their transfers, the funding notice status updates:

| Funding Notice Status    | Meaning                                                                 |
| ------------------------ | ----------------------------------------------------------------------- |
| **LenderReview**         | Funding notice is available for lenders to review and transfer funds    |
| **SettlementInProgress** | At least one lender has started the confirmation process                |
| **PartiallySettled**     | Some lenders have confirmed but not all                                 |
| **Settled**              | All lenders have confirmed their transfers — drawdown is fully complete |

## Rules & Validations

* **Confirm After Transfer** — Only click Confirm and Settle after you have actually completed the bank wire transfer. This action is recorded as a legal confirmation of fund transfer.
* **Wire Reference Required** — You must provide a valid wire reference number before confirming.
* **Wire Confirmation Document Required** — Upload the bank confirmation document before confirming.
* **Amount Must Match** — The transfer amount must match your allocated portion of the drawdown.
* **E-Sign Must Be Complete** — You can only see and act on a funding notice after the facility agent has completed the e-signature for your portion.
* **Individual Confirmation** — Each lender confirms their transfer independently. Your confirmation does not affect or wait for other lenders.
* **Confirmation Is Final** — Once you click Confirm and Settle, the action cannot be reversed. The blockchain token transfer is permanent.
* **Tracked Separately** — Each lender's confirmation is tracked independently with its own transfer status, wire details, and blockchain transaction hash.

## What Happens Next

**After You Confirm:**

* Your participation in the drawdown is marked complete
* Fungible Tokens are transferred on-chain, recording your participation on the blockchain
* The borrower is notified that your funds have been confirmed

**After All Lenders Confirm:**

* The funding notice status changes to **Settled**
* The borrower has received funds from all participating lenders
* The drawdown is fully complete
* Facility utilization is updated to reflect the new drawdown
* The transaction is permanently recorded on the blockchain with all settlement details

![Confirmfundstransfer](.gitbook/assets/confirmfundstransfer.png)
