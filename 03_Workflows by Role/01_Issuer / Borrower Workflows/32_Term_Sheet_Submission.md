# Term Sheet Submission

## Overview

Term sheet submission is the process where borrowers submit their term sheets to facility agents for review. This guide covers how to prepare, sign, and submit term sheets effectively.

## Preparing for Submission

### Step 1: Complete Term Sheet

**Ensure completeness:**
- All required fields filled
- Facility terms specified
- Documents uploaded
- Information accurate
- Ready for signing

### Step 2: Review Information

**Before signing:**
- Review all term sheet details
- Verify amounts and rates
- Check dates and terms
- Ensure accuracy
- Make any final adjustments

### Step 3: Upload Documents

**Required documents:**
- Financial statements (if required)
- KYC documents (if required)
- Collateral documentation (if applicable)
- Other supporting materials

**Document tips:**
- Ensure documents are complete
- Verify document quality
- Check file formats
- Organize documents clearly

---

## Signing the Term Sheet

### Step 1: Initiate DocuSign

**How to start:**
1. Navigate to term sheet
2. Ensure status is "Draft"
3. Click "Sign" or "Initiate DocuSign"
4. DocuSign process begins

### Step 2: Complete Signing

**Signing process:**
1. Review documents in DocuSign
2. Complete all required signature fields
3. Sign electronically
4. Complete signing process
5. DocuSign completion triggers status change

### Step 3: Verify Completion

**After signing:**
- Status changes to "BorrowerSigned"
- Can preview signed term sheet
- Ready for submission
- Cannot edit (after signing)

---

## Submitting the Term Sheet

### Step 1: Preview Signed Version

**Before submitting:**
1. Review signed term sheet
2. Verify all information correct
3. Check documents are attached
4. Ensure everything is complete

### Step 2: Submit for Review

**Submission process:**
1. Navigate to term sheet (via `GET /cf/getTermSheet/:termSheetId`)
2. Ensure status is `'BorrowerSigned'` (validated in code: `termSheet.status === 'BorrowerSigned'`)
3. Click "Submit" button (via `POST /cf/submitTermSheet/:termSheetId`)
4. System validates: status is `'BorrowerSigned'`, DocuSign completed (`docusignStatus: 'completed'`), all required fields filled
5. Database update in `cf_term_sheets` collection:
   - Status changes to `'FAReview'`
   - `submittedAt` set to current timestamp (`DateUtils.nowUTC()`)
   - `submittedBy` set to borrower user ID (`req.userId`)
   - `submissionCount` incremented
   - Entry added to `statusHistory`: `{ status: 'FAReview', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Submitted for facility agent review' }`
   - Entry added to `actionHistory`: `{ action: 'Submit', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Term sheet submitted for facility agent review', details: { previousStatus: 'BorrowerSigned', newStatus: 'FAReview', submissionCount: incremented } }`
6. Facility agent receives notification (via notification system)
7. Status changes to "FAReview" - term sheet locked for editing, waiting for facility agent review

### Step 3: Verify Submission

**After submission:**
- Status changes to "FAReview"
- Facility agent receives notification
- Cannot edit (submitted for review)
- Wait for facility agent decision

---

## Submission Requirements

### Prerequisites

**Must have:**
- Status: BorrowerSigned (signed via DocuSign)
- All required fields filled
- Required documents uploaded
- Information validated
- Ready for review

### Validation

**System checks:**
- All required fields present
- Data format correct
- Documents uploaded
- Signing completed
- Ready for submission

---

## After Submission

### What Happens

**Immediate actions:**
- Status changes to FAReview
- Facility agent notified
- Term sheet locked for editing
- Review process begins

### What You Can Do

**After submission:**
- View term sheet (read-only)
- See review status
- Wait for facility agent decision
- Respond to change requests (if requested)

**What you cannot do:**
- Cannot edit term sheet (submitted)
- Cannot resubmit (already submitted)
- Cannot cancel submission (in review)

---

## Responding to Change Requests

### If Changes Requested

**What happens:**
- Status changes to CHANGES_REQUESTED
- You receive notification
- Can edit term sheet again
- Make requested changes
- Resubmit when ready

### Making Changes

**Process:**
1. Review change request details
2. Make requested modifications
3. Update documents if needed
4. Re-sign if required
5. Resubmit for review

---

## Best Practices

### Before Submission

1. Complete thoroughly: Fill all required fields
2. Review carefully: Verify all information
3. Upload documents: Include all required documents
4. Sign properly: Complete DocuSign process
5. Preview before submit: Review signed version

### Submission Process

1. Submit when ready: Don't rush submission
2. Verify status: Ensure submission successful
3. Monitor progress: Track review status
4. Respond promptly: Address change requests quickly

### After Submission

1. Be patient: Allow time for review
2. Monitor status: Watch for updates
3. Respond to feedback: Address change requests
4. Stay informed: Check notifications

---

## Common Scenarios

### Scenario 1: Smooth Submission

1. Complete term sheet → Draft
2. Sign via DocuSign → BorrowerSigned
3. Submit for review → FAReview
4. Facility agent approves → Accepted
5. Master commitment created

### Scenario 2: Changes Requested

1. Submit term sheet → FAReview
2. Changes requested → CHANGES_REQUESTED
3. Make changes → Still CHANGES_REQUESTED
4. Resubmit → FAReview
5. Facility agent approves → Accepted

### Scenario 3: Rejection

1. Submit term sheet → FAReview
2. Facility agent rejects → Rejected
3. Review rejection reason
4. Create new term sheet → Try again

---

## Troubleshooting

### "Can't submit term sheet"
- Check status is BorrowerSigned
- Verify DocuSign completed
- Ensure all required fields filled
- Check for validation errors

### "Can't sign term sheet"
- Check status is Draft
- Verify documents are ready
- Ensure DocuSign available
- Check for errors

### "Submission not working"
- Verify all requirements met
- Check status allows submission
- Ensure no validation errors
- Contact support if needed

---

## Key Takeaways

1. Complete first: Fill all required information
2. Sign required: Must sign before submission
3. Submit when ready: Don't rush the process
4. Respond to feedback: Address change requests
5. Monitor progress: Track review status

Understanding term sheet submission helps you effectively submit your credit facility requests and navigate the review process.
