---
title: Funding Requests
description: Learn how borrowers create and submit funding requests for credit facilities
---

# Funding Requests

## Overview

Funding requests are how borrowers draw down funds from active credit facilities. After a master commitment is active and deal modelling is complete, borrowers can create funding requests specifying the amount they want to draw, the funding date, purpose, and supporting documentation. The facility agent reviews each request before funds can be disbursed.

## Who Can Use This

- **Borrowers**: Create and submit funding requests for their active facilities

## When This Is Used

Use funding requests when:
- Your master commitment is Active
- Deal modelling has been completed by the facility agent
- You need to draw down funds from your credit facility
- You want to request a specific amount from your available capacity

## Prerequisites

Before creating a funding request:

1. **Active Master Commitment**: The master commitment must be in **Active** status (at least one lender has approved)

2. **Deal Modelling Complete**: The facility agent must have completed deal modelling (Facility Setup Status: Completed)

3. **Loans Mapped (if required)**: You may need to map NFT-minted loans to the facility first

4. **Available Capacity**: You must have available borrowing capacity within your facility limits

## Step-by-Step Process

### Step 1: Access the Master Commitment

1. **Navigate to Credit Facility**
   - Log in to the platform with your Borrower credentials
   - From the left expandable menu, click on **Credit Facility**
   - Locate your active master commitment

2. **Verify Prerequisites**
   - Confirm the master commitment shows **Active** status
   - Check that **Funding Request** button is enabled (indicates deal modelling is complete)

### Step 2: Map Loans (If Required)

Before creating a funding request, you may need to map loans:

1. **Click Map Loans**
   - In the Actions column, click **Map Loans**
   - A screen shows currently mapped loans and totals

2. **Add Loans to Facility**
   - Click **Add Loans to Facility**
   - A popup shows available loans
   - Only loans with **minted NFTs** have enabled checkboxes
   - Select the loans you want to map
   - Click **Next**, then click **Map**
   - Error appears if a loan is already mapped to a different facility

### Step 3: Create Funding Request

1. **Click Funding Request**
   - Click the **Funding Request** button
   - A popup opens for entering request details

![Funding Request Creation - Issuer](imagesByMdFilesFolder/33/FundingRequest_Creation_Issuer.png)

2. **Enter Request Details**
   - **Draw Amount**: Enter the amount you want to draw
   - **Funding Date**: Select the date you need the funds
   - **Purpose of Funds**: Describe what the funds will be used for
   - **Draw Currency**: Select the currency for the drawdown
   - **Upload Collateral Addendum**: Upload supporting collateral documentation

3. **Review the Request**
   - Verify all entered information is correct
   - Ensure the draw amount is within your available capacity
   - Check that the funding date is appropriate
   - Confirm the collateral addendum is uploaded

### Step 4: Submit the Funding Request

1. **Click Review**
   - Click **Review** to create the funding request
   - Status is **Draft**

2. **Click Submit**
   - Click **Submit** to send the request to the facility agent
   - Status changes to **FAReview**
   - Facility agent receives notification

### Step 5: Wait for Facility Agent Review

1. **Monitor Status**
   - Track your funding request status in the Credit Facility dashboard
   - Possible outcomes:
     - **Approved**: Funding notice is generated
     - **Rejected**: Request is declined (you can create a new request)
     - **Changes Requested**: You need to modify and resubmit

2. **Respond to Change Requests (If Any)**
   - If status is **CHANGES_REQUESTED**, edit the request
   - Address the requested changes
   - Resubmit for review

## Funding Request Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| DRAFT | Created but not submitted | Edit, Submit |
| FAReview | Submitted, awaiting FA decision | View only |
| APPROVED | Approved, funding notice generated | View, proceed to token approval |
| REJECTED | Rejected by FA (final) | View only, create new request |
| CHANGES_REQUESTED | FA requested modifications | Edit, resubmit |

## Rules & Validations

- **Active Facility Required**: You can only create funding requests for master commitments with Active status.

- **Deal Modelling Must Be Complete**: The facility agent must complete deal modelling before you can create funding requests.

- **Only NFT-Minted Loans**: Only loans with minted NFTs can be mapped to the facility.

- **Within Capacity**: Draw amount must be within your available borrowing capacity.

- **One at a Time**: Submit one funding request at a time. Wait for the current request to be processed before creating another.

- **Rejected Is Final**: Rejected funding requests cannot be resubmitted. Create a new request if rejected.

## What Happens Next

**After Submitting:**
- Facility agent reviews your request
- You receive notification of the decision

**After Approval:**
- Funding notice is automatically generated
- Facility agent processes the funding notice (token generation, e-sign for each lender)
- You approve token transfer when notified
- Lenders transfer funds and confirm settlement
- Funds are disbursed to you
