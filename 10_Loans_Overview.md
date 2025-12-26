---
title: Loans Overview
description: Learn what loans are and how they work in the platform
---

# Loans Overview

## Overview

Loans are individual credit agreements representing money lent to borrowers. In Intain Markets, loans are the building blocks of pools - you group multiple loans together to create pools for securitization, whole loan sales, or credit facilities. Understanding loans helps you effectively manage your loan portfolios and create successful pools.

## What This Means for the User

When you work with loans in the platform, you're managing individual credit agreements that will be grouped into pools. Each loan contains:

- Borrower information (name, contact details, etc.)
- Financial details (loan amount, interest rate, payment terms, etc.)
- Loan characteristics (FICO score, loan-to-value ratio, geographic location, etc.)
- Status information (where the loan is in its lifecycle)
- Performance data (payments, balances, etc.)

Loans can be mapped to pools, and when you map loans, pool metrics calculate automatically. You can also remove loans from pools (reject them) and reinstate them later if needed.

## Key Concepts Explained

### Loan Upload

You upload loan data into the platform, typically through file upload. The system:

- Processes and standardizes the data
- Validates loan information
- Stores loans in the system
- Makes loans available for mapping to pools

After upload, loans are ready to be mapped to pools or managed individually.

### Loan Mapping

Loans are mapped to pools, meaning you assign them to a specific pool. Important points:

- **One Pool Per Loan**: A loan can only belong to one pool at a time. If you want to move a loan to a different pool, you must unmap it from the current pool first.

- **Automatic Calculations**: When you map loans to a pool, pool metrics calculate automatically. Total balance, loan count, weighted averages, and other statistics update immediately.

- **Real-Time Updates**: If you add or remove loans from a pool, metrics update in real-time to reflect the changes.

### Loan Statuses

Loans have statuses that show where they are in their lifecycle:

- **Unmapped**: Loan is uploaded but not yet assigned to a pool
- **Mapped**: Loan is assigned to a pool
- **Submitted**: Loan is included in a batch for verification
- **Verified**: Loan has been verified and can proceed
- **Minted**: Loan has been tokenized (if applicable)
- **Removed**: Loan has been removed from pool calculations
- **Reinstated**: Loan was removed but put back into the pool

Status controls what actions are available and tracks loan progress.

### Loan Characteristics

Each loan has characteristics that contribute to pool-level metrics:

- **Loan Balance**: The amount of money lent
- **Interest Rate (Coupon)**: The interest rate charged
- **FICO Score**: Borrower's credit score
- **Loan-to-Value Ratio**: For secured loans, the ratio of loan amount to asset value
- **Geographic Location**: Where the borrower is located
- **Loan Type**: Type of loan (auto, personal, mortgage, etc.)
- **Maturity Date**: When the loan is scheduled to be paid off
- **Payment Terms**: How payments are structured

These characteristics aggregate to create pool-level statistics that help investors assess opportunities.

### Removed Loans

Loans can be removed from pools (rejected) for various reasons:

- Data quality issues
- Loans don't meet pool criteria
- Errors need correction
- Pool requirements change

Removed loans are:
- Excluded from pool calculations
- Still visible in the pool for tracking
- Can be reinstated if needed
- Marked with "Removed" status

When loans are removed, pool metrics recalculate automatically to exclude them.

### Reinstated Loans

Removed loans can be reinstated (put back into the pool) when:

- Issues are resolved
- Data is corrected
- Pool requirements change
- You decide to include them again

When loans are reinstated:
- They're included in pool calculations again
- Pool metrics recalculate automatically
- Loan status changes to "Reinstated" or "Active"
- Loan fully participates in the pool

## Important Points to Know

- **One Pool Per Loan**: Loans can only belong to one pool at a time. You must unmap from one pool before mapping to another.

- **Automatic Calculations**: Pool metrics calculate automatically when loans are mapped, removed, or reinstated. You don't need to calculate them manually.

- **Removed Loans Are Excluded**: Removed loans don't affect pool calculations but remain visible for tracking purposes.

- **Status Controls Actions**: Loan status determines what actions are available. Some statuses restrict certain actions.

- **Loan Data Is Standardized**: When you upload loans, the system standardizes the data to ensure consistency across loans and pools.

- **Pool Metrics Aggregate Loan Data**: Pool-level metrics (total balance, weighted averages, etc.) are calculated from the individual loan characteristics.

- **You Can Track Loan History**: The platform maintains history of loan status changes, mappings, and other actions.

- **Loans Contribute to Pool Characteristics**: Individual loan characteristics (FICO scores, interest rates, etc.) aggregate to create pool-level statistics.

- **File Upload Format**: Loans are typically uploaded via file (Excel, CSV, etc.) with specific formats and required fields.

- **Validation Happens on Upload**: The system validates loan data during upload and may flag errors or missing information.

Understanding loans helps you effectively manage your loan portfolios, create successful pools, and ensure loan data quality throughout the structured finance transaction process.
