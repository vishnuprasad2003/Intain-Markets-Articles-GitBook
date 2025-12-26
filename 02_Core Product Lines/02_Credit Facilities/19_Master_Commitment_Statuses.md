# Master Commitment Statuses

## Overview

Master commitments progress through three main statuses from creation to activation. Understanding these statuses helps you know where your facility is in the setup process and what actions are available.

## Status Flow

### Complete Workflow

```
Draft → PendingLenderApproval → ACTIVE
```

Each status represents a specific stage in the master commitment lifecycle.

---

## Status 1: Draft

### What It Means

**Draft** is the initial state after auto-creation. The master commitment:
- Has been automatically created from approved term sheet
- Is ready for facility agent configuration
- Can be edited freely
- Has not been submitted for lender approval

### When It's Set

**Automatically set when:**
- Term sheet status changes to `'Accepted'` (via `POST /cf/acceptTermSheet/:termSheetId`)
- System automatically calls `autoCreateMasterCommitment(termSheet, masterCommitmentId)` function
- Master commitment document created in `cf_master_commitments` collection (MongoDB)
- Initial status is always `'DRAFT'` (stored as string `'DRAFT'` in database)
- `facilitySetupModelStatus` set to `'In Progress'`
- `requiredFieldsCompleted` set to `false`
- `actionHistory` array initialized with: `[{ action: 'Auto-Create', userId: 'system', timestamp: DateUtils.nowUTC(), comments: 'Automatically created from approved term sheet' }]`
- `statusHistory` array initialized with: `[{ status: 'Draft', userId: 'system', timestamp: DateUtils.nowUTC(), comments: 'Auto-created from approved term sheet' }]`

### What Facility Agent Can Do

**Full editing access:**
- Configure all facility rules
- Set up borrowing base calculations
- Define collateral eligibility rules
- Add and configure lender groups
- Edit any field (except pre-populated term sheet data)
- Save multiple times
- Make changes anytime

### What Facility Agent Cannot Do

- Cannot submit for lender approval (must complete configuration first)
- Cannot create funding requests (facility not active yet)

### Pre-Populated Data

**From term sheet (read-only):**
- Facility amount
- Interest rates
- Maturity date
- Advance rates
- Other commercial terms

**Empty for completion:**
- Facility rules
- Lender groups
- Borrowing base setup
- Collateral rules

### Next Steps

1. Complete facility configuration
2. Set up lender groups
3. Configure borrowing base
4. Define collateral rules
5. Submit for lender approval

---

## Status 2: PendingLenderApproval

### What It Means

**PendingLenderApproval** means:
- Facility agent has completed configuration
- Master commitment submitted for lender approval
- Waiting for lender decision
- Any selected lender can approve

### When It's Set

**Set when:**
- Facility agent completes all required fields (via auto-save: `POST /cf/master-commitments/:masterCommitmentId/auto-save-field`)
- Facility agent clicks "Create" or "Submit" button (via `POST /cf/createMasterCommitment`)
- System validates: all required fields filled, `lenderGroups` array has at least one lender, validation rules pass
- Database update in `cf_master_commitments` collection:
  - Status changes to `'PendingLenderApproval'`
  - Entry added to `statusHistory`: `{ status: 'PendingLenderApproval', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Submitted for lender approval' }`
  - Entry added to `actionHistory`: `{ action: 'Submit', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Master commitment submitted for lender approval' }`
  - Each lender in `lenderGroups` array initialized with `lenderStatus: 'pending_approval'`
- Lenders receive notifications (via notification system)

### What Facility Agent Can Do

**Limited actions:**
- View master commitment (read-only)
- See lender approval status
- Monitor approval progress
- May be able to edit (depends on system configuration)

### What Facility Agent Cannot Do

- Usually cannot edit (submitted for approval)
- Cannot activate facility (lenders must approve)

### What Lenders Can Do

**Review and approve:**
- View master commitment details
- Review facility structure
- Evaluate facility terms
- Approve via DocuSign
- Any lender approval activates facility

### What Happens After Approval

**When any lender approves:**
- Lender signs via DocuSign/ZohoSign (via `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign&masterCommitmentId=...&lenderOrgId=...`)
- Database update in `cf_master_commitments` collection:
  - Status changes to `'ACTIVE'` (if not already ACTIVE - first approval activates)
  - Lender's `lenderStatus` in `lenderGroups` array updated to `'approved'`
  - Lender's `approvedAt` timestamp set
  - Entry added to `statusHistory`: `{ status: 'ACTIVE', userId: lenderId, timestamp: DateUtils.nowUTC(), comments: 'Approved by lender' }`
  - Entry added to `actionHistory`: `{ action: 'Lender Approval', userId: lenderId, timestamp: DateUtils.nowUTC(), comments: 'Master commitment approved by lender' }`
- E-signature envelope generated (for documentation purposes - no additional signing required)
- Facility becomes operational: borrowers can create funding requests (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`)
- Lender status eventually updated to `'esignature_completed'` when e-signature envelope generation completes

### Next Steps

Wait for lender approval:
- Approved: Facility becomes ACTIVE
- Rejected: May return to Draft (if system allows)
- No action: Remains pending

---

## Status 3: ACTIVE

### What It Means

**ACTIVE** means:
- Facility is operational
- Approved by at least one lender
- Ready for funding requests
- Fully functional

### When It's Set

**Set when:**
- Any selected lender approves via DocuSign
- Lender signs master commitment
- System updates status to "ACTIVE"
- E-signature envelope generated

### What Happens Automatically

**After approval:**
- Status changes to "ACTIVE"
- E-signature envelope generated for documentation
- Facility becomes operational
- Borrowers notified (if applicable)
- Facility agent can manage active facility

### What Borrowers Can Do

**Create funding requests:**
- Create funding requests against facility
- Request drawdowns
- Submit for facility agent review
- Track funding requests

### What Facility Agent Can Do

**Manage active facility:**
- Review funding requests
- Approve/reject funding requests
- Manage facility operations
- View facility activity
- Generate funding notices

### What Lenders Can Do

**Participate in funding:**
- Review funding notices
- Approve/reject drawdowns
- Confirm fund transfers
- Track participation

### This Is Operational

- Facility is fully functional
- Funding requests can be created
- Drawdowns can proceed
- All parties can participate

---

## Status Transitions

### Forward Progression

**Draft → PendingLenderApproval:**
- Facility agent completes configuration
- Clicks "Create" or "Submit"
- Status changes automatically

**PendingLenderApproval → ACTIVE:**
- Any lender approves via DocuSign
- Status changes automatically
- Facility becomes operational

### Backward Transitions

**Usually not possible:**
- ACTIVE → PendingLenderApproval: Not typical (facility is active)
- PendingLenderApproval → Draft: May be possible if lender rejects (depends on system)
- ACTIVE → Draft: Not possible (facility is operational)

---

## Key Rules

### Editing Rules

**Can edit:**
- Draft status: Full editing allowed

**Cannot edit:**
- PendingLenderApproval: Usually read-only (submitted)
- ACTIVE: Read-only (operational)

### Submission Rules

**Can submit:**
- Draft status only
- All required fields must be filled
- Validation must pass

**Cannot submit:**
- PendingLenderApproval: Already submitted
- ACTIVE: Already active

### Approval Rules

**Can approve:**
- PendingLenderApproval status only
- Any selected lender can approve
- One approval activates facility

**Cannot approve:**
- Draft: Not submitted yet
- ACTIVE: Already approved

---

## Lender Approval Tracking

### Individual Lender Status

**Each lender tracked separately:**
- `lenderStatus`: pending_approval | approved | esignature_completed
- `approvedAt`: Timestamp when approved
- `updatedAt`: Last update timestamp

### Approval Process

**For each lender:**
1. Lender receives notification
2. Lender reviews master commitment
3. Lender signs via DocuSign
4. Lender status updates
5. Master commitment status changes to ACTIVE (on first approval)

### E-Signature Generation

**After approval:**
- E-signature envelope generated
- For documentation purposes
- No actual signing required (already signed via DocuSign)
- Completes lender status to "esignature_completed"

---

## Common Scenarios

### Scenario 1: Smooth Activation

1. Term sheet approved → Master commitment created (Draft)
2. Facility agent configures → Still Draft
3. Facility agent submits → PendingLenderApproval
4. Lender approves → ACTIVE
5. Facility operational

### Scenario 2: Multiple Lenders

1. Master commitment in PendingLenderApproval
2. Lender A approves → ACTIVE (first approval activates)
3. Lender B can still approve (for their own tracking)
4. Lender C can still approve (for their own tracking)
5. All lenders tracked individually

### Scenario 3: Configuration Changes

1. Master commitment in Draft
2. Facility agent makes changes
3. Saves multiple times
4. Submits when ready → PendingLenderApproval
5. Lender approves → ACTIVE

---

## Best Practices

### For Facility Agents

1. Complete configuration: Set up all rules before submitting
2. Review thoroughly: Verify all information correct
3. Test setup: Ensure calculations work
4. Submit when ready: Don't rush submission
5. Monitor approval: Track lender approval progress

### For Lenders

1. Review carefully: Understand facility structure
2. Evaluate terms: Assess facility parameters
3. Approve promptly: Keep workflow moving
4. Track status: Monitor your approval status

### For Borrowers

1. Monitor progress: Track master commitment status
2. Prepare requests: Ready funding requests for when ACTIVE
3. Understand rules: Know facility parameters
4. Stay informed: Watch for status updates

---

## Troubleshooting

### "Can't edit master commitment"
- Check status is "Draft"
- Verify you have permission
- Ensure you're the facility agent
- Check if facility is locked

### "Can't submit for approval"
- Verify status is "Draft"
- Check all required fields filled
- Ensure validation passes
- Verify lender groups configured

### "Lender can't approve"
- Check status is "PendingLenderApproval"
- Verify lender is in lender groups
- Ensure DocuSign process available
- Check lender permissions

### "Status not changing to ACTIVE"
- Verify lender approval completed
- Check DocuSign completion
- Ensure approval process completed
- Contact support if issue persists

---

## Key Takeaways

1. Three statuses: Draft → PendingLenderApproval → ACTIVE
2. Draft is configurable: Facility agent sets up facility
3. PendingLenderApproval waits: For lender approval
4. ACTIVE enables funding: Borrowers can create requests
5. One approval activates: Any lender approval makes it ACTIVE

Understanding master commitment statuses helps you track facility setup progress and know what actions are available at each stage.
