---
title: Token Generation and Issuance
description: Understand how tokens are generated and distributed for funding notices
---

# Token Generation and Issuance

## Overview

Token generation and issuance is the workflow for creating and distributing tokens that represent drawdown amounts in funding notices. After a funding request is approved, the facility agent processes the funding notice by approving it, e-signing for each lender, and then lenders can see the notice and complete fund transfers.

## Workflow Overview

The token generation and issuance workflow begins when a funding request is approved and a funding notice is automatically created. The facility agent approves the funding notice, then e-signs for each lender individually. As each lender's e-sign is completed, that lender can see the funding notice and proceed to transfer funds and confirm settlement.

## Key Stages

**Stage 1: Funding Notice Creation**

When a funding request is approved, a funding notice is automatically created with **Pending Token Generated** status. The notice contains all information from the approved request.

**Stage 2: Facility Agent Approval**

The facility agent reviews the funding notice and clicks **Approve**. This prepares the notice for the e-signature process.

**Stage 3: Facility Agent E-Sign for Each Lender**

The facility agent signs the funding notice for each lender individually using Adobe Sign. The progress shows as **E-sign (0/n)** where n is the number of lenders.

Each time the facility agent signs for a lender:
- The count updates (1/n, 2/n, etc.)
- That lender's e-signature status changes to completed
- That lender can now see the funding notice
- Continue until all lenders are signed (n/n)

![Funding Notice Details - FA](imagesByMdFilesFolder/25/FundingNoticeDetailsFA.png)

**Stage 4: Lender Visibility**

As each lender's e-sign is completed, that lender can see the funding notice in their Credit Facility section.

**Stage 5: Lender Review and Fund Transfer**

Lenders review the funding notice, see their allocated portion, select a payment method, and transfer funds. After transferring, they click **Confirm and Settle**.

![Confirm and Settle - Lender](imagesByMdFilesFolder/ConfirmAndSettleInvestor.png)

**Stage 6: Process Completion**

After lenders confirm settlement, tokens are transferred and the borrower receives the funds. Each lender's confirmation is tracked individually.

## How the Workflow Progresses

**From Approval to E-Sign**

1. Funding request is approved
2. Funding notice is auto-generated (Pending Token Generated)
3. Facility agent clicks Approve
4. Facility agent e-signs for each lender (0/n → n/n)

**From E-Sign to Lender Visibility**

1. Each lender can see the funding notice once their e-sign is complete
2. Lenders navigate to Credit Facility section
3. Action shows Review Funding Notice

**From Lender Review to Completion**

1. Lenders review the funding notice
2. Lenders select payment method
3. Lenders transfer funds
4. Lenders click Confirm and Settle
5. Tokens transferred to borrower
6. Drawdown complete

## Individual Lender Tracking

Throughout the workflow, each lender's participation is tracked individually:
- E-signature status (completed by FA)
- Fund transfer confirmation status
- Individual allocation amounts

## Important Points to Know

**Automatic Notice Creation** - Funding notices are automatically created when funding requests are approved.

**FA Approves First** - The facility agent clicks Approve on the funding notice before e-signing.

**E-Sign Per Lender** - The facility agent signs for each lender individually using Adobe Sign.

**Visibility After E-Sign** - Each lender sees the funding notice once the facility agent has completed their e-sign.

**Confirm and Settle** - Lenders transfer funds and click Confirm and Settle to complete the process.

**Individual Tracking** - Each lender's participation and confirmation is tracked separately.
