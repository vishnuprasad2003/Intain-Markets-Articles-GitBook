# Funding Request Review

## Overview

Funding request review is the process where facility agents evaluate borrower funding requests to ensure they comply with facility rules, have sufficient borrowing capacity, and meet all requirements before approval.

## Review Process

### Purpose

**Review ensures:**
- Compliance with facility rules
- Sufficient borrowing base availability
- Collateral eligibility (if applicable)
- Documentation completeness
- Request reasonableness

### Who Reviews

**Facility Agent:**
- Primary reviewer of funding requests
- Has authority to approve, reject, or request changes
- Ensures compliance with facility terms
- Manages facility operations

---

## Review Criteria

### Compliance Checks

**Facility Rules:**
- Request amount within facility limits
- Drawdown frequency compliance
- Purpose aligns with facility terms
- Other facility rule compliance

**Borrowing Base:**
- Sufficient available capacity
- Request doesn't exceed limits
- Collateral supports request (if applicable)
- Borrowing base calculations correct

### Documentation Review

**Required Documents:**
- Purpose documentation
- Supporting materials
- Collateral documentation (if applicable)
- Financial statements (if required)
- Other required documents

**Document Quality:**
- Documents complete
- Information accurate
- Documents support request
- Meets facility requirements

### Collateral Review (If Applicable)

**Collateral Eligibility:**
- Collateral meets facility criteria
- Collateral valuation appropriate
- Collateral not already pledged
- Collateral concentration within limits

**Collateral Documentation:**
- Collateral details provided
- Valuation documentation included
- Eligibility verified
- Properly documented

---

## Review Actions

### Approve

**When to approve:**
- Request meets all facility rules
- Sufficient borrowing capacity available
- Documentation complete and accurate
- Collateral eligible (if applicable)
- No compliance issues

**What happens:**
- Funding request status changes to "APPROVED"
- Funding notice automatically generated
- Status: PENDING_TOKEN_GENERATION
- Ready for token generation process

### Reject

**When to reject:**
- Request violates facility rules
- Insufficient borrowing capacity
- Documentation incomplete or inaccurate
- Collateral ineligible (if applicable)
- Cannot be fixed with changes

**What happens:**
- Funding request status changes to "REJECTED"
- No funding notice created
- Final state - no further action
- Borrower can create new request

### Request Changes

**When to request changes:**
- Request has correctable issues
- Missing or incomplete documentation
- Minor compliance issues
- Needs clarification or correction
- Can be fixed with modifications

**What happens:**
- Funding request status changes to "CHANGES_REQUESTED"
- Revision number increments
- Current version saved to history
- Borrower can edit and resubmit
- Auto-save re-enabled

---

## Review Workflow

### Step 1: Receive Request

**Facility agent receives:**
- Notification of new funding request
- Request appears in review queue
- Status: FAReview
- Can access request details

### Step 2: Review Request

**Facility agent reviews:**
- Request amount and purpose
- Supporting documentation
- Collateral information (if applicable)
- Compliance with facility rules
- Borrowing base availability

### Step 3: Evaluate Compliance

**Checks performed:**
- Facility rules compliance
- Borrowing base calculations
- Collateral eligibility
- Documentation completeness
- Request reasonableness

### Step 4: Make Decision

**Three options:**
1. **Approve**: If all requirements met
2. **Reject**: If cannot be fixed
3. **Request Changes**: If fixable issues

### Step 5: Execute Decision

**Approve:**
- Click "Approve" button
- Status changes to APPROVED
- Funding notice auto-generated
- Borrower notified

**Reject:**
- Click "Reject" button
- Provide rejection reason
- Status changes to REJECTED
- Borrower notified

**Request Changes:**
- Click "Request Changes" button
- Specify what needs to change
- Provide change details
- Status changes to CHANGES_REQUESTED
- Borrower notified

---

## Review Tools

### Available Information

**Facility Details:**
- Master commitment terms
- Facility rules and limits
- Borrowing base calculations
- Available capacity
- Collateral eligibility rules

**Request Details:**
- Requested amount
- Purpose
- Supporting documentation
- Collateral information
- Borrower information

**Historical Context:**
- Previous funding requests
- Facility utilization
- Payment history
- Compliance history

### Analysis Tools

**Borrowing Base Calculator:**
- Current borrowing base
- Available capacity
- Impact of request
- Remaining capacity after request

**Compliance Checker:**
- Rule compliance verification
- Limit checks
- Eligibility validation
- Documentation completeness

---

## Best Practices

### For Facility Agents

1. **Review thoroughly**: Check all aspects carefully
2. **Verify calculations**: Ensure borrowing base correct
3. **Check compliance**: Verify all rules met
4. **Document decisions**: Provide clear feedback
5. **Respond promptly**: Keep workflow moving

### Review Process

1. **Start with basics**: Check amount and purpose
2. **Verify capacity**: Ensure borrowing base available
3. **Review documentation**: Check completeness
4. **Validate compliance**: Verify rules met
5. **Make decision**: Approve, reject, or request changes

### Communication

1. **Be clear**: Provide specific feedback
2. **Be constructive**: Help borrower understand
3. **Be timely**: Respond promptly
4. **Be professional**: Maintain good communication

---

## Common Scenarios

### Scenario 1: Perfect Request

1. Request received → Review
2. All requirements met → Approve
3. Funding notice generated → Proceeds

### Scenario 2: Missing Documentation

1. Request received → Review
2. Documentation incomplete → Request Changes
3. Borrower adds documents → Resubmits
4. Review again → Approve

### Scenario 3: Exceeds Capacity

1. Request received → Review
2. Amount exceeds available capacity → Reject
3. Provide rejection reason
4. Borrower can create smaller request

### Scenario 4: Collateral Issues

1. Request received → Review
2. Collateral doesn't meet criteria → Request Changes
3. Borrower provides eligible collateral → Resubmits
4. Review again → Approve

---

## Troubleshooting

### "Can't find request to review"
- Check review queue
- Verify request status is FAReview
- Check filters
- Ensure you're assigned as facility agent

### "Unclear what to check"
- Review facility rules
- Check borrowing base calculations
- Verify documentation requirements
- Consult facility terms

### "Decision unclear"
- Review all criteria
- Check facility rules
- Verify calculations
- Consult with team if needed

---

## Key Takeaways

1. **Comprehensive review**: Check all compliance aspects
2. **Three decisions**: Approve, reject, or request changes
3. **Automatic actions**: Approval generates funding notice
4. **Clear feedback**: Provide specific guidance
5. **Efficient process**: Keep workflow moving

Understanding funding request review helps facility agents effectively evaluate requests and ensure facility compliance while enabling borrowers to access funds when appropriate.
