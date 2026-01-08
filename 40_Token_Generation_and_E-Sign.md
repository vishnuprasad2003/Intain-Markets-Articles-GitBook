---
title: Token Generation and E-Sign
description: Learn how facility agents generate tokens and complete e-signatures for funding notices
---

# Token Generation and E-Sign

## Overview

This guide covers how facility agents generate tokens for funding notices and complete the e-signature process for each lender. Learn how to create tokens, distribute them to lenders, sign funding notices individually for each lender, and track per-lender e-signature status.

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
   - Click "Save" button
   - Funding notice must be in pending token generation status
   - Token distribution is configured
   - Each lender is initialized with pending signature status
   - Tokens are created for borrower:
     - Token contract is deployed
     - Tokens are transferred to borrower wallet
     - Contract ownership is transferred to borrower
     - Token contract details are recorded
   - Borrowing base and available capacity are updated
   - Status updates to show tokens are generated

![FA - Funding Notice Save - Token Generation](imagesByMdFilesFolder/40/FA_FundingNotice_Save_TokenGeneration.png)

4. **Verify Token Generation**
   - Confirm tokens are created successfully
   - Verify token distribution is configured correctly
   - Check each lender's allocation is accurate
   - Ensure status shows tokens are generated
   - Review token details

### Completing E-Signatures for Lenders

1. **Sign for First Lender**
   - Initiate electronic signature process for this lender
   - Review funding notice document
   - Complete electronic signature for this lender
   - This lender's signature status is updated to completed
   - Status remains as tokens generated (does not change during signing)

2. **Sign for Remaining Lenders**
   - Initiate signature process for the remaining lender
   - Review funding notice document
   - Sign electronically for this lender
   - This lender's esignatureStatus updates to 'ESIGN_COMPLETED'
   - Continue until all lenders are signed

3. **Track Signing Status**
   - View individual lender signing status
   - See which lenders have completed signatures
   - See which lenders are still pending signatures

4. **Verify All Signatures Complete**
   - Check that all lenders have completed signatures
   - Confirm all required signatures are done
   - Verify status shows tokens are generated

## Rules & Validations

- Tokens must be generated before signing - you cannot sign until tokens are generated.

- You sign for each lender individually - each lender requires a separate signature process.

- Each lender's signature is tracked separately - signature status tracks each lender independently.

- All lenders should be signed before borrower approval - complete all signatures to enable smooth process.

- Signing status is tracked per lender - you can see which lenders are signed and which are pending.

- Status remains "TOKEN_GENERATED" during signing - status doesn't change until borrower approves.

- Electronic signatures are legally binding - signatures represent formal approval for each lender.

## What Happens Next

After generating tokens and completing signatures:
- Tokens are created and allocated to lenders
- All lender signatures are complete
- Funding notice becomes visible to lenders
- Lenders can review and approve drawdowns
- Fund transfer process can proceed

After borrower approval:
- Funding notice status changes to show tokens are approved
- Funding notice becomes visible to lenders
- Lenders receive notifications
- Lenders review and make approval decisions
- Approved lenders transfer funds and confirm

Understanding token generation and e-sign helps facility agents effectively manage funding notices, complete the e-signature process for all lenders, track individual lender signatures, and enable the drawdown process to proceed smoothly.
