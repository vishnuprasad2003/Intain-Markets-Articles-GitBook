# Term Sheet Workflow

## Overview

The term sheet is the first step in creating a credit facility. It's the borrower's proposal outlining the key terms of the facility they want. Understanding the term sheet workflow helps you navigate this critical first phase.

## Term Sheet Status Flow

### Complete Workflow

```
Draft → BorrowerSigned → FAReview → Accepted/Rejected/CHANGES_REQUESTED
```

**Database Collection:** `cf_term_sheets` (MongoDB)

Each status represents a specific stage in the term sheet process. Status changes are tracked in the `statusHistory` array with timestamps, user IDs, and comments. All actions are logged in the `actionHistory` array for complete audit trails.

---

## Status 1: Draft

### What It Means

**Draft** is the initial creation state. The term sheet:
- Has been created with basic information
- Can be edited freely
- Has not been signed yet
- Has not been submitted for review

### What You Can Do

**As Borrower:**
- Edit all term sheet fields
- Upload documents
- Save changes (auto-save enabled)
- Make multiple revisions
- Delete term sheet (if allowed)

**What You Cannot Do:**
- Cannot submit for review (must sign first)
- Cannot preview signed version

### Next Steps

1. Complete all required fields
2. Upload required documents
3. Review information for accuracy
4. Proceed to DocuSign signing

---

## Status 2: BorrowerSigned

### What It Means

**BorrowerSigned** means:
- Borrower has completed DocuSign signing
- Term sheet is electronically signed
- Ready for submission to facility agent
- Borrower can preview the signed term sheet

### How It's Achieved

**DocuSign Process:**
1. Borrower initiates DocuSign from Draft status
2. DocuSign envelope created
3. Borrower signs documents electronically
4. DocuSign completion triggers status change
5. Status automatically changes to "BorrowerSigned"

### What You Can Do

**As Borrower:**
- Preview the signed term sheet
- Submit for facility agent review
- View signed documents
- Make final adjustments (if needed before submission)

**What You Cannot Do:**
- Cannot edit term sheet (after signing, editing restricted)
- Cannot resubmit without changes (if already submitted)

### Next Steps

1. Preview signed term sheet
2. Verify all information correct
3. Submit for facility agent review

---

## Status 3: FAReview

### What It Means

**FAReview** means:
- Term sheet has been submitted to facility agent
- Facility agent is reviewing the proposal
- Waiting for facility agent decision
- No further edits allowed by borrower

### How It's Achieved

**Submission Process:**
1. Borrower clicks "Submit" from BorrowerSigned status (via `POST /cf/submitTermSheet/:termSheetId`)
2. System validates submission readiness: checks status is `'BorrowerSigned'`, verifies DocuSign completed, validates required fields
3. Database update in `cf_term_sheets` collection:
   - Status changes to `'FAReview'`
   - `submittedAt` set to current timestamp
   - `submittedBy` set to borrower user ID
   - `submissionCount` incremented
   - Entry added to `statusHistory`: `{ status: 'FAReview', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Submitted for facility agent review' }`
   - Entry added to `actionHistory`: `{ action: 'Submit', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Term sheet submitted for facility agent review' }`
4. Facility agent receives notification (via notification system)
5. Facility agent can now review (via `GET /cf/getTermSheet/:termSheetId`)

### What Happens

**Facility Agent Can:**
- Review term sheet details
- Analyze facility terms
- Request changes
- Approve term sheet
- Reject term sheet

**Borrower Can:**
- View term sheet (read-only)
- See review status
- Wait for facility agent decision

### Next Steps

Wait for facility agent to:
- Approve (triggers master commitment creation)
- Reject (final state)
- Request changes (allows editing again)

---

## Status 4: Accepted

### What It Means

**Accepted** means:
- Facility agent has approved the term sheet
- Master commitment is automatically created
- Facility setup can begin
- Term sheet phase is complete

### How It's Achieved

**Approval Process:**
1. Facility agent reviews term sheet (via `GET /cf/getTermSheet/:termSheetId`)
2. Facility agent clicks "Approve" (via `POST /cf/acceptTermSheet/:termSheetId`)
3. Database update in `cf_term_sheets` collection:
   - Status changes to `'Accepted'`
   - Entry added to `statusHistory`: `{ status: 'Accepted', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Approved by facility agent' }`
   - Entry added to `actionHistory`: `{ action: 'Approve', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Term sheet approved' }`
4. System automatically calls `autoCreateMasterCommitment()` function:
   - Generates `masterCommitmentId` using format: `MC-MMDDYYYY-XXXX` (where MMDDYYYY is current date, XXXX is random alphanumeric)
   - Creates document in `cf_master_commitments` collection with `'DRAFT'` status
   - Pre-populates read-only fields from term sheet: `advanceRate`, `margin`, `pricingIndex`, `maturityDate`, `drawFrequency`, `covenantTemplate`, `totalCommitmentAmount`, `marketMakerOrgId`, `issuerOrgId`, `issuerId`
   - Sets empty arrays for facility agent to complete: `collateralRules: []`, `lenderGroups: []`, `servicerOrgId: []`
   - Links to term sheet via `termSheetId` field
5. Master commitment starts in "Draft" status and is ready for facility agent configuration

### What Happens Next

**Automatic Actions:**
- Master commitment created automatically
- Pre-populated with term sheet data
- Linked to term sheet via termSheetId
- Facility agent can now configure it

**Borrower Can:**
- ✅ View approved term sheet
- ✅ See master commitment was created
- ✅ Monitor master commitment progress

### This Is Final

- Term sheet cannot be edited after acceptance
- Master commitment takes over
- Workflow moves to master commitment phase

---

## Status 5: Rejected

### What It Means

**Rejected** means:
- Facility agent has rejected the term sheet
- Facility will not proceed
- This is a final state
- No further action possible on this term sheet

### How It's Achieved

**Rejection Process:**
1. Facility agent reviews term sheet
2. Facility agent clicks "Reject"
3. Status changes to "Rejected"
4. Borrower receives notification
5. Term sheet stops here

### What Happens

**No Automatic Actions:**
- No master commitment created
- Facility does not proceed
- Term sheet remains rejected

**Borrower Can:**
- View rejected term sheet
- See rejection reason (if provided)
- Create new term sheet if desired

### This Is Final

- Term sheet cannot be edited after rejection
- Cannot resubmit same term sheet
- Must create new term sheet to try again

---

## Status 6: CHANGES_REQUESTED

### What It Means

**CHANGES_REQUESTED** means:
- Facility agent wants modifications
- Borrower can edit and resubmit
- Term sheet needs revision
- Not a final state

### How It's Achieved

**Change Request Process:**
1. Facility agent reviews term sheet (via `GET /cf/getTermSheet/:termSheetId`)
2. Facility agent clicks "Request Changes" (via `POST /cf/requestChanges/:termSheetId`)
3. Facility agent provides change details in request body: `{ comments: '...', requestedChanges: [...] }`
4. Database update in `cf_term_sheets` collection:
   - Status changes to `'CHANGES_REQUESTED'`
   - `revisionNumber` incremented (e.g., from 1 to 2)
   - Current version saved to `previousVersions` array with revision number
   - `changeRequests` array updated: new entry added with `{ requestId: uuid, requestedBy: facilityAgentId, requestedAt: DateUtils.nowUTC(), comments: '...', sequence: changeRequestsCount + 1 }`
   - `changeRequestsCount` incremented
   - `lastChangeRequestedAt` set to current timestamp
   - `lastChangeRequestedBy` set to facility agent user ID
   - DocuSign status may reset (requires re-signing if documents changed)
   - Auto-save re-enabled (can edit again)
   - Entry added to `statusHistory`: `{ status: 'CHANGES_REQUESTED', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Changes requested by facility agent' }`
   - Entry added to `actionHistory`: `{ action: 'Request Changes', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: '...' }`
5. Borrower receives notification (via notification system)

### What Happens

**Automatic Actions:**
- Revision number increments
- Current version saved to history
- DocuSign status may reset (requires re-signing)
- Auto-save re-enabled
- Change request record created

**Borrower Can:**
- Edit term sheet fields
- Make requested changes
- Upload new documents
- Save changes multiple times
- Resubmit after changes

### Next Steps

1. Review change request details
2. Make requested modifications
3. Re-sign via DocuSign (if needed)
4. Resubmit for review
5. Status changes back to "FAReview"

---

## Key Workflow Rules

### Editing Rules

**Can Edit:**
- Draft status: Full editing allowed
- CHANGES_REQUESTED status: Full editing allowed

**Cannot Edit:**
- BorrowerSigned: Limited editing (before submission)
- FAReview: Read-only
- Accepted: Read-only (final)
- Rejected: Read-only (final)

### Submission Rules

**Can Submit:**
- BorrowerSigned status only
- Must have completed DocuSign
- All required fields filled

**Cannot Submit:**
- Draft: Must sign first
- FAReview: Already submitted
- Accepted/Rejected: Final states

### Auto-Save

**Enabled:**
- Draft status
- CHANGES_REQUESTED status

**Disabled:**
- After submission
- In review states
- In final states

---

## Common Scenarios

### Scenario 1: Smooth Approval

1. Create term sheet → **Draft**
2. Complete information → Still **Draft**
3. Sign via DocuSign → **BorrowerSigned**
4. Submit for review → **FAReview**
5. Facility agent approves → **Accepted**
6. Master commitment auto-created

### Scenario 2: Changes Requested

1. Create term sheet → **Draft**
2. Sign and submit → **FAReview**
3. Facility agent requests changes → **CHANGES_REQUESTED**
4. Make changes → Still **CHANGES_REQUESTED**
5. Re-sign if needed → Still **CHANGES_REQUESTED**
6. Resubmit → **FAReview**
7. Facility agent approves → **Accepted**

### Scenario 3: Rejection

1. Create term sheet → **Draft**
2. Sign and submit → **FAReview**
3. Facility agent rejects → **Rejected**
4. Create new term sheet to try again

---

## Best Practices

### Creating Term Sheets

1. **Complete all fields**: Fill in all required information
2. **Review before signing**: Verify accuracy before DocuSign
3. **Upload documents**: Include all required documents
4. **Save frequently**: Use auto-save feature

### Submitting Term Sheets

1. **Verify completeness**: Ensure all information present
2. **Check documents**: Verify all documents uploaded
3. **Review signed version**: Preview before submitting
4. **Submit when ready**: Don't rush submission

### Responding to Changes

1. **Read carefully**: Understand requested changes
2. **Address all items**: Don't miss any requested changes
3. **Re-sign if needed**: Complete DocuSign again if required
4. **Resubmit promptly**: Keep workflow moving

---

## Troubleshooting

### "Can't submit term sheet"
- Check status is "BorrowerSigned"
- Verify DocuSign completed
- Ensure all required fields filled
- Check for validation errors

### "Can't edit term sheet"
- Check current status
- Only Draft and CHANGES_REQUESTED allow editing
- Verify you have permission
- Check if term sheet is locked

### "Status changed unexpectedly"
- Check notifications for who changed it
- Review status history
- Some status changes are automatic (DocuSign completion)
- Contact support if unclear

Understanding the term sheet workflow helps you effectively navigate the first phase of credit facility creation and know what to expect at each stage.
