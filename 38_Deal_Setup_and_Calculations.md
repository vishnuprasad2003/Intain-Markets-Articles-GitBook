---
title: Deal Setup and Calculations (Deal Modelling)
description: Learn how facility agents configure deal modelling for credit facilities
---

# Deal Setup and Calculations (Deal Modelling)

## Overview

After a master commitment becomes Active, the facility agent must complete deal modelling before borrowers can raise funding requests. Deal modelling involves configuring the operational parameters, borrowing base calculations, and facility rules needed to operate the credit facility.

## Who Can Use This

- **Facility Agents** who configure deal modelling for active facilities

## When This Is Used

Use deal modelling when:
- A master commitment has become **Active** (at least one lender approved)
- You need to configure facility operational parameters
- You want to enable borrowers to raise funding requests
- You're preparing the facility for operations

## Prerequisites

Before starting deal modelling:
- Master commitment must be **Active**
- At least one lender has approved and signed

## Step-by-Step Process

### Step 1: Access Deal Modelling

1. **Navigate to Credit Facility**
   - Log in with your Facility Agent credentials
   - From the left expandable menu, click on **Credit Facility**
   - Go to the **Active Facilities** tab

2. **Find the Master Commitment**
   - Locate the active master commitment
   - Facility Setup Status shows **In Progress**
   - Action column shows **Set Up Deal**

3. **Click Set Up Deal**
   - Click **Set Up Deal** to open the deal modelling screen

![Set Up Deal](imagesByMdFilesFolder/38/SetUpDeal.png)

### Step 2: Complete Deal Modelling Sections

The deal modelling screen has multiple sections in the left menu. Complete each section:

1. **Configure Borrowing Base**
   - Set up borrowing base calculations
   - Configure how available capacity is determined
   - Set advance rates and limits

![Set Up Borrowing Base Calculation](imagesByMdFilesFolder/38/setUpBorrowingBaseCalculation.png)

2. **Configure Parameters**
   - Set up facility parameters
   - Configure interest calculations
   - Set fee structures

![Configure Parameters](imagesByMdFilesFolder/38/ConfigureParameters.png)

3. **Complete Additional Sections**
   - Navigate through all required sections
   - Fill in all mandatory fields
   - Each section configures specific aspects of the facility

### Step 3: Delegation Option

If needed, you can delegate deal modelling:

1. **Click Delegation Button**
   - A **Delegation** button is available at the top
   - Click to request admin to complete deal modelling on your behalf

2. **Admin Completes**
   - If delegated, the admin role will configure the deal modelling

### Step 4: Review and Complete

1. **Navigate to Review Section**
   - Go to the final Review section
   - Review all configured parameters

![Validating Calculations](imagesByMdFilesFolder/38/ValidatingCalculations.png)

2. **Click Create**
   - After reviewing, click **Create**
   - Facility Setup Status changes from **In Progress** to **Completed**

### After Completion

Once deal modelling is complete:
- **Facility Setup Status**: Completed
- **Borrower can now**:
  - Map NFT-minted loans to the facility
  - Create funding requests
- **Funding workflow** can proceed

## Facility Setup Status

| Status | Meaning | Borrower Can Raise Funding Request |
|--------|---------|-------------------------------------|
| **In Progress** | Deal modelling not complete | No |
| **Completed** | Deal modelling complete | Yes |

## Rules & Validations

- **Active MC Required**: Deal modelling can only be completed for Active master commitments.

- **All Sections Required**: Complete all required sections before clicking Create.

- **One-Time Process**: Deal modelling is completed once per facility.

- **Delegation Available**: You can delegate to admin if needed.

- **Required for Funding**: Borrowers cannot raise funding requests until deal modelling is complete.

## What Happens Next

**After Deal Modelling Complete:**
- Borrower can map loans to the facility
- Borrower can create funding requests
- Funding request → FA Review → Funding Notice → Lender Transfer
