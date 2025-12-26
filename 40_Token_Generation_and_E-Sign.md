---
title: Token Generation and E-Sign
description: Learn how facility agents generate tokens and complete e-signatures for funding notices
---

# Token Generation and E-Sign

## Overview

This guide covers how facility agents generate tokens for funding notices and complete the e-signature process for each lender. Learn how to create tokens, distribute them to lenders, sign funding notices individually for each lender, and track per-lender e-signature status to enable the drawdown process.

## Who Can Use This

- Facility Agents who manage funding notices and complete e-signature processes

## When This Is Used

Use token generation and e-sign when:
- Funding request has been approved by you
- Funding notice needs tokens generated
- You need to sign funding notices for lenders
- You want to complete the drawdown process
- You're preparing funding notice for borrower approval

## Step-by-Step Process

### Generating Tokens

1. **Access Funding Notice**
   - Navigate to approved funding notice
   - Verify status shows "PENDING_TOKEN_GENERATION" or similar
   - Open token distribution section
   - Review funding notice details

2. **Configure Token Distribution**
   - Review lender groups and participation percentages
   - Specify token allocation for each lender
   - Set distribution amounts based on lender commitments
   - Confirm allocation percentages match facility participation
   - Review distribution details for accuracy

3. **Initialize Token Distribution**
   - Click "Update Token Distribution" or similar button
   - System initializes tokenDistribution array
   - Each lender is set with esignatureStatus: 'pending'
   - Tokens are created for borrower (FT tokens)
   - Status updates to "TOKEN_GENERATED"

4. **Verify Token Generation**
   - Confirm tokens are created successfully
   - Verify token distribution is configured correctly
   - Check each lender's allocation is accurate
   - Ensure status shows tokens are generated
   - Review token details

### Completing E-Signatures for Lenders

1. **Sign for First Lender**
   - Select first lender from lender list
   - Initiate electronic signature process for this lender
   - Review funding notice document
   - Complete electronic signature for this lender
   - Confirm signature is complete
   - Lender's esignatureStatus updates to 'ESIGN_COMPLETED'
   - Status remains "TOKEN_GENERATED"

2. **Sign for Remaining Lenders**
   - Select next lender
   - Initiate signature process for this lender
   - Review funding notice document
   - Sign electronically for this lender
   - Confirm signature is complete
   - This lender's esignatureStatus updates to 'ESIGN_COMPLETED'
   - Continue until all lenders are signed

3. **Track Signing Status**
   - View individual lender signing status
   - See which lenders have completed signatures (ESIGN_COMPLETED)
   - See which lenders are still pending signatures
   - Monitor overall completion progress
   - Verify all signatures are complete

4. **Verify All Signatures Complete**
   - Check that all lenders have esignatureStatus: 'ESIGN_COMPLETED'
   - Confirm all required signatures are done
   - Verify status shows "TOKEN_GENERATED"
   - Ensure funding notice is ready for borrower approval

### After E-Signature Completion

1. **Borrower Approval Enabled**
   - After all signatures are complete, borrower can approve token transfer
   - Funding notice is ready for borrower review
   - Borrower can see token allocation and approve
   - Borrower approval makes notice visible to lenders

2. **Monitor Process**
   - Track borrower approval status
   - Monitor lender review and approval
   - Track fund transfer confirmations
   - Ensure process progresses smoothly

## Rules & Validations

- Tokens must be generated before signing - you cannot sign until tokens are generated.

- You sign for each lender individually - each lender requires a separate signature process.

- Each lender's signature is tracked separately - esignatureStatus field tracks each lender independently.

- All lenders should be signed before borrower approval - complete all signatures to enable smooth process.

- Signing status is tracked per lender - you can see which lenders are signed and which are pending.

- Status remains "TOKEN_GENERATED" during signing - status doesn't change until borrower approves.

- Electronic signatures are legally binding - signatures represent formal approval for each lender.

- Complete audit trail - all signatures are recorded with timestamps and details.

- Borrower can approve after signatures - borrower approval enables lender visibility.

- Individual tracking - each lender's signature status is tracked independently in tokenDistribution array.

## What Happens Next

After generating tokens and completing signatures:
- Tokens are created and allocated to lenders
- All lender signatures are complete (ESIGN_COMPLETED)
- Borrower can approve token transfer
- After borrower approval, funding notice becomes visible to lenders
- Lenders can review and approve drawdowns
- Fund transfer process can proceed

After borrower approval:
- Funding notice status changes to "TOKEN_APPROVED"
- Funding notice becomes visible to lenders
- Lenders receive notifications
- Lenders review and make approval decisions
- Approved lenders transfer funds and confirm

Understanding token generation and e-sign helps facility agents effectively manage funding notices, complete the e-signature process for all lenders, track individual lender signatures, and enable the drawdown process to proceed smoothly.
