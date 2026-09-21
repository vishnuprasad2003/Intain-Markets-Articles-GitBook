---
title: All Loan States Explained
description: Comprehensive reference for all possible loan statuses and what each means
---

# All Loan States Explained

## Overview

This comprehensive reference guide explains all possible loan statuses in the platform. Loans have multiple status dimensions that track their progression through onboarding, pool mapping, verification, and tokenization. Understanding these statuses helps you know where loans are in their lifecycle, what actions are available, and what to expect next.

## Lifecycle Overview

Loans progress through several stages, each with its own status tracking:

**Onboarding Stage**
```
Upload file → Trigger LTS → Map fields → Save mapping → Loans in Registry (Unmapped)
```

**Pool Mapping Stage**
```
Unmapped → Map to Pool → Mapped (Status shows pool name)
```

**Pool Sharing Stage (within pools)**
```
Mapped → Pool shared, MM accepts → Accepted
Accepted → MM requests removal → Under Reconsider / Reconsider
Reconsider → Issuer accepts → Removed
Reconsider → Issuer rejects → Accepted (stays in pool)
Removed → Reinstate → Reinstated
```

**Verification Stage (batches)**
```
Added to Batch → Pending → Self Certify / Verification Agent → Reviewed
```

**NFT Minting Stage**
```
Reviewed → Mint NFT → Verified (all loans minted)
Not Minted → Mint NFT → Minted
```

## Status Categories

Loans have several status fields that track different aspects:

| Category | Status Field | Purpose |
|----------|-------------|---------|
| Mapping Status | Status | Tracks whether loan is mapped to a pool |
| Pool Loan Status | Loan status within pool | Tracks acceptance, removal, reinstatement |
| Batch Verification Status | Batch Verification Status | Tracks verification progress of batch |
| Verification Status | Verification Status | Tracks how verification was done |
| NFT Status | nftLoanStatus | Tracks tokenization status |

## Mapping Status (Loan Registry)

### Unmapped

**Meaning**: The loan has been onboarded and standardized but is not assigned to any pool.

**When This Occurs**:
- After loan tape standardization is saved
- After a loan is unmapped from a pool

**What You Can Do**:
- View loan details in Loan Registry
- Select and Map to Pool
- Select and Add to Batch
- Delete (only if not in batch)

**What This Indicates**:
- Loan is available for assignment
- Loan does not contribute to any pool metrics
- Loan data is stored in your organization's database

### Mapped (Shows Pool Name)

**Meaning**: The loan is assigned to a pool. The Status column shows "Mapped".

**When This Occurs**:
- After selecting loans and using Map to Pool from Loan Registry

**What You Can Do**:
- View loan in pool's Loans tab
- Loan participates in pool calculations
- Loan can receive feedback (via chat box)
- Loan can be subject to removal requests

**What This Indicates**:
- Loan is part of a specific pool
- Pool metrics include this loan
- Loan is tied to that pool's workflow

## Pool Loan Statuses (Within Pool Context)

These statuses apply when viewing loans in a pool's Loans tab after the pool has been shared.

### Pending

**Meaning**: The loan is mapped to a shared pool, but the recipient (market maker) has not yet accepted the mandate.

**When This Occurs**:
- Pool is shared with market makers (Preview flow)
- Market maker has not yet clicked Accept

**What This Indicates**:
- Waiting for market maker decision
- Loan is in limbo until mandate is accepted
- Once accepted, status progresses to Accepted

### Accepted

**Meaning**: The loan is confirmed as part of the pool after the market maker accepted the mandate.

**When This Occurs**:
- Market maker clicks Accept on the mandate
- All loans in the pool move to Accepted status

**What You Can Do**:
- Market makers and investors can request removal
- Feedback can be provided via chat box

**What This Indicates**:
- Loan is confirmed in the pool
- Recipients can now provide feedback and request removals
- Normal pool operations continue

### Under Reconsider (Market Maker / Investor View)

**Meaning**: This market maker or investor has requested removal of this loan. Waiting for issuer decision.

**When This Occurs**:
- Market maker or investor clicked the cross icon to request removal

**What This Indicates**:
- A removal request has been submitted
- The issuer will decide whether to accept or reject
- Loan remains in calculations until decision is made

### Reconsider (Issuer View)

**Meaning**: A market maker or investor has requested removal of this loan. The issuer needs to decide.

**When This Occurs**:
- A recipient clicked the cross icon to request removal

**What You Can Do**:
- Click **tick icon**: Accept removal (loan becomes Removed)
- Click **cross icon**: Reject removal (loan stays in pool)

**What This Indicates**:
- Action required from issuer
- Review the request and make decision
- Loan remains in calculations until decision

### Removed

**Meaning**: The loan has been removed from pool calculations after the issuer accepted a removal request.

**When This Occurs**:
- Issuer clicked the tick icon on a Reconsider loan

**What This Indicates**:
- Loan is excluded from pool metrics
- Pool metrics have been recalculated without this loan
- Loan remains visible for tracking
- Loan can be reinstated if needed

**Pool Impact**:
- Total balance decreases
- Loan count decreases
- Weighted averages recalculate

### Reinstated

**Meaning**: A previously removed loan has been put back into the pool.

**When This Occurs**:
- Issuer reinstates a removed loan

**What This Indicates**:
- Loan is back in pool calculations
- Pool metrics have been recalculated to include this loan
- Loan fully participates in the pool again

**Pool Impact**:
- Total balance increases
- Loan count increases
- Weighted averages recalculate

## Batch Verification Statuses

### Pending

**Meaning**: The batch has been created but verification is not complete.

**When This Occurs**:
- Loans are added to a new batch
- Initial state of all batches

**What You Can Do**:
- Self Certify
- Submit to verification agent
- Upload documents

**In Certificates Section**:
- View NFT: Disabled
- Mint NFT: Disabled

### Reviewed

**Meaning**: The batch verification process is complete.

**When This Occurs**:
- After self-certification is completed
- After verification agent certifies the batch

**What You Can Do**:
- Proceed to NFT minting
- View batch details

**In Certificates Section**:
- View NFT: Enabled
- Mint NFT: Enabled

### Verified

**Meaning**: All loans in the batch have been minted as NFTs.

**When This Occurs**:
- After all loans in the batch are minted

**What You Can Do**:
- View minted NFTs
- Loans are eligible for credit facility mapping

**In Certificates Section**:
- View NFT: Enabled
- Mint NFT: Disabled (already complete)

## Verification Status

### No

**Meaning**: The batch has not been verified yet.

**When This Occurs**:
- Initial state of all batches

### Certified

**Meaning**: A third-party verification agent verified the batch.

**When This Occurs**:
- Verification agent completes verification

**What This Indicates**:
- Independent verification by external party
- Higher assurance level

### Self Certified

**Meaning**: The issuer logged in as verification agent and verified the batch.

**When This Occurs**:
- Issuer switches to verification agent role and verifies

**What This Indicates**:
- Issuer performed verification in verification agent capacity
- Self-verification by role switch

### Self Certify (Data Only)

**Meaning**: The issuer used the Self Certify button directly from batch details.

**When This Occurs**:
- Issuer clicks Self Certify and completes e-signature

**What This Indicates**:
- Quick self-certification option
- Completed via Adobe Sign e-signature

## NFT Loan Status

### Not Minted

**Meaning**: The loan has not been tokenized yet.

**When This Occurs**:
- Initial state after loan is added to batch
- Batch verification is pending or reviewed but minting not started

**What You Can Do**:
- Complete batch verification first (if pending)
- Use Mint NFT to start tokenization (if reviewed)

**What This Indicates**:
- Loan does not have blockchain representation
- Not eligible for credit facility mapping

### Minted

**Meaning**: The loan has been tokenized as an NFT on the blockchain.

**When This Occurs**:
- After clicking Mint Selected and minting completes

**What This Indicates**:
- Loan has digital token on blockchain
- Loan is eligible for credit facility mapping
- Loan can be used in master commitment transactions

## Quick Reference

**Want to know if a loan can be mapped to a pool?**
- Check Mapping Status: Must be "Unmapped"

**Want to know if a loan can be minted as NFT?**
- Check Batch Verification Status: Must be "Reviewed"
- Check NFT Status: Must be "Not Minted"

**Want to know if a loan can be used in credit facility?**
- Check NFT Status: Must be "Minted"

**Want to know why pool metrics changed?**
- A loan may have been Removed or Reinstated
- Check Loan Status in pool's Loans tab

**Want to know who verified a batch?**
- Check Verification Status: Certified (third party), Self Certified (issuer as VA), Self Certify (Data Only) (issuer directly)
