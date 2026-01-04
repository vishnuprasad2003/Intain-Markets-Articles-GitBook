---
title: Borrower Token Approval
description: Learn how to approve token transfers for funding notices
---

# Borrower Token Approval

## Overview

Borrower token approval is the step where the issuer/borrower enters their C-chain private key or JSON file format to approve the FT tokens to the Intain admin wallet so that they can transfer those FTs to the investors after the payment is completed. This approval makes the funding notice visible to lenders and enables the drawdown process to proceed.

## Who Can Use This

- Borrowers who have funding notices with generated tokens

## When This Is Used

Use token approval when:
- Tokens have been generated for your funding notice by the facility agent
- You want to proceed with the drawdown process
- You need to make the funding notice visible to lenders
- You're ready to enable lender review and approval
- You want to verify token allocation before proceeding

## Step-by-Step Process

### Reviewing Token Allocation

1. **Access Your Funding Notice**
   - Navigate to your funding notices section
   - Find the funding notice with generated tokens
   - Open the funding notice details
   - View token allocation information

2. **Review Token Details**
   - Check requestAmount matches your funding request drawAmount
   - Verify ftContractAddress exists (FT tokens have been created)
   - Review fundingDate and purposeOfFunds
   - Confirm facility information is accurate
   - Ensure status is "TOKEN_GENERATED"

3. **Review Lender Distribution**
   - View tokenDistribution array showing how tokens are distributed to lenders
   - Check each lender's tokensAllocated amount
   - Verify votingPercentage matches facility participation
   - Ensure all lenders are included in tokenDistribution array
   - Review individual lender allocations (tokensAllocated field)

4. **Verify Allocation Accuracy**
   - Confirm total allocation equals request amount
   - Check that lender percentages are correct
   - Verify no errors in distribution
   - Ensure all information is accurate

### Approving Token Transfer

1. **Final Review Before Approval**
   - Review all token allocation details one final time
   - Verify token amounts match your expectations
   - Check lender distribution is accurate
   - Confirm you're ready to proceed
   - Ensure all information is correct

2. **Initiate Approval**
   - Click the "Approve Token Transfer" button or similar
   - System calls API endpoint: POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer
   - Enter your C-chain private key (req.body.privateKey) or upload a JSON file format
   - Optionally provide issuerAddress (req.body.issuerAddress)
   - System validates funding notice status is "TOKEN_GENERATED"
   - System validates FT tokens exist (ftContractAddress)
   - This approves the FT tokens to the Intain admin wallet so they can transfer those FTs to investors after payment is completed
   - Review any confirmation messages
   - Understand that approval makes notice visible to lenders
   - Confirm you want to proceed

![Issuer - Token Approval](imagesByMdFilesFolder/27/Issuer_Token_Approval.png)

3. **Complete Approval**
   - System approves FT tokens to Intain admin wallet via blockchain smart contract
   - Blockchain transaction is executed (approveFt function)
   - Approval transaction hash (approvalTransactionHash) is recorded
   - Status updates from "TOKEN_GENERATED" to "TOKEN_APPROVED"
   - approvedAt timestamp is recorded
   - issuedAt timestamp is recorded
   - Funding notice becomes visible to lenders

4. **Verify Approval Completion**
   - Confirm status shows "TOKEN_APPROVED"
   - Verify funding notice is now visible to lenders
   - Check that lenders receive notifications
   - Review approvalTransactionHash
   - Ensure process can proceed

### After Approval

1. **Lender Visibility**
   - Funding notice is now visible to all lenders
   - Lenders receive notifications about the notice
   - Lenders can review drawdown details
   - Lenders can make approval decisions

2. **Track Lender Decisions**
   - Monitor which lenders have reviewed the notice
   - See which lenders have approved or rejected
   - Track individual lender participation
   - Monitor fund transfer confirmations

3. **Proceed with Drawdown**
   - Approved lenders can proceed with fund transfer
   - Each lender confirms their transfer independently
   - Funds are transferred to you as lenders confirm
   - Drawdown process completes as transfers are confirmed

## Rules & Validations

- You can only approve tokens after they've been generated. Tokens must be created by facility agent before you can approve.

- You must review allocation before approving. Take time to verify token amounts and distribution are correct.

- Approval makes funding notice visible to lenders. Once approved, lenders can see and review the notice.

- Once approved, you cannot easily undo the approval. Approval is a significant step, so verify everything before approving.

- Lenders can then review and approve drawdowns. After your approval, lenders make their own decisions.

- Token amounts must match funding request. The total token amount (sum of tokensAllocated in tokenDistribution array) should equal your approved funding request drawAmount.

- Lender distribution is based on facility participation. tokensAllocated is calculated from lender votingPercentage in lenderGroups, with each lender's portion calculated as (votingPercentage / 100) * drawAmount.

- Approval is required for process to continue. The drawdown process cannot proceed until you approve token transfer. Funding notice must be in "TOKEN_GENERATED" status before approval.

- Status updates after approval. Funding notice status changes from "TOKEN_GENERATED" to "TOKEN_APPROVED" to reflect your approval. Only funding notices with status "TOKEN_APPROVED" are visible to lenders.

- Complete audit trail. Your approval is recorded with timestamp and details.

## What Happens Next

After approving token transfer:
- Funding notice becomes visible to all lenders
- Lenders receive notifications about the notice
- Lenders can review drawdown details and make decisions
- Approved lenders can proceed with fund transfer
- You can track lender decisions and transfer confirmations
- Funds are transferred to you as lenders confirm transfers
- Drawdown process completes as all transfers are confirmed

Understanding borrower token approval helps you complete the drawdown process, enable lenders to participate in your funding requests, and ensure proper verification before funds are disbursed.
