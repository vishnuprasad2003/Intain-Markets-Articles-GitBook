---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where loans are in their lifecycle, what actions are available, and what comes next. This guide explains the loan journey from upload through verification and NFT minting.

## Lifecycle Overview

Loans follow this general progression:

**Onboarding Stage**: Upload loan tape file → Trigger LTS → Map fields → Save mapping → View in Loan Registry

**Pool Mapping Stage**: Select loans in Loan Registry → Map to Pool → Loans contribute to pool metrics

**Verification Stage**: Add loans to batch → Self Certify or submit to Verification Agent → Batch verified

**NFT Minting Stage**: View batch in Certificates → Mint NFT → Loans tokenized on blockchain

Throughout this journey, loans have different statuses that indicate their current state and what actions are possible.

## Status Meanings

### Loan Mapping Status

**Unmapped**

The loan has been onboarded and exists in the Loan Registry but is not assigned to any pool. This is the initial state after loan tape standardization is complete.

- The loan is available for mapping to pools
- The loan does not contribute to any pool metrics
- You can select this loan in the Loan Registry and click Map to Pool
- You can select this loan and click Add to Batch for verification

**Mapped**

The loan has been assigned to a pool from the Loan Registry. The loan is part of a pool and contributes to pool calculations.

- Pool metrics include this loan's balance and characteristics
- The loan appears in the pool's Loans tab
- The loan can be subject to removal requests from market makers or investors
- In the Loan Registry, the Status column shows "Mapped"

### Loan Status Within Pools

When loans are mapped to pools and the pool is shared with other parties, additional statuses track loan acceptance and removal:

**Pending**

The loan is mapped to a pool that has been shared, but the market maker hasn't yet accepted the Preview mandate.

- Loan is waiting for market maker's decision
- Once market maker accepts, loan status progresses

**Accepted**

The loan's inclusion in the pool has been confirmed after the market maker accepts the mandate.

- Loan is confirmed as part of the pool composition
- Market maker or investor can now request removal if needed

**Under Reconsider / Reconsider**

A market maker or investor has requested removal of this loan from the pool. The issuer needs to decide whether to accept or reject the removal request.

- **Market Maker/Investor view**: Shows as "Under Reconsider"
- **Issuer view**: Shows as "Reconsider" with tick (accept) and cross (reject) icons in the Loans tab
- The loan remains in pool calculations until the issuer makes a decision

**Removed**

The loan has been removed from the pool after the issuer accepted a removal request (clicked the tick icon).

- Loan is excluded from pool calculations
- Pool metrics automatically recalculate without this loan
- Loan remains visible in the pool for tracking purposes
- Loan can potentially be reinstated

**Reinstated**

A previously removed loan has been put back into the pool and is included in calculations again.

- Loan is back in pool calculations
- Pool metrics recalculate to include this loan
- Loan fully participates in the pool

### Batch Verification Status

Loans added to batches have verification-related statuses:

**Pending**

The batch has been created but verification has not been completed.

- Loans are grouped in the batch
- Self Certify and verification agent options are available
- NFT minting is not yet enabled

**Reviewed**

The batch verification process has been completed (self-certified or verified by verification agent).

- Loans have passed the verification stage
- NFT minting is now enabled for these loans
- Both View NFT and Mint NFT buttons are active in Certificates section

**Verified**

All loans in the batch have been minted as NFTs.

- NFT minting is complete
- Only View NFT button is enabled
- Loans are tokenized on the blockchain

### Verification Status

The verification status indicates how the loans were verified:

**No**

Initial status. The batch has not been verified yet.

**Certified**

The batch was verified by a third-party verification agent (not the issuer).

**Self Certified**

The issuer logged in as a verification agent and verified the batch themselves.

**Self Certify (Data Only)**

The issuer used the Self Certify button directly in the batch details (without logging in as verification agent).

### NFT Loan Status

**Not Minted**

The loan has not been minted as an NFT yet. The loan is either not in a verified batch, or minting has not been initiated.

**Minted**

The loan has been minted as an NFT on the blockchain. The loan now has a digital token representation and can be used in credit facility transactions.

## What Each Status Indicates

### Unmapped Status Indicates

- The loan is in the Loan Registry and available for assignment
- You can map this loan to any pool using the Map to Pool button
- The loan doesn't affect any pool metrics yet
- This is the starting point for newly onboarded loans

### Mapped Status Indicates

- The loan is part of a specific pool
- Pool metrics include this loan
- In pool details, this loan appears in the Loans tab
- The Status column in Loan Registry shows the pool name

### Under Reconsider / Reconsider Status Indicates

- Someone has requested this loan be removed from the pool
- As issuer, you see tick and cross icons to accept or reject the request
- The loan is still in pool calculations until you decide
- This requires your attention and decision

### Removed Status Indicates

- The loan was removed from pool calculations (you accepted a removal request)
- Pool metrics have been updated without this loan
- The loan is still visible for record-keeping
- You can potentially reinstate this loan later

### Pending (Batch) Status Indicates

- The batch is waiting for verification
- You can self-certify or submit to verification agent
- NFT minting is not yet available
- Complete verification to proceed

### Reviewed (Batch) Status Indicates

- Verification is complete
- NFT minting is now available
- Click Mint NFT in Certificates section to tokenize loans

### Verified (Batch) Status Indicates

- All loans have been minted as NFTs
- Tokenization is complete
- Loans can now be used in credit facilities (if NFTs minted)

## Status Transitions Summary

| From | Action | To |
|------|--------|-----|
| (Uploaded) | Save Mapping | Unmapped |
| Unmapped | Map to Pool | Mapped (shows pool name) |
| Mapped | Pool shared, MM accepts | Accepted |
| Accepted | MM/Investor requests removal | Under Reconsider / Reconsider |
| Reconsider | Issuer clicks tick | Removed |
| Reconsider | Issuer clicks cross | Accepted (remains in pool) |
| Removed | Reinstate action | Reinstated |
| (In Batch) | Created | Pending |
| Pending | Self Certify / Verified | Reviewed |
| Reviewed | Mint NFT | Verified |
