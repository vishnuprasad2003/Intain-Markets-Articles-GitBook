---
title: All Loan States Explained
description: Understand all possible loan statuses and what each means
---

# All Loan States Explained

## Overview

This guide explains all possible loan statuses across different status fields. Loans have multiple status fields that track different aspects of their lifecycle.

## Who Can Use This

- Issuers who manage loans
- Market Makers who review loan data
- Servicers who manage loan administration

## When This Is Used

Understanding loan states helps when:
- You need to track loan progress
- You want to know what actions are available
- You need to understand why certain actions are disabled
- You want to manage loans effectively

## Step-by-Step Process

### Mapping Status

1. **Unmapped**
   - Loan is not assigned to any pool
   - Available for mapping
   - Can be mapped to a pool

2. **Mapped**
   - Loan is assigned to a pool
   - Shows which pool it belongs to
   - Included in pool calculations

### Workflow Status

1. **Standardized**
   - Loan has been processed
   - Data quality validated
   - Ready for mapping

2. **Submitted**
   - Loan is included in a batch
   - Submitted for verification
   - Waiting for verification

3. **Verified**
   - Loan has been verified
   - Verification source recorded
   - Ready for next stages

### Pool Status

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
- You must unmap a loan from one pool before mapping to another
- Removed loans are excluded from pool calculations
- Verified loans can proceed to tokenization
- Some statuses restrict certain actions

## What Happens Next

After understanding loan states:
- You can track loans through their entire journey
- You know what actions are available at each status
- You understand why certain actions are disabled
- You can manage loans effectively throughout their lifecycle
- You know when loans are ready for next stages

Understanding loan states helps you effectively manage loans and track their progress through the platform workflow.
