# Signature Visibility

## Overview

E-signatures are used throughout the platform for document signing. Understanding signature visibility helps you know who can see signatures, when they're visible, and how to access signed documents.

## Where Signatures Are Used

### Term Sheets

**Borrower signature:**
- Borrower signs term sheet via DocuSign/ZohoSign (envelope request type: `termSheetSign`)
- DocuSign completion webhook received (via `GET /docusign/signing-complete?envelopeRequest=termSheetSign&envelopeId=...&termSheetId=...`)
- Database update in `cf_term_sheets` collection:
  - Status changes to `'BorrowerSigned'`
  - `docusignStatus` updated to `'completed'`
  - Signed PDF downloaded from DocuSign/ZohoSign
  - Signed PDF uploaded to IPFS, IPFS hash stored in database
  - Entry added to `statusHistory`: `{ status: 'BorrowerSigned', userId: borrowerId, timestamp: Date, comments: 'DocuSign completed' }`
- Signature visible after completion: Signed document accessible via IPFS hash
- Signed document stored: IPFS hash stored in `cf_term_sheets` document, document retrievable via IPFS
- Available to borrower and facility agent: Both can access signed document via IPFS hash

### Master Commitments

**Lender signature:**
- Lender signs master commitment via DocuSign
- Signature visible after completion
- Signed document stored
- Available to lender and facility agent

### Funding Notices

**Facility agent signature:**
- Facility agent signs for each lender individually (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&fundingNoticeId=...&lenderOrgId=...`)
- Per-lender signatures tracked: Each lender's `esignatureStatus` in `tokenDistribution` array updated individually to `'ESIGN_COMPLETED'`
- Database update in `cf_funding_notices` collection:
  - Individual lender's `esignatureStatus` in `tokenDistribution` array → `'ESIGN_COMPLETED'`
  - `eSignaturePendingCount` decremented by 1
  - Signed PDF downloaded from DocuSign/ZohoSign and stored in IPFS, IPFS hash stored
  - Entry added to `actionHistory`: `{ action: 'E-Signature Completed', userId: facilityAgentId, timestamp: Date, comments: 'E-signature completed for lender', details: { lenderOrgId, esignatureStatus: 'ESIGN_COMPLETED' } }`
- Signed documents stored: IPFS hash stored per lender, documents retrievable via IPFS
- Available to relevant parties: Facility agent, borrower, and specific lender can access their signed document via IPFS hash

### Batch Self-Certification

**Issuer signature:**
- Issuer signs batch certification
- Signature visible after completion
- Signed document stored
- Available to issuer and verification agent

---

## Signature Visibility

### Who Can See Signatures

**After signing:**
- Signer can see their signature
- Reviewing party can see signature
- Authorized parties can see signature
- Stored for audit purposes

**Examples:**
- Borrower sees their term sheet signature
- Facility agent sees borrower's signature
- Lender sees their master commitment signature
- Facility agent sees lender signatures

---

### When Signatures Are Visible

**Visibility timing:**
- After DocuSign completion
- When signing process completes
- Immediately after signing
- Available in document view

**Status impact:**
- Signatures visible after status updates
- Document status reflects signing
- Signed documents accessible
- Audit trail includes signatures

---

## Accessing Signed Documents

### How to Access

**Methods:**
1. Navigate to item details page
2. Go to Documents section
3. Look for signed documents
4. Click to view or download
5. See signature details

### What You'll See

**Signed document:**
- Complete document with signatures
- Signature fields completed
- Signer information
- Signing timestamp
- Document completion certificate

---

## Signature Details

### What's Visible

**Signature information:**
- Signer name
- Signing date and time
- Signature method (DocuSign/ZohoSign)
- Document version
- Completion status

**Document details:**
- Complete signed document
- All signature fields
- Audit trail
- Completion certificate
- IPFS storage reference

---

## Signature Tracking

### Status Tracking

**Signature status:**
- Pending: Not yet signed
- In Progress: Signing process started
- Completed: Signing finished
- Visible: Signature available

**Status updates:**
- Automatic when signing completes
- Webhook updates status
- Document becomes available
- Signature visible

---

## Best Practices

1. **Verify signatures**: Check signatures after completion
2. **Download copies**: Save signed documents
3. **Review details**: Verify signer information
4. **Track status**: Monitor signature completion
5. **Keep records**: Maintain signed document copies

---

## Common Scenarios

### Scenario 1: Term Sheet Signing

1. Borrower initiates DocuSign → Signing process
2. Borrower signs → Signature completed
3. Signature visible → Borrower and facility agent see it
4. Signed document stored → Available for review

### Scenario 2: Master Commitment Signing

1. Lender initiates DocuSign → Signing process
2. Lender signs → Signature completed
3. Signature visible → Lender and facility agent see it
4. Signed document stored → Available for audit

---

## Troubleshooting

### "Can't see signature"
- Check if signing completed
- Verify document status
- Refresh page
- Check document section
- Contact support if missing

### "Signature not showing"
- Wait for webhook processing
- Check document status
- Verify signing completed
- Refresh page
- Contact support if issue persists

---

## Key Takeaways

1. **Multiple uses**: Signatures used throughout platform
2. **Visible after completion**: Signatures visible when signing done
3. **Accessible documents**: Signed documents available for viewing
4. **Complete details**: Signer, date, method all visible
5. **Audit trail**: Signatures part of complete audit trail

Understanding signature visibility helps you know when and how to access signed documents and verify signature completion.
