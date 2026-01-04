---
title: Token Generation and Issuance
description: Understand how tokens are generated and distributed for funding notices
---

# Token Generation and Issuance

## Overview

Token generation and issuance is the complete workflow for creating and distributing tokens that represent drawdown amounts in funding notices. These tokens serve as digital representations of the drawdown that enable tracking, distribution, and management of funds across multiple lenders.

## Workflow Overview

The token generation and issuance workflow begins when a funding request is approved and a funding notice is automatically created. Facility agents generate tokens representing the drawdown amount, configure distribution to lenders based on their participation percentages, and sign funding notices. Borrowers then approve token transfers, making funding notices visible to lenders who can review and approve their participation.

## Key Stages

**Stage 1: Funding Notice Creation** - When a funding request is approved, a funding notice is automatically created with PENDING_TOKEN_GENERATION status. The notice contains all information from the approved request and is ready for token generation.

**Stage 2: Token Distribution Configuration and Token Generation** - Facility agents configure tokenDistribution array with lender allocations (lenderOrgId, lenderName, commitmentAmount, tokensAllocated, votingPercentage). System calls API: PATCH /cf/funding-notices/:fundingNoticeId/token-distribution. During this call, system creates FT tokens for borrower via createFTTokensForBorrower function: deploys FT contract, transfers tokens to borrower wallet, transfers ownership to borrower. System also updates borrowing base via IA calculation. Status changes from PENDING_TOKEN_GENERATION to TOKEN_GENERATED. Each lender initialized with esignatureStatus: 'pending' in tokenDistribution array.

![FA - Funding Notice Save - Token Generation](imagesByMdFilesFolder/25/FA_FundingNotice_Save_TokenGeneration.png)

**Stage 3: Per-Lender E-Signature** - Facility agents sign funding notices for each lender individually AFTER FT tokens are created. System calls DocuSign endpoint: GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&envelopeId=123&fundingNoticeId=FN-456&lenderOrgId=LENDER-789. Each lender's esignatureStatus in tokenDistribution array is updated to ESIGN_COMPLETED. eSignaturePendingCount decrements by 1. eSignatureStatus set to 'ESIGN_COMPLETED' when all lenders complete (eSignaturePendingCount === 0). Status remains TOKEN_GENERATED during this process (does not change).

![Funding Notice Details - FA](imagesByMdFilesFolder/25/FundingNoticeDetailsFA.png)

**Stage 5: Borrower Token Approval** - Borrowers review the token allocation to verify amounts and distribution are correct. Borrowers enter C-chain private key or upload JSON file format. System calls API: POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer. System approves FT tokens to Intain admin wallet for transfer to investors after payment. Status changes from TOKEN_GENERATED to TOKEN_APPROVED. Funding notice becomes visible to lenders.

![Issuer - Token Approval](imagesByMdFilesFolder/25/Issuer_Token_Approval.png)

**Stage 6: Lender Visibility** - After borrower approval, funding notices become visible to lenders. Lenders can see their allocated token portions and review drawdown details. This enables lender review and decision-making.

**Stage 7: Lender Review and Approval** - Lenders review funding notices and approve or reject their participation. Each lender makes independent decisions, and participation is tracked individually. Lenders can see their allocated portion and make decisions accordingly.

![Lender Approval - Funding Notice](imagesByMdFilesFolder/25/LenderApprovalFundingNotice.png)

**Stage 8: Fund Transfer Confirmation** - After approving, lenders transfer funds and confirm transfers. Each lender confirms their transfer independently, completing their participation in the drawdown. The system tracks individual lender confirmations.

![Fund Transfer Confirmation](imagesByMdFilesFolder/25/Fund Transfer Confirmation.png)

## How the Workflow Progresses

**From Approval to Token Generation** - The workflow starts automatically when funding requests are approved. Facility agents initiate token generation, creating tokens for borrowers and configuring distribution. This stage transforms approved requests into tokenized drawdowns ready for distribution.

**From Token Generation to Borrower Approval** - After tokens are generated and distributed, facility agents sign funding notices for each lender. Once all signatures are complete, borrowers can review and approve token transfers. Borrower approval is required before lenders can see notices.

**From Borrower Approval to Lender Review** - Once borrowers approve token transfers, funding notices become visible to lenders. Lenders can review their allocations and drawdown details, enabling informed decision-making about participation.

**From Lender Review to Fund Transfer** - After lenders review and approve, they transfer funds and confirm transfers. Each lender completes their participation independently, and the system tracks all confirmations. Once all lenders confirm, the drawdown process is complete.

**Status Progression** - The workflow progresses through statuses: PENDING_TOKEN_GENERATION (auto-created when funding request approved) → TOKEN_GENERATED (after updateTokenDistribution creates FT tokens) → TOKEN_APPROVED (after borrower approves token transfer). During per-lender DocuSign, status remains TOKEN_GENERATED. Each status represents a specific stage and determines what actions are available. Understanding status helps you know where you are in the process.

**Individual Lender Tracking** - Throughout the workflow, each lender's participation is tracked individually. Token allocations, signature status, approval decisions, and transfer confirmations are all tracked separately, enabling flexible participation and independent decisions.

## Important Points to Know

**Automatic Notice Creation** - Funding notices are automatically created when funding requests are approved. The system creates them with pre-populated request data.

**Token Generation Required** - Facility agents must call updateTokenDistribution API which creates FT tokens for borrower before borrowers can approve transfers. FT tokens are created during updateTokenDistribution call, NOT during DocuSign completion. Tokens represent drawdown amounts digitally (totalSupply = requestAmount * 10^6 with 6 decimals) and enable tracking and distribution to lenders.

**Distribution Based on Participation** - Token distribution is calculated automatically based on lender participation percentages in the facility. Each lender receives their allocated portion.

**Per-Lender E-Signature** - Facility agents sign funding notices for each lender individually, with each lender's signature status tracked separately.

**Borrower Approval Required** - Borrowers must approve token transfers before funding notices become visible to lenders.

**Individual Lender Decisions** - Each lender makes independent decisions about participation. Lenders can approve or reject based on their own criteria, and decisions are tracked separately.

**Complete Documentation** - All token generation, distribution, approvals, and transfers are documented with complete audit trails.

**Status Tracks Progress** - Funding notice status shows where each notice is in the workflow, from token generation through borrower approval to lender review and fund transfer.
