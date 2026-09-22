---
title: Repayment Receipt and NFT Burn
description: Complete task-based guide for investors to review issuer repayment declarations, accept or reject repayment, and burn receivables NFTs on-chain to close their position
---

# Repayment Receipt & NFT Burn

## Overview

This guide provides investors with step-by-step instructions for confirming repayment receipt and burning receivables NFTs to close out their position in an asset sale deal. When the issuer initiates repayment, the investor reviews the repayment declaration (type, amount, date, wire reference), decides to accept or reject it, and — upon acceptance — burns the receivables NFT to finalize deal closure. The burn is an on-chain transaction that permanently retires the token from the investor's wallet.

## Who Can Use This

- **Investors**: All steps in this guide are performed by the investor role (the payee on the repayment settlement)

## When This Is Used

Use this guide when:
- The issuer has initiated repayment on an active asset sale deal
- You have received a wire transfer from the issuer for a repayment
- You need to confirm receipt and close out your investment position
- You need to burn your receivables NFT after repayment confirmation
- The issuer has declared default and you need to acknowledge the declaration

## Step-by-Step Process

### Part 1: Review and Respond to Repayment Declaration

#### Step 1: Access the Deal

1. Navigate to **Asset Sale** from the left sidebar menu
2. Locate the deal showing **Repayment In Progress** status
3. Click on the deal to open the deal details page

#### Step 2: Open the Repayment Receipt Modal

1. Navigate to **Investment Operations** within the deal details
2. Click **Confirm Repayment Receipt**
3. The repayment receipt modal opens showing the issuer's declaration

#### Step 3: Review the Issuer's Declaration

The modal presents the issuer's repayment declaration as read-only fields:

| Field | Description |
|-------|-------------|
| **Repayment Type** | Full Repayment, Partial Repayment, or Defaulted |
| **Repayment Date** | The date the repayment was initiated (hidden for Defaulted) |
| **Repayment Amount** | The amount the issuer has transferred (hidden for Defaulted) |
| **Wire Reference** | The wire memo or transaction ID provided by the issuer |

These values cannot be modified by the investor — they are the issuer's declaration. The investor's role is to verify and respond.

#### Step 4: Choose Your Response

Below the declaration, the **Your Response** section presents two options as radio buttons:

**Accept Repayment**
- Confirm receipt of the repayment as declared by the issuer
- This is the default selection

**Reject Repayment**
- Return to the issuer with a written reason. The outstanding balance remains unchanged.
- When selected, a **Rejection reason** text field appears (required, up to 1,000 characters)
- A character counter shows current length
- The rejection reason is sent to the issuer with your response

> **Important for Defaulted declarations:** When the issuer has declared default, the Reject option is disabled. A declared default cannot be rejected — you can only confirm it. The message reads: "The issuer has declared default on this repayment. Confirm to close the deal."

#### Step 5: Review and Confirm

1. Click **Review & Confirm** (or **Review Rejection** if rejecting)
2. A confirmation panel appears with a complete summary

**For Accept:**
- Message: "You are confirming receipt of the repayment as declared by the issuer."
- Summary shows: Repayment Type, Repayment Amount, Repayment Date, Wire Reference
- Button: **Accept Repayment**

**For Reject:**
- Headline: "Reject this repayment declaration?"
- Message: "The installment will be marked as rejected. The outstanding balance remains unchanged and the issuer may submit a new repayment."
- Summary shows all declaration details plus your decision and rejection reason
- Bullet points:
  - "Repayment figures are not changed — you are rejecting this submission."
  - "The issuer will be notified with your reason for rejection."
- Button: **Confirm Rejection**

**For Default Confirmation:**
- Headline: "Confirm declared default?"
- Message: "Confirming default is permanent. No further repayment can be recorded on this deal."
- Bullet: "A declared default cannot be rejected."
- Button: **Confirm Default**

3. Click the confirmation button to submit your decision
4. The decision is recorded and the issuer is notified

> **Idempotency protection:** The platform uses idempotency keys to prevent duplicate submissions — you cannot accidentally submit the same decision twice.

### Part 2: Burn the Receivables NFT

After accepting repayment, the NFT burn becomes available. The burn permanently retires the receivables NFT from your wallet on-chain.

#### Step 6: Access Receivables

1. Navigate to **Asset Analysis** within the deal details
2. Click on the **Receivables** tab
3. Your receivables NFTs are listed with details including Asset ID, Token ID, and tokenization status

#### Step 7: Initiate the Burn

1. Click the **Burn** button next to the receivable NFT(s) you want to burn
2. You can select specific asset IDs to burn — the platform accepts one or more asset IDs per burn request
3. A confirmation dialog appears with details of the NFT(s) to be burned

> **Eligibility gate:** The burn button is only available when:
> - Repayment has been confirmed (accepted) on the settlement
> - The settlement's NFT status is **Retirement pending**
> - The NFTs have a tokenization status of **Transferred** (meaning they are in your wallet)
> - You are the authenticated Investor (payee) on the repayment settlement

> **For partial repayments:** If the deal is partially settled, the burn is only available for assets whose invoice outstanding amount is zero. Assets with remaining outstanding balance cannot be burned until fully repaid.

#### Step 8: Confirm the Burn

1. Click **Yes, Burn NFT** to confirm
2. The platform submits a burn job that processes asynchronously
3. For each token, the burn job:
   - Verifies the token's current status in LOAN_METADATA (Snowflake) — must be **Transferred**
   - Verifies the token contract address matches the ReceivablesNFT contract
   - Calls the `burnReceivableFromInvestorWallet` function on the ReceivablesNFT smart contract using the investor's organization wallet
   - Updates LOAN_METADATA in Snowflake: sets `TOKENIZATION_STATUS` to **Burned**
   - Records the burn transaction hash and timestamp

4. The burn event is recorded with:
   - Blockchain transaction hash
   - Token ID
   - Receivable ID (on-chain asset identifier)
   - Number of Snowflake rows updated

#### What Happens On-Chain

The burn is an irreversible blockchain transaction:
- The `burnReceivableFromInvestorWallet` function is called on the **ReceivablesNFT** smart contract
- The investor's wallet address (resolved from the investor's organization) is the authorized caller
- The NFT identified by its Token ID is permanently destroyed on-chain
- After a successful on-chain burn, the off-chain LOAN_METADATA is updated to reflect **Burned** status
- If the on-chain burn succeeds but the off-chain update fails, a warning is logged (the on-chain state is authoritative)

### Part 3: Deal Closure

#### Step 9: Settlement Marker Update

After all NFTs on the deal are burned:
- The platform re-reads all LOAN_METADATA rows for the deal to verify every tokenized loan is now in **Burned** status
- If all tokens are burned, the settlement's NFT status is updated from **Retirement pending** to **Retired**
- An audit event (`settlement.token.burned`) is recorded with the category **CHAIN** and action **burn_token**
- The deal's NFT status is also updated to **Retired**

> **Partial burns:** If you only burn some of the deal's tokens, the settlement remains at **Retirement pending** so you can return later to burn the remaining tokens.

#### Step 10: Verify Deal Closure

1. After all burns complete, the deal dashboard updates
2. The deal status changes to **Closed** showing **Fully Repaid** and **100% repaid**
3. All settlement, repayment, and burn events are preserved in the audit trail

#### Step 11: Review Audit Trail (Optional)

1. Navigate to **Settlement Details** within the deal
2. Click **View details** in the Settlement Activity section
3. The complete event trail shows every action from settlement through repayment and closure

## Rules & Validations

- Repayment confirmation is only available when the deal has a repayment settlement in an eligible status
- Only the Investor (payee) on the settlement can confirm receipt or burn NFTs — other users receive an "Access denied" error
- You must verify the repayment amount against your actual wire receipt before accepting
- Rejection requires a written reason (up to 1,000 characters)
- A declared default cannot be rejected — only confirmed
- NFT burn is only available after repayment is accepted and the settlement's NFT status is **Retirement pending**
- For partially settled deals, only assets with zero invoice outstanding can be burned
- Burning an NFT is irreversible — the token is permanently destroyed on-chain
- The settlement marker (**Retirement pending** → **Retired**) only transitions when ALL deal tokens are burned, not just the requested subset
- Idempotency keys prevent duplicate acceptance or rejection submissions
- The burn job processes asynchronously — the status is polled for updates

## What Happens Next

After the deal is closed:
- The deal remains in your Asset Sale dashboard for reference and reporting
- The complete audit trail is permanently preserved, including all blockchain transaction hashes
- Settlement Details provide full visibility into every event from settlement through burn
- No further operational actions are available on a closed deal
- If you rejected the repayment, the issuer is notified and can record a new repayment attempt
