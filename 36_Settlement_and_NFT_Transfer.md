---
title: Settlement and NFT Transfer
description: Understand the settlement workflow and NFT ownership transfer in asset sales
---

# Settlement & NFT Transfer

## Overview

Settlement is the critical stage where financial exchange occurs between investors and the issuer, and ownership of the loan assets is transferred via NFTs on the blockchain. This workflow covers the entire settlement process from fund transfer initiation through NFT minting and transfer to investors, resulting in the deal becoming Active.

## Workflow Overview

The settlement workflow progresses through several coordinated stages involving the issuer, investors, and the underwriter. Settlement uses off-chain fund transfer (bank wire) combined with on-chain NFT ownership recording for complete traceability.

**Fund Transfer** — Investors transfer purchase funds to the issuer via bank wire. Each party confirms their side of the transaction on the platform.

**Payment Confirmation** — The issuer confirms receipt of payment from each investor. Investors confirm that they have sent the payment. Both confirmations are recorded.

**NFT Minting and Transfer** — Once payments are confirmed, the platform mints receivables NFTs representing the loan assets and transfers them to investor wallets. This creates an immutable on-chain record of ownership.

**Deal Activation** — After NFT transfer is complete, the deal status moves from Settled to Active, signaling that the post-sale lifecycle has begun.

## Key Stages

### Stage 1: Settlement Initiation

The settlement process begins after investor commitments are finalized and all investor agreements are signed. The deal status moves to **Settlement In Progress**.

- The platform prepares settlement records for each investor based on their final allocation
- Settlement details including amounts, dates, and bank transfer information become available
- Both issuers and investors can view their settlement obligations

### Stage 2: Fund Transfer

Investors transfer funds to the issuer using bank wire (off-chain transaction).

- Each investor initiates their bank wire transfer for their committed amount
- The platform displays settlement details including transfer amounts and reference information
- Transfer status is tracked per investor

### Stage 3: Payment Confirmation

Both sides confirm the financial transaction on the platform.

- **Investor Side**: The investor logs in and confirms that they have sent the payment
- **Issuer Side**: The issuer confirms receipt of payment from each investor
- Payment confirmation status is tracked per investor (Pending, Confirmed)

### Stage 4: NFT Transfer

Once payments are confirmed, the platform handles the blockchain-based ownership transfer.

- Receivables NFTs are minted representing the loan assets
- NFTs are transferred from the issuer's wallet to each investor's wallet
- The blockchain records the transfer with immutable timestamps and transaction hashes
- NFT transfer details (asset IDs, transaction hashes) become available in the deal details

### Stage 5: Deal Activation

After all NFT transfers are complete, the deal reaches its active state.

- The deal status changes from **Settled** to **Active**
- Investors now hold receivables NFTs in their wallets
- The asset sale settlement activity and audit trail are fully recorded
- The deal enters its post-sale operational lifecycle

## How the Workflow Progresses

The settlement workflow is sequential — each stage must complete before the next begins. Payment confirmation from both sides is required before NFT transfer can proceed. The platform enforces these gates to ensure that financial and ownership transfers are properly synchronized.

The settlement details page in the deal provides a step-by-step view of the settlement lifecycle, showing which stages are complete, which is current, and which are pending. Each participant can view their specific obligations and status.

## How the Workflow Progresses

The deal details page displays a **lifecycle stepper** showing the complete deal progression with six visual steps:

| Step | Label | Deal Statuses Covered |
|------|-------|-----------------------|
| 1 | **Draft** | Draft, Cancelled |
| 2 | **Published** | Pending Review → Approved → Published → Commit → Invest |
| 3 | **Settlement** | Settlement In Progress → Settled |
| 4 | **Active** | Active |
| 5 | **Repayment** | Repayment In Progress |
| 6 | **Closed** | Closed |

Each step shows a visual indicator: a check mark (completed), a numbered ring (current), a clock icon (waiting on counterparty), or grey (upcoming). The stepper also shows a status chip with contextual messages like "Awaiting investor payment", "Investment in Progress", or "Awaiting asset delivery".

The flow direction labels above the stepper indicate the direction of value transfer: **Setup** (Draft), **Investor → Issuer** (Published through Active), and **Issuer → Investor** (Repayment through Closed).

![Settlement Activity](images/36-settlement-and-nft-transfer/settlement-activity.png)

## Important Points to Know

**Off-Chain Settlement** — Fund transfers happen via bank wire (Wire/ACH) outside the platform. The platform records and tracks the confirmations but does not process the actual financial transfer. Stablecoin and Kinexys rails are planned but not yet active.

**On-Chain Ownership** — NFT transfer happens on the blockchain, creating an immutable record of asset ownership. The issuer initiates NFT transfer (requires MFA verification), and all loans in the deal are transferred from the issuer's org wallet to the investor's org wallet.

**Settlement Activity Trail** — The settlement details section maintains a complete activity log showing every confirmation, transfer, and status change with timestamps and actor information. This audit trail is accessible to all deal participants.

**Per-Investor Tracking** — Settlement is tracked individually for each investor. Different investors may be at different stages of the settlement process simultaneously.

**Irreversibility** — Once NFT transfer is complete and the deal is Active, the settlement cannot be reversed. Any corrections would need to be handled through the repayment or administrative workflows.
