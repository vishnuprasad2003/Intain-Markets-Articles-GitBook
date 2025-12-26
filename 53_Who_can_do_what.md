# Who Can Do What

## Overview

This comprehensive guide explains what each role can and cannot do in the Intain Markets platform. Understanding role permissions helps you know what actions are available to you.

## Issuer (Borrower) Permissions

**Role Validation:** Middleware `requireRole('Issuer')` enforces issuer-only access

### Pools & Loans

**Can do:**
- Create pools (via `POST /pools/create` or `POST /pools`) - requires `requireAuth` and `requireRole('Issuer')` middleware
- Map loans to pools (via `POST /maploanstopool`) - validates issuer organization matches pool's `issuerOrgId`
- Edit pool information (when status allows: `'Created'` or `'Preview'` status) - validates `pool_detail.status` allows editing
- Share pools with other organizations (via `POST /configureShareOptions` or `POST /editPreviewOrganizationShareOptions`) - updates `shareOptions` object in `pool_detail` collection
- Remove loans from pools (via `GET /updateLoanStatus`) - sets `loanPoolStatus: 'Removed'` in `previewstdloantape` collection
- Reinstate removed loans (via `GET /updateLoanStatus`) - sets `loanPoolStatus: ''` (empty string) in `previewstdloantape` collection
- Manage loan statuses - can update `loanPoolStatus` field via `GET /updateLoanStatus` endpoint

**Cannot do:**
- Approve pool mandates (market makers do this)
- Approve their own pools
- Finalize deals (market makers do this)

---

### Credit Facilities

**Can do:**
- Create term sheets (via `POST /cf/createTermSheet`) - requires `requireAuth` and `requireRole('Issuer')` middleware, validates `issuerOrgId` matches user's organization
- Sign term sheets via DocuSign (via DocuSign/ZohoSign integration) - webhook updates status to `'BorrowerSigned'` via `GET /docusign/signing-complete?envelopeRequest=termSheetSign`
- Submit term sheets for review (via `POST /cf/submitTermSheet/:termSheetId`) - validates status is `'BorrowerSigned'`, updates to `'FAReview'`
- Create funding requests (via `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft`) - validates master commitment is `'ACTIVE'`, validates `issuerOrgId` matches
- Approve token transfers (via `POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer`) - validates `issuerId` matches `req.userId`, validates status is `'TOKEN_GENERATED'`
- Respond to change requests - can edit when status is `'CHANGES_REQUESTED'`, can resubmit after making changes

**Cannot do:**
- Approve their own term sheets - `requireRole('Issuer')` middleware blocks access to `POST /cf/acceptTermSheet/:termSheetId` (only `requireRole('Market Maker')` or `requireRole('Facility Agent')` allowed)
- Create master commitments (auto-created) - master commitments are automatically created via `autoCreateMasterCommitment()` function when term sheet status changes to `'Accepted'`
- Approve their own funding requests - `requireRole('Issuer')` middleware blocks access to `POST /cf/funding-requests/:fundingRequestId/approve` (only facility agent can approve)
- Sign funding notices (facility agent signs) - facility agent signs for each lender individually via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign`

---

## Market Maker / Facility Agent Permissions

**Role Validation:** Middleware `requireRole('Market Maker')` or `requireRole('Facility Agent')` enforces access

### Pools

**Can do:**
- ✅ Review pools shared with them (via `GET /getpooloverviewdetails` or `GET /getbdbTiles`) - visibility controlled by `shareOptions` object in `pool_detail` collection, checks if `marketMakerOrgId` matches user's organization
- ✅ Accept or reject pool mandates (via `POST /pools/:poolId/acceptance-status`) - updates `poolShareOptions` object with `acceptanceStatus: 'accepted'` or `'rejected'`, changes pool status to `'Deal'` if accepted
- ✅ Request changes to pools - can provide feedback via `POST /:poolId/feedback` endpoint
- ✅ Structure deals - can finalize pools when mandate accepted
- ✅ Finalize pools as deals - status changes to `'Deal'` when mandate accepted (via `POST /pools/:poolId/acceptance-status`)

**Cannot do:**
- ❌ Create pools (issuers do this)
- ❌ Approve their own mandates

---

### Credit Facilities

**Can do:**
- Review term sheets (via `GET /cf/getTermSheet/:termSheetId`) - can view term sheets with `status: 'FAReview'`
- Approve or reject term sheets (via `POST /cf/acceptTermSheet/:termSheetId` or `POST /cf/rejectTermSheet/:termSheetId`) - requires `requireRole('Market Maker')` or `requireRole('Facility Agent')`, validates status is `'FAReview'`
- Request changes to term sheets (via `POST /cf/requestChanges/:termSheetId`) - changes status to `'CHANGES_REQUESTED'`, increments `revisionNumber`
- Create and configure master commitments (via `POST /cf/createMasterCommitment` and `POST /cf/master-commitments/:masterCommitmentId/auto-save-field`) - master commitments auto-created, facility agent configures via auto-save
- Review funding requests (via `GET /cf/funding-requests/:fundingRequestId`) - can view requests with `status: 'FAReview'`
- Approve or reject funding requests (via `POST /cf/funding-requests/:fundingRequestId/approve` or `POST /cf/funding-requests/:fundingRequestId/reject`) - validates status is `'FAReview'`, approval triggers `generateFundingNotice()`
- Generate tokens (via `PATCH /cf/funding-notices/:fundingNoticeId/token-distribution`) - creates FT tokens on blockchain, changes status to `'TOKEN_GENERATED'`
- Sign funding notices for lenders (via `GET /docusign/signing-complete?envelopeRequest=fundingNoticeSign&lenderOrgId=...`) - signs for each lender individually, updates `esignatureStatus` in `tokenDistribution` array

**Cannot do:**
- Create term sheets (borrowers do this) - `requireRole('Issuer')` middleware blocks access to `POST /cf/createTermSheet` for facility agents
- Approve master commitments as lenders - `requireRole('Lender')` middleware blocks facility agents from `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign`
- Create funding requests (borrowers do this) - `requireRole('Issuer')` middleware blocks access to `POST /cf/funding-requests/:masterCommitmentId/check-or-create-draft` for facility agents
- Approve funding notices economically (lenders do this) - `requireRole('Lender')` middleware blocks facility agents from `PATCH /cf/funding-notices/:fundingNoticeId/:lenderOrgId/status` with `status: 'APPROVED'`

---

## Investor / Lender Permissions

### Pools

**Can do:**
- ✅ Review pool previews shared with them
- ✅ Analyze investment opportunities
- ✅ Express interest in pools
- ✅ Provide feedback on pools

**Cannot do:**
- ❌ Create pools
- ❌ Approve pool mandates
- ❌ Structure deals

---

### Credit Facilities

**Can do:**
- Review master commitments
- Approve master commitments via DocuSign
- Review funding notices
- Approve or reject funding notices
- Confirm fund transfers

**Cannot do:**
- Create term sheets
- Create master commitments
- Create funding requests
- Sign funding notices (facility agent signs)
- Approve token transfers (borrower does this)

---

## Servicer Permissions

### Loans

**Can do:**
- View loans assigned to them
- Update loan statuses
- Manage servicing activities
- Track payment information
- View servicing reports

**Cannot do:**
- Create loans
- Map loans to pools
- Approve batches

---

## Paying Agent Permissions

### Payments

**Can do:**
- View payment schedules
- Process payments
- Manage distributions
- Track payment history
- View payment reports

**Cannot do:**
- Create pools
- Approve facilities
- Make investment decisions

---

## Permission Summary Table

| Action | Issuer | Facility Agent | Lender | Servicer | Paying Agent |
|--------|--------|----------------|--------|----------|--------------|
| Create Pool | Yes | No | No | No | No |
| Create Term Sheet | Yes | No | No | No | No |
| Review Term Sheet | No | Yes | No | No | No |
| Approve Term Sheet | No | Yes | No | No | No |
| Create Master Commitment | No | Yes | No | No | No |
| Approve Master Commitment | No | No | Yes | No | No |
| Create Funding Request | Yes | No | No | No | No |
| Review Funding Request | No | Yes | No | No | No |
| Approve Funding Request | No | Yes | No | No | No |
| Approve Funding Notice | No | No | Yes | No | No |
| Sign Funding Notice | No | Yes | No | No | No |

---

## Understanding Permissions

### Why Permissions Exist

**Purpose:**
- Ensure proper workflow
- Maintain security
- Control access
- Protect all parties
- Enforce business rules

**Benefits:**
- Clear responsibilities
- Proper workflow
- Security maintained
- Quality ensured

---

## Best Practices

1. Know your role: Understand what you can do
2. Check permissions: Verify before taking actions
3. Respect workflow: Don't try to skip steps
4. Ask if unsure: Contact support if unclear
5. Work within role: Use your role's capabilities

---

## Troubleshooting

### "I can't do something I think I should"
- Check your role
- Verify you have permission
- Check item status
- Ensure prerequisites met
- Contact support if needed

### "Action is disabled"
- Check why it's disabled (tooltip)
- Verify status allows action
- Check if prerequisites met
- Review permission requirements

---

## Key Takeaways

1. Role-based permissions: Each role has specific capabilities
2. Clear boundaries: Know what you can and cannot do
3. Workflow respect: Permissions enforce proper workflow
4. Security: Permissions maintain security
5. Collaboration: Different roles work together

Understanding who can do what helps you know your capabilities and work effectively within your role's permissions.
