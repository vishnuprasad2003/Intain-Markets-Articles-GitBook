---
title: Who Can Do What
description: Comprehensive role-permission matrix showing what each role can see and do across all platform modules — pools, loans, credit facilities, asset sales, data rooms, and administration
---

# Who Can Do What

## Overview

Your role decides what you can see and which actions are offered to you. The platform checks that role, and the status of the item, before it lets an action through. Hiding a button is not the only control. If you are the wrong role, or the item is in the wrong status, the action is refused.

Two things must both be true: you are the right role, and the item is in a status that allows that action.

## Roles Covered

| Role | Primary Function |
|---|---|
| **Issuer / Borrower** | Creates pools, loans, and term sheets, and starts transactions |
| **Market Maker / Facility Agent** | Reviews pools, structures deals, and approves term sheets and funding requests |
| **Investor / Lender** | Reviews opportunities, approves facilities, and provides funds |
| **Underwriter** | Reviews Asset Sale deals before investors can commit |
| **Servicer** | Uploads loan tapes for deals assigned to them |
| **Rating Agency** | Reviews pools that were shared with them and leaves feedback |
| **Paying Agent** | Moves funds for securitization |
| **Admin** | Manages organizations, users, and KYC, and supports the platform |

The same organization can hold more than one of these roles, but each session uses one role. What you see changes when you sign in as a different role.

## What Each Role Can Do

### Issuer / Borrower

**Pools**

| Action | When Available |
|---|---|
| Create a pool | Any time, from **Set-up Pool** |
| Edit a pool | Pool status is Created |
| Share a pool | Pool status is Created or Preview |
| Submit to a market maker (Start Deal) | After loan NFTs for the pool have been minted |
| Accept or decline a loan removal | When a market maker or investor has asked for a loan to be removed |
| Leave feedback | On your own pools |

**Loans**

| Action | When Available |
|---|---|
| Upload a loan file | Any time, from Imports |
| Standardize the loan tape | After the file is uploaded |
| Save the field mapping | After standardization |
| Map loans to a pool | From the Loan Registry, if the loan is not already mapped |
| Add loans to a batch | From the Loan Registry, if the loan is not already in a batch |
| Self-certify a batch | Batch status is Pending. You confirm with a one-time code |
| Mint NFTs | Batch status is Reviewed |
| View NFTs | After they are minted |

**Credit Facility (as borrower)**

| Action | When Available |
|---|---|
| Create a term sheet | Any time, from Term Sheet Setup |
| Sign a term sheet | Status is **Draft** |
| Submit a term sheet | Status is **Signed** |
| Edit a term sheet | Status is **Changes Requested** |
| Map loans to the facility | The facility is **Active** and deal modelling is complete |
| Create a funding request | The facility is **Active** and deal modelling is complete |
| Edit a funding request | Status is **Draft** or **Changes Requested** |
| Submit a funding request | Status is **Draft**, and the required fields and documents are complete |

**Asset Sale (as issuer)**

| Action | When Available |
|---|---|
| Create a deal | Any time, from Asset Sale |
| Assign loans to a deal | Deal status is **Draft** |
| Publish a deal | After the loans are assigned |
| Start repayment | Deal status is **Active**, after settlement |
| Transfer NFTs | Deal status is **Settlement In Progress**. You confirm with a one-time code |
| Approve a token transfer | When a token approval is required. You confirm with a one-time code |

**Data room**

| Action | When Available |
|---|---|
| Upload, delete, or rename files | On pools and deals where you are the issuer |
| Download files | On your own pools and deals |
| Create folders | On pools and deals where you are the issuer |

### Market Maker / Facility Agent

**Pools**

| Action | When Available |
|---|---|
| Review a pool | When it has been shared with you |
| Accept the mandate | Pool status is Mandate Pending |
| Decline the mandate | Pool status is Mandate Pending |
| Leave feedback | After you accept the mandate |
| Request loan removal | After you accept the mandate |
| Share with an investor | Pool status is Deal |

**Credit Facility (as facility agent)**

| Action | When Available |
|---|---|
| Review, approve, reject, or request changes on a term sheet | The term sheet is **In review** |
| Set up the facility and add lenders | Facility status is **Draft** |
| Create a sub-facility | Facility status is **Draft**, and the contract type allows more than one |
| Send the facility for lender approval | Facility status is **Draft**, and setup is complete |
| Set up the deal (deal modelling) | Facility status is **Active** |
| Review, approve, reject, or request changes on a funding request | The request is **In review** |
| Approve a funding notice | After the funding request is approved and the notice exists |
| Sign for each lender | After the funding notice is approved |

### Investor / Lender

**Pools**

| Action | When Available |
|---|---|
| Review a pool | When it has been shared with you |
| Leave feedback | If feedback was allowed when the pool was shared |
| Download data | If download was allowed when the pool was shared |
| Request loan removal | After the pool is shared with you |

**Credit Facility (as lender)**

| Action | When Available |
|---|---|
| Review the facility | Status is **Pending**, in Opportunities |
| Approve and sign the facility | Status is **Pending** |
| Review a funding notice | After the facility agent has signed for your organization |
| Choose a payment method | While you are reviewing the notice |
| Confirm and settle | After you have transferred the funds |

**Asset Sale (as investor)**

| Action | When Available |
|---|---|
| View deals | When they are published |
| Commit to a deal | The deal is open for commitment |
| Sign the investor agreement | After you commit |
| Confirm settlement | After the agreement is signed and settlement has started |
| Confirm repayment | When the issuer has started repayment |
| Burn NFTs | After repayment is confirmed |

### Underwriter

| Action | When Available |
|---|---|
| Review a deal | The deal is **Pending Review** |
| Approve or reject a deal | After you review it |
| Manage investor allocation | After you approve the deal |

### Servicer

| Action | When Available |
|---|---|
| View assigned deals | Any time. You only see deals assigned to you |
| Upload the monthly loan tape | For those deals |
| View deal details | For those deals |

### Rating Agency

| Action | When Available |
|---|---|
| View shared pools | When a pool is shared with you |
| Leave feedback | If feedback was allowed on the share |
| Download data | If download was allowed on the share |

A rating agency cannot request loan removal, create pools, or approve items.

### Paying Agent

| Action | When Available |
|---|---|
| Transfer funds | When a securitization distribution is ready. You confirm with a one-time code |
| View settlement details | For the securitization deals assigned to you |

### Admin

| Action | When Available |
|---|---|
| Manage organizations | Any time |
| Approve or reject KYC | When a KYC submission is waiting |
| Process a delegated loan-tape standardization | When an issuer has delegated it |
| Process delegated deal modelling | When a facility agent has delegated it |
| View platform-wide analytics | Any time |
| View the platform as another user | Any time. This view is read-only |
| Apply an administrative status correction | When a data fix is required |
| Open the activity log | Any time. Admins see events across organizations |
| Manage user accounts | Any time. Activate, deactivate, or update a profile |

## Important Access Notes

**Your role limits the list.** You see items that are shared with you, assigned to you, or created by your organization. An investor does not see a pool that was never shared. A lender does not see a funding notice until the facility agent has signed for that lender.

**Status limits the buttons.** A term sheet in **Draft** can be edited. A term sheet **In review** cannot be edited by the borrower. A facility agent cannot approve a term sheet that is still **Draft**.

**Both checks apply together.** The right role is not enough. The item also has to be in the right status.

**Sensitive blockchain steps ask for a one-time code.** Minting NFTs, transferring NFTs, approving a token transfer, and moving funds all ask you to confirm with a one-time code, even when your role and the status already allow the action.

**Sharing decides who sees a pool.** The issuer chooses who receives the pool, and separately whether those people can leave feedback or download data.

**Funding notices are per lender.** You see a notice after the facility agent signs for your organization. Other lenders may already see theirs.
