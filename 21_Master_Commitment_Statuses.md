---
title: Master Commitment Statuses
description: >-
  Understand master commitment statuses from creation through lender approval
  and active use
---

# Master Commitment Statuses

## Overview

A master commitment is the agreement for a credit facility. Its status shows who must act next. Lender approval also uses an e-signature, and each lender has their own decision.

## Lifecycle Overview

```
Term Sheet Approved
  → Master commitment is created (Draft)
    → Facility agent configures the facility
      → Facility agent clicks Create Facility (Pending Lender Approval)
        → Any one lender clicks Approve & E-Sign (Active)
          → Facility agent finishes deal modelling (Facility Setup Completed)
            → Funding can begin
```

A fourth status, **InActive**, means the facility has been turned off.

## Status Meanings

### Draft

The master commitment was created automatically from an approved term sheet. The facility agent is still configuring it. Initial details are copied from the term sheet.

The facility agent can edit:

1. **Basic Information** — Name, revolving or term, total commitment, currency, effective date, maturity date, and whether the facility has multiple branches
2. **Parties & Accounts** — Borrower, lenders with amounts and percentages, bank accounts, and payment instructions
3. **Conditions** — Conditions precedent, conditions subsequent, and drawdown conditions
4. **Pricing** — Fixed or floating rate, base rate, spread, margin, and fees
5. **Covenants** — Financial, reporting, and other covenants

During Draft the facility agent can also:

* Add lenders and set each lender’s amount and percentage
* Create, edit, or delete sub-facilities when the facility is set up as multiple branch. Each sub-facility has its own name, type, amount, and currency
* Leave and return later. Entries save as you go

Click **Create Facility** to move from **Draft** to **Pending Lender Approval**. The facility is then shared with the selected lenders.

On the facility agent’s dashboard, the commitment appears under the approved term sheet. The action is **Create Facility**.

### Pending Lender Approval

The facility agent has submitted the commitment. Lenders can review it. Editing is closed.

Lenders see it in **Opportunities** under Credit Facility. **Review & Approve** opens the full details. **Approve & E-Sign** signs the commitment. A lender can reject and give a reason.

The facility agent can view the submission and see each lender’s decision, but cannot edit it.

| Lender Status | Meaning                          |
| ------------- | -------------------------------- |
| **pending**   | No decision yet                  |
| **approved**  | The lender approved and e-signed |
| **rejected**  | The lender rejected              |

If any one lender approves, the commitment becomes **Active**. Other lenders can still decide. One rejection does not block another lender’s approval.

For lenders, the action is **Review & Approve**.

### Active

At least one lender has approved and completed the e-signature in Adobe Sign or ZohoSign. The time of that approval is recorded. What you can do next depends on **Facility Setup Status**.

The facility agent can:

* **Set Up Deal** while Facility Setup Status is In Progress. Sections include Basic Details, Parties & Accounts, Fee Structure, Interest Rate, Covenants, Waterfall, and Review
* Send deal modelling to an admin
* Review funding requests after setup is complete (approve, reject, or request changes)
* Approve funding notices and e-sign for each lender
* Follow settlement

After Facility Setup Status is **Completed**, the borrower can map loans that have an NFT and create funding requests.

Lenders see the facility under **Credit Facility**. They can review a funding notice after the facility agent has e-signed it for them, then click **Confirm and Settle** after sending funds.

* Facility agent: **Active Facilities**, with **Set Up Deal** or **Review Funding Request**
* Lender: **View Facility** and **Review Funding Notice** when a notice is ready
* Borrower: **Map Loans** and **Create Funding Request** only after Facility Setup is Completed

### InActive

The facility has been closed or turned off. No new funding requests or funding notices can be created. The record stays available for history. This status does not return to Active.

## Additional Status: Facility Setup Status

After the commitment is Active, Facility Setup Status tracks deal modelling.

| Facility Setup Status | Meaning                        | Borrower can map loans | Borrower can create a funding request |
| --------------------- | ------------------------------ | ---------------------- | ------------------------------------- |
| **In Progress**       | Deal modelling is not finished | No                     | No                                    |
| **Completed**         | Deal modelling is finished     | Yes                    | Yes                                   |

See [Facility Setup Status](22_Facility_Setup_Status.md).

## What Each Status Indicates

| Status                      | Triggered By                                | Who Acts Next                              | Key Actions                                                                               |
| --------------------------- | ------------------------------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------- |
| **Draft**                   | Term sheet approved (created automatically) | Facility Agent                             | Configure sections, add lenders, create sub-facilities, Create Facility                   |
| **Pending Lender Approval** | Facility agent clicks Create Facility       | Lender                                     | Review & Approve, Approve & E-Sign, or reject                                             |
| **Active**                  | Any one lender approves and e-signs         | Facility agent, then borrower, then lender | Set Up Deal, Map Loans, Create Funding Request, Review Funding Notice, Confirm and Settle |
| **InActive**                | The facility is deactivated                 | None                                       | View history only                                                                         |

* Master commitments are created when a term sheet is approved. There is no separate create step.
* Any one lender’s approval activates the facility.
* Each lender has their own approval and e-sign result. One rejection does not stop the others.
* Lender approval requires Adobe Sign or ZohoSign.
* Draft entries save as you work.
* Sub-facilities are available only on a multiple-branch facility.
* Borrowers cannot request funds until Facility Setup Status is **Completed**, even if the commitment is already Active.
* The facility agent can send deal modelling to an admin while setup is still in progress.
