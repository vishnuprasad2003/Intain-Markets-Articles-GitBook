# Lender Approval & Rejection

## Overview

Lenders review funding notices and can approve or reject individual drawdowns. Each lender makes their own decision, and the system tracks individual lender participation separately.

## Lender Review Process

### What Lenders See

**After borrower token approval:**
- Funding notice becomes visible
- Drawdown details displayed
- Token allocation shown
- Their participation amount visible
- Can review and make decision

### Review Information

**Funding notice details:**
- Request amount
- Purpose of funds
- Funding date
- Facility details
- Borrowing base impact
- Their token allocation

---

## Approval Decision

### What Approval Means

**When lender approves:**
- Lender agrees to participate in drawdown
- Lender's portion will be funded
- Lender's status: APPROVED
- Drawdown can proceed for this lender
- Fund transfer can be confirmed

### How to Approve

**Process:**
1. Review funding notice details (via `GET /cf/funding-notices/:fundingNoticeId`) - only visible if status is `'TOKEN_APPROVED'`
2. Evaluate drawdown request: check `requestAmount`, `purpose`, `fundingDate`, `borrowingBase`, `availableCapacity`
3. Verify token allocation: check lender's entry in `tokenDistribution` array, verify `tokensAllocated` matches expected amount
4. Click "Approve" button (via `PATCH /cf/funding-notices/:fundingNoticeId/:lenderOrgId/status`)
5. Request body: `{ status: 'APPROVED' }`
6. System validates: funding notice status is `'TOKEN_APPROVED'`, lender is in `tokenDistribution` array, lender's `lenderOrgId` matches
7. Database update in `cf_funding_notices` collection:
   - Lender's `lenderApprovalStatus` in `tokenDistribution` array updated to `'APPROVED'`
   - Lender's `approvedAt` timestamp set (if field exists)
   - Entry added to `actionHistory`: `{ action: 'Lender Approval', userId: lenderId, timestamp: DateUtils.nowUTC(), comments: 'Lender approved drawdown', details: { lenderOrgId, status: 'APPROVED' } }`
8. Lender status: APPROVED - individual lender's participation confirmed

### What Happens

**After approval:**
- Lender's `lenderApprovalStatus` in `tokenDistribution` array → `'APPROVED'` (updated via `PATCH /cf/funding-notices/:fundingNoticeId/:lenderOrgId/status`)
- Lender's participation confirmed: individual lender's decision recorded in database
- Drawdown can proceed for this lender: lender can confirm fund transfer (via `POST /cf/funding-notices/:fundingNoticeId/confirm-fund-transfer`)
- Fund transfer can be confirmed: lender's `amountTransferred` and `mintingStatus` can be updated to `'transferred'` and `'completed'` respectively
- Status tracked individually: each lender's status in `tokenDistribution` array is independent, one lender's approval doesn't affect others
- Other lenders can still approve/reject independently: each lender makes their own decision

---

## Rejection Decision

### What Rejection Means

**When lender rejects:**
- Lender declines to participate
- Lender's portion will not be funded
- Lender's status: REJECTED
- Drawdown does not proceed for this lender
- Other lenders can still approve

### How to Reject

**Process:**
1. Review funding notice details
2. Evaluate drawdown request
3. Decide not to participate
4. Click "Reject" button
5. Provide rejection reason (if required)
6. Confirm rejection
7. Lender status: REJECTED

### What Happens

**After rejection:**
- Lender's `lenderApprovalStatus` → REJECTED
- Lender's participation declined
- Drawdown does not proceed for this lender
- Other lenders unaffected
- Status tracked individually

---

## Individual Lender Tracking

### Per-Lender Status

**Each lender tracked separately:**
- `lenderApprovalStatus`: PENDING | APPROVED | REJECTED
- Individual decision per lender
- Independent of other lenders
- Tracks each lender's participation

### Status Values

**PENDING:**
- Lender has not yet decided
- Funding notice visible but not acted on
- Waiting for lender decision

**APPROVED:**
- Lender has approved drawdown
- Lender will participate
- Fund transfer can proceed

**REJECTED:**
- Lender has rejected drawdown
- Lender will not participate
- No fund transfer for this lender

---

## Impact of Decisions

### Approval Impact

**For approving lender:**
- Lender participates in drawdown
- Lender's portion funded
- Lender confirms fund transfer
- Lender's status tracked

**For other lenders:**
- No impact on other lenders
- Each lender decides independently
- Other lenders can still approve/reject
- Individual tracking maintained

### Rejection Impact

**For rejecting lender:**
- Lender does not participate
- No fund transfer for this lender
- Lender's status: REJECTED
- Other lenders unaffected

**For drawdown:**
- Drawdown may proceed with other lenders
- Amount may be adjusted if needed
- Facility agent manages overall drawdown
- Individual lender decisions respected

---

## Best Practices

### For Lenders

**Before deciding:**
1. **Review thoroughly**: Understand drawdown details
2. **Evaluate request**: Assess if appropriate
3. **Check allocation**: Verify your portion
4. **Consider impact**: Understand participation implications
5. **Make informed decision**: Approve or reject based on evaluation

**When approving:**
1. **Verify details**: Ensure information correct
2. **Confirm participation**: Be ready to fund
3. **Approve promptly**: Keep workflow moving
4. **Track status**: Monitor your approval

**When rejecting:**
1. **Provide reason**: Explain why rejecting (if possible)
2. **Reject promptly**: Don't delay unnecessarily
3. **Understand impact**: Know what rejection means
4. **Track status**: Monitor your rejection

---

## Common Scenarios

### Scenario 1: All Lenders Approve

1. Funding notice visible → Lenders see notice
2. Lender A approves → Status: APPROVED
3. Lender B approves → Status: APPROVED
4. Lender C approves → Status: APPROVED
5. All lenders participate → Drawdown proceeds

### Scenario 2: Mixed Decisions

1. Funding notice visible → Lenders see notice
2. Lender A approves → Status: APPROVED
3. Lender B rejects → Status: REJECTED
4. Lender C approves → Status: APPROVED
5. Partial participation → Drawdown proceeds with approving lenders

### Scenario 3: All Lenders Reject

1. Funding notice visible → Lenders see notice
2. Lender A rejects → Status: REJECTED
3. Lender B rejects → Status: REJECTED
4. Lender C rejects → Status: REJECTED
5. No participation → Drawdown may not proceed

---

## Fund Transfer Confirmation

### After Approval

**Lender confirms transfer:**
- Lender approves drawdown
- Lender confirms fund transfer
- Lender's `amountTransferred` → transferred
- Lender's `mintingStatus` → completed
- Transfer complete for this lender

### Individual Confirmation

**Each lender separately:**
- Lender confirms their own transfer
- Independent of other lenders
- Individual tracking maintained
- Per-lender completion status

---

## Troubleshooting

### "Can't see funding notice"
- Check borrower has approved tokens
- Verify funding notice status is TOKEN_APPROVED
- Ensure you're a lender in the facility
- Check your lender group assignment

### "Can't approve or reject"
- Check funding notice status
- Verify you're a lender
- Ensure notice is visible to you
- Check if already decided

### "Status not updating"
- Wait a moment for processing
- Refresh page
- Verify decision was submitted
- Contact support if persists

---

## Key Takeaways

1. **Individual decisions**: Each lender decides independently
2. **Three statuses**: PENDING, APPROVED, or REJECTED
3. **Per-lender tracking**: Individual status for each lender
4. **Independent impact**: One lender's decision doesn't affect others
5. **Fund transfer**: Approved lenders confirm transfers individually

Understanding lender approval and rejection helps lenders know how to evaluate funding notices and make informed decisions about participating in drawdowns.
