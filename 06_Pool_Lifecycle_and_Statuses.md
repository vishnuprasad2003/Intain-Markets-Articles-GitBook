---
title: Pool Lifecycle and Statuses
description: Understand the different stages pools go through from creation to deal completion
---

# Pool Lifecycle and Statuses

## Overview

Pools progress through several statuses from creation to final deal completion. Each status represents a specific stage in the pool's journey and determines what actions are available. Understanding these statuses helps you track where your pool is in the process and know what to expect at each stage.

## Reference Details

### Created Status

**What It Means**: The pool has been created with basic information and is visible only to you, the creator.

**What You Can Do**:
- Add or remove loans
- Edit pool information
- Configure sharing settings
- Assign organizations
- Map loans to the pool
- Review pool metrics

**What You Cannot Do**:
- Share with other parties (you can prepare for sharing)
- Submit for mandate (pool must be shared first)

**Who Can See It**: Only you, the issuer who created it.

**Typical Duration**: This status lasts until you share the pool or submit it for review.

### Preview Status

**What It Means**: The pool has been shared with other organizations for review. Recipients can view and analyze the pool.

**What You Can Do**:
- Continue adding or removing loans
- Edit pool information
- Respond to feedback
- Make changes based on feedback
- Share with additional parties
- Submit for mandate review

**What Recipients Can Do**:
- View pool details and metrics
- Analyze loan characteristics
- Provide feedback
- Request changes (if permissions allow)
- Download data (if permissions allow)

**Who Can See It**: You (the issuer) and organizations the pool is shared with (market makers, investors, rating agencies, etc.).

**Typical Duration**: This status lasts until you submit for mandate or the pool progresses to Deal status.

### Mandate Pending Status

**What It Means**: The pool has been submitted to a market maker for mandate review. The market maker is deciding whether to accept the mandate to structure the deal.

**What You Can Do**:
- View the pool
- Wait for market maker decision
- Limited editing (depends on platform configuration)

**What Market Maker Can Do**:
- Review pool details and metrics
- Accept the mandate
- Reject the mandate
- Request changes or provide feedback

**Who Can See It**: You (the issuer) and the assigned market maker.

**Typical Duration**: This status lasts until the market maker makes a decision (accept or reject).

**Possible Outcomes**:
- **Accepted**: Pool moves to Deal status, and market maker proceeds with structuring.
- **Rejected**: Pool may return to Preview status, and you can submit to another market maker.

### Deal Status

**What It Means**: The market maker has accepted the mandate, and the pool is finalized and structured. The transaction is committed.

**What You Can Do**:
- View the pool
- Track the deal
- Limited or no editing (pool is finalized)

**What Other Parties Can Do**:
- View the finalized deal
- Access deal information
- Manage ongoing activities (servicing, payments, etc.)

**Who Can See It**: All relevant parties based on organization assignments (issuer, market maker, investors, servicers, paying agents, etc.).

**Typical Duration**: This is typically the final status for the pool. The deal is complete, and ongoing activities are managed separately.

**Note**: Once a pool reaches Deal status, it's difficult or impossible to revert to earlier statuses. The pool is considered finalized.

## Important Notes

- **Status Progression**: Pools typically progress from Created → Preview → Mandate Pending → Deal. You cannot skip stages or go backwards easily.

- **Status Changes Are Recorded**: Every status change is recorded with who changed it and when, creating a complete audit trail.

- **Status Controls Actions**: The current status determines what actions are available. Disabled buttons usually indicate the status doesn't allow that action.

- **Multiple Statuses Possible**: Depending on the transaction type and workflow, pools may have additional statuses or qualifiers (for example, "Preview - Under Review" or "Deal - Active").

- **Status Badges**: Statuses are displayed as badges or labels, often color-coded (green for completed, yellow for pending, etc.).

- **Cannot Edit After Deal**: Once a pool becomes a Deal, editing is restricted. Make sure all information is correct before finalizing.

- **Market Maker Rejection**: If a market maker rejects a mandate, the pool may return to Preview status, allowing you to submit to another market maker.

- **Status History**: You can view the complete history of status changes, including who changed them and when, by viewing the pool's audit trail or history.

Understanding pool lifecycle and statuses helps you navigate the platform effectively, know what actions are available at each stage, and track your pool's progress from creation to deal completion.
