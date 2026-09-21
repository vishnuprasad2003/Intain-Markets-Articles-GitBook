---
title: Running the Deal (Recurring Module)
description: Execute monthly deal calculations after loan processing is committed
---

# Running the Deal (Recurring)

This article explains how to execute the monthly deal calculation after loan processing has been completed and committed for the selected payment period.

## Overview

The **Recurring Module** is the execution phase of the monthly deal cycle. In this step, the platform uses:

* Deal configuration defined during **Deal Creation**
* Loan data committed during **Loan Processing**

to calculate payment distributions, evaluate tests, and generate official results for the period.

This step represents the point where the deal logic is applied to finalized loan data.

## Prerequisites

Before running the recurring calculation, ensure that:

* Deal Creation setup is complete
* Loan Processing has been summarized and **committed to the Digital Ledger** for the selected payment period

If either step is incomplete, the recurring calculation cannot be run.

## Accessing the Recurring Module

To access the Recurring view:

1. Navigate to the Deal Dashboard
2. Select the appropriate **Payment Date**
3. Click **Deal** under the Actions column

The Recurring Module opens with tabs that mirror the Deal Creation structure.

## Reviewing Data in the Recurring View

Before running calculations, you can review data across multiple tabs, including:

* **General**: Deal-level details for the selected period
* **Tranches**: Period-specific tranche values used in calculations
* **Fees and Expenses**: Amounts applicable for the period
* **Accounts**: Opening balances and account structure
* **Tests and Variables**: Logic that will be evaluated during calculation

Some values may be editable prior to calculation, depending on deal configuration.

## Running the Calculation

Once all data has been reviewed:

* Click **Calculate Payments**

The platform then:

* Evaluates all expressions and rules
* Applies the payment waterfall
* Executes compliance tests
* Calculates final balances and distributions

All tables update with computed values for the selected payment period.

## Results and Outputs

After calculation:

* Calculate Payments button is disabled
* The results represent the official deal outputs for the period
* Calculated values are available for reporting
* Outputs are stored for audit and reference

At this stage, the monthly deal cycle is complete.

## Re-running the Deal (If Corrections Are Needed)

If an issue is identified after calculation:

1. Click **Edit** and navigate back to Deal Creation
2. Update the relevant setup or expressions
3. Save the changes
4. Return to the Recurring Module
5. Click **Calculate Payments** again

This allows corrected logic to be applied before final reporting.

## Important Notes

* Recurring calculations are performed **per payment period**
* Calculations rely only on **committed loan data**
* Changes to setup affect future calculations unless the deal is recalculated
