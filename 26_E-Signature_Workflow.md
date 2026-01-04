---
title: E-Signature Workflow
description: Learn how electronic signatures work throughout credit facilities
---

# E-Signature Workflow

## Overview

E-signatures are used throughout the credit facility workflow to digitally sign important documents, enabling a complete digital process without paper documents. Electronic signatures are legally binding and provide complete traceability of who signed what and when.

## Workflow Overview

The e-signature workflow spans multiple stages of the credit facility process. Borrowers sign term sheets before submission, lenders sign master commitments to approve facilities, and facility agents sign funding notices for each lender. Each signing stage has specific requirements and outcomes, and signatures are tracked individually with complete audit trails.

## Key Stages

**Stage 1: Term Sheet Signing (Borrowers)** - Borrowers electronically sign term sheets when status is DRAFT. System calls DocuSign endpoint: GET /docusign/signing-complete?envelopeRequest=termSheetSign&envelopeId=123&termSheetId=TS-456. After signing completion, term sheet status changes from DRAFT to BorrowerSigned. Borrowers can then submit term sheets (BorrowerSigned → FAReview).

**Stage 2: Master Commitment Signing (Lenders)** - Lenders electronically sign master commitments to approve facilities. After facility agent finalizes master commitment (Draft → PendingLenderApproval), lenders sign via DocuSign. Any lender approval activates the facility (PendingLenderApproval → ACTIVE). E-Signature envelope is generated for documentation after approval. Individual lender approval status is tracked separately.

**Stage 3: Funding Notice Signing (Facility Agents)** - Facility agents sign funding notices for each lender individually AFTER FT tokens are created. System calls DocuSign endpoint: GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&envelopeId=123&fundingNoticeId=FN-456&lenderOrgId=LENDER-789. Each lender's esignatureStatus in tokenDistribution array is updated to ESIGN_COMPLETED. eSignaturePendingCount decrements by 1. eSignatureStatus set to 'ESIGN_COMPLETED' when all lenders complete (eSignaturePendingCount === 0). Funding notice status remains TOKEN_GENERATED during this process.

**Stage 4: Signature Verification** - After each signing, signatures are verified and recorded. Signed documents are stored securely, and signature status is visible to all parties. Status updates reflect signature completion.

**Stage 5: Document Progression** - After signatures are complete, documents can progress to next stages. Term sheets can be submitted, master commitments activate facilities, and funding notices become visible to lenders. Signatures enable workflow progression.

## How the Workflow Progresses

**Term Sheet Signing Flow** - Borrowers complete term sheets in DRAFT status, then sign electronically via DocuSign. After signing completion, term sheet status changes to BorrowerSigned. Borrowers can then submit term sheets (status changes to FAReview). Facility agents review and make decisions (Accept → Accepted, Reject → Rejected, Request Changes → CHANGES_REQUESTED). If approved (Accepted), master commitments are automatically created with Draft status.

**Master Commitment Signing Flow** - Facility agents configure master commitments in Draft status, then finalize (Draft → PendingLenderApproval). Lenders review and sign via DocuSign to approve facilities. Any lender signature activates the facility (PendingLenderApproval → ACTIVE). E-Signature envelope is generated for documentation after approval. After activation, borrowers can create funding requests.

**Funding Notice Signing Flow** - After funding request is approved, funding notice is auto-created with PENDING_TOKEN_GENERATION status. Facility agent calls updateTokenDistribution (PATCH /cf/funding-notices/:fundingNoticeId/token-distribution) which creates FT tokens and changes status to TOKEN_GENERATED. Facility agents then sign DocuSign for each lender individually (per-lender signing). Each lender's esignatureStatus in tokenDistribution array is updated to ESIGN_COMPLETED. Status remains TOKEN_GENERATED during signing. After all signatures complete (eSignatureStatus: 'ESIGN_COMPLETED'), borrowers can approve token transfers (TOKEN_GENERATED → TOKEN_APPROVED). Lenders can then review and approve drawdowns.

**Signature Tracking** - Throughout the workflow, signatures are tracked with complete details including who signed, when they signed, and what document was signed. This creates complete audit trails for compliance and accountability.

**Status Updates** - After each signing stage, document status updates to reflect signature completion. Term sheets: DRAFT → BorrowerSigned (after DocuSign completion). Master commitments: PendingLenderApproval → ACTIVE (after lender DocuSign approval). Funding notices: Status remains TOKEN_GENERATED during per-lender DocuSign, with individual lender esignatureStatus tracked in tokenDistribution array. eSignatureStatus tracks overall completion ('pending' or 'ESIGN_COMPLETED').

**Document Storage** - All signed documents are stored securely and can be retrieved for audit purposes. Signed versions are preserved, and signature history is maintained for complete traceability.

## Important Points to Know

**Legally Binding** - Electronic signatures are legally binding and enforceable. Once signed, documents are legally valid, and signatures cannot be easily reversed.

**Required Before Progression** - Signatures are required before documents can progress to next stages. Unsigned documents cannot move forward in the workflow.

**Multiple Signatures May Be Required** - Some documents require multiple signatures from different parties. Term sheets need borrower signatures, master commitments need lender signatures, and funding notices need facility agent signatures for each lender.

**Tracked with Timestamps** - Every signature is recorded with who signed and when, creating complete audit trails.

**Stored Securely** - All signed documents are stored securely and can be retrieved for audit purposes. Signed versions are preserved, and signature history is maintained.

**Status Reflects Completion** - Document status updates to reflect signature completion. You can see signature status and completion for all parties.

**Re-signing May Be Required** - If documents are modified significantly, re-signing may be required to ensure signatures reflect current document content.

**Per-Lender Tracking** - For funding notices, facility agents sign for each lender individually, with each lender's signature status tracked separately.

**Enables Workflow Progression** - Signatures enable documents to progress through the workflow.
