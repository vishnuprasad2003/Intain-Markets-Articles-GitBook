---
title: All Loan States Explained
description: Reference for all loan statuses across mapping, pool context, batch verification, and NFT minting
---

# All Loan States Explained

→ Back to [Loans Overview](10_Loans_Overview.md) · [Loan Lifecycle & Statuses](11_Loan_Lifecycle_and_Statuses.md)

## Mapping Status (Loan Registry)

| Status | Meaning | Next action |
|---|---|---|
| **Unmapped** | In registry, not assigned to any pool | Map to Pool or Add to Batch |
| **Mapped** | Assigned to a pool (shows pool name) | Visible in pool's Loans tab |

## Pool Loan Status (Within a Shared Pool)

| Status | Meaning |
|---|---|
| **Pending** | Pool shared; underwriter / facility agent has not yet accepted mandate |
| **Accepted** | Mandate accepted; loan confirmed in pool; feedback and removal requests allowed |
| **Under Reconsider** | Recipient requested removal; shown to the underwriter / facility agent / investor |
| **Reconsider** | Removal request received; shown to the issuer — tick to accept removal, cross to reject |
| **Removed** | Issuer accepted removal; loan excluded from pool calculations |
| **Reinstated** | Previously removed loan put back; included in calculations again |

> When a loan is Removed or Reinstated, pool metrics (balance, count, weighted averages) recalculate automatically.

## Batch Verification Status

| Status | Mint NFT available? | Meaning |
|---|---|---|
| **Pending** | No | Batch created; verification not complete |
| **Reviewed** | Yes | Self-certification or agent verification complete |
| **Verified** | No (already done) | All loans in batch have been minted |

## Verification Status

| Status | Meaning |
|---|---|
| **No** | Not yet verified |
| **Certified** | Third-party verification agent certified the batch |
| **Self Certified** | Issuer verified in verification agent role |
| **Self Certify (Data Only)** | Issuer used Self Certify button + Adobe Sign |

## NFT Loan Status

| Status | Meaning |
|---|---|
| **Not Minted** | Loan has no blockchain token yet |
| **Minted** | Tokenized on-chain; eligible for credit facility mapping |

## Quick Lookup

| Question | Check |
|---|---|
| Can this loan be mapped to a pool? | Mapping Status = **Unmapped** |
| Can this loan be minted as NFT? | Batch Verification Status = **Reviewed** and NFT Status = **Not Minted** |
| Can this loan be used in a credit facility? | NFT Status = **Minted** |
| Why did pool metrics change? | Check if a loan was **Removed** or **Reinstated** in the pool's Loans tab |
