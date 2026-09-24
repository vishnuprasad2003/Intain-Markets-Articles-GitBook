---
title: All Pool States Explained
description: Reference for all pool statuses and loan statuses within a pool
---

# All Pool States Explained

→ Back to [Pools Overview](05_Pools_Overview.md) · [Pool Lifecycle & Statuses](06_Pool_Lifecycle_and_Statuses.md)

## Pool Status — Issuer View

| Status | Meaning | Editing allowed? |
|---|---|---|
| **Created** | Pool is private; visible only to issuer | Yes — full editing |
| **Preview** | Shared via Preview; recipients reviewing; issuer can still edit | Yes |
| **Deal** | Committed via Start Deal; structure locked | No |

## Pool Status — Recipient View

| Status | Who sees it | Meaning | Actions |
|---|---|---|---|
| **Mandate Pending** | Market maker / investor | Preview share received; not yet decided | View, Accept, Reject |
| **Under Review** | Market maker / investor | Mandate accepted | Feedback, loan removal, share with investors |
| **Ready for Deal** | Market maker | Start Deal sent | View, Accept, Reject |

> Underwriters / Facility Agents cannot provide feedback until they accept the mandate.

## Status Transitions

| From | Action | To | Who |
|---|---|---|---|
| (new) | Create Pool | Created | Issuer |
| Created | Share (Preview) | Preview | Issuer |
| Created or Preview | Start Deal | Deal | Issuer |
| Mandate Pending | Accept | Under Review | Underwriter / Facility Agent |
| Mandate Pending | Reject | Can be re-shared | Underwriter / Facility Agent |
| Ready for Deal | Accept | Deal confirmed | Underwriter / Facility Agent |
| Ready for Deal | Reject | Can be re-shared | Underwriter / Facility Agent |

## Editing Rights by Status

| Status | Issuer can edit | Recipient actions |
|---|---|---|
| Created | Yes, fully | Not visible |
| Preview | Yes, fully | View, Accept/Reject, feedback after accept |
| Under Review (MM view) | Yes, fully | Feedback, removal requests, share to investors |
| Deal | No | View and deal structuring |

## Loan Statuses Inside a Pool

| Status | Meaning |
|---|---|
| **Mapped** | Loan is in pool; counts in metrics |
| **Pending** | Market maker has not accepted mandate yet |
| **Accepted** | Mandate accepted; loan confirmed |
| **Under Reconsider** | Removal requested (underwriter / facility agent / investor view) |
| **Reconsider** | Removal requested; awaiting issuer decision (issuer view) |
| **Removed** | Issuer accepted removal; loan excluded from metrics but still visible |
| **Reinstated** | Previously removed loan put back; included in metrics |
