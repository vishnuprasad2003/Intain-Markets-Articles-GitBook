# Credit Facilities Overview

## What is a Credit Facility?

A credit facility is a lending arrangement where a borrower (issuer) can draw down funds as needed, up to a pre-approved limit. Think of it like a line of credit - you get approved for a maximum amount, and you can borrow portions of it when you need them.

## Key Concepts

### Credit Facility Components

A complete credit facility involves four main components:

1. **Term Sheet**: Initial proposal outlining the facility terms
2. **Master Commitment**: Finalized facility agreement with rules and lenders
3. **Funding Requests**: Borrower's requests to draw down funds
4. **Funding Notices**: Documentation for each drawdown with token distribution

### The Complete Workflow

```
Term Sheet → Master Commitment → Funding Requests → Funding Notices
```

Each step builds on the previous one, creating a complete credit facility transaction.

---

## Term Sheet

### What is a Term Sheet?

The term sheet is the initial proposal document where the borrower outlines:
- How much they want to borrow (facility amount)
- Interest rates and fees
- Maturity date
- Key commercial terms
- Proposed facility structure

### Term Sheet Purpose

- Proposal: Borrower proposes facility terms to facility agent
- Negotiation: Starting point for discussions
- Approval: Facility agent reviews and approves or requests changes
- Foundation: Approved term sheet becomes basis for master commitment

### Term Sheet Status Flow

```
Draft → BorrowerSigned → FAReview → Accepted/Rejected/CHANGES_REQUESTED
```

**Database Collection:** `cf_term_sheets` (MongoDB)

**Status Values:**
- **`'DRAFT'`**: Initial creation state, editable, auto-save enabled
- **`'BorrowerSigned'`**: After DocuSign completion (via `GET /docusign/signing-complete?envelopeRequest=termSheetSign`), issuer can preview
- **`'FAReview'`**: Term sheet submitted for facility agent review (via `POST /cf/submitTermSheet/:termSheetId`)
- **`'Accepted'`**: Approved by facility agent (via `POST /cf/acceptTermSheet/:termSheetId`) - **triggers master commitment auto-creation**
- **`'Rejected'`**: Rejected by facility agent (via `POST /cf/rejectTermSheet/:termSheetId`) - final state
- **`'CHANGES_REQUESTED'`**: Facility agent requests modifications (via `POST /cf/requestChanges/:termSheetId`) - allows editing and resubmission

---

## Master Commitment

### What is a Master Commitment?

The master commitment is the finalized facility agreement that:
- Is automatically created when term sheet is approved
- Contains all facility rules and parameters
- Lists all participating lenders
- Defines borrowing base calculations
- Sets up collateral eligibility rules

### Master Commitment Purpose

- Facility Setup: Configures the complete facility structure
- Lender Approval: Lenders approve the facility
- Rules Definition: Establishes borrowing and collateral rules
- Foundation for Funding: Enables funding requests once active

### Master Commitment Status Flow

```
Draft → PendingLenderApproval → ACTIVE
```

**Key point**: Once ACTIVE, borrowers can create funding requests against it.

---

## Funding Requests

### What is a Funding Request?

A funding request is when the borrower asks to draw down funds from the active facility. Each request specifies:
- Amount requested
- Purpose of funds
- Supporting documentation
- Loan collateral (if applicable)

### Funding Request Purpose

- Drawdown: Borrower requests specific amount
- Review: Facility agent reviews for compliance
- Approval: Facility agent approves or requests changes
- Funding: Approved requests trigger funding notice generation

### Funding Request Status Flow

```
DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED
```

**Database Collection:** `cf_funding_requests` (MongoDB)

**Status Values:**
- **`'DRAFT'`**: Initial creation state (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`), editable, auto-save enabled
- **`'FAReview'`**: Submitted for facility agent review (via `POST /cf/funding-requests/:fundingRequestId/submit`), waiting for facility agent decision
- **`'APPROVED'`**: Approved by facility agent (via `POST /cf/funding-requests/:fundingRequestId/approve`) - **triggers funding notice auto-generation**
- **`'REJECTED'`**: Rejected by facility agent (via `POST /cf/funding-requests/:fundingRequestId/reject`) - final state
- **`'CHANGES_REQUESTED'`**: Facility agent requests modifications (via `POST /cf/funding-requests/:fundingRequestId/request-changes`) - allows editing and resubmission

**Key point**: Approved funding requests automatically generate funding notices. The funding notice is created via the `generateFundingNotice()` function which is called automatically when a funding request reaches `'APPROVED'` status. The funding notice starts with `'PENDING_TOKEN_GENERATION'` status.

---

## Funding Notices

### What is a Funding Notice?

A funding notice is the documentation for each drawdown that:
- Is automatically generated when funding request is approved
- Contains drawdown details and calculations
- Distributes tokens to lenders
- Requires e-signatures
- Tracks individual lender participation

### Funding Notice Purpose

- Documentation: Creates official drawdown documentation
- Token Distribution: Allocates tokens to participating lenders
- E-Signature: Requires facility agent and borrower signatures
- Lender Visibility: Makes drawdown visible to lenders for approval

### Funding Notice Status Flow

```
PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
```

**Database Collection:** `cf_funding_notices` (MongoDB)

**Status Values:**
- **`'PENDING_TOKEN_GENERATION'`**: Auto-created when funding request approved, waiting for token generation
- **`'TOKEN_GENERATED'`**: FT tokens created for borrower during `updateTokenDistribution` call (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`), facility agent can sign for lenders
- **`'TOKEN_APPROVED'`**: Borrower approves token transfer (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`), funding notice becomes visible to lenders

**Per-Lender E-Signature Tracking:**
- Each lender in the `tokenDistribution` array has an `esignatureStatus` field: `'pending'` | `'ESIGN_COMPLETED'`
- Facility agent signs for each lender individually via DocuSign (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&lenderOrgId=...`)
- Individual lender's `esignatureStatus` is updated to `'ESIGN_COMPLETED'` when facility agent signs for that specific lender
- The funding notice status remains `'TOKEN_GENERATED'` during per-lender signing - only changes to `'TOKEN_APPROVED'` when borrower approves token transfer

---

## Roles in Credit Facilities

### Borrower (Issuer)

**Responsibilities:**
- Create term sheets
- Submit for facility agent review
- Create funding requests
- Approve token transfers
- Respond to change requests

**What they see:**
- Their term sheets and status
- Their funding requests
- Funding notices requiring approval
- Facility status and details

### Facility Agent

**Responsibilities:**
- Review and approve term sheets
- Create and configure master commitments
- Review funding requests
- Sign funding notices for lenders
- Manage facility setup

**What they see:**
- Term sheets for review
- Master commitments they manage
- Funding requests for review
- Funding notices to sign

### Lender

**Responsibilities:**
- Approve master commitments
- Review funding notices
- Approve or reject drawdowns
- Confirm fund transfers

**What they see:**
- Master commitments pending approval
- Funding notices after borrower approval
- Their participation in facilities
- Fund transfer confirmations

---

## Key Features

### Automatic Creation

**Master Commitment Auto-Creation:**
- **Trigger**: Term sheet status changes to `'Accepted'` (via `POST /cf/acceptTermSheet/:termSheetId`)
- **Function**: System automatically calls `autoCreateMasterCommitment()` function
- **Database**: Creates document in `cf_master_commitments` collection
- **Status**: Created with `'DRAFT'` status
- **Pre-populated fields** (read-only from term sheet): `facilityType`, `advanceRate`, `margin`, `pricingIndex`, `maturityDate`, `drawFrequency`, `covenantTemplate`, `totalCommitmentAmount` (from `requestedCommitmentAmount`), `marketMakerOrgId`, `issuerOrgId`, `issuerId`
- **Empty fields** (for facility agent to complete): `collateralRules` (empty array), `lenderGroups` (empty array), `servicerOrgId` (empty array), `facilityName`, `borrowingBase`, etc.
- **Linkage**: Linked to term sheet via `termSheetId` field

**Funding Notice Auto-Generation:**
- **Trigger**: Funding request status changes to `'APPROVED'` (via `POST /cf/funding-requests/:fundingRequestId/approve`)
- **Function**: System automatically calls `generateFundingNotice()` function
- **Database**: Creates document in `cf_funding_notices` collection
- **Status**: Created with `'PENDING_TOKEN_GENERATION'` status
- **Pre-populated fields**: `requestAmount`, `fundingDate`, `masterCommitmentId`, `facilityName`, `advanceRate`, `bbCalculation`, `availableCapacity`, `borrowingBase`, `utilisationPercentage`, `collateralValue`
- **Token Distribution**: Initialized with each lender having `esignatureStatus: 'pending'` in the `tokenDistribution` array
- **Linkage**: Linked to funding request via `fundingRequestId` field

### Token Integration

**FT Tokens:**
- **Creation**: Created for borrower during `updateTokenDistribution` API call (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)
- **Status Change**: Funding notice status changes from `'PENDING_TOKEN_GENERATION'` to `'TOKEN_GENERATED'` when tokens are created
- **Distribution**: Tokens allocated to lenders based on their commitment amounts in the `tokenDistribution` array
- **Blockchain**: FT tokens are created on the blockchain via smart contract calls (`createFTTokensForBorrower` function)
- **Tracking**: Each lender's token allocation tracked via `tokensAllocated` field in `tokenDistribution` array
- **Approval**: Borrower must approve token transfer (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`) before lenders can see the funding notice

### E-Signature Integration

**DocuSign/ZohoSign:**
- **Term Sheets**: Borrower signs via DocuSign/ZohoSign (via `GET /docusign/signing-complete?envelopeRequest=termSheetSign&termSheetId=...`), status changes from `'DRAFT'` to `'BorrowerSigned'`
- **Master Commitments**: Lender signs via DocuSign/ZohoSign (via `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign&masterCommitmentId=...`), any lender approval changes status from `'PendingLenderApproval'` to `'ACTIVE'`, e-signature envelope generated after approval for documentation
- **Funding Notices**: Facility agent signs for **each lender individually** via DocuSign/ZohoSign (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&fundingNoticeId=...&lenderOrgId=...`), each lender's `esignatureStatus` in `tokenDistribution` array updated to `'ESIGN_COMPLETED'` individually, aggregate `eSignatureStatus` becomes `'ESIGN_COMPLETED'` when all lenders signed
- **IPFS Storage**: Signed documents stored in IPFS, IPFS hash stored in database
- **Complete digital signature workflow**: All signatures tracked with timestamps and user IDs in `statusHistory` and `actionHistory` arrays

### Status-Based Workflow

**Clear Status Progression:**
- Each component has clear statuses
- Status controls available actions
- Workflow ensures proper order
- Status history tracks all changes

---

## Common Workflow

### Complete Facility Setup

1. **Borrower creates term sheet**
   - Fills in facility terms
   - Signs via DocuSign
   - Submits for review

2. **Facility agent reviews**
   - Reviews term sheet
   - Approves or requests changes
   - If approved, master commitment auto-created

3. **Facility agent configures master commitment**
   - Sets up facility rules
   - Adds lenders
   - Configures borrowing base
   - Submits for lender approval

4. **Lender approves**
   - Reviews master commitment
   - Signs via DocuSign
   - Facility becomes ACTIVE

5. **Borrower creates funding request**
   - Requests specific amount
   - Provides documentation
   - Submits for review

6. **Facility agent reviews funding request**
   - Reviews for compliance
   - Approves or requests changes
   - If approved, funding notice auto-generated

7. **Token generation and distribution**
   - Tokens created for borrower
   - Distributed to lenders
   - Facility agent signs for each lender

8. **Borrower approves token transfer**
   - Approves token transfer privilege
   - Funding notice becomes visible to lenders

9. **Lenders review and approve**
   - Review funding notice
   - Approve or reject drawdown
   - Confirm fund transfers

---

## Benefits

### For Borrowers

- Flexible Funding: Draw down funds as needed
- Pre-Approved Limit: Know your borrowing capacity
- Streamlined Process: Digital workflow simplifies requests
- Transparency: See all facility details and status

### For Facility Agents

- Efficient Management: Manage facilities digitally
- Compliance Control: Review and approve requests
- Complete Visibility: See all facility activity
- Automated Workflows: System handles routine tasks

### For Lenders

- **Clear Opportunities**: See funding requests clearly
- **Individual Control**: Approve/reject per drawdown
- **Token Tracking**: Blockchain-based tracking
- **Transparency**: See all facility details

---

## Best Practices

### For Borrowers

1. **Complete term sheets thoroughly**: Provide all required information
2. **Respond to change requests promptly**: Keep workflow moving
3. **Create clear funding requests**: Specify amounts and purposes
4. **Approve tokens promptly**: Enable lender visibility
5. **Track facility status**: Monitor your credit facility

### For Facility Agents

1. **Review thoroughly**: Ensure compliance before approval
2. **Configure master commitments completely**: Set up all rules
3. **Respond promptly**: Keep workflow moving
4. **Sign funding notices timely**: Enable lender participation
5. **Monitor facility activity**: Track all drawdowns

### For Lenders

1. **Review master commitments carefully**: Understand facility terms
2. **Evaluate funding requests**: Assess each drawdown
3. **Approve/reject promptly**: Keep process moving
4. **Confirm transfers**: Complete the funding process
5. **Track participation**: Monitor your involvement

---

## Key Takeaways

1. **Four components**: Term sheet → Master commitment → Funding requests → Funding notices
2. **Automatic creation**: Master commitments and funding notices auto-created
3. **Status-based workflow**: Clear status progression guides process
4. **Role-based actions**: Each role has specific responsibilities
5. **Complete digital**: E-signatures and tokens enable full digital workflow

Understanding credit facilities helps you effectively use this powerful tool for flexible, managed borrowing with multiple lenders.
