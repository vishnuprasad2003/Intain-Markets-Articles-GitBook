---
title: Who Can Do What
description: Comprehensive guide to role permissions and what each role can do
---

# Who Can Do What

## Overview

This comprehensive reference guide explains what each role can do in the Intain Markets platform. The platform automatically enforces these permissions, ensuring that you can only take actions appropriate for your role.

## Roles Covered

The platform supports multiple roles with distinct permissions, each designed for specific responsibilities in structured finance transactions:

- **Issuer (Borrower)** - Creates pools and credit facility requests. They initiate transactions and manage loan portfolios.

- **Market Maker / Facility Agent** - Structures deals and facilitates transactions. They review opportunities, structure deals, and facilitate transactions between issuers and investors.

- **Investor / Lender** - Provides funding and makes investment decisions. They review opportunities, evaluate investments, and provide capital for transactions.

- **Servicer** - Manages ongoing loan administration. They upload loan tapes monthly and handle loan servicing activities after deals are completed.

- **Paying Agent** - Handles payment distributions. They manage payment distributions and ensure funds are properly allocated to all parties.

- **Rating Agency** - Analyzes pools for rating purposes. They review pool data, analyze characteristics, and provide ratings for structured finance transactions.

## What Each Role Can Do

### Issuer (Borrower)

Issuers create and manage pools, submit credit facility requests, and manage loan portfolios. They are the initiators of transactions and have primary responsibility for creating and managing pools and credit facility requests.

**Pools and Loans:**
- Can create pools with basic information, asset class, and transaction type
- Can map loans to pools and manage loan assignments
- Can edit pool information when status allows (Created or Preview status)
- Can share pools with other organizations for review and collaboration
- Can manage loan statuses (map, unmap, remove, reinstate)
- Can respond to feedback and make changes to pools
- Can submit pools for mandate review to market makers
- Can track pool status and workflow progression

**Credit Facilities:**
- Can create term sheets proposing new credit facilities with facility terms, amounts, interest rates, and repayment terms
- Can sign term sheets electronically before submission
- Can submit term sheets for facility agent review
- Can respond to change requests on term sheets by updating and resubmitting
- Can create funding requests against active facilities
- Can specify drawdown amounts, purposes, and funding dates
- Can approve token transfers for funding notices
- Can track funding request and funding notice status

### Market Maker / Facility Agent

Market Makers and Facility Agents help structure deals and facilitate transactions. They play a crucial role in reviewing opportunities, structuring deals, and facilitating transactions between issuers and investors.

**Pools:**
- Can review pools shared with them for mandate consideration
- Can accept or reject pool mandates based on evaluation
- Can request changes to pools to improve quality
- Can provide feedback on pools to help issuers improve
- Can structure deals and move pools toward completion
- Can finalize pools as deals after accepting mandates

**Credit Facilities:**
- Can review term sheets submitted by borrowers
- Can approve, reject, or request changes to term sheets
- Can configure master commitments after they're automatically created
- Can set up facility rules and borrowing base calculations
- Can configure lender groups and participation percentages
- Can review funding requests for compliance with facility rules
- Can verify borrowing capacity and review documentation
- Can approve, reject, or request changes to funding requests
- Can generate tokens for funding notices
- Can sign funding notices for lenders before sending to lenders

### Investor / Lender

Investors and Lenders provide funding for transactions. They review opportunities, evaluate investments, and make funding decisions based on their investment criteria and risk tolerance.

**Pools:**
- Can review pool previews shared with them for investment opportunities
- Can analyze investment opportunities thoroughly
- Can express interest in pools without commitment
- Can provide feedback on pools to help issuers improve
- Can download pool data (if permissions allow) for further analysis
- Can review loan characteristics and pool metrics
- Can evaluate risk-return profiles

**Credit Facilities:**
- Can review master commitments submitted for approval
- Can approve master commitments via electronic signature
- Can reject master commitments if they don't meet criteria
- Can review funding notices after borrower approves token transfer
- Can approve or reject individual drawdowns independently
- Can confirm fund transfers after approving drawdowns
- Can track facility activity and participation
- Can monitor facility status and borrowing capacity

### Servicer

Servicers manage ongoing loan administration after deals are completed. They upload loan tapes monthly and handle loan servicing activities to ensure loans are properly managed.

**Pools and Loans:**
- Can view pools and loans assigned to them for servicing
- Can upload loan tapes monthly
- Can manage loan servicing activities
- Can update loan statuses and information
- Can handle ongoing administration tasks
- Can report on loan performance

### Paying Agent

Paying Agents handle payment distributions. They manage payment distributions and ensure funds are properly allocated to all parties according to deal terms.

**Pools and Facilities:**
- Can view pools and facilities assigned to them for payment processing
- Can manage payment distributions
- Can ensure funds are properly allocated
- Can handle payment-related tasks
- Can track payment distributions

### Rating Agency

Rating Agencies analyze pools for rating purposes. They review pool data, analyze characteristics, and provide ratings for structured finance transactions.

**Pools:**
- Can view pools shared with them for rating analysis
- Can access pool and loan data for analysis
- Can review pool characteristics and metrics
- Can perform rating analysis
- Can download data (if permissions allow) for further analysis

## Important Access Notes

**Each Role Has Specific Permissions** - You can only perform actions allowed by your role. The platform enforces these restrictions automatically.

**Role Determines Actions** - Even if you can see an item, you may not be able to take certain actions if your role doesn't allow them. Your role controls both visibility and action availability.

**Specific Role Requirements** - Some actions require specific roles—only facility agents can approve term sheets, only lenders can approve master commitments, etc.

**Automatic Enforcement** - The platform automatically restricts actions based on your role. You cannot bypass role restrictions.

**Role Controls Visibility and Actions** - Your role controls both what you can see and what actions you can take. The platform filters information and actions based on your role.

**Multiple Roles Possible** - Some users may have multiple roles but must select one role per login session. You can switch roles by logging out and logging back in with a different role.

**Role-Based Views** - The platform shows you only relevant information based on your role. You only see items where you have a role or where items are shared with you.

**Action Buttons Are Role-Aware** - Buttons are enabled or disabled based on your role and permissions, not just item status. Both role and status determine action availability.

**Collaboration Between Roles** - Different roles collaborate through workflows—issuers create, market makers structure, lenders fund, servicers manage, etc.

**Sequential Responsibilities** - Roles have sequential responsibilities in workflows.

**Independent Decisions** - Some roles make independent decisions (like lenders approving drawdowns).
