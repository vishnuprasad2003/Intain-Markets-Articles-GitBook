# Borrower Token Approval

## Overview

Borrower token approval is the step where the borrower approves the transfer of FT tokens, making the funding notice visible to lenders and enabling the drawdown process to proceed.

## What is Token Approval?

### Definition

Token approval means:
- Borrower confirms token allocation is correct
- Borrower approves token transfer privilege
- Enables funding notice visibility to lenders
- Allows token distribution to proceed
- Moves funding notice to next phase

### Purpose

Why approval is needed:
- Borrower confirms token amounts
- Borrower authorizes token transfer
- Enables lender visibility
- Proceeds with drawdown
- Maintains borrower control

---

## Approval Process

### When to Approve

**Appropriate timing:**
- After tokens are generated (TOKEN_GENERATED status)
- After reviewing token allocation
- After facility agent has signed (if required)
- When ready to proceed with drawdown

### How to Approve

**Process:**
1. Navigate to funding notice (via `GET /cf/funding-notices/:fundingNoticeId`)
2. Review token allocation details: check `tokenDistribution` array with lender allocations, verify `tokensAllocated` for each lender, confirm total matches `requestAmount`
3. Verify amounts are correct: ensure distribution percentages match lender commitments
4. Click "Approve Token Transfer" button (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`)
5. Request body includes: `{ privateKey: "...", issuerAddress: "..." }` (borrower's blockchain wallet credentials)
6. System validates: funding notice status is `'TOKEN_GENERATED'`, borrower is issuer (`issuerId` matches `req.userId`), FT tokens exist on blockchain
7. Blockchain transaction: System calls `approveFt()` function to approve token transfer to IntainAdmin wallet address
8. Database update in `cf_funding_notices` collection:
   - Status changes to `'TOKEN_APPROVED'`
   - `approvalTransactionHash` stored (blockchain transaction hash)
   - `approvedAt` set to current timestamp
   - `approvedBy` set to borrower user ID
   - `issuedAt` set to current timestamp
   - Entry added to `statusHistory`: `{ status: 'TOKEN_APPROVED', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Borrower approved token transfer' }`
9. Status changes to TOKEN_APPROVED - funding notice becomes visible to lenders

### What Happens

**After approval:**
- Funding notice status changes to `'TOKEN_APPROVED'` in `cf_funding_notices` collection
- Funding notice becomes visible to lenders: lenders can query funding notices with `status: 'TOKEN_APPROVED'` and see this notice in their dashboard
- Lenders can now see and review the notice: via `GET /cf/funding-notices` (filtered by lender organization ID and status)
- Token transfer privilege enabled: tokens can now be transferred to lenders via blockchain (`approveFt()` transaction completed)
- Blockchain transaction hash stored: `approvalTransactionHash` field contains the transaction hash for audit trail
- Drawdown process can proceed: lenders can approve/reject drawdown and confirm fund transfers

---

## What to Review Before Approval

### Token Allocation

**Check:**
- Total token amount matches request
- Lender allocations are correct
- Distribution percentages accurate
- Individual lender amounts correct

### Funding Notice Details

**Verify:**
- Request amount is correct
- Funding date is appropriate
- Purpose is accurate
- Supporting documentation included

### Facility Agent Signing

**If applicable:**
- Facility agent has signed for lenders
- E-signature status is complete
- All required signatures done
- Ready to proceed

---

## After Approval

### Status Change

**Before approval:**
- Status: TOKEN_GENERATED
- Visible only to borrower and facility agent
- Lenders cannot see notice

**After approval:**
- Status: TOKEN_APPROVED
- Visible to all relevant lenders
- Lenders can review and approve
- Drawdown process continues

### Lender Visibility

**Lenders can now:**
- See funding notice in their dashboard
- Review drawdown details
- See their token allocation
- Approve or reject drawdown
- Confirm fund transfers

### Next Steps

**After approval:**
1. Lenders review funding notice
2. Lenders approve or reject individually
3. Fund transfers confirmed
4. Drawdown completes

---

## Best Practices

### Before Approving

1. Review thoroughly: Check all token details
2. Verify amounts: Ensure allocations correct
3. Check signatures: Verify e-signatures complete (if required)
4. Confirm readiness: Ensure ready to proceed
5. Understand impact: Know what happens after approval

### When Approving

1. Approve promptly: Don't delay unnecessarily
2. Verify details: Double-check before confirming
3. Confirm action: Be sure you want to proceed
4. Track status: Monitor status change

### After Approving

1. Monitor progress: Track lender reviews
2. Respond to lenders: Address any questions
3. Track approvals: Monitor lender decisions
4. Prepare for funds: Ready to receive funds

---

## Common Scenarios

### Scenario 1: Standard Approval

1. Tokens generated → TOKEN_GENERATED
2. Borrower reviews allocation → Verifies amounts
3. Borrower approves → TOKEN_APPROVED
4. Lenders see notice → Review and approve
5. Funds transferred → Drawdown completes

### Scenario 2: After Facility Agent Signing

1. Tokens generated → TOKEN_GENERATED
2. Facility agent signs for lenders → E-signatures complete
3. Borrower reviews → Verifies everything
4. Borrower approves → TOKEN_APPROVED
5. Lenders see notice → Review and approve

### Scenario 3: Immediate Approval

1. Tokens generated → TOKEN_GENERATED
2. Borrower approves immediately → TOKEN_APPROVED
3. Lenders see notice → Review process begins
4. Lenders approve → Funds transferred

---

## Troubleshooting

### "Can't approve tokens"
- Check funding notice status is TOKEN_GENERATED
- Verify tokens have been generated
- Ensure you're the borrower
- Check if already approved

### "Token amounts seem wrong"
- Review token distribution array
- Verify lender allocations
- Check facility agent if needed
- Don't approve if incorrect

### "Status not changing after approval"
- Wait a moment for processing
- Refresh page
- Check if approval was successful
- Contact support if issue persists

---

## Key Takeaways

1. Borrower control: Borrower must approve token transfer
2. Enables visibility: Makes funding notice visible to lenders
3. Status progression: TOKEN_GENERATED → TOKEN_APPROVED
4. Review first: Verify allocation before approving
5. Proceeds workflow: Enables lender review and approval

Understanding borrower token approval helps you know when and how to approve token transfers and enable the drawdown process to continue.
