---
title: Pools Overview
description: Learn what pools are and how they work in structured finance transactions
---

# Pools Overview

## Overview

A pool is a collection of loans grouped together for securitization, whole loan sales, or other structured finance transactions. Pools help you organize loans, present them to investors, calculate aggregate statistics, and manage the entire transaction process from creation to completion.

## What This Means for the User

When you create a pool, you're organizing multiple loans into a single transaction. The platform automatically calculates aggregate metrics from the loans you include, such as:

- Total balance (sum of all loan balances)
- Loan count (number of loans in the pool)
- Weighted average coupon (interest rate weighted by loan balance)
- Weighted average FICO scores (credit scores weighted by loan balance)
- Other characteristics and metrics

These metrics help you and potential investors understand the pool's characteristics and make informed decisions.

Pools progress through statuses from creation to final deal completion. You can share pools with market makers, investors, rating agencies, and other parties, and collaborate through feedback and approvals.

## Key Concepts Explained

### Pool Creation

When you create a pool, you provide basic information like:

- **Pool Name**: A unique name to identify the pool
- **Asset Class**: The type of loans (for example, auto loans, personal loans, mortgages)
- **Transaction Type**: Whether this is for securitization, whole loan sale, or other transaction type
- **Description**: Additional details about the pool
- **Closing Deal Indicator**: Whether this is a closing deal

You also assign organizations to participate in the transaction, such as market makers, investors, servicers, paying agents, and rating agencies.

### Loan Mapping

After creating a pool, you map loans to it. Loans can only belong to one pool at a time, so you must unmap a loan from one pool before mapping it to another. When you map loans:

- Pool metrics calculate automatically
- Total balance updates
- Loan count updates
- Weighted averages recalculate
- All statistics reflect the mapped loans

You can add or remove loans while the pool is in Created or Preview status, and metrics update in real-time.

### Pool Metrics

Pool metrics are aggregate statistics calculated from the mapped loans. Common metrics include:

- **Total Balance**: Sum of all loan balances in the pool
- **Current Balance**: Current outstanding balance (may differ from original balance)
- **Loan Count**: Number of loans included in the pool
- **Weighted Average Coupon**: Interest rate weighted by loan balance
- **Weighted Average FICO**: Credit score weighted by loan balance
- **Average Loan Size**: Total balance divided by loan count
- **Geographic Distribution**: Where borrowers are located
- **Loan-to-Value Ratios**: For secured loans, the ratio of loan amount to asset value

These metrics help you and investors understand pool characteristics and assess risk and return.

### Pool Statuses

Pools progress through statuses:

- **Created**: Pool is created and visible only to you. You can edit freely and map loans.

- **Preview**: Pool is shared with other parties for review. Recipients can view and analyze, and you can continue making changes.

- **Mandate Pending**: Pool has been submitted to a market maker for mandate review. The market maker is deciding whether to accept.

- **Deal**: Market maker has accepted the mandate, and the pool is finalized. Editing is restricted.

Status controls what actions are available and ensures proper workflow progression.

### Pool Sharing

You can share pools with multiple organizations simultaneously:

- **Market Makers**: For structuring and mandate review
- **Investors**: For investment opportunities
- **Rating Agencies**: For analysis and rating
- **Other Parties**: As needed for the transaction

Sharing permissions control what recipients can do - view only, provide feedback, download data, etc.

### Removed Loans

Loans can be removed from pools (rejected) and later reinstated. Removed loans are:

- Excluded from pool calculations
- Still visible in the pool for tracking
- Can be reinstated if needed
- Marked with "Removed" status

When loans are removed or reinstated, pool metrics recalculate automatically.

## Important Points to Know

- Pool names must be unique - you cannot create two pools with the same name.

- Loans can only belong to one pool at a time - you must unmap from one pool before mapping to another.

- Pool metrics calculate automatically - you don't need to calculate them manually, and they update when loans are added or removed.

- You can edit pools while they're in Created or Preview status - once a pool becomes a Deal, editing is restricted.

- Removed loans are excluded from calculations - if you remove a loan, pool metrics update immediately to exclude it.

- Sharing doesn't transfer ownership - you remain the pool creator and can continue managing it.

- Multiple parties can be shared simultaneously - you can share with multiple market makers, investors, etc., at the same time.

- Pool metrics help investors assess opportunities - aggregate statistics make it easier to evaluate pool characteristics.

- Status controls workflow - you can only take actions that are allowed by the current status.

- The platform maintains complete audit trails - all changes, status updates, and actions are recorded with who did what and when.

Understanding pools helps you effectively organize loans, present them to investors, and manage structured finance transactions from start to finish.
