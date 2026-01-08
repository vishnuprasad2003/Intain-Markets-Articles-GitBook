---
title: Token Generation and Issuance
description: Understand how tokens are generated and distributed for funding notices
---

# Token Generation and Issuance

## Overview

Token generation and issuance is the complete workflow for creating and distributing tokens that represent drawdown amounts in funding notices. These tokens serve as digital representations of the drawdown that enable tracking, distribution, and management of funds across multiple lenders.

## Workflow Overview

The token generation and issuance workflow begins when a funding request is approved and a funding notice is automatically created. Facility agents generate tokens representing the drawdown amount, configure distribution to lenders based on their participation percentages, and sign funding notices.

## Key Stages

**Stage 1: Funding Notice Creation** - When a funding request is approved, a funding notice is automatically created with PENDING_TOKEN_GENERATION status. The notice contains all information from the approved request and is ready for token generation.

**Stage 2: Token Distribution Configuration and Token Generation** - Facility agents configure token distribution with lender allocations based on their participation percentages. Tokens are created for the borrower representing the drawdown amount. The system also updates borrowing base and available capacity calculations. Status changes to show tokens are generated.

![FA - Funding Notice Save - Token Generation](imagesByMdFilesFolder/25/FA_FundingNotice_Save_TokenGeneration.png)

**Stage 3: Per-Lender E-Signature** - Facility agents sign funding notices for each lender individually after tokens are created. Each lender's signature status is tracked separately. Status remains as tokens generated during this process.

![Funding Notice Details - FA](imagesByMdFilesFolder/25/FundingNoticeDetailsFA.png)

**Stage 5: Lender Visibility** - Funding notices become visible to lenders. Lenders can see their allocated token portions and review drawdown details. This enables lender review and decision-making.

**Stage 6: Lender Review and Approval** - Lenders review funding notices and approve or reject their participation. Each lender makes independent decisions, and participation is tracked individually. Lenders can see their allocated portion and make decisions accordingly.

![Lender Approval - Funding Notice](imagesByMdFilesFolder/25/LenderApprovalFundingNotice.png)

**Stage 7: Fund Transfer Confirmation** - After approving, lenders transfer funds and confirm transfers. Each lender confirms their transfer independently, completing their participation in the drawdown. The system tracks individual lender confirmations.

![Fund Transfer Confirmation](imagesByMdFilesFolder/25/FundTransferConfirmation.png)

## How the Workflow Progresses

**From Approval to Token Generation** - The workflow starts automatically when funding requests are approved. Facility agents initiate token generation, creating tokens for borrowers and configuring distribution. This stage transforms approved requests into tokenized drawdowns ready for distribution.

**From Token Generation** - After tokens are generated and distributed, facility agents sign funding notices for each lender. Once all signatures are complete, the funding notice are visible to lenders, they can decide the approval.

**From Lender Review to Fund Transfer** - After lenders review and approve, they transfer funds and confirm transfers. Each lender completes their participation independently, and the system tracks all confirmations. Once all lenders confirm, the drawdown process is complete.

**Status Progression** - The workflow progresses through statuses: Pending token generation (when funding notice is created) → Tokens generated (after tokens are created) → Tokens approved (after borrower approves token transfer). During per-lender e-signature, status remains as tokens generated. Each status represents a specific stage and determines what actions are available. Understanding status helps you know where you are in the process.

**Individual Lender Tracking** - Throughout the workflow, each lender's participation is tracked individually. Token allocations, signature status, approval decisions, and transfer confirmations are all tracked separately, enabling flexible participation and independent decisions.

## Important Points to Know

**Automatic Notice Creation** - Funding notices are automatically created when funding requests are approved. The system creates them with pre-populated request data.

**Token Generation Required** - Facility agents must generate tokens before borrowers can approve transfers. Tokens are created when facility agents configure token distribution, not during e-signature completion. Tokens represent drawdown amounts digitally and enable tracking and distribution to lenders.

**Distribution Based on Participation** - Token distribution is calculated automatically based on lender participation percentages in the facility. Each lender receives their allocated portion.

**Per-Lender E-Signature** - Facility agents sign funding notices for each lender individually, with each lender's signature status tracked separately.

**Individual Lender Decisions** - Each lender makes independent decisions about participation. Lenders can approve or reject based on their own criteria, and decisions are tracked separately.

**Complete Documentation** - All token generation, distribution, approvals, and transfers are documented with complete audit trails.

**Status Tracks Progress** - Funding notice status shows where each notice is in the workflow, from token generation through borrower approval to lender review and fund transfer.
