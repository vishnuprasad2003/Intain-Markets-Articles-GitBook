---
title: Borrower Token Approval
description: How borrowers approve tokens in the credit facility workflow
---

# Borrower Token Approval

## Overview

This guide explains the borrower token approval process in the credit facility module. After the facility agent approves the funding notice and tokens are generated, the borrower approves the tokens. This approval enables the facility agent to proceed with e-signing for each lender.

## Who Can Use This

- **Borrowers** who have funding requests approved

## When This Is Used

Use this process when:
- Your funding request has been approved
- The funding notice has been generated
- The facility agent has approved the funding notice
- Tokens have been generated
- You need to approve the tokens

## Borrower Token Approval Flow

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

### Step 1: Access Credit Facility

1. **Navigate to Credit Facility**
   - Log in with your Borrower credentials
   - From the left expandable menu, click on **Credit Facility**
   - Find the funding notice awaiting your token approval

### Step 2: Review Token Details

1. **Review the Funding Notice**
   - Check the drawdown amount
   - Verify lender allocations
   - Confirm the details are correct

### Step 3: Approve Token

1. **Click Approve**
   - Click the Approve Token Action for the funding notice
   - Enter the wallet Private Key and click the **Approve** button to approve the token
   - This enables the FA to proceed with e-signing

2. **Confirmation**
   - Your approval is recorded
   - FA can now e-sign for each lender

## What Happens After Approval

**After Borrower Approves Token:**
- Facility agent can proceed with e-signing
- FA e-signs for each lender (0/n → n/n)
- Each lender sees the funding notice after their e-sign
- Lenders transfer funds and confirm settlement
- Tokens are transferred to the borrower

## Key Points

**After Token Generation** - Borrower token approval occurs after the FA approves and tokens are generated.

**Before FA E-Sign** - This step must complete before the FA can e-sign for lenders.

**Enables FA Action** - Your approval enables the facility agent to proceed with e-signatures.

**Token Receipt** - After lenders settle, tokens are transferred to you.
