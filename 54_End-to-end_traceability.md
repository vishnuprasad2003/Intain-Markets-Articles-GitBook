# End-to-End Traceability

## Overview

End-to-end traceability means you can track every action, status change, and decision from the beginning to the end of any transaction. Intain Markets provides complete traceability through audit trails, status history, and comprehensive logging.

## What is Traceability?

### Definition

**Traceability:**
- Ability to track complete history
- See who did what and when
- Understand why things happened
- Complete audit trail
- Full transaction visibility

**Why it matters:**
- Compliance requirements
- Audit purposes
- Dispute resolution
- Process understanding
- Accountability

---

## What Gets Tracked

### Status Changes

**Every status change:**
- Who changed it: `userId` field from JWT token (`req.userId`), stored in `statusHistory` array
- When it changed: `timestamp` field using `DateUtils.nowUTC()`, stored in `statusHistory` array
- What it changed from: `previousStatus` field (if tracked), or inferred from previous `statusHistory` entry
- What it changed to: `status` field value, stored in `statusHistory` array
- Why it changed (if applicable): `comments` field in `statusHistory` entry, explains reason for change

**Database Structure:**
- **Term Sheets** (`cf_term_sheets` collection): `statusHistory` array contains `[{ status: '...', userId: '...', timestamp: Date, comments: '...', sequence: number, revisionNumber: number }]`
- **Master Commitments** (`cf_master_commitments` collection): `statusHistory` array tracks status changes
- **Funding Requests** (`cf_funding_requests` collection): `statusHistory` array tracks status changes
- **Funding Notices** (`cf_funding_notices` collection): `statusHistory` array tracks status changes
- **Pools** (`pool_detail` collection): Status changes tracked in `statusHistory` array (if implemented)

**Examples:**
- Term sheet: `'DRAFT'` → `'BorrowerSigned'` → `'FAReview'` → `'Accepted'` (each transition logged in `statusHistory`)
- Master commitment: `'DRAFT'` → `'PendingLenderApproval'` → `'ACTIVE'` (each transition logged)
- Funding request: `'DRAFT'` → `'FAReview'` → `'APPROVED'` (each transition logged)

---

### Actions Taken

**Every action:**
- Who took the action: `userId` field from JWT token (`req.userId`), stored in `actionHistory` array
- When action was taken: `timestamp` field using `DateUtils.nowUTC()`, stored in `actionHistory` array
- What action was taken: `action` field (e.g., `'Create'`, `'Approve'`, `'Submit'`, `'Sign'`, `'Request Changes'`), stored in `actionHistory` array
- What was affected: `details` object in `actionHistory` entry, contains affected fields and values
- Result of action: `comments` field and `details` object describe result (e.g., "Funding notice generated", "Status changed to APPROVED")

**Database Structure:**
- **Term Sheets** (`cf_term_sheets` collection): `actionHistory` array contains `[{ action: '...', userId: '...', timestamp: Date, comments: '...', details: {...}, sequence: number, revisionNumber: number }]`
- **Master Commitments** (`cf_master_commitments` collection): `actionHistory` array tracks all actions
- **Funding Requests** (`cf_funding_requests` collection): `actionHistory` array tracks all actions
- **Funding Notices** (`cf_funding_notices` collection): `actionHistory` array tracks all actions

**Examples:**
- Created term sheet: `{ action: 'Create', userId: borrowerId, timestamp: Date, comments: 'Term sheet created', details: { status: 'Draft' } }`
- Approved funding request: `{ action: 'Approve', userId: facilityAgentId, timestamp: Date, comments: 'Funding request approved', details: { previousStatus: 'FAReview', newStatus: 'APPROVED', fundingNoticeId: '...' } }`
- Signed document: `{ action: 'E-Signature Completed', userId: signerId, timestamp: Date, comments: 'DocuSign completed', details: { docusignStatus: 'completed', ipfsHash: '...' } }`
- Generated tokens: `{ action: 'Generate Tokens', userId: facilityAgentId, timestamp: Date, comments: 'FT tokens created', details: { ftContractAddress: '...', totalSupply: number } }`
- Confirmed fund transfer: `{ action: 'Confirm Fund Transfer', userId: lenderId, timestamp: Date, comments: 'Fund transfer confirmed', details: { lenderOrgId: '...', amountTransferred: 'transferred' } }`

---

### Document Changes

**Every document change:**
- Who changed document
- When changed
- What changed
- Previous version saved
- Change reason

**Examples:**
- Term sheet revisions
- Funding request updates
- Document uploads
- Field modifications

---

## Where to See Traceability

### Status History

**Available in:**
- Item details page
- Status history section
- Activity log
- Audit trail view

**Shows:**
- All status changes
- Who made changes
- When changes occurred
- Previous statuses
- Change reasons

---

### Action History

**Available in:**
- Item details page
- Action history section
- Activity log
- Audit trail

**Shows:**
- All actions taken
- Who took actions
- When actions occurred
- Action results
- Related changes

---

### Audit Trail

**Available in:**
- Dedicated audit trail view
- Complete transaction history
- Exportable reports
- Searchable logs

**Shows:**
- Complete history
- All changes
- All actions
- All decisions
- Full timeline

---

## Complete Transaction Flow

### Example: Credit Facility

**Complete traceability:**
1. Term sheet created → Who, when, initial status
2. Term sheet signed → Who signed, when, DocuSign completion
3. Term sheet submitted → Who submitted, when, status change
4. Facility agent reviews → Who reviewed, when, decision
5. Term sheet approved → Who approved, when, master commitment created
6. Master commitment configured → Who configured, when, what changed
7. Master commitment submitted → Who submitted, when, status change
8. Lender approves → Who approved, when, facility activated
9. Funding request created → Who created, when, details
10. Funding request approved → Who approved, when, funding notice created
11. Tokens generated → Who generated, when, token details
12. Borrower approves tokens → Who approved, when, status change
13. Lender approves drawdown → Who approved, when, decision
14. Fund transfer confirmed → Who confirmed, when, completion

**Every step tracked:**
- Complete visibility
- Full audit trail
- All parties recorded
- All timestamps
- All decisions documented

---

## Benefits of Traceability

### Compliance

**For compliance:**
- Regulatory requirements met
- Audit trails maintained
- Documentation complete
- History preserved
- Accountability clear

### Dispute Resolution

**For disputes:**
- Complete history available
- All actions documented
- Decisions recorded
- Timeline clear
- Facts established

### Process Understanding

**For understanding:**
- See how things happened
- Understand workflow
- Learn from history
- Identify patterns
- Improve processes

---

## Best Practices

1. **Review history**: Check status and action history regularly
2. **Understand timeline**: See how things progressed
3. **Learn from history**: Use history to improve
4. **Maintain records**: Keep audit trail accessible
5. **Use for compliance**: Leverage for regulatory needs

---

## Key Takeaways

1. **Complete tracking**: Every action and change tracked
2. **Full history**: Complete audit trail maintained
3. **Who and when**: All parties and timestamps recorded
4. **Compliance ready**: Meets regulatory requirements
5. **Transparency**: Full visibility of all activities

Understanding end-to-end traceability helps you appreciate the platform's comprehensive tracking and use it for compliance, audit, and process understanding.
