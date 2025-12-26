# Funding Notices Overview

## What is a Funding Notice?

A funding notice is the official documentation for each drawdown from a credit facility. It's automatically generated when a funding request is approved and contains all the details needed for the drawdown, including token distribution to lenders.

## Key Concepts

### Automatic Generation

Funding notices are automatically created:
- Trigger: Funding request status changes to `'APPROVED'` (via `POST /cf/funding-requests/:fundingRequestId/approve`)
- Function: System automatically calls `generateFundingNotice(fundingRequest, masterCommitment)` function
- Database: Creates document in `cf_funding_notices` collection (MongoDB)
- No manual creation allowed: Cannot be created via API - only auto-generated
- Created immediately: Happens synchronously during funding request approval process
- ID Generation: `fundingNoticeId` generated using format `FN-MMDDYYYY-XXXX` where MMDDYYYY is current date and XXXX is random alphanumeric suffix

### Purpose

Funding notices serve to:
- Document drawdowns: Create official record of each drawdown
- Distribute tokens: Allocate tokens to participating lenders
- Enable e-signatures: Require facility agent and borrower signatures
- Track participation: Monitor individual lender involvement
- Facilitate funding: Enable lender approval and fund transfer

---

## Funding Notice Components

### Basic Information

**From funding request:**
- Request amount
- Funding date
- Purpose
- Supporting documentation reference

**From master commitment:**
- Facility details
- Facility rules
- Borrowing base information
- Available capacity

### Token Distribution

**For each lender:**
- Tokens allocated
- Lender commitment amount
- Participation percentage
- Individual lender status
- E-signature status (per lender)

### Calculations

**Borrowing base calculations:**
- Current borrowing base
- Available capacity
- Utilization percentage
- Impact of drawdown

---

## Funding Notice Status Flow

### Complete Workflow

```
PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
```

### Status 1: PENDING_TOKEN_GENERATION

**What it means:**
- Funding notice automatically created
- Waiting for token generation
- Tokens not yet created
- Initial state after generation

**What happens:**
- Funding notice created with this status
- Token distribution array initialized
- Each lender has `esignatureStatus: 'pending'`
- Ready for token generation process

**Next steps:**
- Facility agent calls `updateTokenDistribution`
- Tokens created for borrower
- Status changes to TOKEN_GENERATED

### Status 2: TOKEN_GENERATED

**What it means:**
- FT tokens have been created for borrower
- Token distribution updated
- Facility agent can sign for lenders
- Tokens exist but not yet approved for transfer

**What happens:**
- Facility agent calls `updateTokenDistribution` API (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)
- System validates: funding notice status is `'PENDING_TOKEN_GENERATION'`, `tokenDistribution` array provided with lender allocations
- FT tokens created for borrower via blockchain smart contract (`createFTTokensForBorrower` function)
- Database update in `cf_funding_notices` collection:
  - Status changes to `'TOKEN_GENERATED'`
  - `tokenDistribution` array updated: `tokensAllocated` set for each lender based on their commitment amount
  - Borrowing base calculations updated: `borrowingBase`, `availableCapacity`, `utilisationPercentage` recalculated
  - Entry added to `statusHistory`: `{ status: 'TOKEN_GENERATED', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'FT tokens created for borrower' }`
- Each lender still has `esignatureStatus: 'pending'` (facility agent will sign for each lender next)
- Tokens exist on blockchain, borrower owns tokens, ready for facility agent to sign for lenders

**What facility agent can do:**
- Sign funding notice for each lender individually
- Complete DocuSign for each lender
- Update per-lender e-signature status

**What borrower can do:**
- View funding notice
- See tokens have been created
- Approve token transfer when ready

**Next steps:**
- Facility agent signs for each lender
- Borrower approves token transfer
- Status changes to TOKEN_APPROVED

### Status 3: TOKEN_APPROVED

**What it means:**
- Borrower has approved token transfer
- Funding notice visible to lenders
- Lenders can review and approve
- Ready for lender participation

**What happens:**
- Borrower approves token transfer (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`)
- System validates: funding notice status is `'TOKEN_GENERATED'`, borrower is the issuer (`issuerId` matches)
- Database update in `cf_funding_notices` collection:
  - Status changes to `'TOKEN_APPROVED'`
  - Entry added to `statusHistory`: `{ status: 'TOKEN_APPROVED', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Borrower approved token transfer' }`
  - Entry added to `actionHistory`: `{ action: 'Approve Token Transfer', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'Token transfer approved by borrower' }`
- Funding notice becomes visible to lenders (lenders can now query and see funding notices with `status: 'TOKEN_APPROVED'`)
- Lenders can see and act on notice: view funding notice details, approve/reject drawdown, confirm fund transfers
- Token transfer privilege enabled: tokens can now be transferred to lenders

**What lenders can do:**
- View funding notice
- Review drawdown details
- Approve or reject drawdown
- Confirm fund transfers

**This enables:**
- Lender review and approval
- Individual lender participation
- Fund transfer confirmations
- Drawdown completion

---

## Token Distribution

### Per-Lender Tracking

**Each lender tracked separately:**
- `tokensAllocated`: Amount of tokens allocated
- `lenderApprovalStatus`: PENDING | APPROVED | REJECTED
- `esignatureStatus`: pending | ESIGN_COMPLETED
- `mintingStatus`: pending | completed
- `amountTransferred`: pending | transferred

### Aggregate Tracking

**Overall status:**
- `eSignaturePendingCount`: Number of lenders with pending signatures
- `eSignatureStatus`: Aggregate DocuSign status (pending | ESIGN_COMPLETED)
- Total tokens allocated
- Overall approval status

---

## E-Signature Process

### Facility Agent Signing

**Per-lender signing:**
- Facility agent signs for each lender individually
- Each lender has separate DocuSign envelope
- Individual `esignatureStatus` updated per lender
- Aggregate status updates when all complete

**Process:**
1. Tokens already created (TOKEN_GENERATED status)
2. Facility agent initiates DocuSign for Lender A
3. Signs funding notice for Lender A
4. Lender A's `esignatureStatus` → ESIGN_COMPLETED
5. Repeat for each lender
6. Aggregate `eSignatureStatus` → ESIGN_COMPLETED when all done

### Borrower Approval

**Token transfer approval:**
- Borrower approves token transfer privilege
- Enables lender visibility
- Status changes to TOKEN_APPROVED
- Lenders can now see funding notice

---

## Key Features

### Automatic Creation

**When funding request approved:**
- System automatically creates funding notice
- Links to approved funding request
- Pre-populates with request and facility data
- Initializes token distribution

### Token Integration

**FT token creation:**
- Tokens created during `updateTokenDistribution` call
- Allocated to borrower initially
- Distributed to lenders as specified
- Blockchain-based tracking

### Individual Lender Tracking

**Per-lender status:**
- Each lender's participation tracked separately
- Individual approval status
- Per-lender e-signature status
- Individual fund transfer confirmation

---

## Common Workflow

### Complete Process

1. **Funding request approved** → Funding notice auto-created (PENDING_TOKEN_GENERATION)
2. **Token distribution updated** → Tokens created (TOKEN_GENERATED)
3. **Facility agent signs** → Signs for each lender individually
4. **Borrower approves tokens** → Status: TOKEN_APPROVED
5. **Lenders review** → See funding notice
6. **Lenders approve/reject** → Individual decisions
7. **Fund transfers confirmed** → Drawdown completes

---

## Best Practices

### For Facility Agents

1. **Generate tokens promptly**: Call updateTokenDistribution after approval
2. **Sign for all lenders**: Complete e-signatures for each lender
3. **Track individual status**: Monitor per-lender progress
4. **Complete promptly**: Keep workflow moving

### For Borrowers

1. **Monitor notice creation**: Watch for auto-generated notice
2. **Approve tokens timely**: Enable lender visibility promptly
3. **Track progress**: Monitor funding notice status
4. **Respond to lenders**: Address any questions

### For Lenders

1. **Review promptly**: Evaluate funding notices quickly
2. **Make decisions**: Approve or reject clearly
3. **Confirm transfers**: Complete fund transfer confirmations
4. **Track participation**: Monitor your involvement

---

## Key Takeaways

1. Auto-generated: Created automatically when funding request approved
2. Three statuses: PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
3. Token integration: FT tokens created and distributed
4. Per-lender tracking: Individual lender status tracked
5. E-signature workflow: Facility agent signs for each lender

Understanding funding notices helps you track drawdowns and understand how funds flow from facility to borrower through the token-based system.
