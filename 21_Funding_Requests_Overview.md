---
title: Funding Requests Overview
description: Learn what funding requests are and how to create them
---

# Funding Requests Overview

## Overview

A funding request is how borrowers draw down funds from an active credit facility. After a master commitment is active and deal modelling is complete, borrowers can create funding requests specifying the amount, purpose, funding date, and uploading supporting documentation. Each request is reviewed by the facility agent before funds can be disbursed.

## What Funding Requests Are

A funding request is a specific request to borrow a portion of your approved facility limit. You specify how much you need, when you need it, what the funds are for, and upload supporting documentation. Each funding request is reviewed individually by the facility agent.

You can create multiple funding requests over time as long as you stay within your facility limits. Each request goes through its own review and approval process, and approved requests trigger the automatic generation of funding notices.

## Purpose and Use Cases

**For Incremental Borrowing** - Request specific amounts as needed rather than borrowing the full facility limit at once.

**For Purpose-Specific Drawdowns** - Each request specifies the purpose of the funds.

**For Ongoing Capital Access** - Create multiple funding requests over time throughout the facility term.

**For Controlled Disbursement** - Each drawdown is reviewed individually before funds are disbursed.

## Key Components

**Draw Amount** - The specific amount you want to borrow from your available capacity.

**Funding Date** - When you need the funds.

**Purpose of Funds** - Description of what the funds will be used for.

**Draw Currency** - The currency for the drawdown.

**Collateral Addendum** - Supporting documentation uploaded with the request.

## How Funding Requests Work

**1. Prerequisites**

Before creating a funding request:
- Master commitment must be **Active**
- Facility Setup Status must be **Completed** (deal modelling done)
- You may need to map NFT-minted loans to the facility first

**2. Creating the Request**

Navigate to Credit Facility section and click **Funding Request** on your active master commitment. A popup opens where you enter:
- Draw amount
- Funding date
- Purpose of funds
- Draw currency
- Upload Collateral Addendum

![Funding Request Creation - Issuer](imagesByMdFilesFolder/21/FundingRequest_Creation_Issuer.png)

**3. Review and Submit**

Click **Review** to create the funding request (status: DRAFT). Click **Submit** to send to the facility agent for review (status: FAReview).

![Funding Request Submit - By Issuer](imagesByMdFilesFolder/21/funding_request_Submit_By_Issuer.jpg)

**4. Facility Agent Review**

The facility agent reviews the request and can:
- **Approve**: Funding notice is generated (Pending Token Generated)
- **Reject**: Status changes to REJECTED
- **Request Changes**: Status changes to CHANGES_REQUESTED

No e-sign is required for funding request approval.

![Review Funding Request - FA Review](imagesByMdFilesFolder/21/review_funding_request_FAReview.png)

**5. After Approval**

When approved:
- Funding notice is automatically generated
- FA clicks Approve on funding notice
- FA e-signs for each lender (E-sign 0/n)
- Each lender can see the funding notice once their e-sign is complete
- Lenders review, transfer funds, and Confirm and Settle
- Funds are disbursed to borrower

## Funding Request Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| DRAFT | Created, not submitted | Edit, Submit |
| FAReview | Submitted, awaiting FA decision | View only |
| APPROVED | Approved, funding notice generated | View |
| REJECTED | Rejected (final) | Create new request |
| CHANGES_REQUESTED | FA requested modifications | Edit, resubmit |

## Important Points to Know

**Active Facility Required** - Funding requests can only be created for Active master commitments.

**Deal Modelling Required** - Facility Setup Status must be Completed before you can create funding requests.

**Map Loans First** - You may need to map NFT-minted loans to the facility before creating funding requests.

**One at a Time** - Submit one funding request at a time and wait for the decision.

**Rejected Is Final** - Rejected requests cannot be resubmitted; create a new request.

**Auto-Generated Notices** - Approved requests automatically generate funding notices.
