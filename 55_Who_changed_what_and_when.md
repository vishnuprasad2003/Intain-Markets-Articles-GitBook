# Who Changed What and When

## Overview

The platform tracks every change with complete details about who made the change, what changed, and when it happened. This guide explains how to view and understand this change history.

## Status History

### What It Shows

**Status history displays:**
- All status changes: Complete `statusHistory` array from database
- Who changed the status: `userId` field from each `statusHistory` entry
- When status changed: `timestamp` field (UTC date) from each entry
- Previous status value: `previousStatus` field (if tracked) or inferred from previous entry
- New status value: `status` field value
- Reason for change (if provided): `comments` field explains why change occurred

**Database Structure:**
- **Term Sheets** (`cf_term_sheets` collection): `statusHistory` array - query via `GET /cf/getTermSheet/:termSheetId` (may exclude `statusHistory` in projection, use separate endpoint if needed)
- **Master Commitments** (`cf_master_commitments` collection): `statusHistory` array
- **Funding Requests** (`cf_funding_requests` collection): `statusHistory` array
- **Funding Notices** (`cf_funding_notices` collection): `statusHistory` array

**Where to find it:**
- Item details page: `statusHistory` array displayed in UI
- Status History section: Dedicated section showing chronological list
- Activity log: Combined view of `statusHistory` and `actionHistory`
- Audit trail: Complete history for compliance purposes

---

### Understanding Status History

**Example entry:**
- **Status**: FAReview
- **Changed by**: Facility Agent Name
- **Changed at**: 2024-12-25 10:30 AM
- **Previous status**: BorrowerSigned
- **Comments**: "Submitted for review"

**What this tells you:**
- Status changed from BorrowerSigned to FAReview
- Facility Agent made the change
- Changed on December 25 at 10:30 AM
- Reason: Submitted for review

---

## Action History

### What It Shows

**Action history displays:**
- All actions taken: Complete `actionHistory` array from database
- Who took the action: `userId` field from each `actionHistory` entry
- When action occurred: `timestamp` field (UTC date) from each entry
- What was affected: `details` object contains affected fields, previous/new values, related entities
- Result of action: `comments` field and `details` object describe outcome
- Related changes: `details` object may reference related status changes, entity creation, etc.

**Database Structure:**
- **Term Sheets** (`cf_term_sheets` collection): `actionHistory` array - each entry: `{ action: '...', userId: '...', timestamp: Date, comments: '...', details: {...}, sequence: number, revisionNumber: number }`
- **Master Commitments** (`cf_master_commitments` collection): `actionHistory` array
- **Funding Requests** (`cf_funding_requests` collection): `actionHistory` array
- **Funding Notices** (`cf_funding_notices` collection): `actionHistory` array

**Where to find it:**
- Item details page: `actionHistory` array displayed in UI
- Action History section: Dedicated section showing chronological list
- Activity log: Combined view of `statusHistory` and `actionHistory`
- Audit trail: Complete history for compliance purposes

---

### Understanding Action History

**Example entry:**
- **Action**: Approve
- **Taken by**: Facility Agent Name
- **Taken at**: 2024-12-25 2:15 PM
- **Result**: Status changed to APPROVED
- **Comments**: "Request approved, funding notice generated"

**What this tells you:**
- Facility Agent approved the request
- Approval happened on December 25 at 2:15 PM
- Status changed to APPROVED
- Funding notice was generated

---

## Document History

### What It Shows

**Document history displays:**
- Document uploads: Document-specific history arrays (e.g., `collateralProfileHistory`, `financialStatementsHistory`, `kycDocumentsHistory` in term sheets)
- Document changes: Each upload creates entry in history array
- Who uploaded/changed: `uploadedBy` or `updatedBy` field in history entry
- When uploaded/changed: `uploadedAt` or `updatedAt` timestamp in history entry
- Previous versions: `previousVersions` array stores complete document versions with revision numbers
- Change reasons: `comments` field in `actionHistory` explains why document changed

**Database Structure:**
- **Term Sheets** (`cf_term_sheets` collection): 
  - Current documents: `collateralProfile`, `financialStatements`, `kycDocuments`, `collateralData`, `fundingSheet` (each contains `{ ipfsHash: '...', filename: '...', uploadedAt: Date }`)
  - History arrays: `collateralProfileHistory`, `financialStatementsHistory`, `kycDocumentsHistory`, `collateralDataHistory`, `fundingSheetHistory` (each contains array of previous versions)
  - Version tracking: `previousVersions` array stores complete document versions with `revisionNumber`
- **Funding Requests** (`cf_funding_requests` collection): Document history tracked similarly

**Where to find it:**
- Item details page: Document history arrays displayed in Documents section
- Documents section: Shows current documents and history
- Document history: Chronological list of all document versions
- Version history: `previousVersions` array shows complete version history

---

### Understanding Document History

**Example entry:**
- **Document**: Financial Statements
- **Action**: Upload
- **Uploaded by**: Borrower Name
- **Uploaded at**: 2024-12-25 9:00 AM
- **Version**: 1

**What this tells you:**
- Borrower uploaded financial statements
- Uploaded on December 25 at 9:00 AM
- This is version 1

---

## Change Tracking

### Field-Level Changes

**Some systems track:**
- Individual field changes
- Who changed each field
- When each field changed
- Previous value
- New value

**Example:**
- **Field**: Requested Amount
- **Changed by**: Borrower Name
- **Changed at**: 2024-12-25 11:00 AM
- **Previous value**: $5,000,000
- **New value**: $5,500,000

---

## Viewing Change History

### How to Access

**Methods:**
1. Navigate to item details page
2. Look for "Status History" or "Activity Log" section
3. Click to expand history
4. Review all changes
5. See complete timeline

### What You'll See

**History display:**
- Chronological list of changes
- Most recent first (or oldest first)
- Complete details for each change
- User names and timestamps
- Change descriptions

---

## Understanding Change Context

### Why Changes Happened

**Change history shows:**
- What triggered change
- Who initiated change
- Business reason
- Workflow progression
- Related actions

**Example:**
- Status changed to APPROVED
- Changed by Facility Agent
- Reason: "Request meets all requirements"
- Triggered: Funding notice generation

---

## Best Practices

1. **Review history regularly**: Check change history often
2. **Understand timeline**: See how things progressed
3. **Learn from history**: Use history to understand process
4. **Verify changes**: Confirm changes are correct
5. **Use for audit**: Leverage for compliance needs

---

## Common Use Cases

### Use Case 1: Understanding Process

**Scenario:**
- Want to understand how item reached current state
- Review status history
- See all status changes
- Understand workflow progression
- Learn from history

### Use Case 2: Audit Trail

**Scenario:**
- Need audit trail for compliance
- Review complete history
- See all changes and actions
- Document who did what when
- Maintain records

### Use Case 3: Dispute Resolution

**Scenario:**
- Dispute about what happened
- Review change history
- See exact timeline
- Identify who did what
- Resolve dispute with facts

---

## Key Takeaways

1. **Complete tracking**: Every change tracked with who and when
2. **Full history**: Complete change history available
3. **Easy access**: History visible in item details
4. **Comprehensive details**: Who, what, when, why all recorded
5. **Audit ready**: Complete records for compliance

Understanding who changed what and when helps you track complete transaction history and use it for compliance, audit, and process understanding.
