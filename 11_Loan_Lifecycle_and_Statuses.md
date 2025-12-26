---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where each loan is in the process and know what actions are available.

## Who Can Use This

- Issuers who manage loans
- Market Makers who review loan data
- Servicers who manage loan administration
- Other parties involved in loan transactions

## When This Is Used

Understanding loan lifecycle helps when:
- You need to track loan progress
- You want to know what actions are available
- You need to understand why certain actions are disabled
- You want to manage loans effectively

## Step-by-Step Process

### Loan Status Flow

1. **Uploaded**
   - Loan data is imported into the system
   - Loan is standardized and validated
   - Status shows as "Unmapped"

2. **Mapped**
   - Loan is assigned to a pool
   - Status shows which pool it belongs to
   - Loan is included in pool calculations

3. **Submitted**
   - Loan is included in a batch for verification
   - Waiting for verification process
   - Status shows as "Submitted"

4. **Verified**
   - Loan has been verified
   - Verification source is recorded
   - Loan can proceed to next stages

5. **Minted** (if applicable)
   - NFT has been created for the loan
   - Loan is tokenized
   - Status shows as "Minted"

### Status Within Pool

1. **Normal**
   - Loan is active in pool
   - Included in pool calculations
   - Standard status

2. **Reconsider**
   - Loan needs review
   - Flagged for attention
   - Under review

3. **Removed**
   - Loan removed from pool calculations
   - Still visible but excluded
   - Can be reinstated

4. **Reinstated**
   - Loan was removed but put back
   - Now included in pool again
   - Active status restored

## Rules & Validations

- Loans can only belong to one pool at a time
- You must unmap a loan from one pool before mapping it to another
- Removed loans are excluded from pool calculations
- Verified loans can proceed to tokenization
- Some statuses restrict certain actions

## What Happens Next

After understanding loan lifecycle:
- You can track loans through their entire journey
- You know what actions are available at each status
- You understand why certain actions are disabled
- You can manage loans effectively throughout their lifecycle
- You know when loans are ready for next stages

Understanding loan lifecycle and statuses helps you effectively manage loans and track their progress through the platform workflow.
