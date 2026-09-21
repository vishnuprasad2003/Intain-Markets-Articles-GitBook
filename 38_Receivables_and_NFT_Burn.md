---
title: Receivables and NFT Burn
description: Step-by-step guide for managing receivables and burning NFTs after asset sale repayment
---

# Receivables & NFT Burn

## Overview

After an asset sale deal is settled, investors hold receivables NFTs that represent their ownership of the loan assets. These NFTs are minted on the blockchain during settlement and transferred to investor wallets. When the deal is fully repaid, investors burn these NFTs to close out their position, completing the asset sale lifecycle. This guide covers the receivables management and NFT burn process.

## Who Can Use This

- **Investors**: View receivables, manage NFT positions, and burn NFTs after repayment
- **Issuers**: Monitor receivables status across their deals

## When This Is Used

Use this process when:
- An asset sale deal has been settled and NFTs have been transferred to investors
- The issuer has completed repayment and the investor has confirmed receipt
- You want to close out your investment position by burning the receivables NFT
- You need to understand what receivables represent and how they work

## Step-by-Step Process

### Part 1: Understanding Receivables

#### Step 1: What Receivables Represent

After settlement of an asset sale deal:
- Receivables NFTs are minted on the blockchain representing the loan assets
- Each NFT contains metadata linking it to the specific loan portfolio in the deal
- The NFT serves as on-chain proof of ownership of the receivable
- Receivables are visible in the deal details under the **Asset Analysis** section

#### Step 2: View Your Receivables

1. Navigate to **Asset Sale** from the left sidebar menu
2. Click on the relevant deal
3. Navigate to **Asset Analysis** → **Receivables** tab
4. View your receivables with details including asset IDs, amounts, and status

![Receivable Level Data](images/38-receivables-and-nft-burn/receivables-data.png)

### Part 2: Burning NFTs After Repayment

#### Step 3: Verify Repayment Completion

Before burning an NFT, ensure:
- The issuer has initiated repayment for the deal
- You have confirmed receipt of the repayment (see Repayment Flow, article 37)
- The repayment amount matches your expected amount

#### Step 4: Initiate the Burn

1. In the **Receivables** tab, locate the NFT to burn
2. Click the **Burn** button next to the receivable
3. A confirmation dialog appears with details of the NFT to be burned

#### Step 5: Confirm the Burn

1. Review the burn details in the confirmation dialog
2. Click **Yes, Burn NFT** to proceed
3. The platform submits the burn transaction to the blockchain
4. The NFT is permanently burned, removing it from your wallet

#### Step 6: Verify Deal Closure

1. After the burn completes, the deal dashboard updates
2. The deal status changes to **Closed** with **Fully Repaid** designation
3. The burn event is recorded in the settlement activity trail

## Rules & Validations

- NFT burn is only available after the investor has confirmed repayment receipt
- Burning an NFT is irreversible — the tokenized position is permanently destroyed
- The burn transaction is recorded on the blockchain with an immutable timestamp
- Only the investor holding the NFT can initiate the burn
- The burn must be completed for the deal to reach Closed status
- Partial burns are not supported — the full receivable position is burned at once

## What Happens Next

After the NFT is burned:
- The deal reaches its final **Closed** status
- The complete audit trail (settlement → repayment → burn) is preserved
- The deal remains accessible in the Asset Sale dashboard for reporting and compliance
- Settlement Details show the full event history including the burn timestamp and transaction hash
