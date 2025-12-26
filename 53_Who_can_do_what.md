---
title: Who Can Do What
description: Comprehensive guide to role permissions and what each role can do
---

# Who Can Do What

## Overview

This reference guide explains what each role can and cannot do in the Intain Markets platform. Understanding role permissions helps you know what actions are available to you, what others can do, and why certain actions are unavailable.

## Reference Details

### Issuer (Borrower) Permissions

**Pools and Loans**:
- Can create pools
- Can map loans to pools
- Can edit pool information when status allows (Created or Preview)
- Can share pools with other organizations
- Can manage loan statuses (map, unmap, remove, reinstate)
- Can respond to feedback and make changes
- Can submit pools for mandate review

**Credit Facilities**:
- Can create term sheets
- Can sign term sheets electronically
- Can submit term sheets for facility agent review
- Can respond to change requests on term sheets
- Can create funding requests against active facilities
- Can approve token transfers for funding notices
- Can track funding request and funding notice status

**Cannot Do**:
- Cannot approve their own term sheets
- Cannot create master commitments (these are auto-created)
- Cannot approve their own funding requests
- Cannot sign funding notices (facility agents do this)
- Cannot configure master commitments (facility agents do this)

### Market Maker / Facility Agent Permissions

**Pools**:
- Can review pools shared with them
- Can accept or reject pool mandates
- Can request changes to pools
- Can provide feedback on pools
- Can structure deals
- Can finalize pools as deals

**Credit Facilities**:
- Can review term sheets submitted by borrowers
- Can approve, reject, or request changes to term sheets
- Can configure master commitments after they're auto-created
- Can set up facility rules and borrowing base calculations
- Can configure lender groups
- Can review funding requests
- Can approve, reject, or request changes to funding requests
- Can generate tokens for funding notices
- Can sign funding notices for lenders

**Cannot Do**:
- Cannot create pools (issuers create pools)
- Cannot create term sheets (borrowers create term sheets)
- Cannot approve master commitments as lenders (lenders approve)
- Cannot create funding requests (borrowers create requests)
- Cannot approve token transfers (borrowers approve)

### Investor / Lender Permissions

**Pools**:
- Can review pool previews shared with them
- Can analyze investment opportunities
- Can express interest in pools
- Can provide feedback on pools
- Can download pool data (if permissions allow)
- Can review loan characteristics

**Credit Facilities**:
- Can review master commitments submitted for approval
- Can approve master commitments via electronic signature
- Can reject master commitments (if allowed)
- Can review funding notices after borrower approval
- Can approve or reject individual drawdowns
- Can confirm fund transfers
- Can track facility activity

**Cannot Do**:
- Cannot create pools
- Cannot create term sheets
- Cannot create master commitments (these are auto-created)
- Cannot create funding requests
- Cannot configure master commitments (facility agents do this)
- Cannot generate tokens (facility agents do this)

### Servicer Permissions

**Pools and Loans**:
- Can view pools and loans assigned to them
- Can manage loan servicing activities
- Can update loan statuses and information
- Can track payments and loan performance
- Can handle ongoing administration tasks

**Cannot Do**:
- Cannot create pools or loans
- Cannot approve facilities or drawdowns
- Cannot structure deals
- Cannot make investment decisions

### Paying Agent Permissions

**Pools and Facilities**:
- Can view pools and facilities assigned to them
- Can manage payment distributions
- Can ensure funds are properly allocated
- Can handle payment-related tasks

**Cannot Do**:
- Cannot create pools or facilities
- Cannot approve facilities or drawdowns
- Cannot structure deals
- Cannot make investment decisions

### Rating Agency Permissions

**Pools**:
- Can view pools shared with them
- Can access pool and loan data for analysis
- Can review pool characteristics and metrics
- Can perform rating analysis
- Can download data (if permissions allow)

**Cannot Do**:
- Cannot create or modify pools
- Cannot approve facilities or drawdowns
- Cannot structure deals
- Cannot make investment decisions
- Typically read-only access

## Important Notes

- **Each role has specific permissions** - You can only perform actions allowed by your role. The platform enforces these restrictions automatically.

- **You can only perform actions allowed by your role** - Even if you can see an item, you may not be able to take certain actions if your role doesn't allow them.

- **Some actions require specific roles** - Only facility agents can approve term sheets, only lenders can approve master commitments, etc.

- **Permissions are enforced by the system** - The platform automatically restricts actions based on your role.

- **Role determines what you can see and do** - Your role controls both visibility and action availability.

- **Multiple roles possible** - Some users may have multiple roles but must select one role per login session.

- **Role-based views** - The platform shows you only relevant information based on your role.

- **Action buttons are role-aware** - Buttons are enabled or disabled based on your role and permissions.

- **Complete audit trail** - All actions are recorded with role information for accountability.

- **Collaboration between roles** - Different roles collaborate through workflows (issuers create, market makers structure, lenders fund, etc.).

Understanding role permissions helps you know what actions are available to you, understand what others can do, know why certain actions are unavailable, work effectively within your role's capabilities, and understand how different roles collaborate to complete transactions.
