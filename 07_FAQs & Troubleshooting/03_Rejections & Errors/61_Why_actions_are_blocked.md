# Why Actions Are Blocked

## Overview

Understanding why actions are blocked helps you know what needs to happen before you can proceed. This guide explains common reasons actions are blocked and how to resolve them.

## Common Blocking Reasons

### Wrong Status

**Most common reason:**
- Item isn't in the right status for the action
- Workflow doesn't permit the action at current status
- Must progress through statuses in order
- Cannot skip workflow steps

**Examples:**
- Can't submit term sheet when status is Draft (must sign first): Code validates `termSheet.status === 'BorrowerSigned'` before allowing submission (via `POST /cf/submitTermSheet/:termSheetId`)
- Can't approve funding request when status is DRAFT (must be FAReview): Code validates `fundingRequest.status === 'FAReview'` before allowing approval (via `POST /cf/funding-requests/:fundingRequestId/approve`)
- Can't create funding request when master commitment is Draft (must be ACTIVE): Code validates `masterCommitment.status === 'ACTIVE'` before allowing funding request creation (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`)

**Solution:**
- Check current status
- Complete required steps first
- Progress through workflow properly
- Wait for status to change

---

### Missing Information

**Common blocker:**
- Required fields not filled
- Documents not uploaded
- Information incomplete
- Prerequisites missing

**Examples:**
- Can't submit term sheet without required fields
- Can't approve funding request without documentation
- Can't create funding request without active facility

**Solution:**
- Fill all required fields
- Upload required documents
- Complete all information
- Meet all prerequisites

---

### Waiting for Others

**Workflow dependency:**
- Another party needs to act first
- Previous step not completed
- Dependency not satisfied
- Waiting for action

**Examples:**
- Can't approve funding request until borrower submits: Code validates `fundingRequest.status === 'FAReview'` (only set when borrower submits via `POST /cf/funding-requests/:fundingRequestId/submit`)
- Can't create funding request until lender approves master commitment: Code validates `masterCommitment.status === 'ACTIVE'` (only set when lender approves via DocuSign)
- Can't approve tokens until facility agent signs: Code may validate `eSignatureStatus === 'ESIGN_COMPLETED'` or check that facility agent has signed for all lenders before allowing borrower token approval (though actual validation may allow approval even if not all lenders signed - check implementation)

**Solution:**
- Wait for other party to act
- Check what's pending
- Monitor status changes
- Follow up if needed

---

### No Permission

**Role restriction:**
- Your role doesn't allow the action
- You don't have access
- Not assigned to item
- Permissions not granted

**Examples:**
- Borrowers can't approve their own term sheets: `requireRole('Market Maker')` or `requireRole('Facility Agent')` middleware blocks `requireRole('Issuer')` users from `POST /cf/acceptTermSheet/:termSheetId`
- Lenders can't create funding requests: `requireRole('Issuer')` middleware blocks `requireRole('Lender')` users from `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`
- Issuers can't approve master commitments: `requireRole('Lender')` middleware blocks `requireRole('Issuer')` users from `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign`

**Solution:**
- Check your role
- Verify you have permission
- Ensure you're assigned
- Contact support if needed

---

### Already Completed

**Action done:**
- Action already taken
- Status already changed
- Process already done
- No need to repeat

**Examples:**
- Can't submit again if already submitted
- Can't approve again if already approved
- Can't sign again if already signed

**Solution:**
- Check if action already done
- Verify current status
- Don't try to repeat
- Move to next step

---

## How to Identify Blocking Reasons

### Check Tooltips

**Hover over disabled buttons:**
- Tooltips explain why disabled
- Provide specific reason
- Tell you what's needed
- Guide next steps

**Example tooltip:**
- "Cannot submit: Status must be BorrowerSigned"
- "Cannot approve: Missing required documentation"
- "Cannot create: Master commitment must be ACTIVE"

---

### Check Status Messages

**Look for messages:**
- Status messages explain situation
- Show what's blocking
- Indicate what needs to happen
- Provide guidance

**Example messages:**
- "Waiting for facility agent review"
- "Please complete all required fields"
- "Master commitment must be ACTIVE"

---

### Check Requirements

**Review requirements:**
- Check if all fields filled
- Verify documents uploaded
- Ensure prerequisites met
- Confirm status is correct

**Checklist:**
- All required fields complete?
- All documents uploaded?
- Status allows action?
- Prerequisites met?
- Have permission?

---

## Resolving Blocked Actions

### Step 1: Identify the Blocker

**How to identify:**
1. Hover over disabled button (check tooltip)
2. Read status messages
3. Check current status
4. Review requirements
5. Verify permissions

---

### Step 2: Address the Blocker

**How to address:**
1. Complete missing information
2. Wait for required status
3. Wait for other party to act
4. Verify you have permission
5. Complete prerequisites

---

### Step 3: Verify Resolution

**How to verify:**
1. Check if blocker resolved
2. Verify status allows action
3. Ensure all requirements met
4. Try action again
5. Contact support if still blocked

---

## Common Scenarios

### Scenario 1: Status Blocker

**Problem:** Can't submit term sheet
**Reason:** Status is Draft, must be BorrowerSigned
**Solution:** Sign via DocuSign first, then submit

### Scenario 2: Missing Information Blocker

**Problem:** Can't approve funding request
**Reason:** Missing required documentation
**Solution:** Borrower must upload documents first

### Scenario 3: Permission Blocker

**Problem:** Can't approve master commitment
**Reason:** Not a lender in the facility
**Solution:** Verify lender assignment or contact facility agent

### Scenario 4: Dependency Blocker

**Problem:** Can't create funding request
**Reason:** Master commitment not ACTIVE
**Solution:** Wait for lender approval to activate facility

---

## Best Practices

1. Check tooltips first: Hover over disabled buttons
2. Read messages: Check status messages for guidance
3. Verify status: Ensure item is in correct status
4. Check requirements: Verify all prerequisites met
5. Be patient: Some blockers require waiting

---

## Troubleshooting

### "Action blocked but I think it should work"
- Check tooltip for specific reason
- Verify current status
- Check all requirements
- Ensure prerequisites met
- Contact support if unclear

### "Tooltip says I need X but I have X"
- Verify X is actually present
- Check if X meets requirements
- Ensure X is in correct format
- Refresh page
- Contact support if issue persists

---

## Key Takeaways

1. Multiple blockers: Various reasons actions are blocked
2. Check tooltips: Hover for explanations
3. Read messages: Status messages provide guidance
4. Verify requirements: Ensure all prerequisites met
5. Resolve blockers: Address issues to enable actions

Understanding why actions are blocked helps you identify what needs to happen and resolve blockers to proceed with your work.
