---
title: Controls and Accountability
description: Understand the controls and accountability measures in Intain Markets
---

# Controls and Accountability

## Overview

Intain Markets implements controls and accountability measures throughout the platform. These controls operate automatically and are built into the platform's architecture.

## Access Controls

**Role-Based Permissions** - Your role determines what you can see and do:
- Issuers/Borrowers can create pools and term sheets, cannot approve their own submissions
- Facility Agents can approve term sheets and funding requests, cannot create term sheets
- Lenders can approve master commitments and funding notices, cannot create facilities
- Market Makers can accept pool mandates, cannot create pools

**Status-Based Access** - Status controls what actions are available:
- Pools in Created status allow editing, Deal status restricts editing
- Term sheets in Draft allow editing, FAReview restricts editing
- Master commitments in Draft allow editing, ACTIVE restricts structure changes
- Funding requests in DRAFT allow editing, APPROVED restricts changes

**Sharing Controls** - Pool sharing is controlled:
- Issuers control who can see pools through sharing settings
- Sharing permissions control feedback and download access
- Recipients only see pools shared with them

## Workflow Controls

**Status-Based Progression** - Items must progress through statuses in order:
- Pools: Created → Preview → Mandate Pending → Deal
- Term Sheets: Draft → BorrowerSigned → FAReview → Accepted
- Master Commitments: Draft → PendingLenderApproval → ACTIVE
- Funding Requests: DRAFT → FAReview → APPROVED
- Status progression cannot be skipped

**Approval Gates** - Approvals are required before progression:
- Term sheets require facility agent approval before master commitment creation
- Master commitments require lender approval before becoming ACTIVE
- Funding requests require facility agent approval before funding notice generation
- Funding notices require borrower token approval before lender review

**Prerequisite Validation** - Actions require prerequisites:
- Term sheets must be signed before submission
- Master commitments must be ACTIVE before funding request creation
- Tokens must be generated before borrower approval
- Borrower must approve tokens before lenders can review

## Data Controls

**Field Validation** - Required fields are validated:
- Term sheet fields (requestedCommitmentAmount, advanceRate, etc.)
- Pool fields (poolName, assetClass, etc.)
- Funding request fields (drawAmount, purposeOfFunds, etc.)
- Invalid data is rejected with error messages

**Document Requirements** - Required documents are enforced:
- Term sheets require collateral profile, financial statements, KYC documents
- Funding requests require collateral addendum, financial statements, KYC documents
- Documents stored in IPFS with hash verification
- Missing documents prevent submission

**Business Rules** - Business rules enforced automatically:
- Pool metrics calculate automatically from mapped loans
- Borrowing capacity validates against facility limits
- Token allocations match lender voting percentages
- Status transitions follow defined workflows

## Audit Controls

**Action Tracking** - All actions tracked:
- Status changes record who changed, when, previous status, new status
- Approvals record approver, timestamp, comments
- Rejections record rejector, timestamp, reason
- Edits record editor, timestamp, what changed

**Status History** - Complete status progression tracked:
- Every status change recorded with attribution
- Status history shows complete progression
- Previous and new statuses recorded
- Comments and reasons preserved

**Action History** - All actions logged:
- Creation, editing, submission, approval, rejection actions
- Document uploads and updates
- Sharing and permission changes
- Complete action log with timestamps

**Document History** - Document activities tracked:
- Uploads record who uploaded, when, IPFS hash
- Updates preserve previous versions
- Document history arrays maintain records
- IPFS hashes enable document verification

**Relationship Tracking** - Related items tracked:
- Term sheet approval creates master commitment (relationship tracked)
- Funding request approval creates funding notice (relationship tracked)
- Pool to loan mappings tracked

## Key Principles

**Automatic Enforcement** - Controls enforced automatically. Platform ensures proper operation.

**Role-Based Access** - Access controlled by roles and permissions. You can only see and do what's appropriate for your role.

**Status-Based Control** - Status controls what actions are available. Status progression ensures proper workflow order.

**Accountability** - All actions tracked and attributed. You can see who did what and when.

**Permanent Records** - Audit trails are permanent and cannot be modified.

**Validation Before Acceptance** - Data validated before acceptance. Invalid or incomplete data rejected with clear messages.

**Prerequisite Enforcement** - Prerequisites must be met before actions are enabled. Steps cannot be skipped.
