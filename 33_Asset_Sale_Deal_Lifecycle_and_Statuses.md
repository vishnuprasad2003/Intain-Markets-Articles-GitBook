---
title: Asset Sale Deal Lifecycle and Statuses
description: How an Asset Sale deal moves from Draft to Closed, and what each status means
---

# Asset Sale Deal Lifecycle & Statuses

## Overview

Every Asset Sale deal moves through a fixed set of statuses. The current status decides what you can do and who can act. Use this article to follow the path; use [Asset Sale Statuses](70_Asset_Sale_Statuses.md) when you need a status-by-status lookup.

## Lifecycle Overview

**Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed**

Terminal exits: **Cancelled** (before settlement) and **Defaulted** (from repayment).

**Pre-sale** — The issuer creates the deal in **Draft**, then publishes it. The underwriter reviews it in **Pending Review**. Approve moves the deal to **Published**. Reject returns it to **Draft**. Cancel at this stage moves it to **Cancelled**.

**Commitment** — Investors submit amounts (**Commit**). The underwriter finalizes allocation (**Invest**). Investor agreement signing is allowed only in **Invest**.

**Settlement** — After signing, the deal enters **Settlement In Progress**. Each investor’s settlement moves **Created → Funded → Settled**. When transfers finish, the deal is **Settled**, NFTs move to investors, and the deal becomes **Active**.

**Post-sale** — The issuer uploads loan tapes and can initiate repayment (**Repayment In Progress**). The investor accepts or rejects. After a full repayment is accepted, the investor burns the NFT (**Transferred → Retirement pending → Retired**). When all NFTs are retired, the deal is **Closed**.

![Deal Lifecycle Stepper](images/33-asset-sale-deal-lifecycle-and-statuses/deal-lifecycle-stepper.png)

## Status Meanings

| Status | Meaning |
|--------|---------|
| **Draft** | Issuer is building the deal. Basics, loans, sale terms, and the sale agreement can be edited. Visible to the issuer only. |
| **Pending Review** | Submitted to the underwriter. Issuer cannot edit. Underwriter can approve, reject, or cancel. |
| **Published** | Approved and visible to investors (All or Selected). Investors can review and commit. |
| **Commit** | Commitments are open. Sale terms and loan assignment are locked. |
| **Invest** | Allocation is final. This is the only status where the investor agreement can be signed. |
| **Settlement In Progress** | Funds are moving. Settlement records track Created → Funded → Settled. |
| **Settled** | Funds confirmed. Receivables NFTs are minted and transferred. |
| **Active** | Investors hold NFTs. Issuer can upload loan tapes and initiate repayment. |
| **Repayment In Progress** | Issuer has recorded a repayment. Investor must accept, reject, or confirm default. |
| **Closed** | Fully repaid and all NFTs retired. Read-only. |
| **Cancelled** | Stopped before settlement. Kept for audit. Not reactivated. |
| **Defaulted** | Issuer declared default and the investor confirmed it. Permanent. |

## What Each Status Indicates

**You can edit** only in **Draft** (and limited fields in **Cancelled**). After publish, change the package by getting a reject back to Draft.

**Investors first see the deal** at **Published**. Earlier statuses are hidden from them.

**Signing is gated** — if the deal is not **Invest**, the signing action is blocked.

**Settlement is per investor.** One investor can be Funded while another is still Created.

**Repayment outcomes:**
- Accept a full repayment → NFT burn becomes available → **Closed**
- Accept a partial repayment → deal stays live; issuer can record the next installment
- Reject → issuer can submit again (a reason is required)
- Confirm default → **Defaulted**; reject is not allowed

For who can click what at each status, see [Asset Sale Statuses](70_Asset_Sale_Statuses.md).
