# What Happens After Rejection

## Overview

When an item is rejected, it enters a final state with specific consequences. Understanding what happens after rejection helps you know what to expect and how to proceed.

## Rejection Outcomes

### Final State

**What rejection means:**
- Item is rejected
- Process stops here
- No further action possible on rejected item
- This is a final state
- Cannot be reversed

**What you cannot do:**
- Cannot edit rejected item
- Cannot resubmit same item
- Cannot appeal rejection
- Cannot change status

---

## Term Sheet Rejection

### What Happens

**After term sheet rejection:**
- Term sheet status: `'Rejected'` (via `POST /cf/rejectTermSheet/:termSheetId`)
- Database update in `cf_term_sheets` collection:
  - Status changes to `'Rejected'`
  - Entry added to `statusHistory`: `{ status: 'Rejected', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Rejected by facility agent' }`
  - Entry added to `actionHistory`: `{ action: 'Reject', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Term sheet rejected', details: { rejectionReason: '...' } }`
- No master commitment created: `autoCreateMasterCommitment()` function is NOT called (only called when status is `'Accepted'`)
- Facility does not proceed: credit facility workflow stops
- Term sheet remains rejected: final state, cannot be edited or resubmitted
- Borrower notified: notification sent via notification system

### What Borrower Can Do

**Options:**
- View rejected term sheet
- See rejection reason (if provided)
- Create new term sheet
- Learn from rejection
- Try again with improvements

**Cannot do:**
- Cannot edit rejected term sheet
- Cannot resubmit same term sheet
- Cannot appeal rejection

---

## Funding Request Rejection

### What Happens

**After funding request rejection:**
- Funding request status: `'REJECTED'` (via `POST /cf/funding-requests/:fundingRequestId/reject`)
- Database update in `cf_funding_requests` collection:
  - Status changes to `'REJECTED'`
  - `rejectionReason` stored (if provided in request body)
  - Entry added to `statusHistory`: `{ status: 'REJECTED', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Rejected by facility agent' }`
  - Entry added to `actionHistory`: `{ action: 'Reject', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'Funding request rejected', details: { rejectionReason: '...' } }`
- No funding notice created: `generateFundingNotice()` function is NOT called (only called when status is `'APPROVED'`)
- Drawdown does not proceed: funding workflow stops
- Request remains rejected: final state, cannot be edited or resubmitted
- Borrower notified: notification sent via notification system

### What Borrower Can Do

**Options:**
- View rejected request
- See rejection reason (if provided)
- Create new funding request
- Address issues identified
- Try again with corrections

**Cannot do:**
- Cannot edit rejected request
- Cannot resubmit same request
- Cannot appeal rejection

---

## Pool Mandate Rejection

### What Happens

**After pool mandate rejection:**
- Market maker rejects mandate
- Pool may return to Preview status
- Issuer can share with other market makers
- Rejection recorded
- Issuer notified

### What Issuer Can Do

**Options:**
- View rejection (if feedback provided)
- Share with other market makers
- Address feedback (if provided)
- Continue pool preparation
- Find alternative market maker

**Cannot do:**
- Cannot force market maker to accept
- Cannot resubmit to same market maker (usually)

---

## Understanding Rejection Reasons

### Why Reasons Matter

**Rejection reasons help:**
- Understand why rejected
- Learn what went wrong
- Fix issues for next time
- Improve future submissions
- Avoid repeating mistakes

### Common Rejection Reasons

**Term sheets:**
- Terms not acceptable
- Borrower doesn't qualify
- Risk too high
- Documentation insufficient

**Funding requests:**
- Exceeds borrowing capacity
- Violates facility rules
- Documentation incomplete
- Collateral ineligible

---

## Moving Forward After Rejection

### Learn from Rejection

**What to do:**
1. Review rejection reason carefully
2. Understand what went wrong
3. Identify issues to fix
4. Learn from experience
5. Improve for next time

### Create New Item

**When creating new:**
1. Address rejection issues
2. Fix identified problems
3. Improve documentation
4. Make necessary corrections
5. Submit improved version

---

## Best Practices

### After Rejection

1. Don't take it personally: Rejection is part of process
2. Learn from it: Understand why rejected
3. Fix issues: Address problems identified
4. Try again: Create new improved version
5. Be persistent: Don't give up

### Creating New Items

1. **Address issues**: Fix problems from rejection
2. **Improve quality**: Better than before
3. **Complete thoroughly**: Don't repeat mistakes
4. **Seek guidance**: Ask if unclear
5. **Submit confidently**: Improved version

---

## Common Scenarios

### Scenario 1: Term Sheet Rejection

1. Term sheet rejected → Review reason
2. Understand issues → Identify problems
3. Create new term sheet → Address issues
4. Submit improved version → Better quality
5. Gets approved → Success

### Scenario 2: Funding Request Rejection

1. Request rejected → Review reason
2. Amount too high → Reduce amount
3. Create new request → Smaller amount
4. Submit corrected version → Within limits
5. Gets approved → Success

---

## Key Takeaways

1. **Final state**: Rejection is final - cannot be reversed
2. **Learn from it**: Understand why rejected
3. **Create new**: Make new improved version
4. **Fix issues**: Address problems identified
5. **Move forward**: Don't get stuck on rejection

Understanding what happens after rejection helps you know how to proceed and improve your submissions for better outcomes.
