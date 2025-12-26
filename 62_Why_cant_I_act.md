# "Why Can't I Act?"

## Overview

This guide helps you understand why you can't take certain actions and how to resolve common issues preventing you from acting. Use this as a troubleshooting guide when actions are unavailable.

## Quick Diagnosis

### Step 1: Check the Button

**If button is disabled:**
1. Hover over it - tooltip explains why
2. Check status message nearby
3. Look for error or warning messages
4. Review item status
5. Check requirements

---

### Step 2: Check Your Role

**Verify:**
- Are you logged in with correct role?
- Does your role have permission for this action?
- Are you assigned to this item?
- Do you have access?

**Common issues:**
- Logged in with wrong role
- Role doesn't have permission
- Not assigned to item
- Access restricted

---

### Step 3: Check the Status

**Verify:**
- What is current status?
- Does status allow this action?
- Is status correct for workflow?
- Has status changed unexpectedly?

**Common issues:**
- Wrong status for action
- Status doesn't permit action
- Must complete previous steps first
- Status changed unexpectedly

---

### Step 4: Check Requirements

**Verify:**
- Are all required fields filled?
- Are documents uploaded?
- Are prerequisites met?
- Is information complete?

**Common issues:**
- Missing required fields
- Documents not uploaded
- Prerequisites not met
- Information incomplete

---

## Common "Can't Act" Scenarios

### "I Can't Submit My Term Sheet"

**Possible reasons:**
- Status is Draft (must sign first): Code validates `termSheet.status === 'BorrowerSigned'` before allowing submission (via `POST /cf/submitTermSheet/:termSheetId`)
- DocuSign not completed: Code checks `docusignStatus === 'completed'` or validates DocuSign completion before allowing submission
- Required fields not filled: Code validates required fields (`requestedCommitmentAmount`, `advanceRate`, `margin`, `pricingIndex`, `maturityDate`, `drawFrequency`, `marketMakerOrgId`, `issuerId`, `issuerOrgId`) before allowing submission
- Documents not uploaded: Code may validate required documents exist (if required)
- Validation errors: Code performs data type validation (e.g., `parseFloat()` for numbers, `DateUtils.toUTCDate()` for dates) and format checks

**Solutions:**
1. Sign via DocuSign first (via DocuSign/ZohoSign integration, webhook updates status to `'BorrowerSigned'`)
2. Complete all required fields: Fill `requestedCommitmentAmount`, `advanceRate`, `margin`, `pricingIndex`, `maturityDate`, `drawFrequency`, `marketMakerOrgId`, `issuerId`, `issuerOrgId`
3. Upload all documents: Upload via `POST /cf/uploadTermSheetDocument/:termSheetId` if required
4. Fix validation errors: Ensure data types correct (numbers are numbers, dates are valid dates)
5. Then submit: Once status is `'BorrowerSigned'` and all validations pass, submit via `POST /cf/submitTermSheet/:termSheetId`

---

### "I Can't Create a Funding Request"

**Possible reasons:**
- Master commitment not ACTIVE: Code validates `masterCommitment.status === 'ACTIVE'` before allowing funding request creation (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`)
- Facility not operational: Same validation - master commitment must be `'ACTIVE'` status
- No available borrowing capacity: Code may check `availableCapacity > 0` in master commitment before allowing creation
- Missing required information: Code validates required fields (`requestAmount`, `fundingDate`, `purpose`, etc.) before allowing submission
- Not assigned to facility: Code validates `issuerOrgId` matches user's organization (`req.organizationId`) before allowing creation

**Solutions:**
1. Check master commitment status: Verify `status: 'ACTIVE'` in `cf_master_commitments` collection (via `GET /cf/master-commitments/:masterCommitmentId`)
2. Verify facility is ACTIVE: Status must be `'ACTIVE'` (not `'DRAFT'` or `'PendingLenderApproval'`)
3. Check available capacity: Verify `availableCapacity` field in master commitment is greater than 0
4. Complete required information: Fill all required fields (`requestAmount`, `fundingDate`, `purpose`, supporting documentation)
5. Verify assignment: Ensure `issuerOrgId` in master commitment matches your organization ID

---

### "I Can't Approve the Funding Request"

**Possible reasons:**
- Status is not FAReview
- Not the facility agent
- Missing documentation
- Compliance issues
- Not assigned to review

**Solutions:**
1. Check request status
2. Verify you're facility agent
3. Check documentation completeness
4. Review compliance requirements
5. Verify assignment

---

### "I Can't Edit My Pool"

**Possible reasons:**
- Status is Deal (finalized)
- Status is Mandate Pending (under review)
- Don't have permission
- Pool is locked

**Solutions:**
1. Check pool status
2. Verify status allows editing
3. Check your permissions
4. Wait if under review
5. Contact support if needed

---

### "I Can't See the Funding Notice"

**Possible reasons:**
- Borrower hasn't approved tokens: Funding notice status must be `'TOKEN_APPROVED'` (set via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`). If status is `'TOKEN_GENERATED'`, lenders cannot see the notice.
- Status is not TOKEN_APPROVED: Code filters funding notices by `status: 'TOKEN_APPROVED'` when lenders query (via `GET /cf/funding-notices`). Only `'TOKEN_APPROVED'` notices are visible to lenders.
- Not a lender in facility: Code validates lender's `lenderOrgId` exists in `tokenDistribution` array of funding notice. Lender must be in master commitment's `lenderGroups` array.
- Not assigned to lender group: Lender's organization ID must match a `lenderOrgId` in the `tokenDistribution` array
- Wrong role: Code validates `requireRole('Lender')` or `requireRole('Investor')` middleware - must be logged in with lender role

**Solutions:**
1. Wait for borrower token approval
2. Check funding notice status
3. Verify you're a lender
4. Check lender group assignment
5. Verify role

---

## Diagnostic Checklist

### Before Taking Action

**Checklist:**
- [ ] Am I logged in with correct role?
- [ ] Do I have permission for this action?
- [ ] Is item in correct status?
- [ ] Are all required fields filled?
- [ ] Are documents uploaded?
- [ ] Are prerequisites met?
- [ ] Has previous step completed?
- [ ] Is action already done?

---

### If Action Is Disabled

**Check:**
1. Hover over button - read tooltip
2. Check status message
3. Review item status
4. Verify requirements
5. Check permissions
6. Review workflow
7. Contact support if unclear

---

## Getting Help

### Self-Help Steps

1. Check tooltips: Hover over disabled buttons
2. Read messages: Check status and error messages
3. Review documentation: Check relevant guides
4. Check status history: See what happened
5. Verify requirements: Ensure all met

---

### When to Contact Support

**Contact support if:**
- Tooltip unclear or missing
- Requirements seem met but still blocked
- Status seems wrong
- Unexpected blocking
- Need clarification

**Provide:**
- What you're trying to do
- What error or message you see
- Current status
- What you've checked
- Screenshots if helpful

---

## Best Practices

1. Check systematically: Go through checklist
2. Read carefully: Tooltips and messages explain
3. Verify status: Ensure correct status
4. Complete requirements: Meet all prerequisites
5. **Be patient**: Some actions require waiting

---

## Key Takeaways

1. **Multiple reasons**: Various reasons actions unavailable
2. **Check systematically**: Go through diagnostic steps
3. **Read tooltips**: Hover for explanations
4. **Verify requirements**: Ensure all met
5. **Get help**: Contact support when needed

Understanding "why can't I act" helps you diagnose issues and resolve blockers to proceed with your work.
