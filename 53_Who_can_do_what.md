---
title: Who Can Do What
description: Comprehensive guide to role permissions and what each role can do
---

# Who Can Do What

## Overview

This reference guide explains what each role can do in the Intain Markets platform. The platform automatically enforces these permissions.

## Issuer / Borrower Actions

### Pools Module

| Action | When Available |
|--------|----------------|
| Create Pool | Always (via Set-up Pool button) |
| Edit Pool | Status: Created |
| Share Pool | Status: Created or Preview |
| Submit to Market Maker (Start Deal) | After NFT minting complete |
| Accept/Reject Loan Removal | When market maker/investor requests |
| Provide Feedback | On own pools only |

### Loans Module

| Action | When Available |
|--------|----------------|
| Upload Loan File | Always (via Imports section) |
| Trigger LTS | After upload |
| Save Mapping | After LTS mapping |
| Map to Pool | From Loan Registry, loan not already mapped |
| Add to Batch | From Loan Registry, loan not already in batch |
| Self Certify | Batch status: Pending |
| Mint NFT | Batch status: Reviewed |
| View NFT | After minting |

### Credit Facility Module (as Borrower)

| Action | When Available |
|--------|----------------|
| Create Term Sheet | Always (via Term Sheet Setup) |
| Sign Term Sheet | Status: Draft |
| Submit to FA | Status: BorrowerSigned |
| Edit Term Sheet | Status: CHANGES_REQUESTED |
| Map Loans | MC status: Active, Deal modelling: Completed |
| Create Funding Request | MC status: Active, Deal modelling: Completed |

## Market Maker / Facility Agent Actions

### Pools Module

| Action | When Available |
|--------|----------------|
| Review Pool | When shared with you |
| Accept Mandate | Status: Mandate Pending |
| Reject Mandate | Status: Mandate Pending |
| Provide Feedback | After accepting mandate |
| Request Loan Removal | After accepting mandate |
| Share to Investor | Status: Deal |

### Credit Facility Module (as Facility Agent)

| Action | When Available |
|--------|----------------|
| Review Term Sheet | Status: FAReview |
| Approve Term Sheet | Status: FAReview |
| Reject Term Sheet | Status: FAReview |
| Request Changes | Status: FAReview |
| Configure MC (Create Facility) | MC status: Draft |
| Add Lenders | MC status: Draft |
| Create Sub-Facility | MC status: Draft, Multiple branch |
| Set Up Deal (Deal Modelling) | MC status: Active |
| Review Funding Request | Status: FAReview |
| Approve Funding Request | Status: FAReview |
| Approve Funding Notice | After FR approved |
| E-sign for Lenders | After FN approved |

## Investor / Lender Actions

### Pools Module

| Action | When Available |
|--------|----------------|
| Review Pool | When shared with you (Pools section) |
| Provide Feedback | If feedback permission enabled |
| Download Data | If download permission enabled |
| Request Loan Removal | After pool shared with you |

### Credit Facility Module (as Lender)

| Action | When Available |
|--------|----------------|
| Review MC | Status: PendingLenderApproval (Opportunities section) |
| Approve & E-Sign MC | Status: PendingLenderApproval |
| Review Funding Notice | After FA completes e-sign for you |
| Select Payment Method | During funding notice review |
| Confirm and Settle | After transferring funds |

## Servicer Actions

| Action | When Available |
|--------|----------------|
| View Assigned Deals | Always |
| Upload Monthly Loan Tape | Assigned deals |
| View Deal Details | Assigned deals |

## Rating Agency Actions

| Action | When Available |
|--------|----------------|
| View Shared Pools | When shared with you |
| Provide Feedback | If feedback permission enabled |
| Download Data | If download permission enabled |
| Request Loan Removal | Not available |

## Admin Actions

| Action | When Available |
|--------|----------------|
| Manage Organizations | Always |
| Approve KYC | Pending KYC requests |
| Process LTS Delegation | When delegated by issuer |
| Process Deal Modelling Delegation | When delegated by FA |

## Key Points

- **Role determines visibility and actions** - You only see items shared with you or where you have a role
- **Status determines action availability** - Actions are enabled/disabled based on item status
- **Both role AND status matter** - You need the right role AND the right status for actions
- **Platform enforces automatically** - You cannot bypass role restrictions
