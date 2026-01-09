---
title: End-to-End Traceability
description: Understand how Intain Markets tracks actions and changes
---

# End-to-End Traceability

## Overview

Intain Markets tracks every action, status change, and decision with records of who did what, when, and what changed. All changes are recorded automatically with attribution and timestamps.

## What Gets Tracked

### Status History

**Pool Status Changes:**
- Created → Preview → Under Review → Deal
- Records who changed status, when, and comments

**Term Sheet Status Changes:**
- Draft → BorrowerSigned → FAReview → Accepted/Rejected/CHANGES_REQUESTED
- Records who changed status, when, and reasons

**Master Commitment Status Changes:**
- Draft → PendingLenderApproval → ACTIVE
- Records facility agent actions and lender approvals

**Funding Request Status Changes:**
- DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED
- Records borrower submissions and facility agent decisions

**Funding Notice Status Changes:**
- Pending Token Generated → FA Approved → E-signed for lenders
- Records FA actions and lender confirmations

### Action History

**Pool Actions:**
- Creation, sharing, mandate acceptance/rejection
- Loan mapping, removal, reinstatement
- Feedback submission

**Term Sheet Actions:**
- Creation, editing, signing (Adobe Sign)
- Submission, approval, rejection, change requests
- Document uploads

**Master Commitment Actions:**
- Auto-creation from term sheet
- Facility configuration, lender additions
- Lender approvals (with e-signature)

**Funding Request Actions:**
- Creation, editing, submission
- Approval, rejection, change requests
- Document uploads

**Funding Notice Actions:**
- Auto-generation from approved funding request
- FA approval and e-signatures for each lender
- Lender fund transfer confirmations (Confirm and Settle)

### Document History

**IPFS Storage:**
- Documents stored with hash verification
- Each upload generates an IPFS hash
- History arrays track uploads with timestamps

**Document Types Tracked:**
- Term sheet documents (collateral profile, financials, KYC)
- Funding request documents (collateral addendum, supporting docs)
- Pool documents

### Relationship Tracking

| From | To | Link |
|------|-----|------|
| Term Sheet | Master Commitment | termSheetId |
| Master Commitment | Funding Requests | masterCommitmentId |
| Funding Request | Funding Notice | fundingRequestId |
| Pool | Loans | poolid |

### User Attribution

**Every Action Records:**
- User ID and name
- Organization ID and name
- Timestamp
- Role

**Status Changes Record:**
- Who changed
- Previous status
- New status
- Reason/comments

**Approvals/Rejections Record:**
- Approver/rejector
- Timestamp
- Comments
- Role

## How to View History

Navigate to item detail pages and look for:
- **Status History** - All status changes chronologically
- **Action History** - All actions taken chronologically
- **Document History** - Document uploads and updates

## Key Points

**Automatic Recording** - Tracking happens automatically

**Complete History** - All changes preserved in order

**User Attribution** - Every action attributed to user

**Permanent Records** - Cannot be modified

**Access Control** - Based on roles and permissions
