---
title: Loan Rejection and Reinstatement
description: Learn how to remove loans from pools and put them back when needed
---

# Loan Rejection and Reinstatement

## Overview

Sometimes loans need to be removed from pools temporarily or permanently. The platform allows you to reject loans (remove them from pool calculations) and reinstate them (put them back into the pool) when appropriate. This process helps you maintain pool quality, address data issues, and adjust pool composition as needed.

## Who Can Use This

- Issuers who manage pools and loans and need to adjust pool composition
- Market Makers who review pools and may suggest loan removal through feedback

## When This Is Used

Use loan rejection when:
- A loan doesn't meet pool criteria or requirements
- Data quality issues are identified that need correction
- Loans need correction before they can be included
- Pool requirements change and some loans no longer fit
- You need to adjust pool composition or metrics
- Market makers or investors flag loans for removal through feedback
- Compliance issues are identified with specific loans

Use loan reinstatement when:
- Issues with removed loans have been resolved
- Data has been corrected and loan is now eligible
- Pool requirements change and previously removed loans now fit
- You decide to include loans that were removed earlier
- Feedback suggests reinstating specific loans

## Step-by-Step Process

### Rejecting (Removing) a Loan

1. **Identify the Loan to Remove**
   - Navigate to the pool's loan list or loan details page
   - Find the loan you want to remove
   - Review loan details to confirm it should be removed
   - Check why the loan should be removed (data issue, doesn't meet criteria, etc.)

2. **Access Loan Status Update**
   - Select the loan you want to remove
   - Find the status update or loan management section
   - Look for options to update loan status
   - Choose the removal or rejection option

3. **Update Loan Status to "Removed"**
   - Select "Removed" as the new status
   - Confirm the removal action
   - Review any warnings about the impact of removal
   - Complete the status update

4. **Review Immediate Impact**
   - Pool metrics recalculate automatically
   - Total balance decreases by the removed loan's balance
   - Current balance decreases accordingly
   - Loan count decreases by one
   - Weighted averages (coupon, FICO, etc.) recalculate without the removed loan
   - All pool metrics update to reflect the removal

5. **Verify Removal**
   - Confirm the loan status shows as "Removed"
   - Verify pool metrics have updated correctly
   - Check that the loan is still visible but marked as removed
   - Ensure removal is recorded in audit trail

### Reinstating a Loan

1. **Find Removed Loans**
   - Navigate to the pool's loan list
   - Filter to show removed loans (use status filter)
   - Review the list of removed loans
   - See why loans were removed (if reason was recorded)
   - Identify loans that can be reinstated

2. **Review Loan Eligibility**
   - Check if issues with the loan have been resolved
   - Verify data corrections have been made (if applicable)
   - Confirm loan now meets pool criteria
   - Ensure loan is eligible for reinstatement

3. **Select Loan to Reinstate**
   - Choose the loan you want to reinstate
   - Review loan details to confirm it's ready
   - Access the loan status update function

4. **Update Loan Status to "Reinstated"**
   - Select "Reinstated" as the new status
   - Confirm the reinstatement action
   - Complete the status update

5. **Review Immediate Impact**
   - Pool metrics recalculate automatically
   - Total balance increases by the reinstated loan's balance
   - Current balance increases accordingly
   - Loan count increases by one
   - Weighted averages recalculate to include the reinstated loan
   - All pool metrics update to reflect the reinstatement

6. **Verify Reinstatement**
   - Confirm the loan status shows as "Reinstated" or "Active"
   - Verify pool metrics have updated correctly
   - Check that the loan is now included in calculations
   - Ensure reinstatement is recorded in audit trail

### Managing Multiple Loan Changes

1. **Remove Multiple Loans**
   - Select multiple loans from the loan list
   - Update status for all selected loans to "Removed"
   - Confirm the bulk removal
   - Review impact on pool metrics (all removals calculated together)

2. **Reinstate Multiple Loans**
   - Filter to show removed loans
   - Select multiple loans to reinstate
   - Update status for all selected loans to "Reinstated"
   - Confirm the bulk reinstatement
   - Review impact on pool metrics

3. **Track Changes**
   - View loan status history
   - See when loans were removed and reinstated
   - Review who made the changes
   - Monitor pool metric changes over time

## Rules & Validations

- Removed loans are excluded from pool calculations. They don't contribute to total balance, loan count, or weighted averages.

- Removed loans remain visible in the pool. They stay in the loan list, marked with "Removed" status, for tracking purposes.

- You can reinstate removed loans if needed. Removal is not permanent, and loans can be put back into the pool.

- Pool metrics update automatically when loans are removed or reinstated. You don't need to manually recalculate metrics.

- Some pool statuses may restrict removal or reinstatement. For example, you may not be able to remove loans from pools in Deal status.

- Removal and reinstatement are recorded in audit trail. All status changes are tracked with who made the change and when.

- Loan status must be appropriate for the action. You can only remove mapped loans, and you can only reinstate removed loans.

- Pool must be in appropriate status. You can typically only remove or reinstate loans while pool is in Created or Preview status.

- Changes affect pool metrics immediately. There's no delay - metrics update as soon as status changes.

- Multiple changes can be made. You can remove or reinstate multiple loans, and metrics will recalculate for all changes together.

## What Happens Next

After rejecting (removing) a loan:
- Loan is excluded from pool calculations immediately
- Pool metrics update automatically (balance decreases, loan count decreases, averages recalculate)
- Loan remains visible in the pool but marked as "Removed"
- You can reinstate it later if needed
- Removal is recorded in audit trail
- Pool composition reflects only active loans

After reinstating a loan:
- Loan is included in pool calculations again immediately
- Pool metrics update automatically (balance increases, loan count increases, averages recalculate)
- Loan returns to active status (Reinstated or Active)
- Loan fully participates in the pool
- Reinstatement is recorded in audit trail
- Pool composition includes the reinstated loan

After making multiple changes:
- All changes are processed together
- Pool metrics recalculate for all changes at once
- You can see the net impact on pool metrics
- All changes are recorded in audit trail
- Pool composition reflects all active loans

Understanding loan rejection and reinstatement helps you effectively manage loans in your pools, maintain pool quality and compliance, adjust pool composition as needed, and respond to feedback from reviewers. This flexibility allows you to refine pools before finalizing them as deals.
