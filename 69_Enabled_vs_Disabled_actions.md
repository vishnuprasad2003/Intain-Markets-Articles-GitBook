---
title: Enabled vs Disabled Actions
description: Which actions are on or off based on role, status, and completed steps
---

# Enabled vs Disabled Actions

→ Back to [Why Approvals Exist](71_Why_approvals_exist.md)

A button is enabled when your role, the item's status, and all earlier steps are in place. Hover a disabled button for the tooltip explaining why.

## Pools

| Status | Role | On | Off |
|---|---|---|---|
| Created | Issuer | Edit, share, map loans | Start Deal (until NFTs minted) |
| Preview | Issuer | Edit, share more, Start Deal (if NFTs minted), respond to removal requests | — |
| Preview | Market Maker | View, Accept, Reject | Feedback (until accepted) |
| Under Review | Market Maker | Feedback, loan removal requests, share to investors | Edit |
| Under Review | Investor | View, feedback/download if permitted | Edit |
| Deal | Issuer | View | Edit, Share |

## Loans

| Situation | On | Off |
|---|---|---|
| Loan not in pool or batch | Map to Pool, Add to Batch | — |
| Loan already in pool | — | Map to Pool |
| Batch: Pending | Self Certify | Mint NFT |
| Batch: Reviewed | Mint NFT, View NFT (Certificates) | — |
| Batch: Verified | View NFT | Mint NFT |

## Term Sheets

| Status | Role | On | Off |
|---|---|---|---|
| Draft | Borrower | Edit, upload docs, Create Draft (sign) | Submit to FA |
| Signed | Borrower | Submit to FA, view | Edit |
| In review | Borrower | View | Edit |
| In review | Facility Agent | Approve, Reject, Request Changes | Edit |
| Changes Requested | Borrower | Edit, sign, resubmit | — |
| Accepted | Borrower | View | Edit |

## Master Commitments

| Status | Role | On | Off |
|---|---|---|---|
| Draft | Facility Agent | Configure, add lenders, Create Facility | — |
| Pending Lender Approval | Lender | Review & Approve, E-Sign | Edit |
| Pending Lender Approval | Facility Agent | View | Edit |
| Active | Facility Agent | Set Up Deal, review funding requests | Edit facility structure |
| Active | Borrower | Map loans, create funding request (after setup Completed) | Funding request before setup |

## Funding Notices

| Situation | Role | On | Off |
|---|---|---|---|
| Pending Token Generated | Facility Agent | Approve | E-sign |
| After FA approves | Borrower | Approve Token | — |
| After borrower approves | Facility Agent | E-sign (0/n → n/n) | — |
| After FA signs for lender | Lender | Review notice, Confirm and Settle | — |

## Asset Sale

| Situation | Role | On | Off |
|---|---|---|---|
| Deal in Draft | Issuer | Edit, assign loans, Publish (when loans assigned) | Publish before loans assigned |
| Deal in Pending Review | Underwriter | Approve, Reject | — |
| Deal in Published | Investor | Submit Commitment | — |
| Deal in Active | Issuer | Initiate Repayment | — |
| During Repayment In Progress | Investor | Confirm Repayment Receipt | — |
| After confirming repayment | Investor | Burn NFT | — |

## How to Enable a Blocked Action

1. Check the item's current status
2. Finish required fields, documents, and signatures
3. Confirm you are in the correct role
4. Wait if another party must act first
5. Hover the button for the exact tooltip reason
