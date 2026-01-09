---
title: Credit Facilities Overview
description: Learn what credit facilities are and how they work in the platform
---

# Credit Facilities Overview

## Overview

A credit facility is a lending arrangement where a borrower can draw down funds as needed, up to a pre-approved limit. In Intain Markets, credit facilities involve borrowers proposing terms via term sheets, facility agents reviewing and structuring the facility, and lenders approving and funding drawdowns. This module covers the complete credit facility workflow from term sheet creation to fund disbursement.

## What Credit Facilities Are

A credit facility is a flexible borrowing arrangement that allows borrowers to access funds incrementally rather than receiving everything upfront. Unlike traditional loans where you receive the full amount at once, credit facilities provide a pre-approved borrowing limit that you can draw from as needed through funding requests.

Credit facilities involve multiple components that progress through a structured workflow:
- **Term Sheets** propose the facility terms
- **Master Commitments** define the complete facility structure
- **Funding Requests** request specific drawdowns
- **Funding Notices** document approved drawdowns and coordinate fund transfer

## Purpose and Use Cases

**For Flexible Borrowing** - Borrowers can access funds as needed rather than receiving everything upfront, reducing unnecessary borrowing costs.

**For Structured Lending** - Lenders can provide capital through structured arrangements with proper oversight. Each drawdown is reviewed individually.

**For Ongoing Relationships** - Credit facilities support ongoing relationships between borrowers and lenders. Facilities remain active over time, allowing multiple drawdowns.

**For Controlled Disbursement** - Lenders maintain control over fund disbursement through individual drawdown approvals.

## Key Components

**Term Sheets** - Initial proposals that borrowers create to request credit facilities. Term sheets outline key terms like maximum facility amount, interest rates, repayment terms, and other conditions. They must be signed electronically (Adobe Sign) and submitted to the facility agent for review.

**Master Commitments** - Finalized credit facility agreements that define the complete facility structure. They're automatically created when term sheets are approved by the facility agent. The facility agent then configures lenders, facility rules, and other parameters before submitting for lender approval.

**Funding Requests** - Specific requests to draw down funds from an active facility. Borrowers create funding requests when they need funds, specifying the amount, funding date, purpose, and uploading collateral addendum. Each request must be reviewed and approved by the facility agent.

**Funding Notices** - Official documentation for each approved drawdown. They're automatically generated when funding requests are approved. The facility agent e-signs for each lender individually, and each lender can see the funding notice once the facility agent has e-signed for them.

**Deal Modelling** - Configuration of the facility parameters and calculations. After a master commitment becomes active, the facility agent sets up deal modelling before funding requests can be created.

## How Credit Facilities Work

**1. Term Sheet Creation (Borrower)**

The borrower logs in and navigates to the **Credit Facility** section from the left expandable menu. The dashboard shows term sheets and master commitments. Click **Term Sheet Setup** at the top right, which shows two options: **Create via Wizard** or **Upload Signed**.

In Create via Wizard, a popup appears where the borrower enters term sheet details (requested commitment amount, advance rate, margin, pricing index, maturity date, drawdown frequency, etc.) and clicks **Create Draft**. An Adobe Sign popup opens for the borrower to sign the term sheet. Initial status is **Draft**, and after signing it changes to **BorrowerSigned**.

After signing, a **Submit to FA** popup appears. If the borrower submits, the status changes to **FAReview**. If they cancel, they can submit later using the **Submit Term Sheet** action in the dashboard.

![Term Sheet Creation - Issuer](imagesByMdFilesFolder/14/Issuer_TermSheetCreation.png)

**2. Term Sheet Review (Facility Agent)**

The facility agent logs in and navigates to the **Credit Facility** section. The dashboard has top tiles and a table below with **Set-up** and **Active Facilities** tabs. In the Set-up section, term sheets are listed, and under approved term sheets, master commitments appear as a dropdown.

For term sheets in FAReview status, the action column shows **Review Term Sheet**. The facility agent clicks this to open a popup where they can view details, download attached documents, and make a decision:
- **Approve**: Status changes to **Accepted**, master commitment is automatically created
- **Reject**: Status changes to **Rejected**
- **Request Changes**: Status changes to **CHANGES_REQUESTED**, borrower can edit and resubmit

**3. Master Commitment Configuration (Facility Agent)**

When a term sheet is approved, a master commitment is automatically created with **Draft** status and appears as a dropdown under that term sheet. The action shows **Create Facility**.

The facility agent clicks **Create Facility** to open a comprehensive popup with multiple sections (Basic, Parties & Accounts, Economic & Fees, and more, ending with Review & Create).

![Create Master Commitment Facility](imagesByMdFilesFolder/14/CreateMasterCommitmentFacility.png)

In the **Basic** section, the facility agent selects whether this is a single or multiple branch master commitment.

In the **Parties & Accounts** section, the facility agent adds lenders that will participate in this facility.

If **multiple branch** is selected, a **Create Sub-Facility** button appears in the Review & Create section. The facility agent can create sub-master commitments. A dropdown at the top of the popup allows switching between sub-facilities and the main facility. Sub-facilities can only include lenders selected in the main facility, and no two sub-facilities can have the same lenders.

Everything in this popup is auto-saved as the facility agent enters data. When complete, the facility agent clicks **Create Facility** to finalize. The master commitment status changes to **PendingLenderApproval** and is shared with the selected lenders.

**4. Lender Approval**

Lenders log in and navigate to the **Opportunities** section from the left expandable menu. They see the main master commitment (if single) or the sub-master commitment assigned to them.

The action shows **Review & Approve**. The lender clicks this to open a popup where they can review all tabs and details of the facility.

![Credit Facility - Lender Approve](imagesByMdFilesFolder/14/CreditFacility_Lender_Approve.png)

If satisfied, the lender clicks **Approve & E-Sign**. An Adobe Sign popup opens for the lender to sign. After signing, the master commitment (or sub-master commitment) moves to the lender's **Credit Facility** tab.

After any one lender approves and signs, the master commitment status changes to **Active**.

**5. Deal Modelling (Facility Agent)**

After the master commitment becomes active, it appears in the facility agent's **Credit Facility** section under the **Active Facilities** tab.

The facility agent clicks **Set Up Deal** to open the deal modelling screen. There's a **Delegation** button if the facility agent wants the admin to do this on their behalf.

The deal modelling screen has multiple sections in the left menu that need to be filled. After completing all sections, the facility agent goes to the Review section and clicks **Create**. The **Facility Setup Status** changes from **In Progress** to **Completed**.

**6. Loan Mapping (Borrower)**

After deal modelling is complete, the borrower sees the master commitment in their Credit Facility section. The **Map Loans** action button is now enabled (along with **Funding Request**).

The borrower clicks **Map Loans** to see a screen showing mapped loans and totals. Click **Add Loans to Facility** to open a popup showing loans. Only loans with minted NFTs have enabled checkboxes. The borrower selects loans, clicks **Next**, then clicks **Map**. An error appears if a selected loan is already mapped to a different facility.

**7. Funding Request (Borrower)**

The borrower clicks **Funding Request** to open a popup where they enter:
- Draw amount
- Funding date
- Purpose of funds
- Draw currency
- Upload Collateral Addendum

Click **Review** to create the funding request (status: **Draft**). Click **Submit** to submit to the facility agent for review (status: **FAReview**).

![Funding Request Creation - Issuer](imagesByMdFilesFolder/14/FundingRequest_Creation_Issuer.png)

**8. Funding Request Review (Facility Agent)**

The facility agent sees the funding request in the Credit Facility section. The action shows **Review Funding Request**. The facility agent clicks this and can:
- **Approve**: Funding notice is generated with status **Pending Token Generated**
- **Reject**: Status changes to **Rejected**
- **Request Changes**: Status changes to **CHANGES_REQUESTED**

No e-sign is required for funding request approval. After clicking **Approve**, the facility agent clicks the **Approve** button on the funding notice.

**9. Funding Notice E-Sign (Facility Agent)**

After approving the funding request, a funding notice is generated. The funding notice shows **E-sign (0/n)** where n is the number of lenders.

The facility agent clicks E-sign and signs the document for each lender individually using Adobe Sign. Each time the facility agent signs, the count updates (1/n, 2/n, etc.). As each lender's e-sign is completed, that lender can see the funding notice in their Credit Facility section.

![Funding Notice Details - FA](imagesByMdFilesFolder/14/FundingNoticeDetailsFA.png)

**10. Lender Fund Transfer**

Lenders go to the **Credit Facility** section where they see **Review Funding Notice**. They open the funding notice, select the payment method, and after payment is complete, click **Confirm and Settle**.

After confirmation, tokens are transferred and the amount is transferred to the borrower.

![Confirm and Settle - Lender](imagesByMdFilesFolder/ConfirmAndSettleInvestor.png)

## Important Points to Know

**Term Sheet E-Sign Required** - Borrowers must sign the term sheet via Adobe Sign before submitting to the facility agent.

**Auto-Creation of Master Commitment** - When a term sheet is approved, the master commitment is automatically created. You don't create it manually.

**Sub-Facilities for Multiple Lenders** - If multiple branch is selected, the facility agent can create sub-facilities to assign different lenders to different sub-facilities. No two sub-facilities can have the same lenders.

**Deal Modelling Before Funding** - The facility agent must complete deal modelling before borrowers can raise funding requests.

**Only NFT-Minted Loans** - Only loans with minted NFTs can be mapped to master commitments for credit facility transactions.

**E-Sign for Each Lender** - The facility agent e-signs the funding notice for each lender individually. Each lender can see the funding notice once their e-sign is completed.

**Lender Confirms Fund Transfer** - After the lender transfers funds, they click Confirm and Settle to complete the process.
