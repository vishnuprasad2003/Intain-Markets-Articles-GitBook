---
title: Facility Creation
description: Learn how facility agents create and configure master commitments
---

# Facility Creation

## Overview

After a term sheet is approved, a master commitment is automatically created with Draft status. As a facility agent, you configure the master commitment by adding lenders, setting up facility rules, and finalizing the facility structure before submitting to lenders for approval. This guide explains the complete facility creation process.

## Who Can Use This

- **Facility Agents**: Configure master commitments and submit them for lender approval

## When This Is Used

Use facility creation when:
- A term sheet has been approved and a master commitment has been auto-created
- You need to add lenders to the facility
- You want to configure facility rules and parameters
- You need to create sub-facilities for multiple-lender arrangements
- You're ready to submit the facility for lender approval

## Step-by-Step Process

### Step 1: Access the Master Commitment

1. **Navigate to Credit Facility**
   - Log in to the platform with your Facility Agent credentials
   - From the left expandable menu, click on **Credit Facility**
   - The dashboard shows the **Set-up** and **Active Facilities** tabs

2. **Find the Master Commitment**
   - In the **Set-up** tab, locate the approved term sheet
   - Under the term sheet, you'll see the auto-created master commitment as a dropdown
   - The master commitment shows **Draft** status
   - The Actions column shows **Create Facility**

3. **Click Create Facility**
   - Click **Create Facility** to open the facility configuration popup
   - This popup has multiple sections to complete

![Create Facility - FA](imagesByMdFilesFolder/37/CreateFacility_FA.png)

### Step 2: Configure Basic Information

1. **Navigate to Basic Section**
   - The popup shows multiple sections at the top: Basic, Parties & Accounts, Economic & Fees, and more
   - Start with the **Basic** section

2. **Select Facility Type**
   - Choose whether this is a **Single** or **Multiple** branch master commitment
   - **Single**: One master commitment with all lenders together
   - **Multiple**: Allows creating sub-facilities with different lender groups

3. **Enter Basic Details**
   - Review and update basic facility information
   - Some fields are pre-populated from the term sheet (read-only)
   - Enter any additional required information

### Step 3: Set Up Parties and Accounts

1. **Navigate to Parties & Accounts Section**
   - Click on the **Parties & Accounts** section tab

2. **Add Lenders**
   - This is where you add the lenders that will participate in this facility
   - Click **Add Lender** to add a new lender
   - Select the lender organization
   - Enter commitment amount and voting percentage
   - Repeat for all participating lenders

![Set Up Lenders](imagesByMdFilesFolder/37/setUpLenders.png)

3. **Configure Account Information**
   - Enter account details as required
   - Ensure all lender information is complete

### Step 4: Configure Economic Terms and Fees

1. **Navigate to Economic & Fees Section**
   - Click on the **Economic & Fees** section tab

2. **Review Economic Terms**
   - Review interest rate calculations
   - Verify pricing index and margin
   - Configure fee structures

3. **Set Up Facility Rules**
   - Configure borrowing limits
   - Set drawdown frequency rules
   - Define other facility parameters

![Configure Rules](imagesByMdFilesFolder/37/ConfigureRules.png)

### Step 5: Complete Additional Sections

1. **Navigate Through Remaining Sections**
   - Complete all remaining sections as required
   - Each section has specific configuration fields
   - All data is auto-saved as you enter it

2. **Verify All Required Fields**
   - Ensure all mandatory fields are completed
   - Review each section for accuracy

### Step 6: Create Sub-Facilities (If Multiple Branch)

If you selected **Multiple** in the Basic section:

1. **Navigate to Review & Create Section**
   - In the final **Review & Create** section, you'll see a **Create Sub-Facility** button

2. **Create Sub-Facility**
   - Click **Create Sub-Facility**
   - A new sub-master commitment is created
   - All details except lenders are copied from the main facility

![Create Sub-Facility](imagesByMdFilesFolder/37/CreateSubFacility.png)

3. **Switch Between Facilities**
   - A dropdown appears at the top of the popup
   - Use this dropdown to switch between the main facility and sub-facilities
   - Each sub-facility can be configured separately

4. **Assign Lenders to Sub-Facilities**
   - Navigate to Parties & Accounts for the sub-facility
   - Add lenders from those selected in the main facility only
   - **Important**: No two sub-facilities can have the same lenders
   - Each lender can only be in one sub-facility

### Step 7: Review and Submit

1. **Navigate to Review & Create Section**
   - Click on the **Review & Create** section
   - Review all configured settings

2. **Verify Configuration**
   - Check that all lenders are properly assigned
   - Verify facility rules and parameters
   - Ensure all required fields are complete

3. **Click Create Facility**
   - Click the **Create Facility** button to finalize
   - Master commitment status changes from **Draft** to **PendingLenderApproval**
   - The facility is now shared with the selected lenders
   - Lenders see the facility in their **Opportunities** section

## Auto-Save Feature

- All data entered in the Create Facility popup is automatically saved
- You can exit and return later—your progress is preserved
- The master commitment remains in **Draft** status until you click Create Facility
- You can edit any section while in Draft status

## Rules & Validations

- **Only Draft Can Be Edited**: You can only configure master commitments in Draft status. Once submitted for lender approval, you cannot edit.

- **Lenders Must Be Selected**: You must add at least one lender before submitting for approval.

- **Sub-Facility Lender Rules**: For multiple-branch facilities:
  - Sub-facilities can only include lenders selected in the main facility
  - No two sub-facilities can have the same lenders assigned
  - Each lender can only belong to one sub-facility

- **All Fields Required**: All mandatory fields must be completed before you can click Create Facility.

- **Auto-Save Active**: Data is saved automatically as you enter it. You don't need to manually save.

## What Happens Next

**After Creating Facility:**
- Master commitment status changes to **PendingLenderApproval**
- Lenders see the facility in their Opportunities section
- Lenders can Review & Approve the facility

**After Lender Approval:**
- Any one lender approval activates the facility
- Status changes to **Active**
- Facility appears in Active Facilities tab
- You can now set up deal modelling

**After Deal Modelling Complete:**
- Borrower can map loans and create funding requests
- Funding workflow begins
