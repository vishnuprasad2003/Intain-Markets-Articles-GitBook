---
title: Repayment Initiation
description: Complete task-based guide for issuers to initiate repayment — covering the four-step wizard, payment rail selection, repayment type cards, amount validation, wire reference, document upload, and confirmation flow
---

# Repayment Initiation

## Overview

This guide provides issuers with step-by-step instructions for initiating repayment on an active asset sale deal. When borrowers make payments on the underlying loans, the issuer uploads the latest loan tape, opens the repayment modal, selects a payment rail, records payment details (type, amount, date, wire reference, wire confirmation document), reviews the summary, and confirms the repayment. This covers all issuer-side tasks in the repayment phase, including the complete four-step repayment wizard.

## Who Can Use This

- **Issuers**: All steps in this guide are performed by the issuer role

## When This Is Used

Use this guide when:
- Borrowers have made payments on the underlying loans
- You need to pass through repayment funds to investors
- An active deal requires repayment processing
- You want to initiate a full repayment, partial repayment, or declare a default on a deal

## Step-by-Step Process

### Step 1: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Locate the deal in **Active** status that requires repayment
3. Click on the **Deal ID** to open the deal details page

### Step 2: Upload the Latest Loan Tape

1. Navigate to **Deal Operations** within the deal details
2. Click **Edit Loan Tape**
3. Select the loan tape file to upload (Excel format)
4. Select the **As Of Date** for the loan tape data
5. Click **Upload** to begin the upload process
6. After upload, the field mapping interface appears — map each column to the platform's expected fields
7. Verify the field mapping and click **Save Mapping** to confirm

> **Tip:** If you need assistance preparing the loan tape, Intain support can guide you through updating the loan tape in Excel before upload.

> **For Receivables deals:** The loan tape is especially important because the repayment amount is automatically derived from the loan tape's invoice totals. The platform fetches the `currentInstance.totalPaymentAmount` from the uploaded loan tape data.

### Step 3: Open the Repayment Modal

1. Click **Initiate Repayment** from the deal operations menu
2. The repayment modal opens with a four-step wizard:
   - **Step 1: Select Rail** — Choose the payment method
   - **Step 2: Record Payment** — Enter repayment details
   - **Step 3: Review** — Review the summary before confirming
   - **Step 4: Status** — Monitor the repayment progress

A progress tracker at the top of the modal shows your current step.

### Step 4: Select Payment Rail (Wizard Step 1)

Choose your settlement rail from the available options:

| Rail | Description | Availability |
|------|-------------|--------------|
| **Kinexys** | Escrowed book-entry with on-platform confirmations | Coming soon (disabled) |
| **Stablecoin** | USDC via smart contract escrow on the configured chain (e.g., Polygon) | Coming soon (disabled) |
| **Bank (Wire/ACH)** | Traditional rails via instructions on file | **Available** |

Currently, only **Bank (Wire/ACH)** is enabled. Click the Bank card to select it and automatically advance to Step 2.

> **Note:** Hovering over disabled rails shows a tooltip: "Repayment currently supports Bank (Wire/ACH) only. Additional rails will be enabled later."

### Step 5: Record Payment Details (Wizard Step 2)

This step has two sections: **Repayment Type** and **Repayment Details**.

#### Select Repayment Type

Choose one of three repayment type cards:

| Type | Description | Effect |
|------|-------------|--------|
| **Full Repayment** | Full payment of the outstanding balance | Amount auto-populates with outstanding balance |
| **Partial Repayment** | Partial payment; remaining balance stays open | Amount field is cleared for manual entry |
| **Declare Default** | Declare default on this repayment | Amount fields are hidden; default is permanent |

> **Important:** If the outstanding balance is zero, all repayment type cards are disabled with the message: "There is nothing left to repay on this settlement."

> **Warning for Declare Default:** A permanent warning is displayed: "Declaring default is permanent. No further repayment can be recorded after this action."

#### Enter Repayment Details (for Full or Partial)

The following fields appear after selecting Full or Partial repayment:

- **Repayment Method**: Displayed as **"Bank (Wire/ACH)"** (read-only, based on the selected rail)

- **Repayment Date*** (required): Select the date of the repayment using the date picker. Format: MM/DD/YYYY. Future dates are disabled — the payment date cannot be after today.

- **Repayment Amount*** (required): 
  - For **Full Repayment**: Auto-populated with the outstanding balance. You can modify if needed.
  - For **Partial Repayment**: Enter the amount manually.
  - For **Receivables deals**: The amount is automatically fetched from the loan tape's invoice totals (`currentInstance.totalPaymentAmount`). If the loan tape amount is zero or unavailable, an error is shown: "Payment amount from the latest loan tape is 0. Re-upload the loan tape Excel and try again."
  - Accepts up to 4 decimal places. Commas are stripped automatically.
  - Validation: The amount must be greater than zero and cannot exceed the outstanding balance for full repayment.

- **Wire Reference*** (required): Enter the wire memo or transaction ID (e.g., "Wire memo or transaction ID"). This field cannot be empty.

- **Wire Confirmation Document*** (required): Upload the bank wire confirmation document as proof of transfer.
  - Click **Select document** (or **Replace document** if one is already attached) to choose a file
  - Accepted formats: PNG, JPEG, JPG, or PDF up to 10 MB
  - At least one document must be uploaded before proceeding

Click **Next** to save the payment information and proceed to the review step.

> **Validation on Next:** All fields are validated. Error tooltips appear if any required field is missing or invalid:
> - "Select a repayment type to continue."
> - "Enter a repayment amount to continue."
> - "Enter a repayment date to continue."
> - "Enter a wire reference to continue."
> - "Upload a wire confirmation document to continue."

### Step 6: Review and Confirm (Wizard Step 3)

The review screen shows a summary table:

| Item | Value |
|------|-------|
| Repayment Method | Bank (Wire/ACH) |
| Repayment Type | Full Repayment / Partial Repayment |
| Repayment Amount | $XX,XXX.XX |

Click **Review & Confirm** to open the confirmation panel.

The confirmation panel shows the complete summary:

| Item | Value |
|------|-------|
| Deal | Deal Name · Deal ID |
| Repayment Method | Bank (Wire/ACH) |
| Repayment Type | Full / Partial / Defaulted |
| Repayment Amount | $XX,XXX.XX |
| Repayment Date | MM/DD/YYYY |
| Wire Reference | [Your reference] |

The confirmation message reads: **"Confirm that funds have been sent"** with the attestation: "By confirming, you are attesting that the wire transfer has been initiated."

For Declare Default, the message reads: **"This declares default on the outstanding balance"** with bullets:
- "This repayment will be marked as Defaulted."
- "The investor will be notified to acknowledge this declaration."

Click **Confirm** to finalize the repayment submission.

### Step 7: Monitor Repayment Status (Wizard Step 4)

After confirmation, the wizard moves to the Status step:

- **Awaiting Investor Confirmation**: The repayment has been submitted and the investor needs to confirm receipt
- **Repayment Complete**: The investor has accepted the repayment
- **Default Declared**: Default has been declared (for Declare Default)
- **Installment Recorded**: A partial installment has been recorded (for partial repayments)

The modal polls the server every 10 seconds for status updates while open.

#### Partial Repayment Loop

For partial repayments, after the investor confirms receipt of an installment, a **Record Next Installment** option appears. Clicking it resets the wizard to Step 1 for the next installment, clearing all previously entered payment details. This allows the issuer to record multiple partial repayments over time.

#### Retry After Investor Rejection

If the investor rejects the repayment, the modal detects this and redirects the issuer to Step 2 (Record Payment) with a fresh form. Previously uploaded documents are cleared, and the issuer must re-enter payment details and re-upload the wire confirmation for the new attempt.

## Rules & Validations

- Repayment can only be initiated on deals in **Active** status
- A loan tape must be uploaded and field mapping saved before initiating repayment
- For Receivables deals, the repayment amount is derived from the loan tape's invoice totals and cannot be manually overridden
- A wire confirmation document (PNG, JPEG, JPG, or PDF, max 10 MB) is required for submission
- The repayment date cannot be in the future
- Only one repayment can be in progress at a time per deal
- The payment rail is limited to Bank (Wire/ACH) — Kinexys and Stablecoin are coming soon
- Declaring default is permanent — no further repayment can be recorded after default
- Idempotency keys are used to prevent duplicate submissions
- The wire reference / memo is required and cannot be empty

## What Happens Next

After you submit the repayment:
- The deal enters the **Repayment In Progress** phase
- Investors review the repayment details and can **Accept** or **Reject** the repayment
- If accepted, investors proceed to burn their receivables NFTs
- If rejected, the issuer is notified and can record a new repayment attempt
- For partial repayment, additional installments can be recorded after investor confirmation
- After full repayment confirmation and NFT burn, the deal status changes to **Closed**
- See **Repayment Receipt & NFT Burn** (article 64) for the investor's perspective
