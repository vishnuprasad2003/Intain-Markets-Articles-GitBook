---
title: All Pool States Explained
description: Understand all possible pool statuses and what each means
---

# All Pool States Explained

## Overview

This comprehensive reference guide explains all possible pool statuses in the platform. Pools progress through different statuses as they move from creation to deal completion, and the status shown may differ depending on your role and perspective. Understanding these statuses helps you know where a pool is in the workflow, what actions are available, and what to expect next.

## Lifecycle Overview

Pools follow two distinct sharing flows, each with its own status progression:

**Preview Flow (Share Button)**
```
Created → Preview → (recipient sees: Mandate Pending) → (after accept: Under Review) → Deal
```

**Start Deal Flow**
```
Created/Preview → Deal → (recipient sees: Ready for Deal) → (after accept: Deal confirmed)
```

The issuer's view shows the pool status (Created, Preview, Deal). Recipients see different status indicators depending on whether they received a Preview share or a Start Deal invitation, and whether they've accepted or rejected.

**Key Principle**: Pool status controls what actions are available and what editing is permitted. As pools progress toward Deal, editing becomes increasingly restricted.

## Status Meanings

### Pool Statuses (Issuer Perspective)

**Created**

The pool has been created with basic information and is visible only to the issuer who created it. This is the initial stage where the issuer prepares the pool before sharing with anyone.

- **Who sees this**: Only the issuer who created the pool
- **Editing**: Full editing capabilities—can modify pool details, organization assignments, map/unmap loans, upload loan tapes
- **Available actions**: Edit Pool Details, Edit Loan Tape, Share, map loans from Loan Registry
- **Next step**: Share with organizations using the Share button, or wait to Start Deal after prerequisites are met

**Preview**

The pool has been shared with other organizations using the Share button. Recipients can view and analyze the pool, and the issuer can continue making changes based on feedback.

- **Who sees this**: Issuer sees "Preview" status; recipients see "Mandate Pending" or "Under Review" depending on acceptance
- **Editing**: Issuer retains full editing capabilities—can still modify pool, add/remove loans, respond to feedback
- **Available actions**: Edit Pool Details, Edit Loan Tape, Share (with additional orgs), manage sharing permissions, Start Deal (when prerequisites met)
- **Next step**: Wait for recipient decisions, respond to feedback, proceed to Start Deal when ready

**Deal**

The pool has reached the committed deal stage. Either the issuer initiated Start Deal and it was accepted, or the workflow has progressed to deal commitment. Structural editing is restricted.

- **Who sees this**: All parties see "Deal" status (recipients who accepted Start Deal see "Ready for Deal" before accepting, then "Deal" after)
- **Editing**: Structural editing is restricted—pool composition is locked
- **Available actions**: View pool details, proceed with deal structuring and downstream activities
- **Next step**: Deal structuring, investor allocation, documentation, closing

### Recipient-View Statuses

**Mandate Pending**

This is what recipients (market makers, investors, rating agencies) see when a pool has been shared with them through Preview sharing. The recipient has not yet made an Accept/Reject decision.

- **Who sees this**: Recipients who received a Preview share but haven't decided yet
- **Available actions**: View pool details, Accept, Reject
- **Feedback**: Market makers cannot provide feedback until they accept
- **Next step**: Make Accept or Reject decision

**Under Review**

This is what market makers see after they accept a Preview share. The market maker has committed to reviewing the pool and can now provide feedback.

- **Who sees this**: Market makers who accepted a Preview mandate
- **Available actions**: View pool details, provide pool-level feedback, provide loan-level feedback, request loan removals, share with investors
- **Editing**: Issuer still has editing rights; market maker can influence through feedback
- **Next step**: Work with issuer on pool refinement, prepare for Start Deal

**Ready for Deal**

This is what recipients see when the issuer has initiated Start Deal. The pool is finalized (prerequisites met, typically all loans NFT-minted) and ready for deal commitment.

- **Who sees this**: Recipients who received a Start Deal invitation but haven't decided yet
- **Available actions**: View pool details, Accept, Reject
- **Next step**: Make Accept or Reject decision; acceptance confirms the deal

### Loan Statuses Within Pools

Loans mapped to pools have their own status indicators:

**Mapped**

The loan has been mapped to the pool from the Loan Registry and is part of the pool's composition.

- Loan contributes to pool metrics (balance, counts, weighted averages)
- Loan appears in the Loans tab and Loan Tape section
- Loan can be subject to removal requests

**Pending**

The loan is mapped to a pool, but the market maker hasn't yet accepted the Preview mandate.

- Loan is in a holding state awaiting mandate decision
- If market maker accepts, loan status progresses to Accepted

**Accepted**

The loan's inclusion in the pool has been confirmed after a market maker accepts the Preview mandate.

- All loans in the pool move to Accepted status when market maker accepts
- Loan is confirmed as part of the pool composition

**Under Reconsider / Reconsider**

A market maker or investor has requested removal of this loan. The issuer is deciding whether to accept or reject the removal request.

- Market maker/investor view shows: "Under Reconsider"
- Issuer view shows: "Reconsider" with tick (accept) and cross (reject) icons
- Loan remains in calculations until issuer makes decision

**Removed**

The loan has been removed from the pool after the issuer accepted a removal request.

- Loan is excluded from pool calculations (metrics no longer include this loan)
- Loan remains visible in the pool for tracking purposes
- Loan can potentially be reinstated if needed

## What Each Status Indicates

### Created Status Indicates

- You (as issuer) are still preparing the pool privately
- No other organization can see the pool yet
- You have complete control over pool composition and settings
- The pool is in its early preparation phase
- You should complete setup, loan mapping, and configuration before sharing
- This is the right time to ensure pool name, asset class, transaction type, and organization assignments are correct

### Preview Status Indicates

- The pool is being reviewed by other organizations
- Collaboration has begun—recipients can view and analyze
- You (as issuer) still have full editing capabilities
- Feedback may be coming from recipients who have accepted
- The pool is moving toward deal readiness but not yet committed
- This is the phase for iteration and refinement based on feedback

### Mandate Pending Indicates (Recipient View)

- You (as recipient) have received a Preview share and need to decide
- You can view pool details to evaluate before deciding
- Accept will show you as Under Review and enable feedback
- Reject will decline the mandate; issuer may re-share or work with others
- Market makers: you cannot provide feedback until you accept

### Under Review Indicates (Market Maker View)

- You (as market maker) have accepted the Preview mandate
- You can now provide feedback at pool and loan levels
- You can request loan removals if you believe certain loans should be excluded
- You can share the pool with investors
- The issuer may make changes based on your feedback
- The pool is being refined collaboratively before deal commitment

### Ready for Deal Indicates (Recipient View)

- The issuer has initiated Start Deal
- Prerequisites have been met (typically all loans NFT-minted)
- The pool composition is finalized
- Your Accept decision commits the deal
- Reject will decline; issuer may work with other parties
- This is the final decision point before deal commitment

### Deal Status Indicates

- The transaction is finalized and committed
- Structural editing is restricted
- The accepting market maker proceeds with deal structuring
- Downstream activities (investor allocation, documentation, closing) proceed
- The pool has reached its final committed state

### Removed Loan Status Indicates

- The loan was removed from the pool after issuer accepted a removal request
- The loan is excluded from pool calculations
- Pool metrics have been updated to exclude this loan
- The loan remains visible for tracking and audit purposes
- The loan can potentially be reinstated if circumstances change

## Status Transitions Summary

| From Status | Action | To Status | Who |
|-------------|--------|-----------|-----|
| (none) | Create Pool | Created | Issuer |
| Created | Share (Preview) | Preview | Issuer |
| Created/Preview | Start Deal | Deal | Issuer |
| Mandate Pending | Accept | Under Review | Market Maker |
| Mandate Pending | Reject | Mandate Pending (can re-share) | Market Maker |
| Ready for Deal | Accept | Deal (confirmed) | Market Maker |
| Ready for Deal | Reject | Ready for Deal (can re-share) | Market Maker |
| Mapped (loan) | MM requests removal | Under Reconsider | Market Maker/Investor |
| Under Reconsider (loan) | Issuer accepts | Removed | Issuer |
| Under Reconsider (loan) | Issuer rejects | Mapped/Accepted | Issuer |

## Editing Rights by Status

| Pool Status | Issuer Edit Rights | Recipient Actions |
|-------------|-------------------|-------------------|
| Created | Full editing | (not visible to recipients) |
| Preview | Full editing | View, Accept/Reject, Feedback (after accept) |
| Under Review (MM view) | Full editing | Feedback, Loan removal requests, Share to investors |
| Deal | Restricted | View, Deal structuring activities |

Understanding these statuses helps you navigate the pool workflow effectively, know what actions are available at each stage, and collaborate with other parties to move pools toward successful deal completion.
