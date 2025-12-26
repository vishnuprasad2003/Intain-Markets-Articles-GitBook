# Token Approval

## Overview

Token approval is the step where borrowers approve the transfer of FT tokens, making funding notices visible to lenders. This guide covers how to review token allocations and approve token transfers.

## Understanding Token Approval

### What It Means

Token approval:
- Borrower confirms token allocation
- Borrower approves token transfer privilege
- Enables funding notice visibility to lenders
- Allows drawdown process to proceed
- Moves funding notice to next phase

### When to Approve

**Appropriate timing:**
- After tokens are generated (TOKEN_GENERATED status)
- After reviewing token allocation
- After facility agent has signed (if applicable)
- When ready to proceed with drawdown

---

## Reviewing Token Allocation

### Step 1: Access Funding Notice

**How to access:**
1. Navigate to Funding Notices section
2. Find funding notice with TOKEN_GENERATED status
3. Open funding notice details
4. Review token allocation

### Step 2: Review Token Details

**What to check:**
- Total token amount matches request
- Lender allocations are correct
- Distribution percentages accurate
- Individual lender amounts correct
- Token distribution makes sense

### Step 3: Verify Information

**Verify:**
- Request amount is correct
- Funding date is appropriate
- Purpose is accurate
- Supporting documentation included
- Everything looks correct

---

## Approving Token Transfer

### Step 1: Review Complete

**Before approving:**
- Review all token allocation details
- Verify amounts are correct
- Check facility agent signing status (if applicable)
- Ensure ready to proceed

### Step 2: Approve Transfer

**Process:**
1. Navigate to funding notice (via `GET /cf/funding-notices/:fundingNoticeId`)
2. Review token allocation: check `tokenDistribution` array, verify `tokensAllocated` for each lender, confirm total matches `requestAmount`
3. Verify funding notice status is `'TOKEN_GENERATED'` (tokens must be generated first via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)
4. Click "Approve Token Transfer" button (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`)
5. Request body: `{ privateKey: "...", issuerAddress: "..." }` (borrower's blockchain wallet credentials for token approval transaction)
6. System validates: funding notice status is `'TOKEN_GENERATED'`, borrower is issuer (`issuerId` matches `req.userId`), FT tokens exist on blockchain
7. Blockchain transaction: System calls `approveFt()` function to approve token transfer to IntainAdmin wallet address
8. Database update in `cf_funding_notices` collection:
   - Status changes to `'TOKEN_APPROVED'`
   - `approvalTransactionHash` stored (blockchain transaction hash)
   - `approvedAt`, `approvedBy`, `issuedAt` set
   - Entry added to `statusHistory`: `{ status: 'TOKEN_APPROVED', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Borrower approved token transfer' }`
9. Confirm approval: status changes to TOKEN_APPROVED - funding notice becomes visible to lenders

### Step 3: Verify Approval

**After approval:**
- Status changes to TOKEN_APPROVED
- Funding notice visible to lenders
- Lenders can review and approve
- Drawdown process continues

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

### What Lenders See

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

1. Review thoroughly: Check all token details carefully
2. Verify amounts: Ensure allocations are correct
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

Understanding token approval helps you know when and how to approve token transfers and enable the drawdown process to continue.
