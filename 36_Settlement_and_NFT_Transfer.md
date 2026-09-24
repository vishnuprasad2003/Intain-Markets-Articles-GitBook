---
title: Settlement and NFT Transfer
description: >-
  How Asset Sale settlement works across bank wire, stablecoin, and planned
  Kinexys rails
---

# Settlement & NFT Transfer

## Overview

Settlement is the exchange of funds and ownership. Investors pay; the issuer receives payment; receivables NFTs move to investor wallets. When that finishes, the deal becomes **Active**.

## Workflow Overview

Settlement is created per investor after agreements are signed. The method is chosen at **Confirm and Settle**. Each investor can be at a different stage.

| Role            | What they do                                                                 |
| --------------- | ---------------------------------------------------------------------------- |
| **Investor**    | Chooses the rail, sends funds, confirms (bank) or deposits USDC (stablecoin) |
| **Issuer**      | Confirms receipt (bank) and starts NFT transfer (MFA required on bank)       |
| **Underwriter** | Watches progress and the activity trail                                      |

## Key Stages

### Payment rails

| Feature          | Bank (Wire/ACH)              | Stablecoin (USDC)           | Kinexys                        |
| ---------------- | ---------------------------- | --------------------------- | ------------------------------ |
| **Status**       | Active                       | Active                      | Planned (uses bank flow today) |
| **Speed**        | 1–3 days                     | Minutes                     | —                              |
| **Lock timeout** | 3 days                       | 24 hours                    | 3 days                         |
| **Wallet**       | Not required                 | MetaMask (verified address) | —                              |
| **NFT delivery** | Issuer starts transfer (MFA) | Automatic via escrow        | —                              |

**Bank** — Investor wires funds, uploads a confirmation, and clicks **Confirm Payment**. Issuer confirms receipt, then starts NFT transfer after MFA.

**Stablecoin** — Investor connects MetaMask (must match the verified settlement address), approves USDC, and deposits into escrow. Assets deliver automatically. Escrow refunds if settlement is not finished in 24 hours. Wallet needs USDC plus gas (AVAX or ETH).

**Kinexys** — Registered for a future JP Morgan rail. Not active yet.

### Purchase flow

1. **Start** — Deal moves to **Settlement In Progress**. One settlement record is created per investor.
2. **Fund** — Bank: wire + confirm. Stablecoin: deposit USDC. Status **Created → Funded**.
3. **Deliver** — Bank: issuer transfers NFTs after MFA. Stablecoin: escrow delivers NFTs and releases USDC.
4. **Activate** — When all transfers finish, the deal is **Settled**, then **Active**.

### Settlement and NFT statuses

| Settlement              | Meaning                                                   |
| ----------------------- | --------------------------------------------------------- |
| **Created**             | Waiting for funds                                         |
| **Funded**              | Investor funded; issuer confirmation may still be pending |
| **Settled**             | Assets delivered                                          |
| **Repayment Initiated** | Issuer started repayment                                  |
| **Partially Settled**   | Partial repayment accepted                                |
| **Defaulted**           | Default declared                                          |

| NFT                    | Meaning                               |
| ---------------------- | ------------------------------------- |
| **Transferred**        | Investor holds the NFT                |
| **Retirement pending** | Repayment accepted; burn is available |
| **Retired**            | NFT burned; position closed           |

## How the Workflow Progresses

Agreements signed → settlement records created → funds move → NFTs transfer → **Active**. The Settlement Activity timeline logs every confirmation for audit.

## Important Points to Know

* Settlement cannot be reversed after the deal is **Active**.
* Stablecoin settlements can resume if interrupted; an admin can retry a failed run.
* Before using stablecoin, verify the MetaMask address on the organization profile and accept settlement terms.

![Settlement Activity](.gitbook/assets/settlement-activity.png)

See [Repayment Flow](37_Repayment_Flow.md) for the post-sale path.
