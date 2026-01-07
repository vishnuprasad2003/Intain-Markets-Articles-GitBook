---
title: End-to-End Traceability
description: Understand how Intain Markets tracks actions and changes
---

# End-to-End Traceability

## Overview

Intain Markets tracks every action, status change, and decision with records of who did what, when, and what changed. All changes are recorded automatically with attribution and timestamps.

## What Gets Tracked

### Status History

**Pool Status Changes** - Created → Preview → Mandate Pending → Deal
- Records who changed status, when and comments

**Term Sheet Status Changes** - Draft → BorrowerSigned → FAReview → Accepted/Rejected/CHANGES_REQUESTED
- Records who changed status, when and reasons

**Master Commitment Status Changes** - Draft → PendingLenderApproval → ACTIVE
- Records facility agent actions and lender approvals

**Funding Request Status Changes** - DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED
- Records borrower submissions and facility agent decisions

**Funding Notice Status Changes** - PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
- Records token generation, borrower approval, and lender decisions

### Action History

**Pool Actions** - Creation, sharing, mandate submission, loan mapping, removal, reinstatement

**Term Sheet Actions** - Creation, editing, signing, submission, approval, rejection, change requests, document uploads

**Master Commitment Actions** - Auto-creation, facility configuration, lender group updates, lender approvals

**Funding Request Actions** - Creation, editing, submission, approval, rejection, change requests, document uploads

**Funding Notice Actions** - Auto-generation, token generation, token distribution, borrower approval, lender approvals, fund transfer confirmations

### Document History

**IPFS Storage** - Documents are stored in IPFS with hash verification. Each upload generates an IPFS hash stored in the database. Document history arrays track upload history with timestamps and user attribution.

**Term Sheet Documents** - Collateral profile, financial statements, KYC documents, collateral data uploads tracked with IPFS hash, uploader, and timestamp

**Funding Request Documents** - Collateral addendum, financial statements, KYC documents, supporting documents uploads tracked with IPFS hash, uploader, and timestamp

**Document Versioning** - Previous versions are preserved when documents are updated. Document history arrays maintain version history.

### Relationship Tracking

**Term Sheet → Master Commitment** - Master commitment links to term sheet via termSheetId

**Master Commitment → Funding Requests** - Funding requests link via masterCommitmentId

**Funding Request → Funding Notice** - Funding notice links to funding request

**Pool → Loans** - Loans link to pools via poolid field

### User Attribution

Every action records: user ID, user name, organization ID and name, timestamp, and role.

Status changes record: who changed and reason.

Approvals record: approver, timestamp, comments, and role.

Rejections record: rejector, timestamp, reason, and role.

## How to View History

Navigate to item detail pages and look for:
- **Status History** - Shows all status changes chronologically
- **Action History** - Shows all actions taken chronologically
- **Document History** - Shows document uploads and updates

History is organized chronologically. Clicking entries shows complete details about what happened, who was involved, and when.

## Important Notes

**Automatic Recording** - Tracking happens automatically. No additional steps required.

**Complete History** - All changes are preserved in chronological order.

**User Attribution** - Every action is attributed to the user who performed it.

**Permanent Records** - Audit trails are permanent and cannot be modified.

**Access Control** - Access to audit trails is controlled based on roles and permissions.
