# Token Generation & E-Sign

## Overview

This guide covers how facility agents generate tokens for funding notices and complete the e-signature process for each lender. Learn how to create tokens, sign funding notices, and track per-lender e-signature status.

## Token Generation

### When to Generate Tokens

**Appropriate timing:**
- After funding request is approved
- Funding notice is in PENDING_TOKEN_GENERATION status
- Ready to create tokens for borrower
- Before facility agent signing

### How to Generate Tokens

**Process:**
1. Navigate to funding notice (via `GET /cf/funding-notices/:fundingNoticeId`)
2. Verify status is `'PENDING_TOKEN_GENERATION'` (validated in code: `fundingNotice.status === 'PENDING_TOKEN_GENERATION'`)
3. Call `updateTokenDistribution` API (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)
4. Request body contains `tokenDistribution` array: `[{ lenderGroupId, lenderOrgId, lenderName, commitmentAmount, votingPercentage, tokensAllocated }, ...]`
5. System validates: total commitment amount equals `requestAmount`, at least one lender, voting percentages valid (0-100), amounts are numbers
6. FT tokens created for borrower via blockchain smart contract (`createFTTokensForBorrower` function)
7. Database update in `cf_funding_notices` collection:
   - Status changes to `'TOKEN_GENERATED'`
   - `tokenDistribution` array updated with `tokensAllocated` for each lender
   - `borrowingBase`, `availableCapacity`, `utilisationPercentage` recalculated
8. Tokens created for borrower - borrower owns tokens on blockchain

**What happens:**
- FT tokens created for borrower
- Token distribution array initialized
- Each lender initialized with pending status
- Status changes to TOKEN_GENERATED
- Ready for e-signature process

---

## E-Signature Process

### Per-Lender Signing

**Important concept:**
- Facility agent signs for each lender individually
- Each lender has separate DocuSign envelope
- Individual `esignatureStatus` tracked per lender
- Aggregate status tracks overall completion

### Step 1: Initiate Signing for Lender

**Process:**
1. Navigate to funding notice
2. Select lender to sign for
3. Click "Sign for [Lender Name]" or similar
4. Initiate DocuSign for this lender
5. DocuSign envelope created

### Step 2: Complete Signing

**Signing process:**
1. Review funding notice in DocuSign
2. Sign electronically for this lender
3. Complete signing process
4. DocuSign completion triggers update

### Step 3: Status Update

**After signing:**
- DocuSign/ZohoSign webhook received (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&envelopeId=...&fundingNoticeId=...&lenderOrgId=...`)
- Database update in `cf_funding_notices` collection:
  - This lender's `esignatureStatus` in `tokenDistribution` array → `'ESIGN_COMPLETED'` (updated individually)
  - `eSignaturePendingCount` decrements by 1 (stored in funding notice document)
  - Signed PDF downloaded from DocuSign/ZohoSign and stored in IPFS, IPFS hash stored
  - If `eSignaturePendingCount === 0` (all lenders signed), `eSignatureStatus` → `'ESIGN_COMPLETED'` (aggregate status)
  - Entry added to `actionHistory`: `{ action: 'E-Signature Completed', userId: facilityAgentId, timestamp: DateUtils.nowUTC(), comments: 'E-signature completed for lender', details: { lenderOrgId, esignatureStatus: 'ESIGN_COMPLETED' } }`
- Individual status tracked separately: each lender's `esignatureStatus` in `tokenDistribution` array is independent
- Funding notice status remains `'TOKEN_GENERATED'` during per-lender signing (only changes to `'TOKEN_APPROVED'` when borrower approves token transfer)

### Step 4: Repeat for Each Lender

**For remaining lenders:**
1. Select next lender
2. Initiate DocuSign
3. Sign for this lender
4. Update individual status
5. Continue until all lenders signed

---

## Tracking E-Signature Status

### Individual Lender Status

**Per lender:**
- `esignatureStatus`: pending | ESIGN_COMPLETED
- Tracks facility agent's signature for that lender
- Updated individually per lender
- Independent of other lenders

### Aggregate Status

**Overall tracking:**
- `eSignaturePendingCount`: Number of lenders with pending signatures
- `eSignatureStatus`: Aggregate status (pending | ESIGN_COMPLETED)
- Updates when all lenders complete
- Shows overall completion

---

## Best Practices

### For Facility Agents

**Token generation:**
1. Generate promptly: Create tokens soon after approval
2. Verify allocation: Ensure token distribution correct
3. Complete setup: Initialize all lender allocations
4. Monitor status: Track token generation progress

**E-signature process:**
1. Sign for all lenders: Complete per-lender signing
2. Track individual status: Monitor each lender
3. Complete promptly: Keep workflow moving
4. Verify completion: Ensure all signatures done

---

## Common Scenarios

### Scenario 1: Standard Process

1. Funding request approved → Funding notice created
2. Generate tokens → TOKEN_GENERATED
3. Sign for Lender A → Lender A: ESIGN_COMPLETED
4. Sign for Lender B → Lender B: ESIGN_COMPLETED
5. Sign for Lender C → Lender C: ESIGN_COMPLETED
6. All signed → Aggregate: ESIGN_COMPLETED
7. Borrower approves tokens → TOKEN_APPROVED

### Scenario 2: Multiple Lenders

1. Generate tokens → Multiple lenders initialized
2. Sign for each lender individually → Per-lender signing
3. Track individual status → Each lender separately
4. Complete all signatures → Aggregate complete
5. Borrower approves → Proceeds

---

## Troubleshooting

### "Can't generate tokens"
- Check funding notice status is PENDING_TOKEN_GENERATION
- Verify funding request was approved
- Ensure you're the facility agent
- Check API call parameters

### "Can't sign for lender"
- Check tokens have been generated
- Verify funding notice status is TOKEN_GENERATED
- Ensure lender is in lender groups
- Check DocuSign is available

### "Status not updating"
- Wait for webhook processing
- Refresh page
- Verify signing was completed
- Check individual lender status

---

## Key Takeaways

1. Generate tokens first: Create tokens before signing
2. Per-lender signing: Sign for each lender individually
3. Individual tracking: Each lender's status tracked separately
4. Aggregate status: Overall completion tracked
5. Complete process: Finish all lender signatures

Understanding token generation and e-sign helps facility agents effectively manage the token creation and signing process for funding notices.
