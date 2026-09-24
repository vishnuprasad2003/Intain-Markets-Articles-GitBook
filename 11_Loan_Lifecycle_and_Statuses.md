---
title: Loan Lifecycle and Statuses
description: Stages loans go through from upload through NFT minting
---

# Loan Lifecycle & Statuses

## Lifecycle at a Glance

```
Upload tape → Trigger LTS → Map fields → Loan Registry → Map to Pool → Add to Batch → Self Certify / Verify → Mint NFT
```

## Mapping Status

| Status | Meaning | Next action |
|---|---|---|
| **Unmapped** | In Loan Registry; not in any pool | Map to Pool |
| **Mapped** | In a pool; included in pool metrics | Add to Batch |

## Loan Status Within Pools

| Status | Meaning | Who decides |
|---|---|---|
| **Pending** | Pool shared; market maker not yet accepted | — |
| **Accepted** | Mandate accepted; loan confirmed in pool | — |
| **Reconsider** (issuer view) / **Under Reconsider** (others) | Removal requested | Issuer (tick/cross) |
| **Removed** | Issuer accepted removal; excluded from metrics | Reinstated by issuer |
| **Reinstated** | Previously removed; back in metrics | — |

> Loan stays in pool calculations during **Reconsider/Under Reconsider** until issuer decides.

## Batch Verification Status

| Status | Meaning | Available actions |
|---|---|---|
| **Pending** | Batch not verified; awaiting certification | Self Certify, send to verification agent |
| **Reviewed** | Verified/certified; ready to mint | Mint NFT |
| **Verified** | All loans minted | View NFT |

## NFT Status

| Status | Meaning |
|---|---|
| **Not Minted** | No NFT yet |
| **Minted** | NFT exists; loan can be mapped to a credit facility |

## Status Transitions

| From | Action | To |
|---|---|---|
| (uploaded) | Save Mapping | Unmapped |
| Unmapped | Map to Pool | Mapped |
| Mapped | Pool shared, market maker accepts | Accepted |
| Accepted | Removal requested | Under Reconsider / Reconsider |
| Reconsider | Issuer accepts (tick) | Removed |
| Reconsider | Issuer rejects (cross) | Accepted |
| Removed | Reinstate | Reinstated |
| (in batch) | Add to Batch | Pending |
| Pending | Self Certify or verification agent | Reviewed |
| Reviewed | Mint NFT | Verified |

→ See [Loans Overview](10_Loans_Overview.md) for how loans are managed on screen.
→ See [Loan Rejection and Reinstatement](12_Loan_Rejection_and_Reinstatement.md) for how removal requests work.
