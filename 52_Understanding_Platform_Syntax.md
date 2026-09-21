---
title: Understanding Platform Syntax
description: >-
  Learn how expressions and references work across Intain Admin deal
  configuration tables
---

# Platform Syntax

Learn how to use expressions, system variables, and SQL queries to pull data dynamically across the Intain Admin platform.

***

## Overview

To create a dynamic and automated financial model, the Intain Admin platform uses a standardized expression format, referred to as **platform syntax**.

This syntax allows different parts of a deal to communicate with each other. For example, a rule in the Payment Waterfall can automatically read a live balance from a Tranche or an Account to determine exactly how much should be paid.

***

## Standardized Expression Format

Every expression follows a specific structure so the system knows exactly where to look for data:

TabName[EntityName][SubFieldName]

### Expression Components

**TabName**\
  The source table where the data is stored\
  &#xNAN;(Examples: Tranches, Fees, Accounts)
**EntityName**\
  The specific row identifier within that table\
  &#xNAN;(Examples: Tranche ID such as A-1, Fee name such as Trustee Fee)
**SubFieldName**\
  The specific column or field you want to fetch\
  &#xNAN;(Examples: Beginning Principal Balance, Interest Rate)

***

### Example

To fetch the **Beginning Principal Balance** of **Tranche A-1**, use:

Tranches[A-1][Beginning Principal Balance]

This value updates automatically if the tranche balance changes.

***

## Built-in System Variables

The platform includes predefined **system variables**, which act as shortcuts for common financial calculations and date logic.

These variables are especially useful in the **General** and **Payment Rules** tabs.

***

## Date and Period Functions

| Variable              | Description                                                                                                                                               |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CurrentPaymentDate  | Determines the scheduled payment date. If the date falls on a weekend or U.S. holiday, the system automatically adjusts it to the next valid business day |
| ContractPaymentDate | Returns the exact contractual date specified in the deal documents without adjusting for holidays                                                         |
| PeriodCounter       | Returns the total number of months between the first payment date and the current payment date, based on the frequency specified in the General tab       |
| DIM                 | Automatically calculates the total number of days in the current payment month                                                                            |

***

## Date Navigation Helpers

These helpers allow you to look backward or forward in time within expressions:

| Variable | Description                                                                           |
| -------- | ------------------------------------------------------------------------------------- |
| MP     | Fetches data from one month prior                                                     |
| MP3    | Fetches data from three months prior                                                  |
| MP6    | Fetches data from six months prior                                                    |
| LBM    | Identifies the Last Business Day of the Month                                         |
| CDN    | Selects the Calendar Day Next (the next business day if the current day is a holiday) |

***

## System Variables in Context

System variables are **dynamic**, meaning their values may change depending on the step of the payment waterfall where they are accessed.

### Tranches

Variables such as **Current Principal** or **Interest Paid** reflect tranche values at that specific moment in the payment sequence.

### Accounts

**Current Balance** reflects the account balance at the exact payment rule step being evaluated.

### Fees

**Current Fee** represents the fee amount currently due in the payment cycle.

This context-aware behavior allows expressions to respond dynamically as funds move through the deal structure.

***

## Advanced Data Extraction (SQL Queries)

For users who need to fetch and aggregate standardized data directly from the Loan Processing module, the platform supports **SQL queries**.

***

### SQL Rules

**Enclosure**\
  SQL queries must be enclosed within double angle brackets:

<< SQL STATEMENT >>

**Integration**\
  SQL queries can reference:
  * Standardized loan data
  * Other table data
  * System variables
  * System-defined functions
**Formatting**
  * Column names must be enclosed in backticks ( )
  * Specific values must be enclosed in double quotes (")

***

### SQL Example

To sum the **Beginning Loan Balance** for a specific servicer:

<<SELECT SUM(`Beginning Loan Balance`) FROM Table WHERE `Servicer`="Shellpoint">>

The result of this query can be used directly in expressions, tests, or payment rules.

***

## Helpful Tips

**Exact Matches**\
  Entity names (such as Tranche IDs or Fee names) must exactly match the names entered in the source tables.
**Dynamic Updating**\
  Expressions are live. Any change in an underlying table automatically updates all rules that reference it.
**Nesting**\
  System variables and SQL queries can be nested inside more complex formulas to support unique deal requirements.

***

## Key Takeaway

Platform syntax enables Intain Admin to:

Build dynamic and automated deal logic
Maintain consistency across deal tables
React automatically to data changes
Support both simple and advanced financial models

Understanding platform syntax is essential for configuring accurate payment waterfalls, tests, and other deal logic.
