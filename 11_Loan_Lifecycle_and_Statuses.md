---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where each loan is in the process, know what actions are available, and understand why certain actions are disabled.

## Reference Details

### Unmapped Status

**What It Means**: The loan has been uploaded into the system but is not yet assigned to any pool.

**What You Can Do**:
- View loan details
- Map the loan to a pool
- Edit loan information (if allowed)
- Delete the loan (if allowed)

**What Happens Next**: Loan is ready to be mapped to a pool.

**Typical Duration**: This status lasts until you map the loan to a pool.

### Mapped Status

**What It Means**: The loan has been assigned to a pool and is included in pool calculations.

**What You Can Do**:
- View loan details
- Unmap the loan from the pool
- Update loan status (if allowed)
- View pool metrics that include this loan

**What Happens Next**: Loan can proceed to Submitted status if included in a batch, or remain mapped until pool progresses.

**Typical Duration**: This status lasts until the loan is removed, unmapped, or progresses to Submitted status.

### Submitted Status

**What It Means**: The loan has been included in a batch for verification or other processing.

**What You Can Do**:
- View loan details
- Track submission status
- Wait for verification

**What Happens Next**: Loan proceeds to Verified status after verification is complete.

**Typical Duration**: This status lasts until verification is complete.

### Verified Status

**What It Means**: The loan has been verified and can proceed to next stages (such as tokenization).

**What You Can Do**:
- View loan details
- Proceed to tokenization (if applicable)
- Track loan progress

**What Happens Next**: Loan can proceed to Minted status if tokenization is required.

**Typical Duration**: This status lasts until loan is tokenized or reaches final state.

### Minted Status

**What It Means**: An NFT (non-fungible token) has been created for the loan, and the loan is tokenized.

**What You Can Do**:
- View loan and token details
- Track token information
- Manage tokenized loan

**What Happens Next**: Loan is tokenized and can be used in transactions.

**Typical Duration**: This is typically a final status for tokenized loans.

**Note**: Not all loans are tokenized. This status only applies if tokenization is part of your workflow.

### Removed Status

**What It Means**: The loan has been removed from pool calculations but remains visible in the pool.

**What You Can Do**:
- View loan details
- Reinstate the loan (put it back)
- See why it was removed
- Track removed loans

**What You Cannot Do**:
- Loan doesn't contribute to pool calculations
- Loan is excluded from metrics

**What Happens Next**: Loan can be reinstated if needed, or remain removed.

**Typical Duration**: This status lasts until loan is reinstated or permanently removed.

### Reinstated Status

**What It Means**: The loan was previously removed but has been put back into the pool and is included in calculations again.

**What You Can Do**:
- View loan details
- Loan contributes to pool calculations again
- Manage loan normally

**What Happens Next**: Loan returns to active status and fully participates in the pool.

**Typical Duration**: This status may transition to Mapped or Active status, or remain as Reinstated.

### Active Status (Within Pool)

**What It Means**: The loan is active in the pool and included in all calculations.

**What You Can Do**:
- View loan details
- Loan contributes to pool metrics
- Manage loan normally
- Update loan information (if allowed)

**What Happens Next**: Loan continues to be active unless removed or pool progresses.

**Typical Duration**: This is the normal status for active loans in pools.

### Reconsider Status

**What It Means**: The loan needs review or has been flagged for attention.

**What You Can Do**:
- Review loan details
- Investigate why it's flagged
- Take appropriate action
- Resolve the issue

**What Happens Next**: Loan can return to Active status after review, or be removed if issues are found.

**Typical Duration**: This status lasts until the issue is resolved.

## Important Notes

- **Status Progression**: Loans typically progress from Unmapped → Mapped → Submitted → Verified → Minted (if applicable). Status can also change to Removed and back to Reinstated.

- **Status Controls Actions**: The current status determines what actions are available. Some statuses restrict certain actions.

- **Removed Loans Are Excluded**: Removed loans don't affect pool calculations but remain visible for tracking.

- **Status Changes Are Recorded**: Every status change is recorded with who changed it and when, creating a complete audit trail.

- **Multiple Statuses Possible**: Loans may have multiple status indicators (for example, "Mapped - Active" or "Removed - Under Review").

- **Status Badges**: Statuses are displayed as badges or labels, often color-coded for easy identification.

- **Pool Status Affects Loan Status**: Some loan statuses depend on pool status. For example, you may not be able to map loans if the pool is in Deal status.

- **Status History**: You can view the complete history of status changes, including who changed them and when, by viewing the loan's audit trail or history.

- **Not All Statuses Apply**: Some statuses (like Minted) only apply if certain features are enabled or workflows are used.

Understanding loan lifecycle and statuses helps you effectively manage loans, track their progress, and know what actions are available at each stage.
