---
title: Repayment Initiation
description: Task-based guide for issuers to initiate repayment on active asset sale deals
---

# Repayment Initiation

## Overview

This guide provides issuers with step-by-step instructions for initiating repayment on an active asset sale deal. When borrowers make payments on the underlying loans, the issuer uploads the latest loan tape, initiates repayment via bank wire, and submits the repayment for investor confirmation. This covers all issuer-side tasks in the repayment phase.

## Who Can Use This

- **Issuers**: All steps in this guide are performed by the issuer role

## When This Is Used

Use this guide when:
- Borrowers have made payments on the underlying loans
- You need to pass through repayment funds to investors
- An active deal requires repayment processing
- You want to initiate a full or partial repayment on a deal

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

### Step 3: Map Loan Tape Fields

1. After upload, the field mapping interface appears
2. Map each column in your loan tape to the platform's expected fields
3. Verify the field mapping is correct
4. Click **Save Mapping** to confirm

> **Tip:** If you need assistance preparing the loan tape, Intain support can guide you through updating the loan tape in Excel before upload.

### Step 4: Initiate the Repayment

1. Click **Initiate Repayment** from the deal operations menu
2. The repayment initiation wizard opens

### Step 5: Select Payment Rail

1. Choose **Bank Wire** as the payment rail
2. Bank wire is the currently supported off-chain payment method
3. Click **Next** to continue

### Step 6: Configure Repayment Details

Review and complete the repayment information:

1. **Repayment Type**: Auto-calculated based on the uploaded loan tape
   - **Full**: Entire outstanding balance is being repaid
   - **Partial**: A portion of the outstanding balance is being repaid
2. **Repayment Date**: Enter the date of the repayment
3. **Repayment Amount**: Auto-calculated from the loan tape — verify this amount
4. **Memo**: Add any relevant notes about the repayment
5. **Wire Confirmation Document**: Upload the bank wire confirmation document as proof of transfer
6. Click **Next** to proceed to the review step

> **Important:** The repayment amount and repayment type are automatically calculated from the uploaded loan tape data. Always verify these values match your actual wire transfer before submitting.

### Step 7: Review and Submit

1. Review all repayment details on the confirmation screen:
   - Repayment type (Full/Partial)
   - Repayment amount
   - Repayment date
   - Wire confirmation document
   - Memo
2. Click **Confirm** to submit the repayment
3. The deal status changes to **Repayment In Progress**
4. Investors are notified that repayment has been initiated

### Step 8: Monitor Investor Confirmation

1. After submission, monitor the investor confirmation status in the deal details
2. Each investor will review and confirm receipt of the repayment
3. Once all investors confirm, the deal is ready for NFT burn and closure

## Rules & Validations

- Repayment can only be initiated on deals in **Active** status
- A loan tape must be uploaded and field mapping saved before initiating repayment
- The repayment amount is derived from the loan tape and cannot be manually overridden
- A wire confirmation document is required for submission
- Only one repayment can be in progress at a time per deal
- The payment rail is limited to bank wire (off-chain transaction)

## What Happens Next

After you submit the repayment:
- The deal status changes to **Repayment In Progress**
- Investors review the repayment details and confirm receipt
- After confirmation, investors burn their receivables NFTs
- The deal status changes to **Closed** once burn is complete
- See **Repayment Flow** (article 37) for the complete end-to-end process
