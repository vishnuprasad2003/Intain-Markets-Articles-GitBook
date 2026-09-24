---
title: Funding Requests
description: Learn how borrowers create and submit funding requests for credit facilities
---

# Funding Requests

## Overview

A funding request is how you draw money from an active credit facility. After the master commitment is active and the facility agent has finished facility setup, you enter the amount, the date, the purpose, and a supporting document. The facility agent reviews the request before funds can be paid out.

## Who Can Use This

* **Borrowers**: Create and submit funding requests for their active facilities

## When This Is Used

Use a funding request when:

* Your master commitment is **Active**
* The facility agent has finished deal modelling, which is the setup of the facility terms
* You need to draw funds
* You want a specific amount from the capacity you still have

## Prerequisites

Before you create a funding request:

1. **Active master commitment**: The master commitment must be **Active**. That happens after at least one lender has approved it.
2. **Facility setup complete**: The facility agent must finish deal modelling. Facility setup status shows **Completed**.
3. **Loans mapped, if you are asked to**: You may need to attach loans that already have a digital asset record (an NFT) to the facility.
4. **Capacity left**: The draw amount must fit the amount you can still borrow.

## Step-by-Step Process

### Step 1: Access the Master Commitment

1. **Navigate to Credit Facility**
   * Log in with your Borrower account
   * From the left menu, click **Credit Facility**
   * Find your active master commitment
2. **Verify Prerequisites**
   * Confirm the master commitment shows **Active**
   * Confirm **Funding Request** is available. That means facility setup is complete.

### Step 2: Map Loans (If Required)

You may need to map loans before the funding request:

1. **Click Map Loans**
   * In the Actions column, click **Map Loans**
   * The screen lists loans already mapped and the totals
2. **Add Loans to Facility**
   * Click **Add Loans to Facility**
   * A window lists loans you can add
   * Only loans that already have an NFT can be selected. Other checkboxes stay unavailable.
   * Select the loans, click **Next**, then click **Map**
   * You see an error if a loan is already mapped to a different facility

### Step 3: Create Funding Request

1. **Click Funding Request**
   * Click **Funding Request**
   * A window opens for the request

![Funding Request Creation - Issuer](<.gitbook/assets/FundingRequest_Creation_Issuer (2).png>)

2. **Enter Request Details**
   * **Draw Amount**: The amount you want to draw
   * **Funding Date**: The date you need the funds
   * **Purpose of Funds**: What the funds will be used for
   * **Draw Currency**: The currency of this draw
   * **Upload Collateral Addendum**: The supporting collateral document
3. **Review the Request**
   * Check the amount, date, purpose, and currency
   * Confirm the amount is within the capacity you still have
   * Confirm the collateral addendum is attached

### Step 4: Submit the Funding Request

1. **Click Review**
   * Click **Review** to save the request
   * The status is **Draft**
2. **Click Submit**
   * Click **Submit** to send it to the facility agent
   * The status changes to **In review (facility agent)**
   * The facility agent is notified

### Step 5: Wait for Facility Agent Review

1. **Monitor Status**
   * Watch the status on the Credit Facility dashboard
   * Possible results:
     * **Approved**: A funding notice is created
     * **Rejected**: The request is declined. Create a new request if you still need funds.
     * **Changes Requested**: Update the request and submit it again
2. **Respond to Change Requests**
   * If the status is **Changes Requested**, open the request and edit it
   * Address the comments
   * Submit it again. The status returns to **In review (facility agent)**.

## Funding Request Statuses

| Status                         | Meaning                                      | Available Actions                                        |
| ------------------------------ | -------------------------------------------- | -------------------------------------------------------- |
| **Draft**                      | Saved, not submitted                         | Edit, Submit                                             |
| **In review (facility agent)** | Submitted, waiting for a decision            | View only                                                |
| **Approved**                   | Approved. A funding notice has been created. | View, then approve the token transfer when you are asked |
| **Rejected**                   | Rejected. This is final.                     | View only. Create a new request.                         |
| **Changes Requested**          | The facility agent asked for changes         | Edit, resubmit                                           |

## Rules & Validations

* **Active facility**: You can create a funding request only when the master commitment is **Active**.
* **Setup must be finished**: The facility agent must complete deal modelling first. Facility setup status must be **Completed**.
* **Loans with an NFT**: Only loans that already have an NFT can be mapped to the facility.
* **Stay within capacity**: The draw amount must fit the amount you can still borrow.
* **One at a time**: Submit one funding request and wait until it is processed before you create another.
* **Rejected is final**: A rejected request cannot be sent again. Create a new request.

## What Happens Next

**After you submit:**

* The facility agent reviews the request
* You are notified of the decision

**After approval:**

* A funding notice is created automatically
* The facility agent continues the notice, including token creation and a signature for each lender
* You approve the token transfer when you are asked
* Lenders send funds and confirm settlement
* The funds are paid to you
