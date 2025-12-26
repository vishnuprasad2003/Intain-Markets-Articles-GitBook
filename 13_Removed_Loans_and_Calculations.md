---
title: Removed Loans and Calculations
description: Understand how removed loans affect pool calculations and metrics
---

# Removed Loans and Calculations

## Overview

When loans are removed from pools, they're excluded from pool calculations but remain visible for tracking purposes. Understanding how removed loans affect calculations helps you manage pool metrics accurately and make informed decisions about loan inclusion and exclusion.

## What This Means for the User

When you remove a loan from a pool, the platform automatically:

- Excludes the loan from all pool calculations
- Recalculates pool metrics without the removed loan
- Updates total balance, loan count, and weighted averages
- Keeps the loan visible in the pool for tracking

This means pool metrics reflect only active loans, not removed ones. If you reinstate a removed loan, metrics recalculate again to include it.

## Key Concepts Explained

### What "Removed" Means

When a loan is removed from a pool:

- **Excluded from Calculations**: The loan's balance, characteristics, and data are not included in any pool-level calculations.

- **Still Visible**: The loan remains visible in the pool's loan list, marked with "Removed" status, so you can track it.

- **Can Be Reinstated**: You can reinstate removed loans if needed, and they'll be included in calculations again.

- **Status Is Recorded**: The removal is recorded with who removed it and when, creating an audit trail.

### Impact on Pool Metrics

When loans are removed, pool metrics recalculate automatically:

- **Total Balance**: Decreases by the removed loan's balance
- **Current Balance**: Decreases by the removed loan's current balance
- **Loan Count**: Decreases by one (or more if multiple loans are removed)
- **Weighted Average Coupon**: Recalculates using only active loans
- **Weighted Average FICO**: Recalculates using only active loans
- **Average Loan Size**: Recalculates based on remaining loans
- **Geographic Distribution**: Updates to exclude removed loans
- **All Other Metrics**: Recalculate to reflect only active loans

These calculations happen automatically and immediately when loans are removed.

### Impact on Pool Metrics When Reinstated

When removed loans are reinstated:

- **Total Balance**: Increases by the reinstated loan's balance
- **Current Balance**: Increases by the reinstated loan's current balance
- **Loan Count**: Increases by one (or more if multiple loans are reinstated)
- **Weighted Average Coupon**: Recalculates to include the reinstated loan
- **Weighted Average FICO**: Recalculates to include the reinstated loan
- **Average Loan Size**: Recalculates to include the reinstated loan
- **Geographic Distribution**: Updates to include the reinstated loan
- **All Other Metrics**: Recalculate to include the reinstated loan

Again, these calculations happen automatically and immediately.

### Why Loans Are Removed

Common reasons for removing loans include:

- **Data Quality Issues**: Errors in loan data that need correction
- **Doesn't Meet Criteria**: Loan doesn't meet pool requirements or criteria
- **Compliance Issues**: Loan doesn't comply with regulations or standards
- **Pool Requirements Change**: Pool requirements change, and loan no longer fits
- **Temporary Exclusion**: Loan needs to be excluded temporarily for review
- **Error Correction**: Loan was included by mistake and needs to be removed

Understanding why loans are removed helps you make informed decisions about reinstatement.

### Viewing Removed Loans

You can view removed loans by:

- **Filtering the Loan List**: Filter to show only removed loans
- **Status Badge**: Removed loans are marked with "Removed" status badge
- **Loan Details**: View individual loan details to see removal history
- **Audit Trail**: See who removed the loan and when

This visibility helps you track removed loans and decide whether to reinstate them.

## Important Points to Know

- **Removed Loans Don't Affect Metrics**: Removed loans are completely excluded from all pool calculations. Metrics reflect only active loans.

- **Automatic Recalculation**: Pool metrics recalculate automatically when loans are removed or reinstated. You don't need to manually recalculate.

- **Removed Loans Remain Visible**: Removed loans stay in the pool's loan list for tracking purposes, marked with "Removed" status.

- **Can Reinstall Removed Loans**: You can reinstate removed loans if needed, and they'll be included in calculations again.

- **Removal Is Recorded**: Every removal is recorded with who removed it and when, creating a complete audit trail.

- **Metrics Update Immediately**: When loans are removed or reinstated, metrics update immediately. There's no delay or manual refresh needed.

- **Multiple Removals**: You can remove multiple loans at once, and metrics will recalculate for all removals together.

- **Reinstatement Restores Participation**: When loans are reinstated, they fully participate in the pool again, contributing to all metrics.

- **Status History**: You can view the complete history of removals and reinstatements, including who made changes and when.

- **Pool Status May Affect Removal**: Some pool statuses may restrict removal or reinstatement. For example, you may not be able to remove loans from pools in Deal status.

Understanding removed loans and calculations helps you manage pool metrics accurately, make informed decisions about loan inclusion, and ensure pool quality and compliance.
