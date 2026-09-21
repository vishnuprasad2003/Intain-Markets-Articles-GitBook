---
title: Deal Creation and Publishing
description: Step-by-step guide to creating and publishing an asset sale deal
---

# Deal Creation & Publishing

## Overview

Creating and publishing an asset sale deal is the first major phase of the asset sale workflow. The issuer creates a deal, assigns loans from the loan registry or an existing pool, configures sale terms and recourse options, prepares documentation, and publishes the deal for underwriter review. This guide covers the complete process from initial deal creation to underwriter approval.

## Who Can Use This

- **Issuers**: Create deals, assign loans, configure terms, and publish for review
- **Underwriters (Market Makers)**: Review published deals and approve or reject them

## When This Is Used

Use this process when:
- You want to sell a portfolio of loans to investors
- You need to package loans into a structured deal for market distribution
- You want to understand how deals progress from creation to publication
- You need to configure sale terms, recourse options, and deal documentation

## Step-by-Step Process

### Part 1: Creating a Deal (Issuer)

#### Step 1: Access the Asset Sale Dashboard

1. **Navigate to Asset Sale**
   - Log in to the platform with your Issuer credentials
   - From the left sidebar menu, click on **Asset Sale**
   - The Asset Sale dashboard displays all your deals organized by status

#### Step 2: Start Deal Creation — Basics (Step 1 of 3)

1. **Click Create Deal**
   - Click the **Create Deal** button on the dashboard
   - The deal creation wizard opens with three tabs: **Basics**, **Pool Selection**, and **Sale Terms**

2. **Enter Deal Basics**
   - **Deal Name**: Enter a unique, descriptive name for the deal
   - **Transaction Type**: Displayed as "Asset Sale" (read-only)
   - **Sale Route**: Select **Marketed** (open to multiple investors) or **Bilateral** (single investor)
   - **Target Settlement Date**: Set the target date for settlement completion
   - **Governing Law**: Enter the applicable governing law (e.g., "New York")
   - **Buyer Visibility**: Choose **All** (visible to all investors) or **Selected** (choose specific investors)
   - **Arranger / Placement Agent**: Select the market maker organization
   - **Servicing Setup**: Choose **Servicer Retained** or **Servicer Released**
   - **Servicing Fee**: Enter the servicing fee percentage (if servicer is retained)
   - Click **Next** to proceed to pool selection

### Part 2: Assigning Loans (Step 2 of 3)

#### Step 3: Select Assets or Pools

The wizard provides two modes for assigning loans:

1. **Assets Mode** — Select individual loans
   - Browse available loans with their Loan ID, Pool Mapping Status, Verification Status, and NFT Minted Status
   - Click **Add** to open the loan selection modal
   - Select the loans to include and confirm
   - Only loans with NFT Minted status are eligible for assignment

2. **Pools Mode** — Select entire pools
   - Browse available pools with loan counts
   - Select one or more pools to assign all their minted loans to the deal
   - This is the faster method when you want to sell an entire pool's loans

Click **Next** to proceed to sale terms.

### Part 3: Configuring Sale Terms (Step 3 of 3)

#### Step 4: Set Sale Terms and Recourse

1. **Configure Sale Terms**
   - **Purchase Price Basis**: Select **Par**, **Premium**, or **Discount**
   - **Price (%)**: Enter the sale price as a percentage
   - **Cutoff Date**: Set the cutoff date for loan data
   - **Settlement Date**: Set the settlement date (must be on or after cutoff date)
   - **Minimum Pool Size (USD)**: Set the minimum pool balance threshold
   - **Commit Window (days)**: Set how long investors have to commit

2. **Configure Recourse (Optional)**
   - **Recourse Type**: Select from Full Recourse, Limited Recourse, Rep and Warranty Recourse Only, or Non Recourse
   - **Triggers**: Define recourse trigger conditions (e.g., obligor non-payment days, dispute offset threshold, dilution threshold)
   - **Cure / Repurchase Window**: Set the number of days for the cure period (1–90 days)
   - **Recourse Cap**: Define the cap basis (Invoice Amount, Purchase Price, or Portfolio Percentage) and value
   - **Holdback**: Set the holdback percentage and basis (Purchase Price or Face Value)
   - **Replacement Right**: Available when the deal has more than one loan

3. **Upload Sale Agreement (Optional)**
   - Upload the sale agreement PDF that investors will sign via Adobe Sign
   - If no sale agreement is uploaded, investors can upload their own signed documents later

4. **Submit**
   - Click **Submit** to save the deal
   - The deal is created in **Draft** status
   - You are redirected to the deal details page

### Part 5: Publishing the Deal (Issuer)

#### Step 7: Publish for Underwriter Review

1. **Review Deal Package**
   - Verify all deal components are complete: loans assigned, terms configured, documents uploaded
   - Ensure the deal is ready for external review

2. **Publish the Deal**
   - Click the **Publish** action on the deal
   - The deal status changes from **Draft** to **Pending Review**
   - The underwriter receives the deal for evaluation

### Part 6: Underwriter Review

#### Step 8: Underwriter Evaluates the Deal

1. **Review Deal Details**
   - The underwriter accesses the deal from their Asset Sale dashboard
   - They review: deal terms, loan portfolio composition, documentation, and sale terms

2. **Make a Decision**
   - **Approve**: The deal is approved and becomes **Published**, making it visible to investors
   - **Reject**: The deal is rejected and the issuer is notified. The deal may be revised and resubmitted

## Rules & Validations

- A deal must have at least one loan assigned before it can be published
- Sale terms must be configured before publishing (unless marked as optional)
- Only deals in Draft status can be edited by the issuer
- Only deals in Pending Review status can be reviewed by the underwriter
- Cancelled deals cannot be reactivated or re-published
- Loan assignment changes are not permitted after the deal is published

## What Happens Next

After the underwriter approves the deal:
- The deal status becomes **Published** and is visible to investors
- Investors can review deal details and begin the commitment process
- The next step is **Investor Commitment & Allocation** (see article 35)
- If the deal is rejected, the issuer can create a new deal with the same or modified loan portfolio
