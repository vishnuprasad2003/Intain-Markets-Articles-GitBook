---
title: Enabled vs Disabled Actions
description: Understand why actions are enabled or disabled in Intain Markets and what you can do about it
---

# Enabled vs Disabled Actions

## Overview

Intain Markets automatically enables or disables actions based on your role, the item's status, and whether prerequisites are met. Understanding why actions are enabled or disabled helps you know what you can do and what needs to happen before you can proceed.

## Platform-Specific Examples

### Pool Actions by Status

**Created Status** - As an issuer, you can:
- Edit pool information
- Add or remove loans
- Share the pool with other organizations
- Submit pool for mandate

**Preview Status** - As an issuer, you can:
- Continue editing the pool
- Respond to feedback
- Share with additional organizations
- Submit pool for mandate

**Preview Status** - As a market maker, you can:
- View pool details
- Provide feedback
- Accept or reject mandate
- Cannot edit the pool (only issuer can edit)

**Mandate Pending Status** - As an issuer, you can:
- View pool details
- Cannot edit (waiting for market maker decision)
- Cannot share (pool is committed to market maker)

**Mandate Pending Status** - As a market maker, you can:
- Review pool details
- Accept or reject mandate
- Cannot edit the pool

**Deal Status** - As an issuer, you can:
- View pool details
- Cannot edit (pool is finalized)
- Cannot share (deal is committed)

### Term Sheet Actions by Status

**Draft Status** - As a borrower, you can:
- Edit all term sheet fields
- Upload or update documents
- Click "Create Draft" to initiate e-signature
- Cannot submit (must sign first)

**BorrowerSigned Status** - As a borrower, you can:
- Preview the signed term sheet
- Submit for facility agent review
- Cannot edit (must request changes if needed)

**FAReview Status** - As a borrower, you can:
- View term sheet details
- Cannot edit (waiting for facility agent decision)
- Cannot submit (already submitted)

**FAReview Status** - As a facility agent, you can:
- Review term sheet details
- Approve, reject, or request changes
- Cannot edit (borrower must make changes)

**CHANGES_REQUESTED Status** - As a borrower, you can:
- Edit term sheet fields
- Update documents
- Click "Update" to re-sign and resubmit

**Accepted Status** - As a borrower, you can:
- View term sheet details
- Cannot edit (term sheet is approved)
- Master commitment is automatically created

### Master Commitment Actions by Status

**Draft Status** - As a facility agent, you can:
- Edit all facility configuration fields
- Add or remove lenders
- Configure collateral rules
- Set up borrowing base calculations
- Submit for lender approval
- Cannot create funding requests (facility not active)

**PendingLenderApproval Status** - As a facility agent, you can:
- View facility details
- Cannot edit (waiting for lender approval)
- Cannot create funding requests (facility not active)

**PendingLenderApproval Status** - As a lender, you can:
- Review master commitment details
- Approve via e-signature
- Cannot edit (facility agent configures)

**ACTIVE Status** - As a borrower, you can:
- Create funding requests
- View facility details and borrowing capacity
- Cannot edit facility structure

**ACTIVE Status** - As a facility agent, you can:
- Review funding requests
- Approve or reject funding requests
- Generate tokens for funding notices
- Cannot edit facility structure (must create new term sheet)

### Funding Request Actions by Status

**DRAFT Status** - As a borrower, you can:
- Edit funding request details
- Update drawdown amount
- Upload or update supporting documents
- Submit for facility agent review
- Cannot approve (facility agent approves)

**FAReview Status** - As a borrower, you can:
- View funding request details
- Cannot edit (waiting for facility agent decision)
- Cannot submit (already submitted)

**FAReview Status** - As a facility agent, you can:
- Review funding request details
- Approve, reject, or request changes
- Cannot edit (borrower must make changes)

### Funding Notice Actions by Status

**PENDING_TOKEN_GENERATION Status** - As a facility agent, you can:
- Configure token distribution
- Generate tokens for borrower
- Cannot send to lenders (tokens must be generated first)

**TOKEN_GENERATED Status** - As a borrower, you can:
- Review token details
- Approve token transfer to Intain admin wallet
- Cannot proceed (must approve tokens first)

**TOKEN_GENERATED Status** - As a facility agent, you can:
- Sign funding notice for lenders
- Cannot send to lenders (borrower must approve tokens first)

**TOKEN_APPROVED Status** - As a lender, you can:
- Review funding notice details
- Approve or reject drawdown
- Confirm fund transfer after approval
- Cannot approve tokens (borrower already approved)

## Common Reasons Actions Are Disabled

**Wrong Status** - The item isn't in the correct status for this action. For example:
- You cannot submit a term sheet in Draft status (must sign first)
- You cannot create funding requests when master commitment is Draft (must be ACTIVE)
- You cannot approve a funding request when it's in DRAFT status (must be FAReview)

**Missing Prerequisites** - Required steps haven't been completed:
- Term sheet must be signed before submission
- Master commitment must be ACTIVE before creating funding requests
- Tokens must be generated before borrower can approve transfer
- Borrower must approve tokens before lenders can review funding notice

**Waiting for Another Party** - Another party needs to act first:
- Borrower must submit term sheet before facility agent can review
- Facility agent must approve term sheet before master commitment is created
- Facility agent must approve funding request before funding notice is generated
- Borrower must approve tokens before lenders can review funding notice

**Role Permissions** - Your role doesn't have permission:
- Only borrowers can create term sheets and funding requests
- Only facility agents can approve term sheets and funding requests
- Only lenders can approve master commitments and funding notices
- Only issuers can edit pools in Created or Preview status

**Action Already Completed** - The action was already taken:
- Term sheet already submitted (cannot submit again)
- Master commitment already approved (cannot approve again)
- Funding request already approved (cannot approve again)

## How to Enable Actions

**Check Status** - Verify the item is in the correct status for your desired action. Status badges show the current status.

**Complete Prerequisites** - Ensure all required steps are complete:
- Fill all required fields
- Upload required documents
- Complete e-signatures when required
- Wait for previous workflow steps to complete

**Verify Your Role** - Confirm you're logged in with the correct role that has permission for the action.

**Wait for Other Parties** - If waiting for another party, check the item status and notifications to see what's pending.

**Check Tooltips** - Hover over disabled buttons to see tooltips explaining why they're disabled.

## Important Notes

**Status Controls Everything** - Status is the primary factor determining action availability. Each status enables specific actions and disables others.

**Role Determines Access** - Your role determines what actions you can take. Even if status allows an action, you may not have permission based on your role.

**Workflow Order Matters** - Actions must happen in the correct sequence. You cannot skip steps or proceed out of order.

**Prerequisites Are Required** - All prerequisites must be met before actions are enabled. Partial completion keeps actions disabled.

**Tooltips Explain Restrictions** - Disabled buttons show tooltips explaining why they're disabled. Check these tooltips to understand what's needed.

**Status Changes Enable Actions** - When status changes, new actions become available. Monitor status changes to see when actions become enabled.

**Individual Tracking** - Each user's permissions and access are tracked individually. Your enabled/disabled actions reflect your specific role and access.

**Complete Requirements** - All requirements must be met before actions are enabled. Missing any requirement keeps actions disabled.

Understanding why actions are enabled or disabled helps you navigate the platform effectively and know what needs to happen before you can proceed with your desired actions.
