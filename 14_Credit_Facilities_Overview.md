---
title: Credit Facilities Overview
description: Learn what credit facilities are and how they work in the platform
---

# Credit Facilities Overview

## Overview

A credit facility is a lending arrangement where a borrower can draw down funds as needed, up to a pre-approved limit. You get approved for a maximum amount and can borrow portions of it when needed, rather than receiving all funds at once. Credit facilities provide flexibility for borrowers while giving lenders control over fund disbursement.

## What Credit Facilities Are

A credit facility is a flexible borrowing arrangement that allows borrowers to access funds incrementally rather than receiving everything upfront. Unlike traditional loans where you receive the full amount at once, credit facilities provide a pre-approved borrowing limit that you can draw from as needed. Each drawdown is a separate funding request that must be reviewed and approved before funds are disbursed.

Credit facilities involve multiple components: term sheets propose the facility, master commitments define the complete facility structure, funding requests request specific drawdowns, and funding notices document approved drawdowns. The facility remains active over time, supporting multiple drawdowns as long as you stay within approved limits.

## Purpose and Use Cases

Credit facilities serve several important purposes:

**For Flexible Borrowing** - Borrowers can access funds as needed rather than receiving everything upfront, reducing unnecessary borrowing costs.

**For Structured Lending** - Lenders can provide capital through structured arrangements with proper oversight. Each drawdown is reviewed individually, ensuring compliance with facility rules.

**For Ongoing Relationships** - Credit facilities support ongoing relationships between borrowers and lenders. Facilities remain active over time, allowing multiple drawdowns.

**For Controlled Disbursement** - Lenders maintain control over fund disbursement through individual drawdown approvals.

**For Capacity Management** - Facilities track borrowing capacity, utilization, and available capacity, ensuring borrowers stay within approved limits.

## Key Components

**Term Sheets** - Initial proposals that borrowers create to request credit facilities. Term sheets outline key terms like maximum facility amount, interest rates, repayment terms, and other conditions. They must be signed electronically and submitted for facility agent review.

**Master Commitments** - Finalized credit facility agreements that define the complete facility structure. They're automatically created when term sheets are approved and contain all the rules, parameters, lender information, and borrowing base calculations needed to operate the facility.

**Funding Requests** - Specific requests to draw down funds from an active facility. Borrowers create funding requests when they need funds, specifying the amount, purpose, and providing supporting documentation. Each request must be reviewed and approved.

**Funding Notices** - Official documentation for each approved drawdown. They're automatically generated when funding requests are approved and contain details about the drawdown, token distribution to lenders, and fund transfer instructions.

**Facility Rules** - Rules that govern how the facility operates, including borrowing limits, collateral eligibility, drawdown frequency, repayment terms, and other requirements. These rules are defined in master commitments and enforced throughout the facility lifecycle.

**Borrowing Base Calculations** - Formulas and rules that determine how much you can borrow based on collateral, financial metrics, or other factors. Borrowing base calculations determine available borrowing capacity.

## How Credit Facilities Work

**Term Sheet Proposal** - Borrowers create term sheets proposing credit facilities with key terms. Term sheets are signed electronically and submitted to facility agents for review. Facility agents can approve, reject, or request changes.

![Term Sheet Creation - Issuer](imagesByMdFilesFolder/14/Issuer_TermSheetCreation.png)

**Master Commitment Creation** - When term sheets are approved (status: 'Accepted'), master commitments are automatically created via autoCreateMasterCommitment function. System generates masterCommitmentId (format: MC-MMDDYYYY-XXXX), creates master commitment with Draft status, pre-populates with term sheet data (facilityType, advanceRate, margin, pricingIndex, maturityDate, drawFrequency, covenantTemplate, totalCommitmentAmount, marketMakerOrgId, issuerOrgId, issuerId), initializes empty arrays (collateralRules: [], lenderGroups: []), sets facilitySetupModelStatus: 'In Progress', requiredFieldsCompleted: false, contractType: 'single'. Facility agents configure the complete facility structure, including facility rules, borrowing base calculations, lender groups, and other parameters.

![Create Master Commitment Facility](imagesByMdFilesFolder/14/CreateMasterCommitmentFacility.png)

**Lender Approval** - After facility agents configure master commitments, they finalize via POST /cf/createMasterCommitment (status: Draft → PendingLenderApproval). Lenders review and approve via DocuSign (GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign&envelopeId=123&masterCommitmentId=MC-456&lenderOrgId=LENDER-789). System updates lenderGroup: sets lenderStatus to 'esignature_completed', sets approvedAt timestamp. System checks if master commitment status is not already ACTIVE. If not ACTIVE, system updates status: PendingLenderApproval → ACTIVE, calls sendMasterCommitmentToIA function. Any lender approval activates the facility, making it operational for funding requests.

![Credit Facility - Lender Approve](imagesByMdFilesFolder/14/CreditFacility_Lender_Approve.png)

**Funding Requests** - Once facilities are active, borrowers can create funding requests to draw down funds. Each request specifies the amount, purpose, and includes supporting documentation. Facility agents review requests for compliance and available capacity.

![Funding Request Creation - Issuer](imagesByMdFilesFolder/14/FundingRequest_Creation_Issuer.png)

**Funding Notice Generation** - When funding requests are approved (status: FAReview → APPROVED), funding notices are automatically generated via generateFundingNotice function with PENDING_TOKEN_GENERATION status. Facility agents call updateTokenDistribution (PATCH /cf/funding-notices/:fundingNoticeId/token-distribution) which creates FT tokens and changes status to TOKEN_GENERATED. Facility agents sign DocuSign for each lender individually (status remains TOKEN_GENERATED, individual lender esignatureStatus updated to ESIGN_COMPLETED). Borrowers approve token transfers (POST /cf/funding-notices/:fundingNoticeId/approve-token-transfer) which changes status to TOKEN_APPROVED, making notices visible to lenders.

![Funding Notice Details - FA](imagesByMdFilesFolder/14/FundingNoticeDetailsFA.png)

**Lender Review and Approval** - Lenders review funding notices and approve or reject individual drawdowns. Each lender makes independent decisions, and participation is tracked individually.

![Lender Approval - Funding Notice](imagesByMdFilesFolder/14/LenderApprovalFundingNotice.png)

**Fund Disbursement** - After lenders approve, they transfer funds and confirm transfers. Funds are disbursed to borrowers, completing the drawdown process.

![Fund Transfer Confirmation](imagesByMdFilesFolder/14/Fund Transfer Confirmation.png)

**Active Facilities View** - The credit facility dashboard shows all active facilities, allowing you to view facility details, check borrowing capacity, and access funding request options.

![Credit Facility - Active Facilities Tab - Issuer](imagesByMdFilesFolder/14/credit_facility_active_facilities_tab_issuer.png)

## Important Points to Know

**Flexible Drawdowns** - Credit facilities allow borrowers to request specific amounts as needed, up to approved limits. Each drawdown is a separate funding request that must be reviewed and approved.

**Structured Approval Process** - Each component requires appropriate approvals—term sheets need facility agent approval, master commitments need lender approval, and funding requests need facility agent and lender approval.

**Automatic Generation** - Master commitments are automatically created when term sheets are approved, and funding notices are automatically created when funding requests are approved.

**Individual Lender Tracking** - Each lender's participation is tracked individually, allowing for independent decisions. Lenders can approve or reject individual drawdowns based on their own criteria.

**Borrowing Capacity Management** - Facilities track borrowing capacity, utilization, and available capacity, ensuring borrowers stay within approved limits.

**Multiple Drawdowns Over Time** - You can create multiple funding requests over time as long as you stay within facility limits and available borrowing capacity.

**Complete Documentation** - All facility activities are documented with complete audit trails, ensuring transparency and supporting compliance.
