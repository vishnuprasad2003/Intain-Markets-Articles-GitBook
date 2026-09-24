---
title: Token Approval
description: >-
  Complete guide to the token approval workflow in credit facility funding
  notices, from token generation through borrower approval to lender settlement
---

# Token Approval

## Overview

Token approval is the part of a credit facility drawdown where digital tokens are created, the borrower allows those tokens to be transferred, and the facility agent signs the funding notice for each lender. A token is a digital record of the draw that can be split among the lenders. Borrowers, facility agents, and lenders each have a step, and each step waits for the one before it.

![Issuer Token Approval](<.gitbook/assets/Issuer_Token_Approval (3).png>)

## Who Can Use This

* **Borrowers**: Approve the token transfer after the tokens are created
* **Facility agents**: Approve the funding notice, which creates the tokens, then sign for each lender
* **Lenders**: See the funding notice after their signature is complete, then send funds and confirm settlement

## When This Is Used

Token approval starts after:

1. The borrower has submitted a funding request and the facility agent has **approved** it
2. A funding notice has been created and is **Pending token generation**
3. The facility agent has approved the funding notice, which creates the tokens
4. The funding notice status is **Tokens generated**

This is part of the drawdown. It is not a separate task you start from an empty screen.

## Step-by-Step Process

### Step 1: Facility Agent Approves the Funding Notice

**Who does this:** Facility agent

After the funding request is approved, the funding notice is **Pending token generation**:

1. Open **Credit Facility**, then **Active Facilities**
2. Find the funding notice under the master commitment
3. Review the draw amount and each lender's share
4. Click **Approve**

**What happens:**

* Tokens are created for this draw and assigned to the borrower
* The funding notice shows the token's blockchain address under **FT contract**. FT means the digital token for this funding notice.
* The status changes to **Tokens generated**
* Each lender's row starts as **pending**, with signature status **pending signature**
* Each lender's token amount follows their share of the commitment

### Step 2: Borrower Approves the Token Transfer

**Who does this:** Borrower

When the status is **Tokens generated**:

1. Open **Credit Facility** and find the funding notice
2. Review the total tokens, the FT contract, and each lender's share, percentage, and commitment amount
3. Click **Approve Token**
4. Enter your **Wallet Private Key**. This is the secret for the wallet that holds the tokens.
5. Click **Approve**

**What the approval does:**

* Your wallet allows the platform to transfer the tokens for this draw
* The approval is recorded on the blockchain, the shared digital ledger that tracks the tokens
* The funding notice keeps a record of that approval

**What you see next:**

* The notice history shows the approval
* The facility agent can start **E-sign**

### Step 3: Facility Agent E-Signs for Each Lender

**Who does this:** Facility agent

After the borrower approves:

1. The action shows **E-sign (0/n)**. The number n is the count of lenders.
2. Click the e-sign action
3. A signing window opens in Adobe Sign or ZohoSign for one lender
4. Sign for that lender
5. The count moves forward: **E-sign (1/n)**, then **E-sign (2/n)**, through **E-sign (n/n)**

**For each lender:**

* That lender's signature status changes from **pending signature** to **signed**
* A signed copy of the notice is saved
* That lender can see the funding notice
* That lender's organization is notified

**Signature progress:**

| What you see     | Meaning                       |
| ---------------- | ----------------------------- |
| **E-sign (0/3)** | No lender has been signed yet |
| **E-sign (1/3)** | Signed for 1 of 3 lenders     |
| **E-sign (2/3)** | Signed for 2 of 3 lenders     |
| **E-sign (3/3)** | Every lender is signed        |

The notice shows how many signatures are done and how many are still waiting. Each lender's row shows **pending signature** or **signed**.

### Step 4: Lenders Act on the Funding Notice

**Who does this:** Each lender

After their signature is complete, each lender:

1. Opens the funding notice in **Credit Facility** or **Opportunities**
2. Reviews their amount and token share
3. Sends the funds through their bank
4. Returns to the platform and clicks **Confirm and Settle**

**What happens:**

* That lender's tokens are transferred
* The notice records the transfer for that lender as completed
* Settlement for that lender is marked complete

### Step 5: Funding Notice Completion

When every lender has confirmed:

* The funding notice status changes to **Tokens transferred**
* The notice history records the completion
* The drawdown is finished

## Token Approval Status Summary

| Status                                    | Stage                                        | What it means                                                                                   |
| ----------------------------------------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Pending token generation**              | After the funding request is approved        | The funding notice exists. Tokens are not created until the facility agent approves the notice. |
| **Tokens generated**                      | After the facility agent approves the notice | Tokens exist. The borrower still needs to approve the transfer.                                 |
| Borrower approved                         | After the borrower approves                  | The platform may transfer the tokens. The facility agent can sign for lenders.                  |
| **E-sign (0/n)** through **E-sign (n/n)** | While the facility agent signs               | Signatures progress one lender at a time                                                        |
| **Tokens transferred**                    | After every lender settles                   | Tokens have been delivered. The drawdown is complete.                                           |

## Rules & Validations

| Rule                           | Details                                                                                                                      |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| **Order**                      | Facility agent approves the notice, tokens are created, the borrower approves, the facility agent signs, then lenders settle |
| **Status checks**              | An action is available only when the notice is at the matching status                                                        |
| **Which lenders are included** | Lenders who have signed the master commitment are included in the token split                                                |
| **Who can see the notice**     | A lender sees the funding notice after their own signature is **signed**                                                     |
| **Already done**               | If tokens are already created, or the borrower has already approved, repeating the step does not do it again                 |
| **Approvals stay in place**    | The borrower's approval and each lender's token transfer cannot be reversed from the screen                                  |
| **Where signatures apply**     | Signatures are on the funding notice. Approving the funding request does not require a signature.                            |

## What Happens Next

**After the status is Tokens transferred:**

* The borrower has received the funds from the lenders
* Lenders hold tokens for their share of the draw
* The funding notice keeps the record of approvals, signatures, and transfers
* The amount used on the credit facility is updated
* You can create another funding request for any capacity that remains
