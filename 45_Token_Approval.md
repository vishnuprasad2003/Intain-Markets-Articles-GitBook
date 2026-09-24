---
title: Token Approval
description: >-
  Token generation, borrower approval, facility agent e-signing, and lender settlement in a credit facility drawdown
---

# Token Approval

Token approval runs after a funding request is approved and a funding notice exists. It covers token creation, borrower approval, facility agent e-signing, and lender settlement.

![Issuer Token Approval](<.gitbook/assets/Issuer_Token_Approval (3).png>)

## Steps

### Step 1 — Facility Agent Approves the Funding Notice

1. **Credit Facility → Active Facilities** → find the funding notice (status: **Pending Token Generation**)
2. Review draw amount and each lender's share
3. Click **Approve**
4. Tokens created; funding notice shows the FT contract address; status → **Tokens Generated**

### Step 2 — Borrower Approves Token Transfer

1. Open the funding notice → review total tokens, FT contract, and each lender's share
2. Click **Approve Token** → enter **Wallet Private Key** → **Approve**
3. Approval recorded on the blockchain; facility agent can now e-sign

### Step 3 — Facility Agent E-Signs for Each Lender

1. Action shows **E-sign (0/n)**
2. Click → Adobe Sign / ZohoSign window opens for the next unsigned lender → sign
3. Counter advances: **E-sign (1/n)**, **E-sign (2/n)**, through **E-sign (n/n)**
4. Each lender can see the notice as soon as their signature is done

| Counter | Meaning |
|---|---|
| E-sign (0/3) | No lender signed yet |
| E-sign (1/3) | 1 lender can now see the notice |
| E-sign (3/3) | All lenders signed |

### Step 4 — Lenders Send Funds and Settle

1. Lender opens funding notice → reviews amount and token share
2. Sends funds via bank wire
3. Returns to platform → **Confirm and Settle**
4. Tokens transferred for that lender; settlement recorded

When all lenders settle → funding notice status → **Tokens Transferred**; drawdown complete.

## Status Summary

| Status | Meaning |
|---|---|
| **Pending Token Generation** | Funding notice exists; tokens not yet created |
| **Tokens Generated** | Tokens created; borrower must approve transfer |
| **E-sign (0/n) → (n/n)** | Facility agent signing per lender |
| **Tokens Transferred** | All lenders settled; drawdown complete |

## Key Rules

- Steps must happen in order: facility agent approves → tokens created → borrower approves → facility agent signs → lenders settle
- A lender sees the notice only after the facility agent signs for them
- Only lenders who signed the master commitment are included in the token split
- Borrower approval and lender token transfers cannot be reversed from the screen
