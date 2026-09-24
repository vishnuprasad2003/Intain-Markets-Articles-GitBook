---
title: Asset Sale Deal Setup
description: Issuer checklist to create, configure, and publish an Asset Sale deal
---

# Asset Sale Deal Setup

## Overview

This is the issuer’s task list for the pre-sale phase: create the deal, assign loans, set terms, attach the sale agreement, and publish for underwriter review. Use this page while you work. For every wizard field and validation, see [Deal Creation & Publishing](34_Deal_Creation_and_Publishing.md).

![Asset Sale Deal Details — Issuer View](.gitbook/assets/deal-details-issuer.png)

## Who Can Use This

* **Issuers** — all steps below

The Arranger / Placement Agent you pick on Basics is the Market Maker who will review the deal. They do not fill this wizard for you.

## When This Is Used

Use this when you are selling a loan portfolio and need a deal in **Draft**, then **Pending Review**. Do not use this for repayment — that starts only after the deal is **Active**. If you only need to fix a Draft deal, skip Create Deal and open the existing Deal ID.

## Step-by-Step Process

### 1. Create the deal

Open **Asset Sale** → **Create Deal**. Complete **Basics**:

* **Deal Name** (required) and **Arranger / Placement Agent** (required)
* **Sale Route** — Marketed or Bilateral
* **Target Settlement Date**, **Governing Law**
* **Buyer Visibility** — All investors or Selected
* **Servicing Setup** and **Servicing Fee**

Click **Next**. The first Next creates the deal, assigns a Deal ID, and saves **Draft**.

### 2. Assign loans

On **Pool Selection**, add minted loans one by one (**Assets**) or map one or more pools (**Pools**). Only loans with NFT minted status can be assigned. Remove rows with **Delete** if you added the wrong assets. At least one loan is required before publish.

### 3. Set sale terms

On **Sale Terms**, set purchase price basis (Par / Premium / Discount), price, cutoff date, settlement date, minimum pool size, and commit window. Add a recourse profile only if the sale uses recourse. Optionally upload the sale agreement PDF — if you skip it, a signed file can be added later.

Click **Submit**. You land on deal details. Status is still **Draft**.

### 4. Publish

On deal details, confirm loans, terms, servicing, and documents. Click **Publish**. Status becomes **Pending Review**. You cannot edit loans or sale terms while the underwriter is reviewing.

### 5. Watch the result

| Underwriter action | Your next step                                                |
| ------------------ | ------------------------------------------------------------- |
| **Approve**        | Deal becomes **Published**. Investors can commit.             |
| **Reject**         | Deal returns to **Draft**. Fix the package and publish again. |
| **Cancel**         | Deal is **Cancelled**. It is not reactivated.                 |

Track commitments and agreement signing on the same deal page after publication.

## Rules & Validations

* Deal Name and Arranger are required to leave Basics.
* Dates must stay in order: cutoff ≤ settlement ≤ target settlement.
* Only **Draft** deals can be fully edited.
* After publish, loans and sale terms are locked.
* Cancelled deals cannot re-enter the live path.
* Replacement Right cannot be enabled on a single-asset bilateral deal.
* The wizard restores a session draft if you leave and return before Submit.

## What Happens Next

The underwriter allocates investors. You can see commitments on deal details but you do not set allocation. After agreements are signed, you confirm bank-wire receipt (or watch stablecoin escrow) during settlement.

If the underwriter asks for a different pool or price, expect a reject to **Draft** — you cannot patch those fields while the deal is in **Pending Review**. Keep the Deal ID; do not create a second deal unless you intend to cancel the first.

See [Investor Commitment & Allocation](35_Investor_Commitment_and_Allocation.md). After the deal is **Active**, use [Repayment Initiation](47_Repayment_Initiation_Issuer.md).
