# Funding Requests

## Overview

This guide covers how borrowers create, manage, and submit funding requests against active credit facilities. Learn how to request drawdowns, provide supporting documentation, and track request status.

## Creating Funding Requests

### Prerequisites

**Before creating:**
- Master commitment must be ACTIVE
- Facility must be operational
- You must have access to facility
- Facility must have available capacity

### Step 1: Access Funding Request Creation

**How to start:**
1. Navigate to active master commitment (via `GET /cf/master-commitments/:masterCommitmentId`) - must have `status: 'ACTIVE'`
2. System validates: master commitment exists, status is `'ACTIVE'`, borrower has access (`issuerOrgId` matches)
3. Go to Funding Requests section
4. Click "Create Funding Request" or "Check or Create Draft" (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft?issuerOrgId=...`)
5. System checks if draft exists: queries `cf_funding_requests` collection for document with `masterCommitmentId`, `issuerOrgId`, and `status: 'DRAFT'`
6. **Draft Prevention**: If draft exists, returns existing draft instead of creating new one (prevents multiple drafts)
7. If no draft exists, creates new funding request in `cf_funding_requests` collection with `status: 'DRAFT'`
8. Funding request form opens with draft data

### Step 2: Enter Request Details

**Required information:**
- Requested Amount: Amount you want to draw down
- Purpose: Purpose of the funds
- Funding Date: When you need the funds
- Supporting Documentation: Documents supporting the request

**Tips:**
- Request amount within facility limits
- Provide clear purpose
- Include all required documentation
- Be specific about funding date

### Step 3: Add Collateral (If Applicable)

**If collateral required:**
- Select loans to use as collateral
- Provide collateral details
- Include collateral documentation
- Verify collateral eligibility

### Step 4: Save or Submit

**Options:**
- Save as Draft: Save for later completion
- Submit: Submit immediately for review

**Draft status:**
- Can edit freely
- Auto-save enabled
- Can complete later
- Submit when ready

---

## Managing Funding Requests

### Viewing Requests

**Where to see:**
- Funding Requests section
- Master commitment details
- Your dashboard
- Status-based lists

### Request Statuses

**DRAFT:**
- Request created but not submitted
- Can edit freely
- Auto-save enabled

**FAReview:**
- Submitted for facility agent review
- Cannot edit
- Waiting for decision

**APPROVED:**
- Facility agent approved
- Funding notice generated
- Drawdown can proceed

**REJECTED:**
- Facility agent rejected
- Final state
- Must create new request

**CHANGES_REQUESTED:**
- Facility agent wants modifications
- Can edit and resubmit
- Iterative improvement

---

## Updating Funding Requests

### Editing Draft Requests

**When you can edit:**
- Status is DRAFT
- Request not yet submitted
- You have permission

**How to edit:**
1. Navigate to request
2. Click "Edit" button
3. Update information
4. Save changes
5. Can save multiple times

### Responding to Change Requests

**When changes requested:**
- Status changes to CHANGES_REQUESTED
- Can edit again
- Make requested modifications
- Resubmit when ready

**Process:**
1. Review change request details
2. Make requested changes
3. Update documentation if needed
4. Resubmit for review
5. Status changes back to FAReview

---

## Submitting Funding Requests

### Before Submitting

**Check:**
- All required fields filled
- Documentation complete
- Information accurate
- Amount within limits
- Ready for review

### Submission Process

**How to submit:**
1. Review request thoroughly (via `GET /cf/funding-requests/:fundingRequestId`)
2. Verify all information: check `requestAmount`, `purpose`, `fundingDate`, supporting documentation
3. Click "Submit" button (via `POST /cf/funding-requests/:fundingRequestId/submit`)
4. System validates: status is `'DRAFT'`, all required fields filled, master commitment is `'ACTIVE'`
5. Database update in `cf_funding_requests` collection:
   - Status changes to `'FAReview'`
   - `submittedAt` set to current timestamp
   - `submittedBy` set to borrower user ID
   - `submissionCount` incremented
   - Current version saved to `previousVersions` array
   - Entry added to `statusHistory`: `{ status: 'FAReview', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Submitted for market maker approval' }`
   - Entry added to `actionHistory`: `{ action: 'Submit', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Funding request submitted for market maker approval', details: { previousStatus: 'DRAFT', newStatus: 'FAReview', submissionCount: incremented } }`
6. Facility agent receives notification (via notification system)
7. Confirm submission: status changes to FAReview - request locked for editing, waiting for facility agent decision

### After Submission

**What happens:**
- Status changes to FAReview
- Facility agent receives notification
- Cannot edit (submitted)
- Wait for facility agent decision

---

## Best Practices

### Creating Requests

1. Complete thoroughly: Fill all required fields
2. Provide documentation: Include supporting materials
3. **Be specific**: Clear purpose and details
4. **Check limits**: Ensure amount within capacity
5. **Review before submit**: Verify accuracy

### Managing Requests

1. **Track status**: Monitor request progress
2. **Respond promptly**: Address change requests quickly
3. **Update as needed**: Keep information current
4. **Monitor approvals**: Track approval status

### After Approval

1. **Monitor funding notice**: Track notice creation
2. **Approve tokens**: Enable lender visibility
3. **Track progress**: Monitor drawdown status
4. **Prepare for funds**: Ready to receive funds

---

## Common Scenarios

### Scenario 1: Standard Request

1. Create request → DRAFT
2. Complete information → Still DRAFT
3. Submit for review → FAReview
4. Facility agent approves → APPROVED
5. Funding notice generated

### Scenario 2: Changes Requested

1. Submit request → FAReview
2. Changes requested → CHANGES_REQUESTED
3. Make changes → Still CHANGES_REQUESTED
4. Resubmit → FAReview
5. Facility agent approves → APPROVED

### Scenario 3: Rejection

1. Submit request → FAReview
2. Facility agent rejects → REJECTED
3. Review rejection reason
4. Create new request → Try again

---

## Troubleshooting

### "Can't create funding request"
- Check master commitment is ACTIVE
- Verify you have access to facility
- Ensure facility has available capacity
- Check you have permission

### "Can't submit request"
- Verify status is DRAFT
- Check all required fields filled
- Ensure documentation uploaded
- Verify validation passes

### "Request rejected"
- Review rejection reason
- Understand why rejected
- Fix issues for next request
- Create new request with corrections

---

## Key Takeaways

1. **Create against active facilities**: Master commitment must be ACTIVE
2. **Complete thoroughly**: Provide all required information
3. **Submit when ready**: Don't rush submission
4. **Respond to feedback**: Address change requests
5. **Track progress**: Monitor request status

Understanding funding requests helps you effectively request and receive funds from your credit facilities.
