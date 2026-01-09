---
title: New Features
description: Learn about new features and capabilities added to Intain Markets
---

# New Features

## Overview

This document tracks features and capabilities currently implemented in Intain Markets.

## Implemented Features

### Credit Facility Module

**Automatic Master Commitment Creation:**
- When term sheets are approved, master commitments are automatically created
- Master commitment created with Draft status
- Pre-populated with term sheet data
- Facility agent configures facility structure and submits for lender approval

**Per-Lender E-Signature Tracking:**
- Facility agents sign funding notices for each lender individually
- E-sign progress shows as (0/n) → (n/n)
- Each lender's signature status tracked separately
- Each lender can see funding notices once their e-sign is complete

**Individual Lender Approval Tracking:**
- Each lender's approval status tracked separately
- Facility becomes ACTIVE when at least one lender approves
- Each lender's approval tracked with timestamps

**Token Generation:**
- Tokens automatically created for funding notices
- Unique blockchain contract address stored
- Token distribution calculated from lender participation percentages
- Tokens created on Avalanche C-Chain

### E-Signature Integration

**Adobe Sign Integration:**
- Term sheets signed via Adobe Sign before submission
- Master commitments signed via Adobe Sign for lender approval
- Funding notices signed via Adobe Sign per lender
- Signed documents stored securely

**Signature Tracking:**
- Term sheet status changes to BorrowerSigned after signing
- Master commitment lender signatures tracked individually
- Funding notice signatures tracked per lender (E-sign 0/n → n/n)

### Status Tracking

**Comprehensive Status History:**
- All status changes tracked with who, when, and reason
- Action history shows all actions taken
- Complete audit trails maintained

**Status Workflows:**
- Term Sheets: Draft → BorrowerSigned → FAReview → Accepted
- Master Commitments: Draft → PendingLenderApproval → ACTIVE
- Funding Requests: DRAFT → FAReview → APPROVED
- Funding Notices: Pending Token Generated → FA Approved → E-signed for lenders

### Pool Module

**Loan Mapping from Loan Registry:**
- Select loans and click Map to Pool
- Loans can only be mapped to one pool at a time

**NFT Minting:**
- Batch verification required before minting
- Certificates section for minting and viewing NFTs

**Pool Sharing:**
- Share with market makers, investors, rating agencies
- Control feedback and download permissions per share

### Loans Module

**Loan Tape Standardization (LTS):**
- Upload loan files via Imports section
- Basic and Intelligent AI mapping options
- Save mappings for future use

**Batch Verification:**
- Self Certify option for issuers
- Submit to verification agent option
- Status: Pending → Reviewed → Certified

## Current Development

**Payment Integration:**
- Kinexys integration for fund transfers
- Circle integration for fund transfers
- Payment methods selectable during Confirm and Settle

**Multi-Blockchain Support:**
- Solana integration for token transfers
- Users can choose Avalanche or Solana

## How to Stay Informed

Check release notes, documentation updates, and platform notifications for new features and enhancements.
