---
title: Borrower Token Approval
description: >-
  How borrowers approve token transfers in the credit facility funding notice workflow
---

# Borrower Token Approval

After the facility agent approves the funding notice and tokens are created, the borrower must approve the token transfer before the facility agent can sign for each lender.

![Issuer Token Approval Screen](<.gitbook/assets/Issuer_Token_Approval (2).png>)

## When This Is Used

Status must be **Tokens Generated** (facility agent has already approved the funding notice).

## Steps

1. **Credit Facility → Active Facilities** → open the master commitment → find the funding notice with status **Tokens Generated**
2. Review: draw amount, **FT contract** (blockchain address of this draw's token), total token supply, and each lender's share
3. Click **Approve Token** → enter your **Wallet Private Key** → **Approve**
4. Approval recorded on the blockchain; facility agent can now e-sign for lenders

## What Comes Next

1. Facility agent signs for each lender (**E-sign 0/n → n/n**)
2. Each lender sees the notice after their signature is done
3. Lenders send funds → **Confirm and Settle**
4. Tokens transferred; notice status → **Tokens Transferred**

## Key Rules

- You can only approve when status is **Tokens Generated**
- A valid wallet private key is required
- The facility agent cannot start lender signatures until you approve
- Approval is irreversible and recorded on the blockchain
- A second attempt does not create a duplicate approval if it's already recorded

→ See [Token Approval](45_Token_Approval.md) for the full drawdown sequence including all roles.
