# Funding Notice Review

## Overview

Funding notice review is the process where lenders review funding notices after borrower token approval and decide whether to approve or reject individual drawdowns. This guide covers how lenders evaluate funding notices and make approval decisions.

## Receiving Funding Notices

### How Funding Notices Are Received

**When you receive a funding notice:**
- Borrower approves token transfer
- Funding notice status: TOKEN_APPROVED
- Funding notice becomes visible to lenders
- You receive notification
- Notice appears in review queue

### What You See

**Funding notice information:**
- Request amount
- Purpose of funds
- Funding date
- Facility details
- Your token allocation
- Borrowing base impact
- Other drawdown details

---

## Reviewing Funding Notices

### Step 1: Access Funding Notice

**How to access:**
1. Check notifications or review queue
2. Navigate to funding notices
3. Open funding notice details
4. Review all information

### Step 2: Evaluate Drawdown Request

**What to evaluate:**
- Request amount: Appropriate and within limits
- Purpose: Legitimate and acceptable
- Timing: Appropriate funding date
- Impact: Effect on facility utilization
- Risk: Risk assessment of drawdown

### Step 3: Review Token Allocation

**What to review:**
- Your allocated token amount
- Your participation percentage
- Total drawdown amount
- Token distribution details
- Your portion of drawdown

### Step 4: Assess Facility Impact

**What to assess:**
- Borrowing base impact
- Utilization after drawdown
- Remaining capacity
- Facility health
- Overall facility status

---

## Making Approval Decisions

### Option 1: Approve Drawdown

**When to approve:**
- Drawdown request is appropriate
- Amount is acceptable
- Purpose is legitimate
- Risk is acceptable
- Ready to participate

**How to approve:**
1. Review funding notice thoroughly
2. Evaluate drawdown request
3. Click "Approve" button
4. Confirm approval
5. Lender status: APPROVED

**What happens:**
- Your `lenderApprovalStatus` → APPROVED
- Your participation confirmed
- Drawdown can proceed for your portion
- Fund transfer can be confirmed
- Status tracked individually

### Option 2: Reject Drawdown

**When to reject:**
- Drawdown request not appropriate
- Amount concerns
- Purpose concerns
- Risk too high
- Cannot participate

**How to reject:**
1. Review funding notice
2. Decide to reject
3. Click "Reject" button
4. Provide rejection reason (if required)
5. Confirm rejection

**What happens:**
- Your `lenderApprovalStatus` → REJECTED
- Your participation declined
- Drawdown does not proceed for your portion
- Other lenders unaffected
- Status tracked individually

---

## Individual Lender Tracking

### Per-Lender Decisions

**Each lender separately:**
- Individual approval or rejection
- Independent decisions
- Per-lender status tracking
- No impact on other lenders

### Status Values

**PENDING:**
- Not yet decided
- Funding notice visible
- Waiting for decision

**APPROVED:**
- Approved drawdown
- Will participate
- Fund transfer can proceed

**REJECTED:**
- Rejected drawdown
- Will not participate
- No fund transfer

---

## Fund Transfer Confirmation

### After Approval

**Confirm transfer:**
1. Approve drawdown
2. Transfer funds to borrower
3. Click "Confirm Fund Transfer"
4. Status: transferred
5. Participation complete

**Status updates:**
- `amountTransferred` → transferred
- `mintingStatus` → completed
- Participation finalized
- Drawdown complete for this lender

---

## Best Practices

### For Lenders

**Review process:**
1. Review thoroughly: Understand drawdown details
2. Evaluate request: Assess if appropriate
3. Check allocation: Verify your portion
4. Assess impact: Understand facility impact
5. Make informed decision: Approve or reject based on evaluation

**Decision making:**
1. Be clear: Understand what you're approving
2. Be timely: Respond promptly
3. Be professional: Maintain good communication
4. Track status: Monitor your participation

---

## Common Scenarios

### Scenario 1: Approve Drawdown

1. Receive funding notice → Review
2. Request appropriate → Approve
3. Status: APPROVED → Transfer funds
4. Confirm transfer → Complete

### Scenario 2: Reject Drawdown

1. Receive funding notice → Review
2. Request not appropriate → Reject
3. Status: REJECTED → No participation
4. Other lenders unaffected → Independent decision

### Scenario 3: Multiple Drawdowns

1. Receive multiple notices → Review each
2. Approve some → Reject others
3. Individual decisions → Per drawdown
4. Track participation → Monitor status

---

## Troubleshooting

### "Can't see funding notice"
- Check borrower has approved tokens
- Verify funding notice status is TOKEN_APPROVED
- Ensure you're a lender in facility
- Check your lender group assignment

### "Can't approve or reject"
- Check funding notice status
- Verify you're a lender
- Ensure notice is visible
- Check if already decided

---

## Key Takeaways

1. **Individual decisions**: Each lender decides independently
2. **Review thoroughly**: Understand drawdown before deciding
3. **Per-lender tracking**: Individual status for each lender
4. **Independent impact**: One lender's decision doesn't affect others
5. **Fund transfer**: Approved lenders confirm transfers

Understanding funding notice review helps lenders effectively evaluate drawdown requests and make informed decisions about participating in individual funding draws.
