# All Pool States Explained

## Overview

This comprehensive guide explains all possible pool statuses and states in the Intain Markets platform. Understanding these states helps you know where your pool is in the workflow and what actions are available.

## Pool Status Values

**Database Collection:** `pool_detail` (MongoDB)

### Created

**What it means:**
- Pool has been created with basic information (via `POST /pools/create` or `POST /pools`)
- Document stored in `pool_detail` collection with `status: 'Created'`
- Initial setup is complete: `poolId` generated (format: `{poolname.slice(0,2)}{issuerOrgName.charAt(0)}{assetclass.charAt(0)}{date.substring(2,4)}{length+1 padded to 3 digits}`), basic fields populated
- Pool is ready for loan mapping and configuration: loans can be mapped via `POST /maploanstopool`

**What you can do:**
- Add loans to the pool
- Edit pool information
- Configure sharing options
- View basic metrics
- Share with other organizations

**Who can see it:**
- Only the issuer who created it

**Next status:**
- Preview (when shared)
- Or remains Created (if not shared)

---

### Preview

**What it means:**
- Pool is being shared with potential market makers and investors
- Pool is in review stage
- Recipients can view and analyze the pool

**What you can do:**
- ✅ Continue adding or removing loans
- ✅ Update pool information
- ✅ Share with additional parties
- ✅ Respond to feedback
- ✅ View updated metrics

**Who can see it:**
- Issuer who created it
- Organizations it's been shared with

**Next status:**
- Mandate Pending (when market maker accepts)
- Or remains Preview (if no mandate)

---

### Mandate Pending

**What it means:**
- Pool has been shared with a market maker (via `POST /pools/:poolId/submit/marketmakers`)
- Status changes to `'Mandate Pending'` when pool is submitted to market maker
- Market maker is reviewing and deciding whether to accept: market maker can accept/reject via `POST /pools/:poolId/acceptance-status`
- Waiting for market maker's decision: `poolShareOptions` object tracks market maker acceptance status
- Database field: `status: 'Mandate Pending'` in `pool_detail` collection
- Database field: `poolShareOptions` object contains market maker acceptance status: `{ marketMakerOrgId: { acceptanceStatus: 'pending' | 'accepted' | 'rejected', ... } }`

**What you can do:**
- View pool details
- See mandate status
- Limited editing (depends on system configuration)
- Communicate with market maker

**Who can see it:**
- Issuer
- Market maker reviewing the mandate

**Next status:**
- Deal (if market maker accepts)
- Preview (if market maker rejects)
- Or remains Mandate Pending (if no decision)

---

### Deal

**What it means:**
- Pool has been finalized and structured: status changes to `'Deal'` when market maker accepts mandate (via `POST /pools/:poolId/acceptance-status` with `acceptanceStatus: 'accepted'`)
- Transaction is committed: pool is finalized, cannot be edited
- Loans are locked in: loans in pool cannot be easily removed
- Database field: `status: 'Deal'` in `pool_detail` collection
- Database field: `poolShareOptions` updated: market maker's `acceptanceStatus: 'accepted'` in `poolShareOptions` object
- This is typically final: pool cannot be edited, read-only access for most operations

**What you can do:**
- View all pool information
- Download reports and documents
- Track deal progress
- View complete audit trail

**What you cannot do:**
- Cannot edit pool information
- Cannot add or remove loans easily
- Cannot change basic details

**Who can see it:**
- All relevant parties (issuer, market maker, investors, servicers, etc.)

**This is final:**
- Deal status is typically final
- Pool is committed and structured
- Ready for execution

---

## Status Transitions

### Forward Progression

**Created → Preview:**
- Happens when you share the pool
- You control when this happens
- Can happen immediately after creation

**Preview → Mandate Pending:**
- Happens when market maker is assigned
- May happen when market maker accepts to review
- Or when you specifically assign market maker

**Mandate Pending → Deal:**
- Happens when market maker accepts the mandate
- Pool is finalized and structured
- Usually requires market maker action

### Backward Transitions

**Deal → Preview:**
- Usually not possible (deal is finalized)

**Mandate Pending → Preview:**
- If market maker rejects or mandate is withdrawn

**Preview → Created:**
- If you stop sharing (depends on system configuration)

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

---

## Status and Permissions

### Editing Permissions

**Created/Preview:**
- Full editing allowed

**Mandate Pending:**
- Limited editing

**Deal:**
- Read-only

### Sharing Permissions

**Created:**
- Can share

**Preview:**
- Can share with more parties

**Mandate Pending:**
- Sharing restricted (under review)

**Deal:**
- Sharing not applicable (already finalized)

### Loan Management

**Created/Preview:**
- Can add/remove loans

**Mandate Pending:**
- Limited changes

**Deal:**
- Loans locked

---

## Best Practices

1. **Understand status before acting**: Check current status before taking actions
2. **Plan your workflow**: Know what status you want to reach and how
3. **Monitor transitions**: Watch for status change notifications
4. **Review history**: Check status history if something seems wrong
5. **Complete before sharing**: Ensure pool is ready before moving to Preview

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

---

## Key Takeaways

1. **Four main statuses**: Created, Preview, Mandate Pending, Deal
2. **Status controls actions**: What you can do depends on status
3. **Status changes are meaningful**: Represent business events
4. **History is preserved**: Every change is recorded
5. **Workflow guides you**: Status progression ensures proper order

Understanding all pool states helps you navigate the platform effectively and know what to expect at each stage of your pool's journey.
