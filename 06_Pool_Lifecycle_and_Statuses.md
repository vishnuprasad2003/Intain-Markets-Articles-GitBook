# Pool Lifecycle & Statuses

## Overview

A pool goes through several stages from creation to final deal completion. Understanding these statuses helps you know where your pool is in the process and what actions are available.

## Pool Status Flow

### Complete Lifecycle

```
Created → Preview → Mandate Pending → Deal
```

Each status represents a specific stage in the pool's journey.

---

## Status Definitions

### 1. Created

**What it means:**
- Pool has been created with basic information in MongoDB `pool_detail` collection
- Initial setup is complete with `status: "Created"`
- Pool starts with `numberofloans: 0`, `originalbalance: 0`, `currentbalance: 0`
- `shareOptions: {}` and `poolShareOptions: {}` are empty objects
- Pool is ready for loan mapping and configuration

**What you can do:**
- Add loans to the pool (map loans using `/maploanstopool` endpoint)
- Edit pool information (update description, organization assignments via `/updatePoolDetails`)
- Configure sharing options (set `shareOptions` for preview sharing)
- View basic metrics (though metrics will be zero until loans are mapped)
- Share with other organizations (configure `shareOptions` to grant access)

**What you cannot do:**
- Cannot finalize as a deal yet (must submit to market maker first via `/pools/:poolId/submit/marketmakers`)
- Cannot see pool in market maker/investor views (not shared yet)

**Who can see it:**
- Only the issuer who created it (visible via `/issuers/:issuerOrgId/pools` endpoint)
- Pool is stored with `issuerOrgId` field identifying the owner

**Next steps:**
- Map loans to the pool (loans will have `poolid` field set, `Status` changes to "Mapped", `loanPoolStatus` set to "Pending")
- Complete pool configuration (add organizations, set description)
- Share as preview when ready (configure `shareOptions` to make visible to other organizations)

---

### 2. Preview

**What it means:**
- Pool is being shared with potential market makers and investors
- Pool status remains "Created" or may show as "Preview" in UI (status field in database)
- Organizations are added to `shareOptions` object with permissions (`allowFeedBack`, `allowDownload`)
- Recipients can view and analyze the pool via role-specific endpoints

**What you can do:**
- Continue adding or removing loans (loans can still be mapped/unmapped)
- Update pool information (description, organization assignments)
- Share with additional parties (add more organizations to `shareOptions` via `/configureShareOptions`)
- Respond to feedback (view and respond to pool-level or loan-level feedback)
- View updated metrics (metrics recalculate as loans are added/removed)
- Edit share options (modify `allowFeedBack` and `allowDownload` per organization via `/editPreviewOrganizationShareOptions`)

**What you cannot do:**
- Cannot finalize as deal (must submit to market maker first, which changes status to "Deal")
- Cannot see pool in market maker's "Deal" view (only in preview view until mandate accepted)

**Who can see it:**
- Issuer who created it (via `/issuers/:issuerOrgId/pools`)
- Market makers (via `/previewunderwriterpool?marketMakerOrgId=...&mailId=...`)
- Investors (via `/previewinvestorpool?investorOrgId=...&mailId=...`)
- Rating agencies (via `/getPreviewPoolsByRatingAgencyOrg?ratingAgencyOrgId=...&mailid=...`)
- Organizations listed in `shareOptions` object

**How Sharing Works:**
- Issuer configures `shareOptions` object: `{ [orgId]: { allowFeedBack: true/false, allowDownload: true/false, orgName: "...", orgType: "..." } }`
- Recipients can view pool details via `/getbypoolid?poolId=...`
- Recipients can view loans via `/getpreviewstdloantapeusinglatestdate?poolId=...&asOfDate=...`
- Recipients can provide feedback if `allowFeedBack: true` via `/:poolId/feedback` endpoint

**Next steps:**
- Wait for market maker to accept mandate (changes `poolShareOptions[orgId].acceptanceStatus` to "Accepted")
- Or continue sharing with more parties (add more organizations to `shareOptions`)
- Address any feedback received (view via `/:poolId/feedback` endpoint)

---

### 3. Mandate Pending

**What it means:**
- Pool has been submitted to market maker via `/pools/:poolId/submit/marketmakers` endpoint
- Pool status changes to "Deal" in database
- `poolShareOptions` object is created/updated with `acceptanceStatus: "pending"` for each market maker
- Market maker is reviewing and deciding whether to accept the mandate

**What you can do:**
- View pool details (via `/getbypoolid?poolId=...`)
- See mandate status (check `poolShareOptions[marketMakerOrgId].acceptanceStatus` field)
- Limited editing (pool status is "Deal", but some fields may still be editable)
- Communicate with market maker (via feedback system at `/:poolId/feedback`)
- View loans (via `/getpreviewstdloantapeusinglatestdate`)

**What you cannot do:**
- Cannot easily change pool basic information (status is "Deal")
- Cannot remove market makers easily (they're in `poolShareOptions` with pending status)
- Cannot share with other market makers for mandate (one mandate process at a time per pool)

**Who can see it:**
- Issuer (via `/issuers/:issuerOrgId/pools` - sees pool with "Deal" status)
- Market maker reviewing the mandate (via `/marketmakers/:marketMakerOrgId/pools` - sees pools where they're assigned)
- Market maker can also see via `/marketmakers/:marketMakerOrgId/pools/both-options` (includes pools in both `poolShareOptions` and `shareOptions`)

**Mandate Acceptance Process:**
- Market maker reviews pool and decides
- Market maker updates acceptance status via `/pools/:poolId/acceptance-status` endpoint
- **Accept**: `poolShareOptions[orgId].acceptanceStatus` changes to "Accepted"
- **Reject**: `poolShareOptions[orgId].acceptanceStatus` changes to "Rejected"
- **Request Changes**: Market maker can provide feedback via `/:poolId/feedback` endpoint

**Next steps:**
- Wait for market maker decision:
  - Accept: `acceptanceStatus` becomes "Accepted", pool moves toward deal structuring
  - Reject: `acceptanceStatus` becomes "Rejected", pool may return to available status
  - Request Changes: Feedback added, issuer can address and resubmit

---

### 4. Deal

**What it means:**
- Pool status is "Deal" in database (set when submitted to market maker via `/pools/:poolId/submit/marketmakers`)
- Market maker has accepted the mandate (`poolShareOptions[orgId].acceptanceStatus: "Accepted"`)
- Transaction is committed and structured
- Loans are mapped and included in pool calculations

**What you can do:**
- View all pool information (via `/getbypoolid?poolId=...`)
- Download reports and documents (loan tapes via `/downloadpreviewstdloantape`)
- Track deal progress (view status, metrics, loan counts)
- View complete audit trail (status history, feedback history)
- View pool documents (via `/getPoolDocument?poolId=...`)
- View loans with filters (via `/LoantapeDynamicFilters` with complex filters)

**What you cannot do:**
- Cannot edit pool basic information easily (status is "Deal", updates restricted)
- Cannot easily add or remove loans (loans can be removed but affects deal structure)
- Cannot change pool name, asset class, or transaction type (core fields locked)
- Cannot delete pool (pool deletion clears all fields except `poolId` and `_id`, unmaps all loans)

**Who can see it:**
- Issuer (via `/issuers/:issuerOrgId/pools`)
- Market maker (via `/marketmakers/:marketMakerOrgId/pools` or `/marketmakers/:marketMakerOrgId/pools/both-options`)
- Investors (via `/investors/:investorOrgId/pools/both-options` if shared)
- Servicers (if assigned in `servicerOrgId` array)
- Paying agents (if assigned in `payingAgentOrgId` array)
- Rating agencies (if assigned in `ratingAgencyOrgId` array)

**Deal Structure:**
- Pool has `status: "Deal"`
- `poolShareOptions` contains market maker acceptance status
- `shareOptions` contains preview sharing permissions
- Loans are in PostgreSQL `poolloantape` table for analytics
- Pool metrics are calculated from active loans

**Next steps:**
- Deal execution and funding (proceed with transaction)
- Ongoing servicing and management (servicers manage loans)
- Payment processing (paying agents handle distributions)

---

## Status Transitions

### How Status Changes

**Created → Preview**
- Happens when you share the pool with other organizations
- You control when this happens
- Can happen immediately after creation

**Preview → Mandate Pending**
- Happens when a market maker is assigned and reviewing
- May happen automatically when market maker accepts to review
- Or when you specifically assign a market maker

**Mandate Pending → Deal**
- Happens when market maker accepts the mandate
- Pool is finalized and structured
- Usually requires market maker action

**Backward Transitions**
- **Deal → Preview**: Usually not possible (deal is finalized)
- **Mandate Pending → Preview**: If market maker rejects or mandate is withdrawn
- **Preview → Created**: If you stop sharing (depends on system configuration)

---

## Understanding Status Messages

### Common Status Indicators

**"Pool Created Successfully"**
- Pool is in Created status
- Ready for configuration

**"Pool Shared for Preview"**
- Pool is in Preview status
- Recipients can view it

**"Waiting for Market Maker Response"**
- Pool is in Mandate Pending status
- Market maker is reviewing

**"Deal Finalized"**
- Pool is in Deal status
- Transaction is committed

### Status Badges

The platform shows status with color-coded badges:
- Blue/Green: Active, in progress
- Yellow/Orange: Waiting, pending action
- Gray: Finalized, completed
- Red: Rejected, stopped

---

## Status and Permissions

### What Status Controls

**Editing Permissions**
- Created/Preview: Full editing allowed
- Mandate Pending: Limited editing
- Deal: Read-only

**Sharing Permissions**
- Created: Can share
- Preview: Can share with more parties
- Mandate Pending: Sharing restricted (under review)
- Deal: Sharing not applicable (already finalized)

**Loan Management**
- Created/Preview: Can add/remove loans
- Mandate Pending: Limited changes
- Deal: Loans locked

---

## Status History

### Viewing Status Changes

You can see:
- Current status: Displayed prominently
- Status history: Complete list of all status changes
- Who changed it: User or system that made the change
- When it changed: Timestamp of the change
- Why it changed: Reason or trigger (if applicable)

### Why Status History Matters

- **Audit trail**: Complete record of pool progression
- **Understanding**: See how pool reached current state
- **Troubleshooting**: Identify when issues occurred
- **Compliance**: Meet regulatory requirements

---

## Common Scenarios

### Scenario 1: Quick Preview Sharing

1. Create pool → **Created**
2. Immediately share with investors → **Preview**
3. Continue adding loans → Still **Preview**
4. Market maker accepts → **Mandate Pending**
5. Deal finalized → **Deal**

### Scenario 2: Careful Preparation

1. Create pool → **Created**
2. Add all loans and review metrics → Still **Created**
3. When satisfied, share → **Preview**
4. Market maker reviews → **Mandate Pending**
5. Deal completed → **Deal**

### Scenario 3: Market Maker Rejection

1. Pool in **Preview**
2. Market maker assigned → **Mandate Pending**
3. Market maker rejects → Back to **Preview**
4. Share with different market maker → **Mandate Pending** again
5. New market maker accepts → **Deal**

---

## Best Practices

1. Understand status before acting: Check current status before taking actions
2. Plan your workflow: Know what status you want to reach and how
3. Monitor transitions: Watch for status change notifications
4. Review history: Check status history if something seems wrong
5. Complete before sharing: Ensure pool is ready before moving to Preview
6. Respond promptly: Address feedback quickly to keep workflow moving

---

## Troubleshooting

### "Why can't I edit my pool?"
- Check the status - Deal status prevents editing
- Mandate Pending may have limited editing

### "Why isn't my pool visible to investors?"
- Ensure pool is in Preview status
- Verify you've shared it with the right organizations
- Check sharing permissions

### "How do I change status back?"
- Usually can't go backward from Deal
- Mandate Pending can return to Preview if rejected
- Contact support if you need to revert status

### "Status changed unexpectedly"
- Check notifications for who changed it
- Review status history for details
- Some status changes are automatic (e.g., when market maker accepts)

Understanding pool lifecycle and statuses helps you navigate the platform effectively and know what to expect at each stage of your pool's journey.
