---
title: Funding Notices Overview
description: Learn what funding notices are and how they work in credit facilities
---

# Funding Notices Overview

## Overview

Funding notices are official documents generated when funding requests are approved. They document each drawdown from a credit facility, including the amount, allocation to lenders, and coordination of fund transfer. The funding notice workflow ensures proper e-signing by the facility agent and fund transfer by lenders.

## What Funding Notices Are

A funding notice is the formal documentation of an approved drawdown from a credit facility. When a borrower's funding request is approved by the facility agent, the system automatically generates a funding notice. This notice tracks the e-signature process and fund transfer from lenders.

Funding notices contain:
- Drawdown amount and date
- Allocation to each lender
- E-signature status for each lender
- Fund transfer confirmation status

## Purpose and Use Cases

**For Documenting Drawdowns** - Funding notices create a formal record of each drawdown from the facility, documenting amounts, dates, and participating lenders.

**For Coordinating Fund Transfer** - The funding notice workflow coordinates the steps required to transfer funds from lenders to the borrower.

**For E-Signature Tracking** - Funding notices track the facility agent's e-signature for each lender individually.

**For Tracking Lender Participation** - Each lender's portion and fund transfer confirmation status are tracked individually.

## How Funding Notices Work

**1. Auto-Generation**

When a funding request is approved by the facility agent, the system automatically generates a funding notice with status **Pending Token Generated**.

**2. Facility Agent Approval**

The facility agent clicks **Approve** on the funding notice.

**3. Facility Agent E-Sign for Each Lender**

In the facility agent's Credit Facility section (Active Facilities tab), the funding notice shows **E-sign (0/n)** where n is the number of lenders.

The facility agent clicks E-sign and signs the document for each lender individually using Adobe Sign. Each time the facility agent signs, the count updates (1/n, 2/n, etc.).

![Funding Notice Details - FA](imagesByMdFilesFolder/24/FundingNoticeDetailsFA.png)

**4. Lender Visibility**

As the facility agent completes each lender's e-sign, that lender can see the funding notice in their Credit Facility section.

**5. Lender Fund Transfer**

Lenders go to their Credit Facility section and see **Review Funding Notice**. They review the notice, select a payment method, transfer funds, and click **Confirm and Settle**.

![Confirm and Settle - Lender](imagesByMdFilesFolder/ConfirmAndSettleInvestor.png)

**6. Process Completion**

After lenders confirm settlement, tokens are transferred and the borrower receives the funds. Each lender's confirmation is tracked individually.

## Individual Lender Tracking

Each lender in the funding notice has individual tracking:

| Field | Description |
|-------|-------------|
| E-signature Status | Whether FA has signed for this lender |
| Fund Transfer Status | Whether lender has confirmed transfer |

## Important Points to Know

**Auto-Generated** - Funding notices are automatically created when funding requests are approved. You cannot create them manually.

**FA Signs Per Lender** - The facility agent must e-sign for each lender individually. The E-sign (0/n) counter shows progress.

**Lender Visibility After E-Sign** - Each lender sees the funding notice once the facility agent has completed the e-sign for that specific lender.

**Individual Tracking** - Each lender's participation is tracked separately. Lenders confirm their own fund transfers independently.

**Confirm and Settle** - After transferring funds, lenders click Confirm and Settle to complete the process.
