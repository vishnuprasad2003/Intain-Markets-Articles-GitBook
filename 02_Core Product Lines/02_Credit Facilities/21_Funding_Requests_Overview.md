# Funding Requests Overview

## What is a Funding Request?

A **funding request** is when a borrower requests to draw down funds from an active credit facility. Each request specifies the amount needed, the purpose, and includes supporting documentation. Funding requests must be reviewed and approved by the facility agent before funds can be disbursed.

## Key Concepts

### Purpose

Funding requests enable:
- Flexible borrowing: Draw down funds as needed
- Controlled access: Facility agent reviews each request
- Compliance: Ensures requests meet facility rules
- Documentation: Creates record of each drawdown

### Prerequisites

**Before creating funding request:**
- Master commitment must be `'ACTIVE'` status (validated in code: `masterCommitment.status === 'ACTIVE'`)
- Facility must be operational (master commitment in `cf_master_commitments` collection with `status: 'ACTIVE'`)
- Borrower must have access to facility (validated via `issuerOrgId` matching borrower's organization)
- Facility must have available capacity (checked via `availableCapacity` field in master commitment)
- Borrower can check or create draft (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft?issuerOrgId=...`)

### Relationship to Master Commitment

**Funding requests are:**
- Created against a specific master commitment (database collection: `cf_funding_requests` in MongoDB)
- Linked to master commitment via `masterCommitmentId` field
- Subject to facility rules and limits (validated during review)
- Reviewed for compliance with facility terms (via `POST /cf/funding-requests/:fundingRequestId/submit`)
- **Draft Prevention**: System prevents multiple drafts - if draft exists (status `'DRAFT'`), returns existing draft instead of creating new one (via `checkOrCreateDraft` function)

---

## Funding Request Components

### Basic Information

**Required details:**
- Requested amount
- Purpose of funds
- Request date
- Supporting documentation

### Collateral Information

**If applicable:**
- Loans to be used as collateral
- Collateral details
- Collateral valuation
- Collateral eligibility verification

### Supporting Documentation

**May include:**
- Purpose documentation
- Collateral documentation
- Financial statements
- Other supporting materials

---

## Funding Request Status Flow

### Complete Workflow

```
DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED
```

### Status 1: DRAFT

**What it means:**
- Funding request has been created
- Can be edited freely
- Not yet submitted for review
- Auto-save enabled

**What borrower can do:**
- Edit all fields
- Upload documents
- Save changes multiple times
- Submit when ready

**Next steps:**
- Complete all required information
- Upload supporting documents
- Review before submitting
- Submit for facility agent review

### Status 2: FAReview

**What it means:**
- Funding request submitted to facility agent
- Facility agent is reviewing
- Waiting for facility agent decision
- No further edits allowed by borrower

**What facility agent can do:**
- Review request details
- Verify compliance with facility rules
- Check borrowing base availability
- Verify collateral eligibility
- Approve, reject, or request changes

**What borrower can do:**
- View request (read-only)
- See review status
- Wait for facility agent decision

**Next steps:**
Wait for facility agent to:
- Approve (triggers funding notice generation)
- Reject (final state)
- Request changes (allows editing again)

### Status 3: APPROVED

**What it means:**
- Facility agent has approved the request
- Funding notice is automatically generated
- Drawdown can proceed
- Tokens will be created

**What happens automatically:**
- System automatically calls `generateFundingNotice()` function
- Funding notice created in `cf_funding_notices` collection (MongoDB) with `status: 'PENDING_TOKEN_GENERATION'`
- `fundingNoticeId` generated using format: `FN-MMDDYYYY-XXXX` (where MMDDYYYY is current date, XXXX is random alphanumeric)
- Linked to approved funding request via `fundingRequestId` field
- Pre-populated with request data: `requestAmount`, `fundingDate`, `bbCalculation`, `availableCapacity`, `borrowingBase`, `utilisationPercentage`, `collateralValue`
- Pre-populated with facility data: `masterCommitmentId`, `facilityName`, `advanceRate`, `contractType`, `marketMakerOrgId`, `issuerOrgId`, `issuerId`
- Token distribution array initialized: each lender from master commitment's `lenderGroups` added with `esignatureStatus: 'pending'`
- `eSignatureTotalCount` and `eSignaturePendingCount` set to number of lenders
- `eSignatureStatus` set to `'pending'`
- Ready for token generation (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)

**What borrower can do:**
- View approved request
- See funding notice was created
- Monitor funding notice progress
- Approve token transfer when ready

**This triggers next phase:**
- Funding notice generation
- Token creation process
- E-signature workflow

### Status 4: REJECTED

**What it means:**
- Facility agent has rejected the request
- Drawdown will not proceed
- This is a final state
- No further action possible

**What happens:**
- No funding notice created
- Request remains rejected
- Borrower can create new request if needed

**This is final:**
- Cannot resubmit same request
- Must create new request to try again

### Status 5: CHANGES_REQUESTED

**What it means:**
- Facility agent wants modifications
- Borrower can edit and resubmit
- Request needs revision
- Not a final state

**What happens:**
- Revision number increments
- Current version saved to history
- Auto-save re-enabled
- Change request record created

**What borrower can do:**
- Edit funding request
- Make requested changes
- Update documents
- Resubmit after changes

**Next steps:**
1. Review change request details
2. Make requested modifications
3. Resubmit for review
4. Status changes back to "FAReview"

---

## Creating Funding Requests

### When to Create

**Appropriate times:**
- When you need funds from facility
- When facility is ACTIVE
- When you have available borrowing capacity
- When you have supporting documentation ready

### How to Create

**Process:**
1. Navigate to active master commitment
2. Click "Create Funding Request"
3. Fill in required information:
   - Requested amount
   - Purpose
   - Request date
   - Supporting documentation
4. Add collateral (if applicable)
5. Review information
6. Save as draft or submit

### Required Information

**Must provide:**
- Requested amount (within facility limits)
- Purpose of funds
- Supporting documentation
- Collateral information (if required)

---

## Facility Agent Review

### Review Process

**Facility agent evaluates:**
- Compliance with facility rules
- Borrowing base availability
- Collateral eligibility
- Documentation completeness
- Request reasonableness

### Review Decisions

Three possible outcomes:
1. Approve: Request meets all requirements
2. Reject: Request doesn't meet requirements
3. Request Changes: Needs modifications

### Approval Criteria

**Must meet:**
- Facility rules compliance
- Available borrowing capacity
- Collateral eligibility (if applicable)
- Documentation completeness
- Other facility requirements

---

## Automatic Actions

### Funding Notice Generation

**When request approved:**
- Funding notice automatically created
- Status: PENDING_TOKEN_GENERATION
- Pre-populated with request data
- Linked to funding request
- Ready for token generation

### What Gets Created

**Funding notice contains:**
- Request amount
- Funding date
- Facility details
- Master commitment reference
- Token distribution setup (initialized)

---

## Best Practices

### For Borrowers

1. Prepare thoroughly: Have all information ready
2. Complete accurately: Fill in all required fields
3. Provide documentation: Include supporting materials
4. Review before submit: Verify information correct
5. Respond to changes: Address change requests promptly

### For Facility Agents

1. Review thoroughly: Check all compliance requirements
2. Verify capacity: Ensure borrowing base available
3. Check collateral: Verify eligibility if applicable
4. Respond promptly: Keep workflow moving
5. Document decisions: Provide clear feedback

---

## Common Scenarios

### Scenario 1: Smooth Approval

1. Borrower creates request → DRAFT
2. Completes information → Still DRAFT
3. Submits for review → FAReview
4. Facility agent approves → APPROVED
5. Funding notice auto-generated

### Scenario 2: Changes Requested

1. Borrower creates and submits → FAReview
2. Facility agent requests changes → CHANGES_REQUESTED
3. Borrower makes changes → Still CHANGES_REQUESTED
4. Resubmits → FAReview
5. Facility agent approves → APPROVED

### Scenario 3: Rejection

1. Borrower creates and submits → FAReview
2. Facility agent rejects → REJECTED
3. Borrower creates new request to try again

---

## Key Takeaways

1. Drawdown mechanism: How borrowers access facility funds
2. Review required: Facility agent must approve each request
3. Status-based workflow: Clear progression through statuses
4. Auto-generation: Approved requests create funding notices
5. Change requests: Iterative improvement process

Understanding funding requests helps you effectively request and receive funds from your credit facility.
