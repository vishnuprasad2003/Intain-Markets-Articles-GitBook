---
title: Facility Creation
description: How facility agents configure and submit master commitments for lender approval
---

# Facility Creation

After a term sheet is approved, a master commitment is created automatically with **Draft** status. The facility agent configures it and submits for lender approval.

## Who Can Use This

**Facility Agents** — after a term sheet has been approved.

## Steps

1. **Credit Facility → Set-up tab** → find the approved term sheet → open the master commitment dropdown (status: **Draft**) → click **Create Facility**

2. In the **Basic** section: select **Single** or **Multiple** branch
   - **Single** — one facility with all lenders together
   - **Multiple** — allows sub-facilities with different lender groups

3. **Parties & Accounts** → click **Add Lender** → select organisation → enter commitment amount and voting percentage → repeat for all lenders

![Set Up Lenders](.gitbook/assets/setUpLenders.png)

4. **Economic & Fees** → review interest rate, pricing index, margin, fees, borrowing limits, and drawdown frequency

![Configure Rules](.gitbook/assets/ConfigureRules.png)

5. Complete all remaining sections (all data auto-saves as you go)

6. **Multiple branch only** — **Review & Create → Create Sub-Facility** → configure each sub-facility; assign lenders from the main facility (no two sub-facilities can share the same lenders)

![Create Sub-Facility](.gitbook/assets/CreateSubFacility.png)

7. **Review & Create** → verify all settings → click **Create Facility**
   - Status → **Pending Lender Approval**
   - Lenders see the facility in their **Opportunities** section

![Create Facility - FA](.gitbook/assets/CreateFacility_FA.png)

## After Lender Approval

- Any one lender approval activates the facility → status → **Active**
- Facility moves to **Active Facilities** tab
- Facility agent completes deal modelling (**Set Up Deal**)
- Borrower can then map loans and create funding requests

## Key Rules

- Only Draft commitments can be configured — no editing after submitting for approval
- At least one lender must be added before submitting
- Sub-facility lenders must be a subset of main facility lenders
- Auto-save is active; exit and return at any time while in Draft

→ See [Facility Approval](58_Facility_Approval.md) for the lender approval process.
→ See [Roles in Credit Facilities](17_Roles_in_Credit_Facilities.md) for role overview.
