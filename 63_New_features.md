---
title: New Features
description: Learn about new features and capabilities added to Intain Markets
---

# New Features

## Overview

This document tracks features and capabilities currently implemented in Intain Markets.

## Implemented Features

### Credit Facility Module

**Automatic Master Commitment Creation** - When term sheets are approved, master commitments are automatically created:
- Master commitment created with Draft status
- Pre-populated with term sheet data
- Facility agent configures facility structure and submits for lender approval

**Per-Lender E-Signature Tracking** - Facility agents sign funding notices for each lender individually:
- Each lender's signature status tracked separately in tokenDistribution array
- esignatureStatus field shows 'pending' or 'ESIGN_COMPLETED' for each lender
- eSignaturePendingCount tracks remaining lenders with pending signatures

**Individual Lender Approval Tracking** - Each lender's approval status tracked separately:
- lenderStatus in lenderGroups array shows 'pending_approval', 'approved', or 'esignature_completed'
- Facility becomes ACTIVE when at least one lender approves
- Each lender's approval tracked with timestamps

**FT Token Generation** - Tokens automatically created for funding notices:
- Tokens generated when facility agent configures token distribution
- ftContractAddress stores unique blockchain contract address
- Token distribution calculated from lender voting percentages
- Tokens created on Avalanche C-Chain

**Borrower Token Approval** - Borrowers approve token transfers before lenders can review:
- Borrowers enter C-chain private key or upload JSON file
- Approval updates status to TOKEN_APPROVED
- Funding notices become visible to lenders after approval

### E-Signature Integration

**Electronic Signatures** - Full support for electronic signatures:
- Term sheets signed via DocuSign before submission
- Master commitments signed via AdobeSign for lender approval
- Funding notices signed via DocuSign per lender
- Signed documents stored in IPFS

**Signature Tracking** - Signature status tracked throughout workflows:
- Term sheet status changes to BorrowerSigned after signing
- Master commitment lender signatures tracked individually
- Funding notice signatures tracked per lender

### Status Tracking

**Comprehensive Status History** - All status changes tracked:
- Status history shows who changed status, when, and reason
- Action history shows all actions taken
- Complete audit trails maintained

**Status Workflows** - Clear status progressions:
- Term Sheets: Draft → BorrowerSigned → FAReview → Accepted
- Master Commitments: Draft → PendingLenderApproval → ACTIVE
- Funding Requests: DRAFT → FAReview → APPROVED
- Funding Notices: PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED

## Current Development

**Payment Integration** - Working on payment integration:
- Kinexys integration for fund transfers
- Circle integration for fund transfers
- Payment methods selectable during fund transfer confirmation

**Participation Agreement Flow** - Introducing participation agreement workflow for credit facilities

**Multi-Blockchain Support** - Enhancing token generation:
- Solana integration for FT token transfers
- Users can choose Avalanche or Solana during token generation

## How to Stay Informed

Check release notes, documentation updates, and platform notifications for new features and enhancements.
