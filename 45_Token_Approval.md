---
title: Token Approval
description: Understanding the token approval process in credit facilities
---

# Token Approval

## Overview

This guide explains the token approval process in the credit facility module. After the facility agent approves the funding notice and tokens are generated, the borrower approves the tokens. This approval enables the facility agent to e-sign for each lender.

## Who Approves Tokens

The **Borrower** is responsible for token approval.

## When Token Approval Happens

Token approval occurs after:
1. Funding request is approved by the facility agent
2. Funding notice is auto-generated
3. Facility agent approves the funding notice
4. Tokens are generated

## Token Approval Flow

```
Funding Request APPROVED
       ↓
Funding Notice Generated (Pending Token Generated)
       ↓
FA clicks Approve
       ↓
Tokens Generated
       ↓
Borrower Approves Token
       ↓
FA E-signs for each lender (0/n → n/n)
       ↓
Funding Notice VISIBLE TO LENDERS
       ↓
Lenders review → Transfer funds → Confirm and Settle
       ↓
Tokens transferred to Borrower
```

## Step-by-Step Process

### Step 1: FA Approves Funding Notice

1. Facility agent reviews the funding notice
2. Facility agent clicks **Approve**
3. Tokens are generated

### Step 2: Borrower Approves Token

1. **Borrower Accesses Funding Notice**
   - Navigate to Credit Facility
   - Find the funding notice with generated tokens

2. **Borrower Clicks Approve**
   - Review the token details
   - Enter Wallet Private Key and click **Approve** to approve the token

3. **Approval Recorded**
   - Token approval is recorded
   - FA can now proceed with e-signing

### Step 3: FA E-Signs for Each Lender

1. Action shows **E-sign (0/n)** where n = number of lenders
2. FA clicks E-sign for each lender via Adobe Sign
3. Count progresses: (0/n) → (1/n) → (n/n)
4. Each lender sees the funding notice after their e-sign

### Step 4: Lenders Act

1. Lenders see the funding notice
2. Lenders review and transfer funds
3. Lenders click **Confirm and Settle**
4. Tokens are transferred to the borrower

## Token Approval Status

| Status | Meaning |
|--------|---------|
| **Tokens Generated** | Awaiting borrower token approval |
| **Token Approved** | Borrower has approved, FA can e-sign |

## Key Points

**Borrower Action** - The borrower must approve tokens after they are generated.

**Before FA E-Sign** - Token approval must complete before the FA can e-sign for lenders.

**Enables E-Sign Process** - Token approval enables the facility agent to proceed with e-signatures.

**Sequential Process** - FA Approve → Token Generated → Borrower Approve → FA E-Sign

## What Happens Next

**After Token Approval:**
- FA can e-sign for each lender
- Each lender sees the funding notice after their e-sign
- Lenders review and transfer funds
- Lenders click Confirm and Settle
- Tokens transferred to borrower
