---
title: Facility Setup Status
description: What facility setup status means and why it gates borrower funding actions
---

# Facility Setup Status

After a master commitment becomes **Active**, the facility agent must complete **deal modelling** before borrowers can map loans or create funding requests. **Facility Setup Status** tracks this.

## Statuses

| Status | Meaning | Borrower actions |
|---|---|---|
| **In Progress** | Deal modelling not finished | Map Loans and Create Funding Request are off |
| **Completed** | Deal modelling done | Map Loans and Create Funding Request are on |

Once **Completed**, the status does not go back.

## Deal Modelling (Facility Agent Steps)

**Active Facilities tab → Set Up Deal**

Sections to complete (all auto-saved):
1. **Basic Details** — deal name, type, currency, dates, payment frequency, day count
2. **Parties & Accounts** — borrower, facility agent, lenders, bank accounts
3. **Fee Structure** — upfront, commitment, agent, and other fees
4. **Interest Rate** — fixed or floating, base rate, spread, margin, default rate
5. **Covenants** — financial, reporting, and other covenants
6. **Waterfall** — payment distribution order
7. **Review** → click **Create** → Facility Setup Status → **Completed**

> Work is auto-saved as you go. You can leave and return without losing entries.

## Delegation

The facility agent can delegate deal modelling to an admin:

1. Click **Delegation** at the top of the deal modelling screen
2. Admin completes the sections and clicks **Create**
3. Facility Setup Status → **Completed**

Delegation can only be done while status is **In Progress**.

## What Each Role Sees

| Facility Setup Status | Facility Agent | Borrower | Lender |
|---|---|---|---|
| **In Progress** | Set Up Deal | Map Loans / Funding Request: off | View only |
| **Completed** | Review Funding Request | Map Loans / Funding Request: on | Review Funding Notice |

→ See [Funding Requests](44_Funding_Requests.md) for borrower steps after completion.
→ See [Master Commitment Overview](20_Master_Commitment_Overview.md) for the full lifecycle.
