---
title: Funding Requests Overview
description: Learn what funding requests are and how to create them
---

# Funding Requests Overview

## Overview

A funding request is when a borrower requests to draw down funds from an active credit facility. Each request specifies the amount needed, the purpose, includes supporting documentation, and must be reviewed and approved by the facility agent before funds can be disbursed.

## What Funding Requests Are

A funding request is a specific request to borrow a portion of your approved facility limit. You specify how much you need, what you'll use it for, and provide documentation to support your request. Each funding request is reviewed individually by facility agents to ensure it complies with facility rules and that sufficient borrowing capacity is available.

Funding requests are separate from the facility itself—you can create multiple funding requests over time as long as you stay within your facility limits. Each request goes through its own review and approval process, and approved requests trigger the creation of funding notices that are sent to lenders for their review and approval.

## Purpose and Use Cases

Funding requests enable flexible access to approved facility limits:

**For Incremental Borrowing** - You can request specific amounts as needed rather than borrowing the full facility limit at once.

**For Purpose-Specific Drawdowns** - Each request specifies the purpose of the funds, allowing you to request funds for specific business needs.

**For Ongoing Capital Access** - You can create multiple funding requests over time, providing ongoing access to capital throughout the facility term.

**For Controlled Disbursement** - Each drawdown is reviewed individually, ensuring proper oversight and compliance with facility rules.

**For Capacity Management** - Funding requests are evaluated against available borrowing capacity, ensuring you stay within approved limits.

**For Documentation** - Each request includes supporting documentation, providing transparency and justification for fund usage.

## Key Components

**drawAmount** - The specific amount you want to borrow (numeric field). This must be within your available borrowing capacity, which is calculated based on facility rules and current utilization. You can request any amount up to your available capacity.

**purposeOfFunds** - A detailed description of what the funds will be used for (string field). This helps facility agents and lenders understand how funds will be used and evaluate the request appropriately.

**fundingDate** - When you need the funds (date field). This helps coordinate timing and ensures funds are available when needed.

**Supporting Documentation** - Documents that justify the request and demonstrate compliance with facility rules. Document fields include: **collateralAddendum** (collateral addendum document, stored in IPFS), **financialStatements** (financial statements, stored in IPFS), **kycDocuments** (KYC documentation, stored in IPFS). Document history arrays track upload history.

**Collateral Information** - Collateral information is included in the collateralAddendum document. If the facility requires collateral, you specify which loans or assets will be used, including collateral details, descriptions, and valuations if required.

**Status** - The current stage of the request in its workflow, such as DRAFT, FAReview, APPROVED, REJECTED, or CHANGES_REQUESTED. Status determines what actions are available and what needs to happen next.

## How Funding Requests Work

**Creation** - You create funding requests against active facilities by specifying the amount, purpose, funding date, and uploading supporting documentation. Requests start in DRAFT status, allowing you to work on them before submission.

![Funding Request Creation - Issuer](imagesByMdFilesFolder/21/FundingRequest_Creation_Issuer.png)

**Submission** - When ready, you submit funding requests to facility agents for review. Status changes to FAReview, and facility agents evaluate the request for compliance with facility rules and available borrowing capacity.

![Funding Request Submit - By Issuer](imagesByMdFilesFolder/21/funding_request_Submit_By_Issuer.jpg)

**Facility Agent Review** - Facility agents review requests to ensure they comply with facility rules, verify sufficient borrowing capacity is available, review documentation, and assess overall request quality. They can approve, reject, or request changes.

![Review Funding Request - FA Review](imagesByMdFilesFolder/21/review_funding_request_FAReview.png)

**Approval Outcomes** - When approved, funding notices are automatically created. When rejected, you receive a reason and can create new requests. When changes are requested, you can update and resubmit.

**Funding Notice Generation** - Approved requests automatically trigger funding notice creation. Funding notices document the approved drawdown and are sent to lenders for review. Tokens are generated, and the drawdown process proceeds.

**Lender Review** - Lenders review funding notices and approve or reject individual drawdowns. Each lender makes independent decisions, and participation is tracked individually.

**Fund Disbursement** - After lender approval, funds are transferred to borrowers. Lenders confirm transfers, completing the drawdown process.

## Important Points to Know

**Flexible Drawdowns** - You can request any amount up to your available borrowing capacity, not necessarily the full facility limit.

**Individual Review** - Each funding request is reviewed individually by facility agents to ensure compliance with facility rules and available borrowing capacity.

**Automatic Notice Generation** - When approved, funding notices are automatically generated and sent to lenders for review and approval.

**Multiple Requests Over Time** - You can create multiple funding requests over time as long as you stay within your facility limits and available borrowing capacity.

**Three Possible Outcomes** - Facility agents can approve requests (creating funding notices), reject requests (requiring new requests), or request changes (allowing updates and resubmission).

**Complete Documentation** - All funding requests are documented with complete details, supporting documentation, and audit trails.

**Status Tracks Progress** - Request status shows where each request is in its workflow, from creation through review to approval or rejection.
