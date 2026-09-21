---
title: Repayment Flow
description: Step-by-step guide for the asset sale repayment process from issuer to investor
---

# Repayment Flow

## Overview

The repayment flow is the post-sale process where the issuer repays investors when borrowers make payments on the underlying loans. The issuer uploads the latest loan tape, initiates repayment via bank wire, and the investor confirms receipt. This guide covers the complete repayment process from loan tape upload through deal closure.

## Who Can Use This

- **Issuers**: Upload loan tapes, initiate repayment, and submit wire confirmation
- **Investors**: Review repayment details, confirm receipt, and burn receivables NFTs
- **Intain (Support)**: Optional assistance with loan tape preparation

## When This Is Used

Use this process when:
- Borrowers have made payments on the underlying loans in an active asset sale deal
- The issuer needs to pass through repayment to investors
- You want to understand how repayment moves from issuer to investor
- A deal is ready to be closed after full repayment

## Step-by-Step Process

### Phase 1: Upload Loan Tape (Issuer)

#### Step 1: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Click on the **Deal ID** for the deal requiring repayment
3. The deal details page opens showing the current deal status

#### Step 2: Upload the Latest Loan Tape

1. Navigate to **Deal Operations** within the deal details
2. Click **Edit Loan Tape**
3. Choose the loan tape file to upload
4. Select the **As Of Date** for the loan tape data
5. Click **Upload**

#### Step 3: Map Loan Tape Fields

1. After upload, the field mapping interface appears
2. Map the loan tape columns to the platform's expected fields
3. Click **Save Mapping** to confirm the field mapping

> **Note:** With Intain's assistance, the issuer can prepare the latest loan tape in Excel. Intain guides the process, and the prepared document is then uploaded to the platform.

### Phase 2: Initiate Repayment (Issuer)

#### Step 4: Start the Repayment

1. Click **Initiate Repayment** from the deal operations menu
2. The repayment initiation wizard opens

#### Step 5: Configure Payment Details

1. **Repayment Type**: Select the type of repayment:
   - **Full Repayment** — Pay the entire outstanding balance, closing the deal
   - **Partial Repayment** — Pay a portion of the balance; the deal remains active for future installments
   - **Declare Default** — Declare a default on the deal (no amount required)
2. **Repayment Date**: Enter the date of the repayment (cannot be a future date)
3. **Repayment Amount**: Enter or verify the repayment amount (must be greater than zero and not exceed the outstanding balance). For receivables deals, this is pre-filled from the uploaded loan tape's invoice totals.
4. **Wire Reference**: Enter the bank wire reference number
5. **Wire Confirmation Document**: Upload the bank wire confirmation document (PNG, JPEG, or PDF, max 10 MB)
6. Click **Next** to proceed to review

> **Note:** For receivables asset sales, the repayment amount is pre-calculated from the uploaded loan tape's invoice totals. Always verify this matches your actual wire transfer before submitting.

#### Step 6: Review and Confirm

1. Review all repayment details on the confirmation screen
2. Verify the repayment type, amount, date, and wire confirmation
3. Click **Review & Confirm**, then confirm in the inline confirmation panel
4. The deal status changes to **Repayment In Progress**
5. For partial repayments, after the investor confirms receipt, you can **Record Next Installment** to initiate additional payments

### Phase 3: Confirm Receipt (Investor)

#### Step 7: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Click on the deal that shows a repayment pending

#### Step 8: Review Repayment Details

1. Navigate to **Investment Operations** within the deal details
2. Click **Confirm Repayment Receipt**
3. Review the repayment details: amount, date, type, and wire confirmation

#### Step 9: Accept or Reject the Repayment

1. Click **Review & Confirm** after reviewing the details
2. Choose your response:
   - **Accept Repayment** — If the transferred amount is correct, select Accept and confirm. The repayment is recorded and the deal progresses.
   - **Reject Repayment** — If there is a discrepancy, select Reject and provide a rejection reason (required, up to 1,000 characters). The installment is marked as rejected, and the issuer can submit a new repayment.
3. If the issuer declared a default, you can only **Confirm Default** (reject is not available for default declarations)

### Phase 4: Burn the NFT (Investor)

#### Step 10: Access Receivables

1. Navigate to **Asset Analysis** within the deal details
2. Click on the **Receivables** tab
3. The receivables list shows the NFTs held for this deal

#### Step 11: Burn the NFT

1. Click **Burn** next to the receivable NFT
2. A confirmation dialog appears
3. Click **Yes, Burn NFT** to confirm the burn
4. The NFT is burned on the blockchain, removing the investor's tokenized claim

### Phase 5: Deal Closure

#### Step 12: Deal Status Updates to Closed

1. After the NFT burn is complete, the deal dashboard shows the repayment as complete
2. The deal status changes to **Closed** with status details showing **Fully Repaid** and **100% repaid**
3. The settlement audit trail is fully preserved

#### Step 13: Review Audit Trail (Optional)

1. Navigate to **Settlement Details** within the deal
2. Click **View details** in the Settlement Activity section (bottom-right)
3. The full event trail expands, showing every action from settlement through repayment and closure

## Rules & Validations

- Repayment can only be initiated on deals in **Active** status
- The loan tape must be uploaded and mapped before repayment can be initiated
- Repayment amount is auto-calculated from the loan tape and cannot be manually overridden
- The issuer must upload a wire confirmation document as part of the repayment initiation
- Only bank wire (off-chain) is currently supported as a payment rail for repayment
- Investors must confirm receipt before the NFT burn step becomes available
- NFT burn is irreversible — once burned, the receivable position is permanently closed

## What Happens Next

After the deal is closed:
- The deal status shows **Closed** with full repayment details
- All settlement and repayment events are preserved in the audit trail
- The deal remains accessible for reporting and compliance review
- No further operational actions are available on a closed deal
