---
title: Deal Creation and Publishing
description: >-
  Create an Asset Sale deal in the 3-step wizard, assign loans, set sale terms,
  and publish for review
---

# Deal Creation & Publishing

## Overview

The issuer creates an Asset Sale deal in a 3-step wizard, assigns loans, sets sale terms, optionally uploads a sale agreement, then publishes the deal for underwriter review.

## Who Can Use This

* **Issuers** — create, edit, and publish
* **Underwriters (Market Makers)** — approve or reject after publish

## When This Is Used

Use this when you are packaging loans to sell and need a deal ready for underwriter review and investor distribution.

## Step-by-Step Process

### 1. Open the wizard

1. Go to **Asset Sale** in the sidebar and click **Create Deal**.
2. The wizard has three tabs: **Basics**, **Pool Selection**, and **Sale Terms**.

### 2. Basics

| Field                          | Notes                                                                           |
| ------------------------------ | ------------------------------------------------------------------------------- |
| **Deal Name**                  | Required. Unique, descriptive. Read-only after the deal is created from Review. |
| **Transaction Type**           | Always **Asset Sale** (read-only).                                              |
| **Sale Route**                 | **Marketed** (default, multiple investors) or **Bilateral** (one investor).     |
| **Target Settlement Date**     | Cannot be in the past, or before cutoff / settlement dates already set.         |
| **Governing Law**              | Free text (for example, New York).                                              |
| **Buyer Visibility**           | **All** (default) or **Selected** (then pick investor organizations).           |
| **Arranger / Placement Agent** | Required. Market Maker who will review the deal.                                |
| **Servicing Setup**            | **Servicer Retained** (default) or **Servicer Released**.                       |
| **Servicing Fee**              | 0–100, one decimal allowed.                                                     |

Click **Next**. Deal Name and Arranger are required. The first Next creates the deal and assigns a Deal ID.

### 3. Assign loans

Toggle **Assets** or **Pools**.

**Assets** — Pick minted loans (Loan/Asset ID, pool mapping, verification, NFT minted). Use **Add Assets**, or select rows and **Delete** to remove them.

**Pools** — Pick one or more pools. All minted loans in those pools are assigned. Asset Class can be set only before any loans are assigned.

Click **Next**.

### 4. Sale terms

| Field                       | Notes                                                                |
| --------------------------- | -------------------------------------------------------------------- |
| **Purchase Price Basis**    | Par (default), Premium, or Discount.                                 |
| **Price (%)**               | Decimal percentage; must match the basis.                            |
| **Cutoff Date**             | Not in the past; not after settlement or target settlement.          |
| **Settlement Date**         | Not in the past; on or after cutoff; on or before target settlement. |
| **Minimum Pool Size (USD)** | Whole number.                                                        |
| **Commit Window (days)**    | Whole number; platform maximum applies.                              |

**Recourse (optional)** — Type (Full, Limited, Rep and Warranty Only, Non-Recourse), triggers, thresholds, cure window, cap, holdback, and Replacement Right (Yes/No). Replacement Right cannot be used on a single-asset bilateral deal.

**Sale agreement (optional)** — Upload a PDF. If you skip this, a signed file can be uploaded later.

Click **Submit**. The deal is saved as **Draft** and you land on deal details.

### 5. Publish and review

1. On deal details, confirm loans, terms, and documents.
2. Click **Publish**. Status becomes **Pending Review**.
3. The underwriter approves (**Published**) or rejects (**Draft**).

## Rules & Validations

* Deal Name and Arranger are required to leave Basics.
* At least one loan is required before publish.
* Only **Draft** or **Cancelled** deals can be edited.
* Dates must stay in order: cutoff ≤ settlement ≤ target settlement.
* After publish, loan assignment and sale terms are locked.
* The wizard restores a session draft if you leave and come back.

## What Happens Next

Approved deals become **Published** and investors can commit. See [Investor Commitment & Allocation](35_Investor_Commitment_and_Allocation.md). If rejected, revise in Draft and publish again.
