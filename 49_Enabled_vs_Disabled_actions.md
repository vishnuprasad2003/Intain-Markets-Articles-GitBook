---
title: Enabled vs Disabled Actions
description: Understand why actions are enabled or disabled in Intain Markets
---

# Enabled vs Disabled Actions

## Overview

Intain Markets automatically enables or disables actions based on your role, the item's status, and whether prerequisites are met.

## Pool Actions

### Created Status

**As Issuer:**
- **Enabled:** Edit pool details (Edit button)
- **Enabled:** Add/remove loans
- **Enabled:** Share pool with organizations
- **Disabled:** Start Deal (NFT minting not complete)

### Preview Status

**As Issuer:**
- **Enabled:** Edit pool details
- **Enabled:** Respond to feedback
- **Enabled:** Share with additional organizations
- **Enabled:** Start Deal (if NFT minting complete)
- **Enabled:** Accept/reject loan removal requests

**As Market Maker:**
- **Enabled:** View pool details
- **Enabled:** Accept or Reject mandate
- **Disabled:** Edit pool (issuer only)
- **Disabled:** Provide feedback (must accept mandate first)

### Under Review Status (After Accept)

**As Market Maker:**
- **Enabled:** Provide feedback
- **Enabled:** Request loan removal
- **Enabled:** Share to investors
- **Disabled:** Edit pool

**As Investor:**
- **Enabled:** View pool details
- **Enabled:** Provide feedback (if permission enabled)
- **Enabled:** Download data (if permission enabled)
- **Disabled:** Edit pool

### Deal Status

**As Issuer:**
- **Enabled:** View pool details
- **Disabled:** Edit pool (finalized)
- **Disabled:** Share (deal committed)

## Loan Actions

### Loan Registry

**As Issuer:**
- **Enabled:** Map to Pool (if loan not already mapped)
- **Enabled:** Add to Batch (if loan not already in batch)
- **Disabled:** Map to Pool (if loan already mapped to another pool)
- **Disabled:** Add to Batch (if loan already in batch)

### Batch Verification

**Status: Pending**
- **Enabled:** Self Certify
- **Disabled:** Mint NFT

**Status: Reviewed**
- **Enabled:** View details
- **Enabled:** Mint NFT (in Certificates section)

### Certificates Section

**Status: Pending**
- **Disabled:** View NFT
- **Disabled:** Mint NFT

**Status: Reviewed**
- **Enabled:** View NFT
- **Enabled:** Mint NFT

**Status: Verified**
- **Enabled:** View NFT
- **Disabled:** Mint NFT (already minted)

## Term Sheet Actions

### Draft Status

**As Borrower:**
- **Enabled:** Edit all fields
- **Enabled:** Upload documents
- **Enabled:** Create Draft (initiates e-sign)
- **Disabled:** Submit to FA (must sign first)

### BorrowerSigned Status

**As Borrower:**
- **Enabled:** Submit to FA
- **Enabled:** View term sheet
- **Disabled:** Edit (must get changes requested)

### FAReview Status

**As Borrower:**
- **Enabled:** View term sheet
- **Disabled:** Edit (waiting for FA decision)

**As Facility Agent:**
- **Enabled:** Approve
- **Enabled:** Reject
- **Enabled:** Request Changes
- **Disabled:** Edit

### CHANGES_REQUESTED Status

**As Borrower:**
- **Enabled:** Edit term sheet
- **Enabled:** Update and resubmit
- **Enabled:** Re-sign via e-sign

### Accepted Status

**As Borrower:**
- **Enabled:** View term sheet
- **Disabled:** Edit (approved, MC auto-created)

## Master Commitment Actions

### Draft Status

**As Facility Agent:**
- **Enabled:** Edit facility configuration
- **Enabled:** Add lenders
- **Enabled:** Create sub-facilities (if Multiple Branch)
- **Enabled:** Create Facility (submit to lenders)

### PendingLenderApproval Status

**As Facility Agent:**
- **Enabled:** View details
- **Disabled:** Edit configuration

**As Lender:**
- **Enabled:** Review & Approve (with e-sign)
- **Disabled:** Edit configuration

### Active Status

**As Facility Agent:**
- **Enabled:** Set Up Deal (deal modelling)
- **Enabled:** Review funding requests
- **Disabled:** Edit facility structure

**As Borrower:**
- **Enabled:** Map loans (if deal modelling complete)
- **Enabled:** Create funding request (if deal modelling complete)
- **Disabled:** Create funding request (if deal modelling not complete)

## Funding Request Actions

### DRAFT Status

**As Borrower:**
- **Enabled:** Edit request details
- **Enabled:** Submit to FA
- **Disabled:** Approve (FA role only)

### FAReview Status

**As Borrower:**
- **Enabled:** View request
- **Disabled:** Edit

**As Facility Agent:**
- **Enabled:** Approve
- **Enabled:** Reject
- **Enabled:** Request Changes

## Funding Notice Actions

### Pending Token Generated Status

**As Facility Agent:**
- **Enabled:** Approve
- **Disabled:** E-sign (must approve first)

### After FA Approves

**As Facility Agent:**
- **Enabled:** E-sign (0/n → n/n)

### After E-Sign Complete (Per Lender)

**As Lender:**
- **Enabled:** Review Funding Notice
- **Enabled:** Select Payment Method
- **Enabled:** Confirm and Settle

## Common Reasons Actions Are Disabled

| Reason | Example |
|--------|---------|
| Wrong Status | Cannot submit term sheet in Draft (must sign first) |
| Missing Prerequisites | Cannot create funding request (deal modelling not complete) |
| Waiting for Other Party | FA must e-sign for each lender before they see notice |
| Role Permissions | Only FA can approve term sheets |
| Already Completed | Cannot approve already approved item |

## How to Enable Disabled Actions

1. **Check Status** - Verify item is in correct status
2. **Complete Prerequisites** - Fill required fields, upload documents, complete e-signatures
3. **Verify Role** - Confirm you're logged in with correct role
4. **Wait for Others** - Some actions require another party to act first
5. **Check Tooltips** - Hover over disabled buttons for explanations
