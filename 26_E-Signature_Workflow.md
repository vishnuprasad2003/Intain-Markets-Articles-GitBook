# E-Signature Workflow

## Overview

E-signatures are used throughout the credit facility workflow to digitally sign important documents. The platform supports DocuSign and ZohoSign for electronic signatures, enabling a complete digital workflow without paper documents.

## E-Signature in Credit Facilities

### Where E-Signatures Are Used

**Term Sheets:**
- Borrower signs term sheet
- Required before submission
- Status changes to BorrowerSigned after signing

**Master Commitments:**
- Lender signs master commitment
- Any lender approval activates facility
- E-signature envelope generated after approval

**Funding Notices:**
- Facility agent signs for each lender individually
- Per-lender signing process
- Individual e-signature status tracked

**Batch Self-Certification:**
- Issuer self-certifies batches
- E-signature completion updates verification source

---

## Term Sheet E-Signature

### Process

**Step 1: Initiate Signing**
- Borrower initiates DocuSign from Draft status (via DocuSign/ZohoSign integration in UI)
- DocuSign envelope created with term sheet documents (PDF generated from term sheet data)
- Documents prepared for signing: envelope ID generated, signing URL created
- Envelope request type: `envelopeRequest=termSheetSign`

**Step 2: Sign Documents**
- Borrower receives signing request (embedded signing in UI or email link)
- Reviews documents in DocuSign/ZohoSign interface
- Signs electronically (clicks signature field, applies electronic signature)
- Completes signing process (all required fields signed)

**Step 3: Completion**
- DocuSign/ZohoSign webhook sends completion notification
- System receives webhook (via `GET /docusign/signing-complete?envelopeRequest=termSheetSign&envelopeId=...&termSheetId=...`)
- Database update in `cf_term_sheets` collection:
  - Status changes to `'BorrowerSigned'`
  - `docusignStatus` updated to `'completed'`
  - Signed PDF downloaded from DocuSign/ZohoSign
  - Signed PDF uploaded to IPFS, IPFS hash stored in database
  - Entry added to `statusHistory`: `{ status: 'BorrowerSigned', userId: borrowerId, timestamp: DateUtils.nowUTC(), comments: 'DocuSign completed' }`
- Borrower can preview signed term sheet (via `GET /cf/getTermSheet/:termSheetId`)
- Ready for submission (via `POST /cf/submitTermSheet/:termSheetId`)

### Status Impact

**Before signing:**
- Status: Draft
- Can edit freely
- Cannot submit

**After signing:**
- Status: BorrowerSigned
- Can preview signed version
- Can submit for review
- Limited editing

---

## Master Commitment E-Signature

### Process

**Step 1: Lender Approval**
- Master commitment in PendingLenderApproval status
- Lender reviews facility
- Lender initiates DocuSign
- Signs master commitment

**Step 2: Approval Completion**
- Lender signs via DocuSign
- Status changes to ACTIVE
- Facility becomes operational
- E-signature envelope generated (for documentation)

### Key Points

**Any lender can approve:**
- One lender approval activates facility
- No complex voting required
- Simple approval mechanism

**E-signature generation:**
- Envelope generated after approval
- For documentation purposes
- No additional signing required
- Completes lender status tracking

---

## Funding Notice E-Signature

### Per-Lender Signing

**Important: This is different!**
- Facility agent signs for each lender individually
- Each lender has separate DocuSign envelope
- Individual `esignatureStatus` tracked per lender
- Aggregate status tracks overall completion

### Process

**Step 1: Tokens Generated**
- Funding notice status: `'TOKEN_GENERATED'` (after `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`)
- FT tokens already created on blockchain for borrower
- Each lender in `tokenDistribution` array has `esignatureStatus: 'pending'`
- Ready for facility agent signing (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&fundingNoticeId=...&lenderOrgId=...`)

**Step 2: Facility Agent Signs Per Lender**
- Facility agent initiates DocuSign for Lender A (envelope request type: `fundingNoticeSign`, includes `lenderOrgId` parameter)
- DocuSign envelope created with funding notice documents for Lender A
- Facility agent signs funding notice for Lender A (embedded signing or email-based)
- DocuSign completion webhook received with `lenderOrgId` parameter
- Database update in `cf_funding_notices` collection:
  - Lender A's `esignatureStatus` in `tokenDistribution` array updated to `'ESIGN_COMPLETED'`
  - `eSignaturePendingCount` decremented by 1
  - Signed PDF downloaded and stored in IPFS, IPFS hash stored
  - If `eSignaturePendingCount === 0` (all lenders signed), `eSignatureStatus` updated to `'ESIGN_COMPLETED'`
- Repeat for each lender (separate DocuSign envelope per lender)

**Step 3: Aggregate Status**
- `eSignaturePendingCount` decrements per signing (stored in `cf_funding_notices` document)
- When all lenders signed (`eSignaturePendingCount === 0`), `eSignatureStatus` → `'ESIGN_COMPLETED'`
- Individual statuses remain tracked separately in `tokenDistribution` array (each lender's `esignatureStatus` field)
- Funding notice status remains `'TOKEN_GENERATED'` during per-lender signing (only changes to `'TOKEN_APPROVED'` when borrower approves token transfer)

### Individual Tracking

**Per lender:**
- `esignatureStatus`: pending | ESIGN_COMPLETED
- Tracks facility agent's signature for that lender
- Updated individually per lender
- Independent of other lenders

**Aggregate:**
- `eSignaturePendingCount`: Number remaining
- `eSignatureStatus`: Overall completion status
- Updates when all lenders complete

---

## E-Signature Providers

### DocuSign

**Features:**
- Embedded signing (no email required)
- Webhook-based status updates
- Automatic document download
- IPFS storage integration
- Audit trail download

**Supported workflows:**
- Term sheet signing
- Master commitment signing
- Funding notice signing
- Batch self-certification

### ZohoSign

**Features:**
- Embedded signing
- Webhook-based status updates
- Automatic document download
- IPFS storage integration
- Completion certificate download

**Supported workflows:**
- Term sheet signing
- Master commitment signing
- Funding notice signing
- Batch self-certification

---

## E-Signature Status Tracking

### Status Values

**Pending:**
- E-signature not yet initiated
- Waiting for signing
- Initial state

**In Progress:**
- Signing process started
- Documents sent for signing
- Waiting for completion

**Completed:**
- Signing completed
- Documents signed
- Status updated
- Process complete

### Status Updates

**Automatic updates:**
- Webhook receives completion notification
- Status updates automatically
- Related entity status may change
- Notifications sent

---

## E-Signature Workflow Best Practices

### For Borrowers

1. **Review before signing**: Read documents carefully
2. **Sign promptly**: Complete signing quickly
3. **Verify completion**: Check status updated
4. **Keep records**: Save signed documents

### For Facility Agents

1. **Sign for all lenders**: Complete per-lender signing
2. **Track individual status**: Monitor each lender
3. **Complete promptly**: Keep workflow moving
4. **Verify completion**: Ensure all signatures done

### For Lenders

1. **Review before signing**: Understand what you're signing
2. **Sign promptly**: Complete signing quickly
3. **Verify completion**: Check status updated
4. **Keep records**: Save signed documents

---

## Common Scenarios

### Scenario 1: Term Sheet Signing

1. Borrower creates term sheet → Draft
2. Initiates DocuSign → Signing process
3. Signs documents → Completion
4. Status: BorrowerSigned → Can submit

### Scenario 2: Master Commitment Approval

1. Master commitment: PendingLenderApproval
2. Lender reviews → Initiates DocuSign
3. Lender signs → Approval
4. Status: ACTIVE → Facility operational

### Scenario 3: Funding Notice Signing

1. Tokens generated → TOKEN_GENERATED
2. Facility agent signs for Lender A → Lender A: ESIGN_COMPLETED
3. Facility agent signs for Lender B → Lender B: ESIGN_COMPLETED
4. All lenders signed → Aggregate: ESIGN_COMPLETED
5. Borrower approves tokens → TOKEN_APPROVED

---

## Troubleshooting

### "Can't initiate signing"
- Check entity status allows signing
- Verify you have permission
- Ensure documents are ready
- Check e-signature provider status

### "Signing not completing"
- Check email for signing request
- Verify signing link is valid
- Complete all required fields
- Contact support if stuck

### "Status not updating"
- Wait for webhook processing
- Refresh page
- Check e-signature provider status
- Contact support if persists

---

## Key Takeaways

1. Digital workflow: Complete e-signature process
2. Multiple providers: DocuSign and ZohoSign supported
3. Status tracking: Automatic status updates
4. Per-lender signing: Individual tracking for funding notices
5. Complete audit trail: All signatures recorded

Understanding e-signature workflow helps you navigate the digital signing process and know what to expect at each stage.
