---
title: Who Can Do What
description: >-
  Role-permission matrix showing what each role can see and do across pools, loans, credit facilities, asset sales, and administration
---

# Who Can Do What

Two checks must both pass: **you are the right role** and **the item is in the right status**.

## Issuer / Borrower

| Area | Actions |
|---|---|
| **Pools** | Create, edit (Created status), share (Created/Preview), Start Deal (after NFT minting), accept/reject loan removal requests |
| **Loans** | Upload loan tape, standardize (LTS), map to pool, add to batch, self-certify batch, mint NFTs |
| **Credit Facility** | Create/sign/submit term sheet, edit (Changes Requested), map loans, create/edit/submit funding requests |
| **Asset Sale** | Create deal, assign loans, publish, initiate repayment, transfer NFTs, approve token transfers |
| **Data Room** | Upload, delete, rename, create folders on own pools and deals |

## Market Maker / Facility Agent

| Area | Actions |
|---|---|
| **Pools** | Review shared pools, accept/reject mandate, leave feedback (post-acceptance), request loan removal, share with investors |
| **Credit Facility** | Review/approve/reject/request changes on term sheets and funding requests, set up facility, add lenders, send for approval, set up deal (deal modelling), approve funding notice, sign for each lender |

## Investor / Lender

| Area | Actions |
|---|---|
| **Pools** | Review shared pools, leave feedback (if permitted), download data (if permitted), request loan removal |
| **Credit Facility** | Review/approve facility, sign, review funding notice, choose payment method, confirm settlement |
| **Asset Sale** | View published deals, commit, sign investor agreement, confirm settlement, confirm repayment, burn NFTs |

## Other Roles

| Role | Actions |
|---|---|
| **Underwriter** | Review, approve, or reject Asset Sale deals; manage investor allocation |
| **Servicer** | View assigned deals, upload monthly loan tape |
| **Rating Agency** | View and leave feedback on shared pools (cannot request loan removal) |
| **Paying Agent** | Transfer funds for securitization distributions (OTP required) |
| **Admin** | Manage organisations and users, approve/reject KYC, process delegated tasks, view activity log, apply status corrections |

## Key Notes

- **Status limits buttons.** A term sheet in **Draft** can be edited; one **In review** cannot be edited by the borrower.
- **Sharing decides visibility.** Investors only see pools shared with them.
- **OTP required** for: minting NFTs, transferring NFTs, approving token transfers, moving funds.
- **Funding notices are per lender.** You see a notice after the facility agent signs for your organisation.

→ See [Enabled vs Disabled Actions](69_Enabled_vs_Disabled_actions.md) for why buttons appear greyed out.
