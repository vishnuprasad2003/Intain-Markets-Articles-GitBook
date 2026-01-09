---
title: Facility Setup Status (Deal Modelling)
description: Understand deal modelling and facility setup status
---

# Facility Setup Status (Deal Modelling)

## Overview

After a master commitment becomes Active, the facility agent must complete deal modelling before borrowers can raise funding requests. The Facility Setup Status tracks whether this configuration is complete. This guide explains the deal modelling process and what each status means.

## What is Deal Modelling

Deal modelling is the process where the facility agent configures the operational parameters for an active credit facility. This includes setting up calculations, parameters, and rules needed for the facility to operate. Deal modelling can only be completed after the master commitment is Active.

## Facility Setup Status Values

### In Progress

**Meaning**: Deal modelling has not been completed yet.

**When This Occurs**:
- Initial state after master commitment becomes Active
- Facility agent has not completed the deal modelling process

**What This Means**:
- Borrower **cannot** raise funding requests yet
- Borrower **cannot** map loans to the facility yet
- Facility agent needs to complete deal modelling

### Completed

**Meaning**: Deal modelling is complete.

**When This Occurs**:
- Facility agent has completed all sections in deal modelling
- Facility agent has clicked **Create** in the Review section

**What This Means**:
- Borrower **can** now map loans to the facility
- Borrower **can** now raise funding requests
- Funding workflow can proceed

## Step-by-Step: Completing Deal Modelling

### Step 1: Access Deal Modelling

1. **Navigate to Credit Facility**
   - Log in with your Facility Agent credentials
   - From the left expandable menu, click on **Credit Facility**
   - Go to the **Active Facilities** tab

2. **Find the Master Commitment**
   - Locate the active master commitment
   - Action column shows **Set Up Deal**

3. **Click Set Up Deal**
   - Click **Set Up Deal** to open the deal modelling screen

### Step 2: Complete Deal Modelling Sections

1. **Navigate Through Sections**
   - The deal modelling screen has multiple sections in the left menu
   - Complete each section as required

2. **Delegation Option**
   - A **Delegation** button is available at the top
   - Click this to request the admin to complete deal modelling on your behalf
   - If delegated, the admin role will do the configuration

3. **Fill All Required Fields**
   - Complete each section with the required information
   - Ensure all parameters are configured correctly

### Step 3: Complete Deal Modelling

1. **Navigate to Review Section**
   - Go to the last section (Review)

2. **Click Create**
   - Click **Create** to complete deal modelling
   - Facility Setup Status changes from **In Progress** to **Completed**

### Step 4: Borrower Can Now Raise Funding Requests

After deal modelling is complete:
- The borrower's **Map Loans** action is enabled
- The borrower's **Funding Request** action is enabled
- The funding workflow can proceed

## Important Points

**Active Master Commitment Required** - Deal modelling can only be completed for Active master commitments.

**Must Complete Before Funding Requests** - Borrowers cannot raise funding requests until deal modelling is complete.

**Delegation Available** - Facility agents can delegate deal modelling to the admin role.

**One-Time Process** - Deal modelling is completed once per facility.

## What Happens Next

**After Deal Modelling is Complete:**
- Borrower can map NFT-minted loans to the facility
- Borrower can create funding requests
- Funding request → FA Review → Funding Notice → Lender Transfer
