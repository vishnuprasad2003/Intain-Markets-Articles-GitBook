---
title: Facility Setup Status
description: Understand facility setup status, deal modelling, and what each status means for credit facility participants
---

# Facility Setup Status

## Overview

After a master commitment becomes **Active**, the facility agent must finish **deal modelling** before the borrower can map loans or create funding requests. **Facility Setup Status** shows whether that setup is done.

## Lifecycle Overview

```
Master Commitment becomes Active
  → Facility Setup Status: In Progress
    → Facility agent finishes deal modelling
      → Facility Setup Status: Completed
```

Once the status is **Completed**, it does not go back. Deal modelling is done once for each facility.

## Status Meanings

### In Progress

This is the default as soon as a lender approves the master commitment. Deal modelling is not finished.

| Role | What you can do |
|------|-----------------|
| **Facility Agent** | **Set Up Deal** is available on Active Facilities |
| **Borrower** | Map Loans and Create Funding Request stay off |
| **Lender** | You can view the facility. Funding actions are not available yet |

The facility agent sees **Set Up Deal**. The borrower sees the facility with those two actions disabled.

### Completed

Deal modelling is finished. The facility agent, or an admin if the task was delegated, completed every section and clicked **Create** in Review.

| Role | What you can do |
|------|-----------------|
| **Facility Agent** | **Review Funding Request** appears when a borrower submits a request |
| **Borrower** | **Map Loans** and **Create Funding Request** are on. Only loans with an NFT can be mapped |
| **Lender** | **Review Funding Notice** appears after the facility agent generates a notice and e-signs for you |

## What is Deal Modelling

Deal modelling is where the facility agent sets the parties, fees, interest, covenants, and payment order. Entries save as you go, so you can leave and continue later.

### Deal Modelling Sections

1. **Basic Details** — Deal name, deal type, currency, closing date, maturity date, payment frequency, day count (for example 30/360 or Actual/360), and business day convention.
2. **Parties & Accounts** — Borrower, facility agent, lenders, bank accounts, and wire instructions.
3. **Fee Structure** — Upfront, commitment, agent, and other fees.
4. **Interest Rate** — Fixed or floating, base rate (for example SOFR), spread, margin, default rate, and interest period.
5. **Covenants** — Financial, reporting, and other covenants.
6. **Waterfall** — The order in which payments are distributed.
7. **Review** — A summary, and the **Create** button that finishes deal modelling.

### Saving Your Work

Each section saves as you enter it. Closing the browser does not discard what you already entered.

### Delegation to Admin

**Delegation** is at the top of the deal modelling screen.

1. Click **Delegation**.
2. An admin can open the same sections.
3. When the admin clicks **Create** in Review, Facility Setup Status becomes **Completed**.

You can delegate only while the status is **In Progress**. After you delegate, the admin finishes the setup.

## What Each Status Indicates

| Facility Setup Status | Facility Agent | Borrower: Map Loans | Borrower: Create Funding Request | Lender |
|----------------------|----------------|---------------------|----------------------------------|--------|
| **In Progress** | Set Up Deal | Off | Off | View only |
| **Completed** | Review Funding Request, when one is submitted | On | On | Review Funding Notice, when one is ready |

- Deal modelling is available only when the master commitment is **Active**. Draft and Pending Lender Approval do not show **Set Up Deal**.
- Every section must be complete before **Create** is available in Review.
- After **Completed**, deal modelling cannot be opened again to change the setup.
- Delegation cannot be taken back.
- A facility cannot have a second deal model.

## What Happens After Completion

1. The borrower maps loans that have an NFT.
2. The borrower submits a funding request with the amount, purpose, and documents.
3. The facility agent approves, rejects, or requests changes.
4. Approval creates a funding notice, which then goes through e-signature.
5. Lenders review the notice, send funds, and click **Confirm and Settle**.
6. Tokens transfer and the draw is complete.

Facility Setup Status is the gate between an active commitment and the first draw.
