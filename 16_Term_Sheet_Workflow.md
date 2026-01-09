---
title: Term Sheet Workflow
description: Understand the term sheet process from creation to approval
---

# Term Sheet Workflow

## Overview

The term sheet is the first step in creating a credit facility. As a borrower, you create a term sheet proposing the key terms of the facility you want, sign it via Adobe Sign, and submit it to the facility agent for review. The facility agent then reviews and decides to approve, reject, or request changes.

## Who Can Use This

- **Borrowers**: Create term sheets and submit them for facility agent review
- **Facility Agents**: Review term sheets and make approval decisions

## When This Is Used

Use the term sheet workflow when:
- You want to propose a new credit facility
- You need to understand how term sheets progress from creation to approval
- You need to review and respond to change requests
- You want to know what happens after term sheet approval

## Step-by-Step Process

### Part 1: Creating a Term Sheet (Borrower)

#### Step 1: Access the Credit Facility Dashboard

1. **Navigate to Credit Facility**
   - Log in to the platform with your Borrower credentials
   - From the left expandable menu (which expands when you hover over it), click on **Credit Facility**
   - The Credit Facility dashboard displays with term sheets you've created and master commitments

#### Step 2: Start Term Sheet Setup

1. **Click Term Sheet Setup**
   - Click the **Term Sheet Setup** button at the top right of the dashboard
   - Two options appear:
     - **Create Via Wizard**: Opens a popup form to create the term sheet step-by-step
     - **Upload Signed**: Upload an already-signed term sheet document

2. **Select Create Via Wizard**
   - Click **Create Via Wizard** to open the term sheet creation popup

![Accessing Term Sheet - Create New Term Sheet](imagesByMdFilesFolder/16/AccessingTermsheetCreateNewTermSheet.png)

#### Step 3: Enter Term Sheet Details

1. **Fill in Facility Information**
   - **Requested Commitment Amount**: Enter the maximum amount you want to borrow
   - **Advance Rate**: Specify what percentage of collateral value can be borrowed (e.g., 85%)
   - **Pricing Index**: Select the base interest rate index (e.g., SOFR, SOFR 1M)
   - **Margin**: Enter the spread to be added to the pricing index (e.g., 2.5%)
   - **Fixed Rate**: Enter a fixed interest rate if applicable (alternative to index + margin)
   - **Maturity Date**: Select when the facility will mature
   - **Drawdown Frequency**: Choose how often drawdowns are allowed (e.g., Monthly, Quarterly)
   - **Covenant Template**: Select the applicable covenant template

![Add Term Sheet Details](imagesByMdFilesFolder/16/2_AddTermSheetDetails.png)

#### Step 4: Upload Required Documents

1. **Upload Supporting Documents**
   - **Collateral Profile**: Upload your collateral profile document
   - **Financial Statements**: Upload your financial statements
   - **KYC Documents**: Upload KYC documentation
   - **Collateral Data**: Upload collateral data files

![Upload Documents](imagesByMdFilesFolder/16/UploadDocuments.png)

#### Step 5: Create Draft and Sign

1. **Create the Draft**
   - Review all entered information for accuracy
   - Verify all required fields are filled
   - Ensure documents are uploaded correctly
   - Click **Create Draft**
   - Status changes to **Draft**

![Issuer - Term Sheet Creation](imagesByMdFilesFolder/16/Issuer_TermSheetCreation.png)

2. **Sign via Adobe Sign**
   - After clicking Create Draft, an Adobe Sign popup window opens automatically
   - The popup shows the term sheet document with all the details you entered
   - Review the document
   - Complete the electronic signature process
   - After signing, status changes to **BorrowerSigned**

#### Step 6: Submit to Facility Agent

1. **Submit Term Sheet Popup Appears**
   - After signing, a **Submit to FA** popup appears
   - Review the submission details

2. **Choose to Submit or Cancel**
   - Click **Submit** to submit the term sheet to the facility agent
   - Status changes from **BorrowerSigned** to **FAReview**
   - Facility agent receives notification
   - If you click **Cancel**, you can submit later from the dashboard

![Submit Term Sheet to FA](imagesByMdFilesFolder/16/SubmitTermSheetToFA.png)

3. **Dashboard Actions After Signing**
   - If you cancelled the Submit popup, the action column in the dashboard shows **Submit Term Sheet**
   - Click this action to submit when ready
   - After submitting, the action changes to **View Term Sheet**

### Part 2: Facility Agent Review

#### Step 1: Access Review

1. **Navigate to Credit Facility**
   - Log in as Facility Agent
   - Go to **Credit Facility** section from the left menu
   - Find the term sheet in the Set-up tab

2. **Click Review Term Sheet**
   - In the Actions column, click **Review Term Sheet**
   - A popup opens showing all term sheet details and attached documents

![Review Term Sheet - FA](imagesByMdFilesFolder/16/review_term_sheet_FA.png)

#### Step 2: Make Decision

1. **Review Options**
   - In the Review Term Sheet popup, three buttons are available:
     - **Approve**: Term sheet meets requirements
     - **Reject**: Term sheet doesn't meet requirements
     - **Request Changes**: Modifications are needed

2. **Approve**
   - Click **Approve** when all requirements are met
   - Status changes to **Accepted**
   - Master commitment is automatically created with **Draft** status
   - Borrower receives notification

3. **Reject**
   - Click **Reject** when requirements are not met
   - Provide rejection reason
   - Status changes to **Rejected** (final state)
   - Borrower receives notification
   - Rejected term sheets cannot be resubmitted; borrower must create a new one

4. **Request Changes**
   - Click **Request Changes** when modifications are needed
   - Enter details about what needs to be changed
   - Status changes to **CHANGES_REQUESTED**
   - Borrower receives notification and can edit and resubmit

### Part 3: Responding to Change Requests (Borrower)

#### Step 1: Review Change Request

1. **Check Dashboard**
   - Term sheet status shows **CHANGES_REQUESTED**
   - Action column shows **Edit Term Sheet**
   - Read the change request details carefully

![Review Changes Requested - Issuer](imagesByMdFilesFolder/16/ReviewChangesRequestedIssuer.png)

#### Step 2: Make Changes

1. **Edit Term Sheet**
   - Click **Edit Term Sheet** action
   - The term sheet opens for editing
   - Update fields as requested by the facility agent
   - Modify documents if needed
   - Address all requested changes

#### Step 3: Update and Re-sign

1. **Click Update**
   - After making all changes, click **Update**
   - An Adobe Sign popup appears again
   - Complete the electronic signature
   - Status changes to **BorrowerSigned**

2. **Resubmit**
   - After signing, the Submit to FA popup appears
   - Click **Submit** to resubmit the updated term sheet
   - Status changes to **FAReview**
   - Facility agent reviews the updated term sheet

## Term Sheet Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| Draft | Initial creation, not yet signed | Edit, sign |
| BorrowerSigned | Signed by borrower, ready to submit | Submit to FA |
| FAReview | Submitted, awaiting facility agent decision | View (borrower), Review (FA) |
| Accepted | Approved by facility agent | View (master commitment created) |
| Rejected | Rejected by facility agent (final) | View only |
| CHANGES_REQUESTED | Facility agent requested modifications | Edit, sign, resubmit |

## Rules & Validations

- **Signing Required**: You must sign the term sheet via Adobe Sign before submitting. Unsigned term sheets cannot be submitted.

- **One Submission at a Time**: Term sheets can only be submitted once. After submission, you wait for the facility agent's decision.

- **No Edit After Submission**: You cannot edit term sheets while they're in FAReview status. You can only edit in Draft or CHANGES_REQUESTED status.

- **Rejected Is Final**: Rejected term sheets cannot be resubmitted. Create a new term sheet if rejected.

- **Auto-Create Master Commitment**: When approved, a master commitment is automatically created. You don't need to create it manually.

## What Happens Next

**After Creating and Signing:**
- Submit to facility agent when ready
- Wait for facility agent review

**After Submitting:**
- Facility agent reviews your term sheet
- You receive notification of the decision (Approved, Rejected, or Changes Requested)

**After Approval:**
- Master commitment is automatically created
- Facility agent configures the facility (adds lenders, rules)
- Facility agent submits to lenders for approval
- After lender approval, facility becomes active

**After Rejection:**
- Review rejection reason
- Create a new term sheet addressing the issues

**After Changes Requested:**
- Edit the term sheet to address requested changes
- Sign and resubmit for review
