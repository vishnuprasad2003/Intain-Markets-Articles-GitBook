---
title: Borrower Token Approval
description: >-
  Step-by-step guide for borrowers to approve token transfers in the credit
  facility funding notice workflow
---

# Borrower Token Approval

## Overview

This guide explains the borrower token approval process in the Credit Facility module. After the facility agent approves a funding notice and fungible tokens (FT) are generated on the blockchain, the borrower must approve the token transfer before the facility agent can proceed with e-signing for each lender. This approval is a critical on-chain authorization step — the borrower's wallet signs an ERC-20 `approve` transaction that grants the platform permission to transfer the newly minted FT tokens to lenders as part of the settlement process.

![Issuer Token Approval Screen](<.gitbook/assets/Issuer_Token_Approval (2).png>)

## Who Can Use This

* **Borrowers (Issuers)** who have an active credit facility with approved funding requests
* The borrower must have access to their blockchain wallet private key to sign the approval transaction

## When This Is Used

Use this process when all of the following conditions are met:

1. Your funding request has been **approved** by the facility agent (status: `APPROVED`)
2. A funding notice has been automatically generated (status: `PENDING_TOKEN_GENERATION`)
3. The facility agent has clicked **Approve** on the funding notice, triggering FT contract deployment
4. Tokens have been generated — the funding notice status is now `TOKEN_GENERATED`
5. The `tokenDistribution` array has been populated with lender allocations
6. You need to authorize the platform to transfer tokens to lenders on your behalf

This step must complete **before** the facility agent can initiate e-signatures for individual lenders.

## Borrower Token Approval Flow

The token approval sits in a specific position within the broader funding notice lifecycle:

```
Funding Request APPROVED
       ↓
Funding Notice Generated (PENDING_TOKEN_GENERATION)
       ↓
FA clicks Approve → FT contract deployed on Avalanche C-Chain
       ↓
Status: TOKEN_GENERATED
       ↓
Borrower Approves Token (ERC-20 approve transaction)
       ↓
FA E-signs for each lender (0/n → n/n)
       ↓
Funding Notice VISIBLE TO LENDERS (per-lender visibility)
       ↓
Lenders review → Transfer funds → Confirm and Settle
       ↓
FT tokens transferred to Borrower → TOKEN_TRANSFERRED
```

## Step-by-Step Process

### Step 1: Access the Credit Facility

1. Log in to Intain Markets with your **Borrower** credentials
2. From the left expandable menu, click on **Credit Facility**
3. Navigate to the **Active Facilities** tab
4. Locate the master commitment that contains the funding notice awaiting your token approval
5. The funding notice will show status **TOKEN\_GENERATED**, indicating that the FT contract has been deployed and tokens are ready for your approval

### Step 2: Review Token Details

Before approving, review the funding notice details to ensure accuracy:

**Funding Notice Information:**

| Field                                     | What to Verify                                                                               |
| ----------------------------------------- | -------------------------------------------------------------------------------------------- |
| Funding Notice ID                         | Confirm this is the correct funding notice for your drawdown                                 |
| Draw Amount                               | Verify the total drawdown amount matches your approved funding request                       |
| FT Contract Address (`ftContractAddress`) | The on-chain address of the deployed FT token contract — this is the token you are approving |
| Total Token Supply                        | The total number of FT tokens minted, corresponding to the draw amount                       |

**Token Distribution (Per-Lender Breakdown):**

| Field                     | Description                                                |
| ------------------------- | ---------------------------------------------------------- |
| `lenderOrgId`             | The lender organization receiving tokens                   |
| `lenderName`              | Display name of the lender                                 |
| `tokensAllocated`         | Number of tokens allocated to this lender                  |
| `participationPercentage` | Lender's percentage share of the total commitment          |
| `commitmentAmount`        | The lender's commitment amount under the master commitment |
| `esignatureStatus`        | Should show `pending` at this stage                        |
| `lenderApprovalStatus`    | Should show `PENDING` at this stage                        |

Verify that the lender allocations, participation percentages, and commitment amounts are correct before proceeding.

### Step 3: Approve the Token Transfer

1. Click the **Approve Token** action button on the funding notice
2. A modal or form will appear requesting your wallet credentials
3. Enter your **Wallet Private Key** — this is the private key associated with the borrower's blockchain wallet
4. Click the **Approve** button to submit the approval

**What Happens On-Chain:** The platform uses your private key to sign an ERC-20 `approve` transaction on the FT contract. This transaction authorizes the platform's escrow contract (or admin wallet) to transfer the total FT token supply on your behalf. The transaction is submitted to the Avalanche C-Chain, and the resulting transaction hash is recorded in the funding notice's audit trail.

**What Happens in the Platform:**

* The approval transaction is recorded in the funding notice's `actionHistory` with action type `LENDER_STATUS_UPDATED` (or equivalent approval action)
* The approval timestamp and your user ID are stored
* The funding notice status is updated to reflect that the borrower has approved
* The facility agent's **E-sign** action button becomes enabled

### Step 4: Confirmation

After successful approval:

* You will see a confirmation message indicating the token transfer privilege has been approved
* The action history on the funding notice will show your approval with a timestamp
* The facility agent can now proceed to e-sign for each lender

If the approval fails (e.g., incorrect private key, insufficient gas, network issue), an error message will be displayed. You can retry the approval — the system checks the on-chain state and will not create a duplicate approval.

## What Happens After Approval

Once the borrower approves the token transfer, the following sequence occurs:

1. **FA E-Signs for Each Lender** — The facility agent initiates the e-signature process. The action shows **E-sign (0/n)** where `n` is the number of participating lenders. The FA signs for each lender individually via Adobe Sign or ZohoSign. The count progresses: `(0/n) → (1/n) → ... → (n/n)`.
2. **Per-Lender Visibility** — Each lender gains visibility into the funding notice only after the facility agent completes the e-sign for that specific lender. A lender with a completed e-sign (`esignatureStatus: 'ESIGN_COMPLETED'`) can see and act on the funding notice; others cannot yet.
3. **Lender Fund Transfer** — Each lender reviews the funding notice, transfers the required funds through their banking channel, and clicks **Confirm and Settle** in the platform.
4. **FT Token Delivery** — As each lender confirms settlement, the platform executes the FT token transfer from the borrower's approved allocation to the lender. Each transfer generates a unique `transactionHash` recorded in the lender's `tokenDistribution` entry. The lender's `mintingStatus` updates to `completed`.
5. **Funding Notice Completion** — When all lenders have received their FT tokens (`mintingStatus: 'completed'` for every entry in `tokenDistribution`), the funding notice status transitions to **TOKEN\_TRANSFERRED**, marking the completion of the funding cycle.

## Rules & Validations

| Rule                        | Details                                                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Timing**                  | Token approval can only occur after tokens are generated (`TOKEN_GENERATED` status)                             |
| **Prerequisite for E-Sign** | The facility agent cannot begin e-signing until the borrower approves                                           |
| **Wallet Required**         | The borrower must provide a valid blockchain wallet private key to sign the on-chain approval                   |
| **One-Time Action**         | Once approved, the action cannot be undone — the on-chain approval persists                                     |
| **Idempotent**              | If the approval has already been granted on-chain, repeating the action will not create a duplicate transaction |

## Key Points

**After Token Generation** — Borrower token approval occurs only after the facility agent approves the funding notice and FT tokens are deployed on the Avalanche C-Chain.

**Before FA E-Sign** — This step is a mandatory prerequisite. The e-signature process for individual lenders cannot begin until the borrower has approved the token transfer.

**On-Chain Authorization** — This is not just a UI confirmation. Your wallet signs a real ERC-20 `approve` transaction on the blockchain, granting the platform permission to move tokens.

**Token Receipt** — After all lenders complete their fund transfers and settlements, FT tokens are delivered, and the funding notice reaches `TOKEN_TRANSFERRED` status. The borrower receives the drawn-down funds while lenders hold the corresponding FT tokens.

**Audit Trail** — The approval transaction hash, timestamp, and actor are permanently recorded in both the platform's action history and the blockchain, providing a complete audit trail for compliance purposes.
