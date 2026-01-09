---
title: Master Commitment Overview
description: Learn what master commitments are and how they work
---

# Master Commitment Overview

## Overview

A master commitment is the finalized credit facility agreement that defines the complete facility structure. It's automatically created when a term sheet is approved by the facility agent. The facility agent then configures lenders, facility rules, and other parameters before submitting for lender approval. Once any lender approves, the facility becomes active.

## What Master Commitments Are

A master commitment is the complete agreement that defines how a credit facility will operate. It contains all the terms, rules, lender configurations, and parameters that govern facility operations.

Master commitments are **automatically created** from approved term sheets—you cannot create them manually. They start in Draft status with information pre-populated from the term sheet. The facility agent then configures the complete structure including lender groups, facility rules, and parameters.

## Purpose and Use Cases

**For Facility Structure** - Master commitments define the complete facility structure, including all rules, parameters, and configurations.

**For Lender Configuration** - Facility agents add lenders, set commitment amounts, and configure participation percentages.

**For Sub-Facility Management** - For multiple-lender arrangements, facility agents can create sub-master commitments with different lender groups.

**For Facility Activation** - Master commitments must be approved by lenders before facilities become active and borrowers can raise funding requests.

## Key Components

**Facility Terms** - Basic facility information from the approved term sheet: maximum facility amount, interest rates, advance rate, maturity date. This information is pre-populated and read-only.

**Lender Groups** - Configuration of lenders participating in the facility, including:
- Lender organization
- Commitment amount
- Voting percentage
- Individual approval tracking

**Sub-Facilities** - For multiple-branch master commitments:
- Main facility with all selected lenders
- Sub-facilities assigned to specific lender groups
- No two sub-facilities can have the same lenders

**Deal Modelling** - After activation, the facility agent sets up deal modelling to configure calculations and parameters needed before funding requests can be created.

## How Master Commitments Work

**1. Automatic Creation**

When a term sheet is approved by the facility agent, a master commitment is automatically created with **Draft** status. It appears as a dropdown under the approved term sheet in the facility agent's Credit Facility dashboard.

**2. Facility Agent Configuration**

The facility agent clicks **Create Facility** to open a comprehensive configuration popup with multiple sections:
- **Basic**: Select single or multiple branch facility
- **Parties & Accounts**: Add lenders and their commitment amounts
- **Economic & Fees**: Configure interest rates and fee structures
- **Additional Sections**: Complete all required configurations
- **Review & Create**: Final review and submission

![Create Master Commitment Facility](imagesByMdFilesFolder/14/CreateMasterCommitmentFacility.png)

All data is auto-saved as the facility agent enters it.

**3. Sub-Facility Creation (Multiple Branch)**

If multiple branch is selected, the facility agent can create sub-facilities:
- Click **Create Sub-Facility** in the Review & Create section
- A new sub-master commitment is created
- Use the dropdown at the top to switch between main and sub-facilities
- Assign lenders from the main facility to each sub-facility
- No two sub-facilities can have the same lenders

**4. Submission for Lender Approval**

Click **Create Facility** to finalize. Status changes from **Draft** to **PendingLenderApproval**. The facility is shared with selected lenders in their **Opportunities** section.

**5. Lender Approval**

Lenders see the facility in their Opportunities section with **Review & Approve** action. They review the facility details and click **Approve & E-Sign** to sign via Adobe Sign.

![Lender Approval - Master Commitment](imagesByMdFilesFolder/18/LenderApproval_MasterCommitment.png)

After any one lender approves and signs, the master commitment status changes to **Active**.

**6. Deal Modelling**

After activation, the facility agent completes deal modelling:
- Navigate to Active Facilities tab
- Click **Set Up Deal**
- Complete all sections in the deal modelling screen
- Click **Create** in the Review section
- Facility Setup Status changes to **Completed**

**7. Operational Use**

After deal modelling is complete:
- Borrower can map NFT-minted loans to the facility
- Borrower can create funding requests
- Funding workflow proceeds

## Important Points to Know

**Auto-Created Only** - Master commitments are automatically created when term sheets are approved. You cannot create them manually.

**Pre-Populated Data** - Term sheet data is pre-populated into the master commitment and is read-only.

**FA Configuration Required** - The facility agent must complete all configuration before submitting for lender approval.

**Sub-Facility Rules** - For multiple-branch facilities:
- Sub-facilities can only include lenders from the main facility
- No two sub-facilities can have the same lenders

**Any Lender Activates** - Once any one lender approves, the master commitment becomes Active.

**Deal Modelling Required** - After activation, deal modelling must be completed before borrowers can raise funding requests.

**No Edit After Active** - Once Active, the master commitment cannot be edited.
