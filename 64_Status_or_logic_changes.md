---
title: Status or Logic Changes
description: Learn about changes to status workflows and business logic in Intain Markets
---

# Status or Logic Changes

## Overview

This document tracks changes to status workflows, business logic, and process flows implemented in Intain Markets.

## Implemented Changes

### Credit Facility Workflow

**Dedicated Credit Facility Flow** - Credit facilities now have separate workflow:
- Term Sheet → Master Commitment → Funding Request → Funding Notice
- Separate from securitization and pool workflows
- Focused specifically on credit facility transactions

**Automatic Master Commitment Creation** - Master commitments auto-created when term sheets approved:
- Triggered when term sheet status changes to Accepted
- Created with Draft status
- Pre-populated with term sheet data
- Facility agent configures and submits for lender approval

**Lender Approval Workflow** - Simplified lender approval process:
- Any selected lender can approve to activate facility
- Status changes from PendingLenderApproval to ACTIVE on first approval
- Each lender's approval tracked individually
- E-signature envelope generated after approval for documentation

### Pool Preview Loan Status

**Loan Status Visibility** - Removed and reinstated loans now visible:
- Removed loans maintain "Removed" status and visible in UI
- Reinstated loans show "Reinstated" status and visible
- Complete loan status history maintained and displayed
- Users can see all loan statuses including removed and reinstated

### Status Value Standardization

**Status Values Updated** - Status values standardized:
- Term sheet "Approved" changed to "Accepted"
- Master commitment "Active" changed to "ACTIVE"
- Status values consistent across platform

### Funding Notice Workflow

**Automatic Funding Notice Generation** - Funding notices auto-generated:
- Created automatically when funding request approved
- Status starts as PENDING_TOKEN_GENERATION
- Facility agent generates tokens and configures distribution
- Status changes to TOKEN_GENERATED after token creation
- Borrower approves tokens, status changes to TOKEN_APPROVED

**Per-Lender E-Signature** - Facility agent signs for each lender:
- Each lender's signature tracked separately
- esignatureStatus in tokenDistribution array tracks individual signatures
- All signatures must complete before process continues

### Business Logic Updates

**Validation Rules** - Field and document validation:
- Required fields validated before submission
- Required documents enforced (collateral profile, financial statements, KYC documents)
- Invalid data rejected with error messages

**Status Progression** - Status progression enforced:
- Items must progress through statuses in order
- Cannot skip workflow steps
- Prerequisites must be met before actions enabled

**Token Allocation** - Token distribution calculated automatically:
- Based on lender voting percentages
- Each lender receives tokensAllocated amount
- Total tokens equal drawdown amount

## Impact on Users

**Workflow Changes** - Users work with:
- Dedicated credit facility workflow separate from securitization
- Automatic master commitment and funding notice creation
- Per-lender signature and approval tracking
- Visible loan status including removed and reinstated

**Status Management** - Status values standardized and consistent. Status history shows complete progression.

**Documentation** - Documentation reflects current workflows and status values.
