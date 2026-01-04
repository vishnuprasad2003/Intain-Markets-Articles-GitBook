---
title: Token Approval
description: Learn how to review token allocations and approve token transfers for funding notices
---

# Token Approval

## Overview

Token approval is the step where borrowers approve the transfer of tokens, making funding notices visible to lenders. This guide covers how to review token allocations, verify distribution accuracy, and approve token transfers.

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

1. **Access Funding Notice**
   - Navigate to Funding Notices section
   - Find funding notice with tokens generated
   - Status shows tokens are generated (e.g., "TOKEN_GENERATED")
   - Open funding notice details

2. **Review Token Details**
   - **Total Token Amount**: Check total matches your funding request amount
   - **Funding Date**: Verify funding date is correct
   - **Purpose**: Review purpose of funds
   - **Facility Information**: Confirm facility details are accurate
   - Verify all information matches your funding request

3. **Review Lender Distribution**
   - View how tokens are distributed to lenders
   - **Allocated Token Amount**: See each lender's allocated token portion
   - **Participation Percentage**: Check percentages match facility participation
   - **Lender Name**: Verify all lenders are included
   - **Commitment Amount**: Review each lender's commitment amount
   - Review total distribution equals request amount

4. **Verify Allocation Accuracy**
   - Confirm total allocation equals request amount
   - Check that lender percentages are correct
   - Verify no errors in distribution
   - Ensure all lenders are included
   - Review individual allocations for accuracy

5. **Review Complete Information**
   - Ensure request amount is correct
   - Check funding date is appropriate
   - Verify purpose is accurate
   - Confirm facility details are correct
   - Review all information one final time

### Approving Token Transfer

1. **Final Review Before Approval**
   - Review all token allocation details carefully
   - Verify token amounts match your expectations
   - Check lender distribution is accurate
   - Confirm all information is correct
   - Ensure funding notice status is "TOKEN_GENERATED"
   - Verify FT tokens have been created (ftContractAddress exists)
   - Ensure you're ready to proceed

2. **Understand Approval Impact**
   - Approval makes funding notice visible to lenders
   - Lenders can review and make decisions
   - Process moves forward to lender review
   - Status changes from TOKEN_GENERATED to TOKEN_APPROVED
   - You cannot easily undo approval
   - Ensure everything is correct before approving

3. **Enter Private Key**
   - Provide your C-chain private key or JSON file format
   - Private key is required for blockchain transaction
   - System uses private key to approve FT tokens to Intain admin wallet
   - This enables token transfer to investors after payment
   - Ensure private key is secure and correct

4. **Initiate Approval**
   - Click "Approve Token Transfer" button or similar
   - Review any confirmation messages
   - Understand what happens after approval
   - Confirm you want to proceed

![Issuer - Token Approval](imagesByMdFilesFolder/34/Issuer_Token_Approval.png)

5. **Complete Approval**
   - Tokens are approved to Intain admin wallet via blockchain
   - Approval transaction is executed and recorded
   - Status updates to show tokens are approved
   - Funding notice becomes visible to lenders
   - Lenders receive notifications

6. **Verify Approval Completion**
   - Confirm status shows "TOKEN_APPROVED"
   - Verify funding notice is now visible to lenders
   - Check that lenders receive notifications
   - Review approval transaction hash
   - Ensure process can proceed
   - Status reflects approval

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
   - View lender decision status

3. **Proceed with Drawdown**
   - Approved lenders can proceed with fund transfer
   - Each lender confirms their transfer independently
   - Funds are transferred to you as lenders confirm
   - Drawdown process completes as transfers are confirmed
   - You receive funds from confirming lenders

## Rules & Validations

- You can only approve tokens after they've been generated - tokens must be created by facility agent before you can approve.

- You must review allocation before approving - take time to verify token amounts and distribution are correct.

- Approval makes funding notice visible to lenders - once approved, lenders can see and review the notice.

- Once approved, you cannot easily undo the approval - approval is a significant step, so verify everything before approving.

- Lenders can then review and approve drawdowns - after your approval, lenders make their own decisions.

- Token amounts must match funding request - the total token amount should equal your approved funding request amount.

- Lender distribution is based on facility participation - each lender's portion is calculated based on their participation percentage in the facility.

- Approval is required for process to continue - the drawdown process cannot proceed until you approve token transfer.

- Status updates after approval - funding notice status changes to reflect your approval.

- Complete audit trail - your approval is recorded with timestamp and details.

## What Happens Next

After approving token transfer:
- Funding notice becomes visible to all lenders
- Lenders receive notifications about the notice
- Lenders can review drawdown details and make decisions
- Approved lenders can proceed with fund transfer
- You can track lender decisions and transfer confirmations
- Funds are transferred to you as lenders confirm transfers
- Drawdown process completes as all transfers are confirmed

After lenders approve:
- Approved lenders transfer their allocated portions
- Each lender confirms transfer independently
- You receive funds from confirming lenders
- Drawdown process completes as transfers are confirmed
- Complete documentation is maintained

Understanding token approval helps you complete the drawdown process, enable lenders to participate in your funding requests, verify token allocation accuracy, and ensure proper verification before funds are disbursed.
