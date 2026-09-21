---
title: Settlement and NFT Transfer
description: Understand the settlement workflow, payment rails (Bank Wire, Stablecoin, Kinexys), escrow mechanics, NFT ownership transfer, and the end-to-end settlement process in Intain Markets
---

# Settlement & NFT Transfer

## Overview

Settlement is the critical stage where financial exchange occurs between investors and the issuer, and ownership of the loan assets is transferred via NFTs on the blockchain. This document covers the entire settlement process — from payment rail selection and fund transfer initiation through on-chain escrow, NFT minting, and transfer to investors — resulting in the deal becoming **Active**.

The settlement engine is a **unified module** that supports both the **investment purchase flow** (investor pays issuer) and the **repayment flow** (issuer pays investor). It handles multiple payment rails, multi-party tracking, and cross-chain asset delivery with full audit traceability.

## Who Can Use This

| Role | Settlement Capability |
|------|----------------------|
| **Issuer** | Initiates settlement, confirms receipt of payment, triggers NFT transfer, releases escrow funds |
| **Investor** | Selects payment method, confirms fund transfer, receives NFTs in wallet |
| **Underwriter (Market Maker)** | Views settlement progress and activity trail |
| **Servicer / Paying Agent** | May act as payee on behalf of the issuer for fund receipt |
| **Admin** | Can retry failed settlements, view audit trail, impersonate for troubleshooting |

## Payment Rails

The platform supports three payment rails for settlement. The payment method is selected during the **Confirm and Settle** phase and determines how funds move between parties.

### 1. Bank (Wire/ACH) — Traditional Off-Chain Settlement

Bank wire is the default payment rail for most transactions. Funds move off-chain through traditional banking infrastructure.

**How it works:**
- The investor initiates a bank wire transfer for their committed amount
- The platform records and tracks the confirmation but **does not process** the actual financial transfer
- Both the investor and issuer confirm the transfer on the platform
- After receipt confirmation, assets are delivered via the standard NFT transfer process

**Key characteristics:**
- Lock timeout: **3 days** (the settlement window before assets are returned)
- Off-chain settlement — the platform tracks confirmations only
- No MetaMask or wallet interaction required for the fund transfer itself
- The issuer manually confirms receipt of payment

**Payment details recorded:**
- Wire reference number
- Transfer amount
- Wire confirmation document (uploaded)
- Bank account details (from organization profile)

### 2. Stablecoin (USDC) — On-Chain Settlement via Smart Contract Escrow

Stablecoin settlement uses **USDC (ERC-20)** on the Avalanche or Ethereum blockchain with a **cross-chain escrow** system powered by the **Wormhole bridge** for asset delivery.

**How it works:**
1. **Escrow Deployment** — Two smart contracts are deployed: a **USDC Escrow** on Ethereum mainnet (or Avalanche C-Chain) and an **Asset Escrow** on the Avalanche L1 subnet. Both are linked via Wormhole Core Bridge addresses.
2. **MetaMask Connection** — The investor connects their MetaMask wallet (must match their verified settlement wallet address registered during onboarding)
3. **USDC Approval** — The investor approves the USDC escrow contract to spend the required amount via an ERC-20 `approve` transaction
4. **Balance Validation** — The platform checks the wallet has sufficient USDC token balance and native gas (AVAX or ETH)
5. **Deposit** — The investor deposits USDC into the escrow factory contract, referencing the settlement's on-chain ID (a keccak256 hash of the settlementId)
6. **Cross-Chain VAA** — Once funded, a **Wormhole Verified Action Approval (VAA)** is generated. The platform fetches this VAA from Wormhole guardians (with retry logic: up to 60 retries at 5-second intervals)
7. **Asset Delivery** — The Asset Escrow on the Avalanche L1 delivers NFT assets in batches (up to 50 per transaction) to the investor's wallet
8. **Settlement Finalization** — A settlement VAA is fetched from the L1 and used to finalize the USDC escrow on mainnet, releasing funds to the issuer

**Key characteristics:**
- Lock timeout: **24 hours** (shorter window since on-chain is automated)
- Fully automated end-to-end once the investor deposits USDC
- Cross-chain: USDC on Ethereum/Avalanche C-Chain ↔ Assets on Avalanche L1 subnet
- USDC uses **6 decimal places** (standard ERC-20 USDC on all networks)
- Settlement amounts are stored in whole currency units (100 = $100 = 100 USDC)
- Escrow contract addresses are returned by `POST /settlements/query` (not hardcoded)

**Supported chains:**
| Chain | Environment | Chain ID | USDC Contract |
|-------|-------------|----------|---------------|
| Avalanche Fuji Testnet | Test/UAT | 43113 (0xa869) | `0x5425890298aed601595a70AB815c96711a31Bc65` |
| Ethereum Mainnet | Production | 1 (0x1) | `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48` |

**MetaMask error handling:**
The platform provides clear error messages for every wallet interaction scenario:
- MetaMask not installed → "Install MetaMask to continue"
- Wrong network → Automatic chain switch prompt
- Wrong wallet account → Prompt to select the verified wallet
- Insufficient USDC balance → "Connected wallet does not have enough USDC"
- Insufficient gas → "Connected wallet does not have gas available"
- User rejected approval → "Approval was rejected in MetaMask"
- Transaction reverted → Specific failure message per step

### 3. Kinexys — JP Morgan Payment Rail (Future)

Kinexys is a **planned** payment rail that will enable institutional-grade payment settlement through JP Morgan's blockchain payment infrastructure.

**Current status:** Registered in the platform's rail registry and available as a payment type option. Currently routes through the same off-chain flow as Bank (Wire/ACH) with a 3-day lock timeout. Full Kinexys API integration is in development.

**When available, it will provide:**
- Institutional blockchain-based payment processing
- Faster settlement finality than traditional wire
- Integration with JP Morgan's on-ledger payment network

### Payment Rail Comparison

| Feature | Bank (Wire/ACH) | Stablecoin (USDC) | Kinexys |
|---------|-----------------|-------------------|---------|
| **Status** | Active | Active | Planned |
| **Settlement speed** | Manual (1–3 days) | Automated (minutes) | TBD |
| **Lock timeout** | 3 days | 24 hours | 3 days |
| **On-chain** | No (fund transfer off-chain) | Yes (USDC + Wormhole) | Hybrid |
| **Wallet required** | No | Yes (MetaMask) | TBD |
| **Manual confirmation** | Both parties | Investor deposits only | TBD |
| **Asset delivery** | Manual NFT transfer | Automatic via escrow | TBD |
| **Refund on timeout** | N/A | Automatic escrow refund | TBD |

## Settlement Workflow — Purchase Flow

The purchase flow is the primary settlement path: the investor pays the issuer for asset ownership.

### Stage 1: Settlement Initiation

The settlement process begins after investor commitments are finalized and all investor agreements are signed. The deal status moves to **Settlement In Progress**.

- The platform creates a settlement record for each investor based on their final allocation
- Settlement details (amounts, dates, bank transfer information) become available
- Both issuers and investors can view their settlement obligations
- The settlement overall status is **Created**

### Stage 2: Payment Rail Selection

Before transferring funds, the investor (or issuer, depending on configuration) selects the payment method.

**For Asset Sale deals:**
- The payment rail is selected in the settlement details section of the deal
- Available options: **Bank (Wire/ACH)**, **Stablecoin**, **Kinexys**
- The selection is saved via `PATCH /settlements/:settlementId/payment-info`
- Additional platform details (Solana vs Avalanche) can be specified

**For Securitization deals:**
- Payment mode is set at the deal level and applies to all tranches
- Can be updated while the deal is in configuration

### Stage 3: Fund Transfer

How funds move depends on the selected payment rail:

**Bank (Wire/ACH):**
1. The investor initiates a bank wire transfer for their committed amount
2. The investor uploads a **wire confirmation document** on the platform
3. The investor clicks **Confirm Payment** to declare that funds have been sent
4. Transfer status updates to "Funding Confirmed" per investor

**Stablecoin (USDC):**
1. The investor connects MetaMask wallet (must match verified settlement address)
2. The platform validates the chain configuration and wallet balance
3. The investor approves the USDC spend amount via MetaMask
4. The investor deposits USDC into the escrow contract
5. The escrow status updates automatically — no manual confirmation needed
6. If the deposit doesn't complete within 24 hours, the escrow automatically refunds

### Stage 4: Payment Confirmation

Both sides confirm the financial transaction on the platform.

- **Investor Side**: The investor confirms that they have sent the payment (bank wire) or the platform auto-confirms (stablecoin)
- **Issuer Side**: The issuer confirms receipt of payment from each investor. For stablecoin, the issuer can release escrow funds directly
- Payment confirmation status is tracked per investor (Pending → Confirmed)
- Settlement overall status moves from **Created** → **Funded**

**Issuer actions for stablecoin settlement:**
- If escrow is deposited but not yet settled: Button shows **"Release Escrow Funds"**
- If escrow is settled: Button shows **"Confirm Received Funds"**
- Release triggers the cross-chain asset delivery automatically

### Stage 5: NFT Minting and Transfer

Once payments are confirmed, the platform handles the blockchain-based ownership transfer.

**For Bank (Wire/ACH) settlements:**
- The issuer initiates NFT transfer (requires **MFA verification**)
- Receivables NFTs are minted representing the loan assets
- NFTs are transferred from the issuer's organization wallet to each investor's organization wallet
- The blockchain records the transfer with immutable timestamps and transaction hashes

**For Stablecoin settlements:**
- Asset delivery happens **automatically** through the escrow smart contract
- Assets are delivered in batches of up to **50 per transaction** to the investor's wallet
- A Wormhole VAA is generated for each cross-chain transfer
- The settlement finalizes on the USDC escrow to release funds to the issuer
- No manual NFT transfer action is needed

**NFT transfer details available after completion:**
- Asset token IDs
- Transaction hashes
- Block timestamps
- Source and destination wallet addresses

### Stage 6: Deal Activation

After all NFT transfers are complete, the deal reaches its active state.

- The deal status changes from **Settled** to **Active**
- Investors now hold receivables NFTs in their wallets
- The asset sale settlement activity and audit trail are fully recorded
- The deal enters its post-sale operational lifecycle (repayment phase)
- Overall settlement status: **Settled**

## Settlement Statuses

### Overall Settlement Status

| Status | Description |
|--------|-------------|
| **Created** | Settlement record created; awaiting fund transfer |
| **Funded** | Payer has confirmed fund transfer; awaiting payee receipt confirmation |
| **Settled** | Settlement complete; assets delivered to investor |
| **Repayment Initiated** | Issuer has declared a repayment (repayment flow only) |
| **Partially Settled** | Partial repayment confirmed; balance remains |
| **Settled Late** | Repayment cleared after the target settlement date |
| **Defaulted** | Issuer declared default on the deal |
| **In Recovery** | Investor-initiated recovery (reserved for future use) |
| **Written Off** | Asset written off (reserved for future use) |

### Rail (On-Chain) Status

| Status | Description |
|--------|-------------|
| **READY** | Rail initialized, ready to begin |
| **IN_PROGRESS** | On-chain transactions executing |
| **DELIVERING** | Assets being transferred to investor wallet |
| **DELIVERED** | All assets successfully delivered |
| **SETTLED** | USDC escrow finalized, funds released |
| **REFUNDED** | Settlement cancelled, USDC returned to investor |
| **FAILED** | Settlement failed (admin can retry) |

### NFT Status

| Status | Context | Description |
|--------|---------|-------------|
| **TRANSFERRED** | Purchase flow | Assets delivered from escrow to investor wallet |
| **HELD** | Repayment flow | NFT held by investor during active repayment period |
| **BURN_PENDING** | Repayment flow | Repayment settled; awaiting investor NFT burn |
| **BURNED** | Repayment flow | Investor has burned the NFT, completing the lifecycle |

### Lock Status (Stablecoin Escrow)

| Status | Description |
|--------|-------------|
| **IDLE** | No lock active |
| **LOCKING** | Collateral being locked in escrow |
| **LOCKED** | Collateral locked; settlement can proceed |
| **LOCK_FAILED** | Lock attempt failed |
| **UNLOCKING** | Assets being returned to issuer (timeout or cancellation) |
| **UNLOCKED** | Assets returned; escrow released |
| **UNLOCK_FAILED** | Unlock attempt failed |

## Settlement Activity Timeline

The settlement details section maintains a complete activity log showing every confirmation, transfer, and status change with timestamps and actor information. This audit trail is accessible to all deal participants.

| Timeline Event | Description |
|----------------|-------------|
| Settlement created | Initial settlement record created |
| Payment document uploaded | Wire confirmation or payment proof uploaded |
| Payment confirmed by payer | Investor confirmed fund transfer |
| Receipt confirmed by payee | Issuer/Paying Agent confirmed receipt |
| Payment rejected by payee | Issuer rejected the payment; investor must retry |
| Assets transferred | NFTs delivered to investor wallet |
| NFT transferred | On-chain NFT ownership transfer recorded |
| Assets returned to issuer | Settlement cancelled; assets reverted |
| Repayment declared by issuer | Issuer initiated repayment |
| Default declared by issuer | Issuer declared default |
| Repayment confirmed by investor | Investor accepted repayment |
| Repayment rejected by investor | Investor rejected repayment; issuer retries |
| NFT retirement pending | Burn process initiated |
| NFT retired | Investor burned the RNFT |

## How the Workflow Progresses

The settlement workflow is sequential — each stage must complete before the next begins. Payment confirmation from both sides is required before NFT transfer can proceed. The platform enforces these gates to ensure that financial and ownership transfers are properly synchronized.

The settlement details page in the deal provides a step-by-step view of the settlement lifecycle, showing which stages are complete, which is current, and which are pending. Each participant can view their specific obligations and status.

## Lifecycle Stepper

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

## Escrow Mechanics (Stablecoin Settlements)

For stablecoin settlements, the platform deploys and manages smart contract escrows:

### USDC Escrow (Ethereum Mainnet / Avalanche C-Chain)
- Holds investor's USDC deposit
- Connected to Wormhole Core Bridge for cross-chain messaging
- Supports: `fundSettlement`, `finalizeSettlement` (after receiving settlement VAA)
- Automatic refund if settlement fails or times out

### Asset Escrow (Avalanche L1 Subnet)
- Holds the issuer's loan asset NFTs as collateral
- Delivers assets in batches to investor wallets
- Cross-chain enabled via Wormhole for USDC release signaling
- Supports: `deliverBatch`, `publishFailure` (for refund flow)

### Cross-Chain Flow
```
Investor deposits USDC → USDC Escrow (Mainnet) → Wormhole VAA
     ↓
Wormhole guardians verify → Asset Escrow (L1) activated
     ↓
Assets delivered to investor wallet (batches of 50)
     ↓
Settlement published on L1 → Wormhole VAA → USDC Escrow finalizes
     ↓
USDC released to issuer wallet
```

### Failure and Refund Flow
If a stablecoin settlement fails or times out:
1. Delivered assets are reverted (returned to issuer wallet)
2. A failure is published on the L1 Asset Escrow
3. A failure VAA is generated via Wormhole
4. The USDC Escrow finalizes with the failure VAA, refunding the investor
5. Settlement status: **REFUNDED**

## Multi-Blockchain Support

The platform is designed for multi-blockchain settlement:

| Platform | Blockchain | Token | Status |
|----------|------------|-------|--------|
| **Avalanche** | Avalanche L1 Subnet | NFT Assets (ERC-721) | Active |
| **Avalanche C-Chain / Ethereum** | EVM Mainnet | USDC (ERC-20) | Active |
| **Solana** | Solana | XFT (Compressed NFTs) | In Development |

**Solana/XFT Integration (In Development):**
- XFT minting on Solana for settlement demands
- Investor receives XFT tokens in their Solana receiver vault
- Payment cannot start until XFT minting completes
- Lock window with automatic return of FT collateral if payment is not completed
- Email notifications: "XFT Minted" alerts with payment deadline

## Wallet Onboarding for Settlement

Before participating in stablecoin settlement, users must complete wallet onboarding:

1. **Settlement Chain Confirmation** — Confirm the settlement blockchain (e.g., "Avalanche Fuji Testnet" in test, "Ethereum Mainnet" in production). Settlement token: **USDC (ERC-20) · 1:1 USD parity**
2. **Wallet Verification** — Connect and verify your MetaMask wallet address. This becomes your **verified settlement wallet** used for all stablecoin settlements
3. **Legal Acknowledgement** — Accept the platform's settlement terms

The verified wallet address is stored on your organization profile and cannot be changed without admin intervention.

## Circle Pay-Ins Integration

Organizations can optionally enable **Circle** for managing pay-ins:

- **Pay-Ins via Circle**: When enabled, Circle's wire instructions are provided during settlement
- **Pay-Outs via Circle**: When enabled, Circle handles fund disbursement
- Payment type defaults to **Wire** when Circle is enabled
- Circle integration is configured in the organization's **Payment Settings** (Profile → Payment Settings)

## Important Points to Know

**Per-Investor Tracking** — Settlement is tracked individually for each investor. Different investors may be at different stages of the settlement process simultaneously. Each investor's participant record includes their payment type, escrow state, wallet address, and confirmation status.

**Irreversibility** — Once NFT transfer is complete and the deal is Active, the settlement cannot be reversed. Any corrections would need to be handled through the repayment or administrative workflows.

**MFA for NFT Transfer** — The issuer must complete MFA verification before initiating NFT transfer (bank wire settlements). This adds a security gate to prevent unauthorized asset transfers.

**Settlement Resumability** — Stablecoin settlements are designed to be resumable. If the platform restarts during settlement, in-progress and delivering settlements are automatically resumed on startup. Failed settlements can be retried by an admin via `/settlements/retry-failed`.

**Counterparty Roles** — The payee (fund receiver) can be either the Issuer directly or a **Paying Agent** acting on behalf of the issuer. The UI dynamically labels wallet addresses based on the counterparty role (e.g., "Issuer receiving wallet" or "Paying Agent receiving wallet").

**Product Flow Isolation** — The settlement engine is shared between **Whole Loan Sale** and **Securitization** product lines. However, UI rules and status logic are isolated per product flow to prevent cross-contamination. The system infers the flow from the transaction type ("Whole Loan Sale" vs "Securitization") or subject type ("Deal" vs "Tranche").

**Idempotency** — Settlement API calls are idempotent. Retrying a confirmation or deposit will not duplicate the action. The escrow contracts enforce single-use deposit per settlement ID.
