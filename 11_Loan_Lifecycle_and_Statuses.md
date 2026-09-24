---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

A loan’s status shows where it is, which actions are available, and what comes next. This guide covers the path from upload through verification and NFT minting.

## Lifecycle Overview

**Onboarding** — Upload the loan tape, click **Trigger LTS**, match fields, save, then open the Loan Registry.

**Pool mapping** — Select loans and click **Map to Pool**. Those loans count in the pool’s metrics.

**Verification** — Add loans to a batch, then **Self Certify** or send the batch to a verification agent.

**NFT minting** — Open the batch in **Certificates** and click **Mint NFT**.

## Status Meanings

### Loan Mapping Status

**Unmapped**

The loan is in the Loan Registry and is not in a pool. This is the state after you save field mapping.

- You can map it to a pool
- It does not affect any pool’s metrics
- You can add it to a batch

**Mapped**

The loan is in a pool and counts in that pool’s calculations.

- The pool’s Loans tab includes it
- A market maker or investor can ask for it to be removed
- The Loan Registry Status column shows **Mapped**

### Loan Status Within Pools

These statuses appear after the pool is shared.

**Pending**

The loan is in a shared pool, and the market maker has not accepted the preview mandate yet.

**Accepted**

The market maker accepted the mandate, so the loan stays in the pool. A market maker or investor can still request removal.

**Under Reconsider / Reconsider**

Someone requested removal. The issuer decides whether to accept or reject that request.

- Market makers and investors see **Under Reconsider**
- The issuer sees **Reconsider**, with a tick to accept removal and a cross to reject it
- The loan stays in pool calculations until the issuer decides

**Removed**

The issuer accepted the removal request.

- The loan is left out of pool calculations
- Metrics update without it
- It stays visible for tracking
- It can be reinstated

**Reinstated**

A removed loan is back in the pool and counts in calculations again.

### Batch Verification Status

**Pending**

The batch exists and is not verified yet. Self Certify and the verification agent path are available. NFT minting is off.

**Reviewed**

The batch was self-certified or verified by a verification agent. **View NFT** and **Mint NFT** are on in Certificates.

**Verified**

Every loan in the batch has been minted. Only **View NFT** is on.

### Verification Status

**No** — The batch is not verified yet.

**Certified** — A third-party verification agent verified the batch.

**Self Certified** — The issuer signed in as a verification agent and verified the batch.

**Self Certify (Data Only)** — The issuer used **Self Certify** on the batch directly.

### NFT Loan Status

**Not Minted** — The loan has no NFT yet. It may not be in a reviewed batch, or minting has not been started.

**Minted** — The loan has an NFT and can be used in a credit facility.

## What Each Status Indicates

### Unmapped

The loan is available in the Loan Registry. **Map to Pool** assigns it. It does not affect pool metrics yet.

### Mapped

The loan belongs to one pool and is included in that pool’s metrics. It appears on the pool’s Loans tab. The Loan Registry can show the pool name.

### Under Reconsider / Reconsider

Someone asked to remove the loan. As issuer, use the tick or the cross. Until you decide, the loan still counts in the pool.

### Removed

You accepted a removal request. Metrics no longer include the loan. It remains visible, and you can reinstate it later.

### Pending (batch)

The batch is waiting for verification. Self-certify it or send it to a verification agent. Minting is not available yet.

### Reviewed (batch)

Verification is done. Open Certificates and click **Mint NFT**.

### Verified (batch)

Minting is finished. Loans with NFTs can be mapped to a credit facility.

## Status Transitions Summary

| From | Action | To |
|------|--------|-----|
| (Uploaded) | Save Mapping | Unmapped |
| Unmapped | Map to Pool | Mapped (shows pool name) |
| Mapped | Pool shared, market maker accepts | Accepted |
| Accepted | Market maker or investor requests removal | Under Reconsider / Reconsider |
| Reconsider | Issuer clicks the tick | Removed |
| Reconsider | Issuer clicks the cross | Accepted (stays in the pool) |
| Removed | Reinstate | Reinstated |
| (In batch) | Batch created | Pending |
| Pending | Self Certify or verification agent | Reviewed |
| Reviewed | Mint NFT | Verified |
