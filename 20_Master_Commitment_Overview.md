---
title: Master Commitment Overview
description: What master commitments are and how they work in credit facilities
---

# Master Commitment Overview

A master commitment is the finalized credit facility agreement. It is created automatically when a term sheet is approved — you cannot create one manually.

## What It Contains

| Component | Description |
|---|---|
| **Facility terms** | Pre-populated from approved term sheet (read-only): amount, rates, advance rate, maturity |
| **Lender groups** | Organisations, their commitment amounts, and voting percentages |
| **Sub-facilities** | (Multiple-branch only) Separate lender groups within the main facility |
| **Deal modelling** | Facility setup completed by facility agent after activation |

## How It Works

1. **Created automatically** when facility agent approves the term sheet → status **Draft**
2. **Facility agent configures** — adds lenders, sets amounts, creates sub-facilities if needed → clicks **Create Facility**
3. **Status → Pending Lender Approval** — lenders see it in **Opportunities**
4. **Any one lender Approve & E-Sign** → status → **Active**
5. **Facility agent completes deal modelling** (Set Up Deal) → Facility Setup Status → **Completed**
6. **Borrower can now map loans and create funding requests**

![Create Master Commitment Facility](.gitbook/assets/CreateMasterCommitmentFacility.png)
![Lender Approval - Master Commitment](.gitbook/assets/LenderApproval_MasterCommitment.png)

## Sub-Facility Rules

- Sub-facilities can only include lenders from the main facility
- No two sub-facilities can share the same lenders
- Each lender belongs to one sub-facility only

## Key Rules

- Master commitments cannot be edited after they move to **Pending Lender Approval**
- One lender's approval activates the facility for all parties
- Borrowers cannot create funding requests until Facility Setup Status is **Completed**
- No new funding requests can be created on an **InActive** commitment

→ See [Master Commitment Statuses](21_Master_Commitment_Statuses.md) for full status reference.
→ See [Facility Creation](50_Facility_Creation.md) for facility agent configuration steps.
