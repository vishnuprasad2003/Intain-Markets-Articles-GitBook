---
title: Who Changed What and When
description: Learn how to view change history in Intain Markets
---

# Who Changed What and When

## Overview

Intain Markets tracks every change with details about who made it, what changed, and when. All changes are recorded automatically with attribution and timestamps.

## Status History

**Pool Status History** - Shows progression: Created → Preview → Mandate Pending → Deal
- Each entry shows: who changed status, when, previous status, new status, and comments

**Term Sheet Status History** - Shows progression: Draft → BorrowerSigned → FAReview → Accepted/Rejected/CHANGES_REQUESTED
- Each entry shows: who changed status, when, previous status, new status, and reason

**Master Commitment Status History** - Shows progression: Draft → PendingLenderApproval → ACTIVE
- Each entry shows: who changed status, when, previous status, new status, and comments

**Funding Request Status History** - Shows progression: DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED
- Each entry shows: who changed status, when, previous status, new status, and reason

**Funding Notice Status History** - Shows progression: PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
- Each entry shows: who changed status, when, previous status, new status, and details

**How to View** - Navigate to item detail page, look for "Status History" section. Changes are displayed chronologically.

## Action History

**Pool Actions** - Creation, sharing, mandate submission, mandate acceptance/rejection, loan mapping, removal, reinstatement

**Term Sheet Actions** - Creation, signing, submission, approval, rejection, change requests, document uploads

**Master Commitment Actions** - Auto-creation, facility configuration, lender group updates, lender approvals

**Funding Request Actions** - Creation, submission, approval, rejection, change requests, document uploads

**Funding Notice Actions** - Auto-generation, token generation, token distribution, borrower approval, lender approvals, fund transfer confirmations

**How to View** - Navigate to item detail page, look for "Action History" or "Activity" section. Actions are displayed chronologically.

## Document History

**Term Sheet Documents** - Tracks collateral profile, financial statements, KYC documents, collateral data uploads
- Records: IPFS hash, uploader, timestamp
- Previous versions preserved in history arrays

**Funding Request Documents** - Tracks collateral addendum, financial statements, KYC documents, supporting documents uploads
- Records: IPFS hash, uploader, timestamp
- Previous versions preserved in history arrays

**IPFS Storage** - Documents stored in IPFS. Each upload generates IPFS hash stored in database. Document history arrays maintain upload history.

**How to View** - Navigate to item detail page, look for document sections. Document history shows all uploads with uploader, timestamp, and IPFS hash.

## Change Attribution

**User Attribution** - Every change records: user ID, user name, organization ID and name, role, timestamp

**Status Change Attribution** - Records: who changed, when, previous status, new status, reason or comments

**Approval Attribution** - Records: approver, when, comments, role

**Rejection Attribution** - Records: rejector, when, reason, role

## Viewing Change History

**Item Detail Pages** - Navigate to pools, term sheets, master commitments, funding requests, or funding notices. Look for:
- "Status History" - Shows all status changes
- "Action History" - Shows all actions taken
- "Activity" - Shows recent activities
- "Document History" - Shows document uploads and updates

**Chronological Display** - History organized chronologically. Most recent first or chronological order. Each entry shows complete details.

**Detailed Information** - Clicking entries shows: what happened, who was involved, when it occurred, what changed.

## Important Notes

**Complete History** - All changes recorded permanently. Cannot be deleted or modified.

**User Attribution** - Every change attributed to specific user.

**Timestamps** - All timestamps use consistent time standards.

**History Cannot Be Modified** - Change history is permanent.

**Access Control** - History visibility based on roles and permissions.
