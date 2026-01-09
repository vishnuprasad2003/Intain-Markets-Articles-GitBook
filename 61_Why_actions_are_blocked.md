---
title: Why Actions Are Blocked
description: Understand common reasons actions are blocked and how to resolve them
---

# Why Actions Are Blocked

## Overview

Actions are blocked when certain conditions aren't met. This guide explains common blocking reasons and solutions.

## Common Blocking Reasons

### 1. Wrong Status

**Examples:**
- Cannot submit term sheet (status is Draft, must sign first)
- Cannot edit term sheet (status is FAReview, waiting for FA)
- Cannot create funding request (MC not ACTIVE)

**Solution:** Check item status and complete required steps to progress

### 2. Missing Prerequisites

**Examples:**
- Cannot submit term sheet (not signed via Adobe Sign)
- Cannot mint NFT (batch verification not complete)
- Cannot create funding request (deal modelling not complete)

**Solution:** Complete the prerequisite step first

### 3. Waiting for Another Party

**Examples:**
- Term sheet in FAReview (waiting for FA decision)
- MC in PendingLenderApproval (waiting for lender)
- Funding notice not visible (FA hasn't completed your e-sign)

**Solution:** Wait for the other party to complete their action

### 4. Role Permissions

**Examples:**
- Cannot approve term sheet (not logged in as FA)
- Cannot approve MC (not logged in as Lender)
- Cannot edit pool (not the issuer who created it)

**Solution:** Log in with the correct role

### 5. Action Already Completed

**Examples:**
- Cannot submit term sheet again (already submitted)
- Cannot mint NFT again (already minted)
- Cannot approve again (already approved)

**Solution:** Check if action was already taken; proceed to next step

## Blocking Reasons by Module

### Pools

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Edit pool | Status is Deal | Cannot edit after deal finalized |
| Start Deal | NFTs not minted | Complete NFT minting first |
| Share pool | No orgs selected | Edit pool, add organizations |

### Loans

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Map to Pool | Loan already mapped | Unmap from current pool first |
| Mint NFT | Batch not verified | Complete batch verification |
| Add to Batch | Loan already in batch | Remove from current batch first |

### Term Sheets

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Submit to FA | Not signed | Click Create Draft, complete e-sign |
| Edit | Status is FAReview | Wait for FA decision |
| Edit | Status is Accepted | Cannot edit approved items |

### Master Commitments

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Create Funding Request | MC not ACTIVE | Wait for lender approval |
| Create Funding Request | Deal modelling not done | FA must complete Set Up Deal |
| Edit configuration | Status is ACTIVE | Cannot edit active facilities |

### Funding Requests

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Approve | Status is DRAFT | Borrower must submit first |
| Edit | Status is FAReview | Wait for FA decision |
| Edit | Status is APPROVED | Cannot edit approved items |

### Funding Notices

| Blocked Action | Common Reason | Solution |
|----------------|---------------|----------|
| Lender can't see | FA hasn't e-signed for you | FA must complete your e-sign |
| Confirm and Settle | Haven't reviewed | Complete review first |

## How to Diagnose

1. **Check Status Badge** - Shows current status of item

2. **Hover Over Button** - Tooltips explain why disabled

3. **Check Your Role** - Verify you're logged in correctly

4. **Review Prerequisites** - Check if required steps are complete

5. **Check Notifications** - May indicate what's pending

## Quick Reference

| If You Can't... | Check... |
|-----------------|----------|
| Submit term sheet | Is it signed? |
| Create funding request | Is MC ACTIVE? Is deal modelling complete? |
| Mint NFT | Is batch verification complete (Reviewed)? |
| See funding notice (as lender) | Has FA completed your e-sign? |
| Edit item | Is status Draft or CHANGES_REQUESTED? |
| Approve item | Are you logged in as the approving role? |
