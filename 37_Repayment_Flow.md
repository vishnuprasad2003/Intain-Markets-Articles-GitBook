---
title: Repayment Flow
description: Complete step-by-step guide for the asset sale repayment process — from loan tape upload through repayment initiation, investor confirmation, NFT burn, and deal closure
---

# Repayment Flow

## Overview

The repayment flow is the post-sale process in asset sale deals where the issuer repays investors when borrowers make payments on the underlying loans. This is a critical workflow that moves funds from the issuer to the investor and ultimately closes the deal by burning the investor's NFT receivable position.

The process involves multiple phases: the issuer uploads the latest loan tape, initiates repayment via bank wire, and the investor confirms receipt. Upon confirmation, the investor burns the receivables NFT on the blockchain, permanently closing their tokenized position. This guide covers the complete repayment lifecycle from loan tape upload through deal closure, including all repayment types, installment statuses, investor decisions, and the NFT burn lifecycle.

## Who Can Use This

- **Issuers**: Upload loan tapes, configure repayment details, initiate repayment, and submit wire confirmation
- **Investors**: Review repayment details, accept or reject repayments, confirm defaults, and burn receivables NFTs
- **Intain internal team**: Where applicable, can prepare the latest loan tape and upload it on behalf of the Issuer

## When This Is Used

Use this process when:
- Borrowers have made payments on the underlying loans in an active asset sale deal
- The issuer needs to pass through repayment to investors
- You want to understand the complete repayment lifecycle from initiation through deal closure
- A deal is ready to be fully or partially repaid
- A default needs to be declared on a deal

## Repayment Types

The platform supports three types of repayment, each with different behaviors and outcomes:

| Repayment Type | Description | Amount Required | Deal Outcome |
|---------------|-------------|-----------------|-------------- |
| **Full Repayment** | Pay the entire outstanding balance | Must equal outstanding balance | Deal closes after confirmation and NFT burn |
| **Partial Repayment** | Pay a portion of the outstanding balance | Must be > 0 and ≤ outstanding balance | Deal remains active; issuer can record next installment |
| **Declare Default** | Declare a default on the deal | Not required (no amount) | Deal status changes to Defaulted after investor confirmation |

## Step-by-Step Process

### Phase 1: Upload Loan Tape (Issuer)

#### Step 1: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Click on the **Deal ID** for the deal requiring repayment
3. The deal details page opens showing the current deal status (must be **Active**)

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

> **Note:** Where applicable, the Intain internal team can prepare the latest loan tape and upload it on behalf of the Issuer. The Issuer still reviews the deal and records the repayment.

### Phase 2: Initiate Repayment (Issuer)

#### Step 4: Start the Repayment

1. Click **Initiate Repayment** from the deal operations menu
2. The repayment initiation wizard opens

#### Step 5: Configure Payment Details

Fill in the following fields:

1. **Repayment Type** — Select **Full Repayment**, **Partial Repayment**, or **Declare Default**. What each type does is in the table above.

2. **Repayment Date** — Enter the date of the repayment. The date **cannot be a future date**. It must be today or a past date.

3. **Repayment Amount** — Enter or verify the amount:
   - **Full Repayment**: must equal the outstanding balance
   - **Partial Repayment**: greater than zero, and not above the outstanding balance
   - **Declare Default**: no amount
   - **Receivables deals**: the amount comes from the loan tape and cannot be typed over. Confirm it matches the wire before you submit.

4. **Wire Reference** — Enter the bank wire reference number. Required for Full and Partial repayment.

5. **Wire Confirmation Document** — Upload proof of the wire. Accepted formats are **PNG**, **JPEG**, or **PDF**, up to **10 MB**.

6. Click **Next** to proceed to the review screen.

#### Step 6: Review and Confirm

1. Review all repayment details on the confirmation screen
2. Verify the repayment type, amount, date, wire reference, and wire confirmation document
3. Click **Review & Confirm**, then confirm on the summary
4. The deal status changes to **Repayment In Progress**
5. The status step shows **Awaiting Investor Confirmation**

### Phase 3: Confirm Receipt (Investor)

#### Step 7: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Click on the deal that shows a repayment pending

#### Step 8: Review Repayment Details

1. Navigate to **Investment Operations** within the deal details
2. Click **Confirm Repayment Receipt**
3. Review the repayment details:
   - Repayment type (Full, Partial, or Default)
   - Repayment amount
   - Repayment date
   - Wire reference number
   - Wire confirmation document (viewable/downloadable)

#### Step 9: Accept or Reject the Repayment

1. Click **Review & Confirm** after reviewing the details
2. Choose your decision:

**Accept Repayment:**
- Select **Accept** and confirm
- For a full repayment, the investor can then burn the NFT and the deal can close
- For a partial repayment, the status step shows **Installment Recorded**. The issuer can click **Record Next Installment** for the next payment

**Reject Repayment:**
- Select **Reject**
- Enter a reason (required, up to 1,000 characters)
- The issuer is notified and can submit a new repayment

**Confirm Default (only when the issuer declared default):**
- **Reject** is not available
- Confirm the declaration
- The deal status changes to **Defaulted**, and the status step shows **Default Declared**

## What the status step shows

| What you see | Meaning |
|--------------|---------|
| **Awaiting Investor Confirmation** | The issuer submitted the repayment. The investor has not responded yet. |
| **Repayment Complete** | A full repayment was accepted. |
| **Installment Recorded** | A partial repayment was accepted. The issuer can record the next payment. |
| **Default Declared** | The investor confirmed the default. |

### Phase 4: Burn the NFT (Investor)

After a Full Repayment is confirmed, the investor must burn their receivables NFT to close their tokenized position.

#### Step 10: Access Receivables

1. Navigate to **Asset Analysis** within the deal details
2. Click on the **Receivables** tab
3. The receivables list shows the NFTs held for this deal

#### Step 11: Burn the NFT

1. Click **Burn** next to the receivable NFT
2. A confirmation dialog appears
3. Click **Yes, Burn NFT** to confirm the burn
4. The NFT burn is submitted to the blockchain

### NFT Status Lifecycle

The NFT progresses through defined states during repayment:

| NFT Status | Meaning |
|-----------|---------|
| **Transferred** | The investor holds the receivables NFT after settlement — the normal state during an active deal |
| **Retirement pending** | Repayment is confirmed; the investor can retire (burn) the NFT |
| **Retired** | The NFT has been permanently burned on the blockchain — the investor's tokenized claim is removed |

```
Transferred → (investor retires NFT after repayment confirmed) → Retirement pending → (blockchain confirms) → Retired
```

**Important:** NFT retirement is **irreversible**. Once an NFT is burned on the blockchain, the receivable position is permanently closed and cannot be recovered. Retirement can only be initiated after the repayment installment has been confirmed.

### Phase 5: Deal Closure

#### Step 12: Deal Status Updates to Closed

1. After the NFT burn is complete, the deal dashboard shows the repayment as complete
2. The deal status changes to **Closed** with status details showing **Fully Repaid** and **100% repaid**
3. The settlement audit trail is fully preserved

#### Step 13: Review Audit Trail (Optional)

1. Navigate to **Settlement Details** within the deal
2. Click **View details** in the Settlement Activity section (bottom-right)
3. The full event trail expands, showing every action from settlement through repayment and closure

## Deal Status Transitions During Repayment

The deal status tracks the overall state of the transaction throughout the repayment process:

| Deal Status | Status Detail | When This Occurs |
|------------|---------------|-----------------|
| **Active** | — | Deal is operational, before any repayment |
| **Repayment In Progress** | — | After issuer initiates repayment |
| **Active** | Partially Repaid | After a partial repayment is confirmed and deal returns to active for next installment |
| **Closed** | Fully Repaid | After full repayment confirmed and NFT burned |
| **Defaulted** | Default Declared → Default Confirmed | After default is declared and investor confirms |

### Partial Repayment Cycle

For partial repayments, the process can repeat multiple times:

The issuer records a partial payment. The deal shows **Repayment In Progress** until the investor accepts. After acceptance, the issuer uses **Record Next Installment**. This repeats until the deal is fully repaid or a default is confirmed.

## Rules & Validations

- **Deal Must Be Active** — Repayment can only be initiated on deals in **Active** status
- **Loan Tape Required** — The loan tape must be uploaded and field mapping completed before repayment can be initiated
- **Repayment Date** — Cannot be a future date
- **Repayment Amount** — Must be greater than zero for Full and Partial types; must equal outstanding balance for Full; must not exceed outstanding balance for Partial; not required for Declare Default
- **Receivables Pre-Calculation** — For receivables asset sales, the repayment amount is auto-calculated from the loan tape's invoice totals and cannot be manually overridden
- **Wire Reference** — Required for Full and Partial repayment types
- **Wire Confirmation Document** — Required; must be PNG, JPEG, or PDF; maximum 10 MB
- **Payment method** — Repayment uses bank wire only
- **Rejection reason** — Required when the investor rejects a repayment; maximum 1,000 characters
- **NFT burn** — The investor can burn the NFT only after they accept a full repayment
- **NFT Burn Is Irreversible** — Once burned, the receivable position is permanently closed on the blockchain
- **Next Installment** — Record Next Installment is only available after a partial repayment has been confirmed
- **Default Cannot Be Rejected** — When the issuer declares a default, the investor can only Confirm Default; the reject option is not available

## What Happens Next

**After Full Repayment and NFT Burn:**
- The deal status shows **Closed** with **Fully Repaid** and **100% repaid**
- All settlement and repayment events are preserved in the audit trail
- The deal remains accessible for reporting and compliance review
- No further operational actions are available on a closed deal

**After Partial Repayment:**
- The deal returns to **Active** status with a partially repaid indicator
- The issuer can click **Record Next Installment** to initiate the next partial payment
- This cycle continues until the deal is fully repaid or a default is declared

**After Default Confirmation:**
- The deal status changes to **Defaulted** with **Default Confirmed**
- The deal is effectively closed with default status
- All events are preserved in the audit trail

**After Rejection:**
- The issuer sees the investor’s reason and can submit a new repayment
- The deal remains in **Repayment In Progress** status until a new repayment is submitted and confirmed
