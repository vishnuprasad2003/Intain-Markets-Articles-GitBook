---
title: Asset Sale Statuses
description: >-
  Lookup of Asset Sale deal, settlement, and NFT statuses — who can act and what
  happens next
---

# Asset Sale Statuses

→ Back to [Asset Sale Deal Lifecycle & Statuses](33_Asset_Sale_Deal_Lifecycle_and_Statuses.md)

## Overview

This is the status lookup for Asset Sale deals. For the story of how a deal moves through these states, see [Deal Lifecycle & Statuses](33_Asset_Sale_Deal_Lifecycle_and_Statuses.md).

## Lifecycle Overview

**Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed**

Exits: **Cancelled** (before settlement), **Defaulted** (from repayment).

Settlement records use **Created, Funded, Settled, Repayment Initiated, Partially Settled, Defaulted**. NFTs use **Transferred, Retirement pending, Retired**.

## Status Meanings

| Status                     | Who acts               | What you can do                                                 | Next                                |
| -------------------------- | ---------------------- | --------------------------------------------------------------- | ----------------------------------- |
| **Draft**                  | Issuer                 | Edit basics, loans, sale terms, agreement; publish or cancel    | Pending Review, Cancelled           |
| **Pending Review**         | Underwriter            | Approve, reject, or cancel. Issuer is read-only.                | Published, Draft, Cancelled         |
| **Published**              | Investors, Underwriter | Investors commit. Underwriter watches incoming amounts.         | Commit, Cancelled                   |
| **Commit**                 | Investors, Underwriter | Submit or update commitments; manage allocation                 | Invest                              |
| **Invest**                 | Selected investor      | Sign the agreement (this status only)                           | Settlement In Progress              |
| **Settlement In Progress** | Investor, Issuer       | Send and confirm funds; issuer starts NFT transfer (bank + MFA) | Settled                             |
| **Settled**                | Platform               | NFTs mint and transfer                                          | Active                              |
| **Active**                 | Issuer, Investor       | Upload loan tape; initiate repayment; view analytics            | Repayment In Progress, Defaulted    |
| **Repayment In Progress**  | Investor, Issuer       | Accept or reject repayment; burn NFTs; record next installment  | Closed, Active (partial), Defaulted |
| **Closed**                 | All (read-only)        | View history and reports                                        | —                                   |
| **Cancelled**              | Issuer / Underwriter   | View history. Limited edit. No reactivation.                    | —                                   |
| **Defaulted**              | Investor               | Confirm default (cannot reject)                                 | —                                   |

**Approved** may appear briefly after underwriter approval before the deal is **Published**. Treat Published as the investor-visible live state.

## What Each Status Indicates

| Status                         | Phase      | Editable?               |
| ------------------------------ | ---------- | ----------------------- |
| Draft                          | Pre-sale   | Yes                     |
| Pending Review                 | Pre-sale   | No (issuer)             |
| Published                      | Pre-sale   | No                      |
| Commit                         | Commitment | No (terms locked)       |
| Invest                         | Commitment | Agreements only         |
| Settlement In Progress         | Settlement | No                      |
| Settled                        | Settlement | No                      |
| Active                         | Post-sale  | Loan tape only          |
| Repayment In Progress          | Closure    | No                      |
| Closed / Cancelled / Defaulted | Terminal   | No (Cancelled: limited) |

**Settlement statuses**

| Status              | Meaning                    |
| ------------------- | -------------------------- |
| Created             | Waiting for funds          |
| Funded              | Payer confirmed funding    |
| Settled             | Assets delivered           |
| Repayment Initiated | Issuer started repayment   |
| Partially Settled   | Partial repayment accepted |
| Defaulted           | Default declared           |

**NFT statuses**

| Status             | Meaning                |
| ------------------ | ---------------------- |
| Transferred        | Investor holds the NFT |
| Retirement pending | Burn is available      |
| Retired            | All NFTs burned        |
