---
title: Deal Creation and Publishing
description: Step-by-step guide to creating, configuring, and publishing an asset sale deal — including all wizard fields, dropdown options, recourse configuration, and validation rules
---

# Deal Creation & Publishing

## Overview

Creating and publishing an asset sale deal is the first major phase of the asset sale workflow. The issuer creates a deal through a three-step wizard, assigns loans from the loan registry or existing pools, configures sale terms and recourse options, optionally uploads a sale agreement document, and submits the deal. After submission, the deal enters Draft status and can be published for underwriter (Market Maker) review. This guide covers the complete process from initial deal creation through underwriter approval, including every field, dropdown option, and validation rule as they appear in the platform.

## Who Can Use This

- **Issuers**: Create deals, assign loans, configure terms, and publish for review
- **Underwriters (Market Makers)**: Review published deals and approve or reject them

## When This Is Used

Use this process when:
- You want to sell a portfolio of loans or receivables to investors
- You need to package loans into a structured deal for market distribution
- You want to understand how deals progress from creation to publication
- You need to configure sale terms, recourse options, and deal documentation

## Step-by-Step Process

### Part 1: Creating a Deal — Basics (Step 1 of 3)

#### Step 1: Access the Asset Sale Dashboard

1. Log in to the platform with your Issuer credentials
2. From the left sidebar menu, click on **Asset Sale**
3. The Asset Sale dashboard displays all your deals organized by status
4. Click the **Create Deal** button on the dashboard
5. The deal creation wizard opens with three tabs: **1. Basics**, **2. Pool Selection**, and **3. Sale Terms**

#### Step 2: Enter Deal Basics

Complete the following fields on the Basics tab:

- **Deal Name*** (required): Enter a unique, descriptive name for the deal (e.g., "Spring Residential Pool A"). Maximum length is enforced — names are trimmed if they exceed the limit. Once a deal is created from the Review flow, the deal name becomes read-only and cannot be changed.

- **Transaction Type**: Displayed as **"Asset Sale"** (read-only). This value is set automatically and cannot be changed.

- **Sale Route**: Select from the dropdown:
  - **Marketed** (default) — the deal is open to multiple investors
  - **Bilateral** — the deal is offered to a single investor

- **Target Settlement Date**: Select a date. The date picker enforces these rules:
  - Cannot be in the past
  - Cannot be before the cutoff date or settlement date (if already set)
  - Cannot exceed the maximum target settlement offset (platform-configured limit)

- **Governing Law**: Free-text field (e.g., "New York"). Enter the applicable governing law jurisdiction for the deal.

- **Buyer Visibility**: Select from the dropdown:
  - **All** (default) — the deal is visible to all investors on the platform
  - **Selected** — when chosen, a multi-select investor picker appears, allowing you to choose specific investor organizations

- **Arranger / Placement Agent*** (required): Select the Market Maker organization from the dropdown. This is the underwriter who will review, publish, and manage buyer commitments for the deal. The dropdown is populated from organizations with the Market Maker role.

- **Servicing Setup**: Select from the dropdown:
  - **Servicer Retained** (default) — the issuer's organization remains the servicer
  - **Servicer Released** — servicing is transferred; you can select a different servicer

- **Retained Servicer / Released Servicer**: When Servicer Retained is selected, this field auto-populates with the issuer's servicer organization and is read-only. When Servicer Released is selected, you can choose a servicer from the dropdown.

- **Servicing Fee**: Enter the servicing fee percentage (e.g., "0.25"). Accepts decimal values between 0 and 100. Only digits and one decimal point are allowed.

Click **Next** to create the deal and proceed to pool selection.

> **Validation on Next**: The deal name and arranger are required. If either is missing, an error message appears and you cannot proceed. On first submission, the deal is created server-side and assigned a Deal ID. On subsequent visits to the Basics tab, clicking Next updates the existing deal.

### Part 2: Assigning Loans (Step 2 of 3)

#### Step 3: Select Assets or Pools

The Pool Selection tab provides a toggle between two modes:

**Assets Mode** (default) — Select individual loans:
- Browse available loans with columns: **Loan ID** (or **Asset ID** for receivables), **Pool Mapping Status**, **Verification Status**, and **NFT Minted Status**
- Click **Add Assets** (or **Add Loans**) to open the loan selection modal and pick loans to assign
- Select loans using checkboxes (individual or select-all) and click **Delete** to remove selected loans from the deal
- Only loans with NFT Minted status are eligible for assignment
- The table supports infinite scroll for large loan sets
- The **Asset Class** label is displayed based on the deal's asset class (read-only in Assets mode)

**Pools Mode** — Select entire pools:
- An **Asset Class** dropdown lets you select the asset class (only available before loans are assigned)
- Browse available pools with columns: **Pool Name** and **Loan Count** (or **Asset Count**)
- Select one or more pools using checkboxes to assign all their minted loans to the deal
- When pools are selected, clicking **Next** calls the pool assignment API

Click **Next** to proceed to sale terms.

### Part 3: Configuring Sale Terms (Step 3 of 3)

#### Step 4: Set Sale Terms

Complete the following fields on the Sale Terms tab:

- **Purchase Price Basis**: Select from the dropdown:
  - **Par** (default)
  - **Premium**
  - **Discount**

- **Price (%)**: Enter the sale price as a percentage (e.g., "98.50"). Accepts decimal values. The format is validated before submission — price and basis must be consistent.

- **Cutoff Date**: Select a date. The date picker enforces:
  - Cannot be in the past
  - Cannot be after the settlement date (if set)
  - Cannot be after the target settlement date (if set)

- **Settlement Date**: Select a date. The date picker enforces:
  - Cannot be in the past
  - Cannot be before the cutoff date (if set)
  - Cannot be after the target settlement date (if set)

- **Minimum Pool Size (USD)**: Enter a whole number for the minimum pool balance threshold (e.g., "10000000"). Only digits are accepted.

- **Commit Window (days)**: Enter the number of days investors have to commit (e.g., "5"). Only whole numbers are accepted. A platform-configured maximum applies.

#### Step 5: Configure Recourse (Optional)

The Recourse Profile section appears below the sale terms fields. All recourse fields are optional.

- **Recourse Type**: Select from the dropdown:
  - **Full Recourse** — all trigger options are available
  - **Limited Recourse** — all trigger options are available
  - **Rep and Warranty Recourse Only** — limited triggers: Invoice invalid/fictitious, Breach of reps and warranties, Documentary exception
  - **Non-Recourse** — limited triggers: Invoice invalid/fictitious, Breach of reps and warranties, Documentary exception

- **Recourse Triggers**: Checkboxes for applicable triggers (availability depends on recourse type):
  - Invoice invalid / fictitious
  - Breach of reps and warranties
  - Documentary exception
  - Dispute / offset beyond threshold (shows threshold fields when checked)
  - Credit memo / dilution beyond threshold (shows threshold fields when checked)
  - Obligor non-payment after X days (shows days field when checked)

- **Dispute / Offset Threshold (% / $)**: Appears when the dispute trigger is selected. Percentage (0–100) and dollar amount fields.

- **Dilution Threshold (% / $)**: Appears when the dilution trigger is selected. Percentage (0–100) and dollar amount fields.

- **Obligor Non-Payment Days**: Appears when the obligor non-payment trigger is selected. Whole number of days.

- **Cure / Repurchase Window (days)**: Number of days for the cure period. Whole numbers only.

- **Recourse Cap Basis**: Select from the dropdown:
  - **Invoice Amount**
  - **Purchase Price**
  - **Portfolio Percentage**

- **Recourse Cap Value**: Enter the cap value corresponding to the selected basis.

- **Holdback / Reserve (%)**: Enter the holdback percentage. When greater than zero, the holdback basis field appears.

- **Holdback Basis**: Select from the dropdown (shown when holdback percentage > 0):
  - **Purchase Price**
  - **Face Value**

- **Replacement Right**: Select from the dropdown:
  - **Yes**
  - **No**
  - Note: Replacement Right cannot be enabled on single-asset bilateral deals. The platform will show an error if you attempt this.

#### Step 6: Upload Sale Agreement (Optional)

- Use the **Upload** button in the footer area to attach a sale agreement PDF
- If a sale agreement is already attached, its filename is shown with an option to replace or remove it
- Sale agreement is optional — if not uploaded, investors can upload their own signed documents later
- The upload happens when you click Submit

#### Step 7: Submit

- Click **Submit** to save the deal with all sale terms and the uploaded sale agreement
- The deal is saved in **Draft** status
- You are redirected to the deal details page
- The session draft is cleared after successful submission

### Part 4: Publishing the Deal

#### Step 8: Publish for Underwriter Review

1. From the deal details page, verify all deal components are complete: loans assigned, terms configured, documents uploaded
2. Click the **Publish** action on the deal
3. The deal status changes from **Draft** to **Pending Review**
4. The underwriter receives the deal for evaluation

### Part 5: Underwriter Review

#### Step 9: Underwriter Evaluates the Deal

1. The underwriter accesses the deal from their Asset Sale dashboard
2. They review: deal terms, loan portfolio composition, documentation, and sale terms
3. **Approve**: The deal is approved and becomes **Published**, making it visible to investors
4. **Reject**: The deal is rejected and the issuer is notified; the deal reverts to Draft for revision

## Rules & Validations

- **Deal Name** and **Arranger / Placement Agent** are required fields — the wizard will not proceed without them
- A deal must have at least one loan assigned before it can be published
- Sale terms must be configured before final submission
- Only deals in **Draft** or **Cancelled** status can be edited by the issuer
- Only deals in **Pending Review** status can be reviewed by the underwriter
- Cancelled deals cannot be reactivated or re-published
- Loan assignment changes are not permitted after the deal is published
- The servicing fee must be between 0% and 100%
- Price accepts decimal values; minimum pool size and commit window accept whole numbers only
- Date fields enforce chronological consistency: cutoff ≤ settlement ≤ target settlement
- Replacement Right is blocked on single-asset bilateral deals
- The deal creation wizard auto-saves a session draft — if you navigate away and return, your progress is restored

## What Happens Next

After the underwriter approves the deal:
- The deal status becomes **Published** and is visible to investors
- Investors can review deal details and begin the commitment process
- The next step is **Investor Commitment & Allocation** (see article 35)
- If the deal is rejected, the issuer can revise and resubmit the deal
