---
title: Master Commitment Statuses
description: >-
  Understand the complete master commitment lifecycle — from auto-creation
  through lender approval to active operations — including all statuses,
  actions, and role-specific behaviors
---

# Master Commitment Statuses

## Overview

Master commitments are the binding agreements at the heart of every credit facility. They progress through a defined set of statuses from auto-creation to operational use, and understanding these statuses helps you know what actions are available, who needs to act next, and what each transition means for the facility. The master commitment lifecycle is tightly coupled with e-signature workflows and per-lender tracking, making it important to understand both the overall commitment status and the individual lender statuses within it.

## Lifecycle Overview

The master commitment follows this progression:

```
Term Sheet Approved
  → Auto-Create Master Commitment (status: Draft)
    → FA Configures Facility Sections
      → FA Clicks "Create Facility" (status: PendingLenderApproval)
        → Any One Lender Clicks "Approve & E-Sign" (status: Active)
          → FA Completes Deal Modelling (facilitySetupStatus: Completed)
            → Full Funding Workflow Available
```

There is also a fourth status — **InActive** — for facilities that have been deactivated.

## Status Meanings

### Draft

**What This Status Represents:** The master commitment has been **automatically created** from an approved term sheet, and the facility agent is configuring the facility details. This is the initial configuration phase where all the facility parameters are set up.

**When This Occurs:**

* Immediately and automatically after a term sheet is approved by the facility agent
* The system creates the master commitment and populates initial fields from the approved term sheet data

**What the Facility Agent Can Do During Draft:**

The facility agent has full editing access to configure the facility through multiple sections:

1. **Basic Information** — Facility name, facility type (revolving or term), total commitment amount, currency, effective date, maturity date, and multi-branch configuration
2. **Parties & Accounts** — Borrower details, lender list with individual commitment amounts and percentages, bank account details for each party, and payment instructions
3. **Conditions** — Conditions precedent, conditions subsequent, and drawdown conditions
4. **Pricing** — Interest rate type (fixed or floating), base rate reference, spread, margin, fees (upfront, commitment, agent fees)
5. **Covenants** — Financial covenants, reporting covenants, and other covenant requirements

**Additional Draft Capabilities:**

* **Add Lenders** — Add participating lenders and set their individual commitment amounts and percentage allocations
* **Create Sub-Facilities** — If the facility is configured as multi-branch (`isMultiBranch: true`), the facility agent can create sub-facilities, each with its own name, type, amount, and currency
* **Edit Sub-Facilities** — Modify or delete sub-facilities during Draft
* **Auto-Save** — All data auto-saves as the facility agent enters information in each section, so progress is preserved across sessions

**What Happens Next:**

* The facility agent clicks **Create Facility** to finalize the configuration and submit it for lender approval
* The status transitions from **Draft** to **PendingLenderApproval**
* The facility is shared with the selected lenders

**Dashboard View:**

* Appears under the approved term sheet as a dropdown for the facility agent
* Action column displays: **Create Facility**

### PendingLenderApproval

**What This Status Represents:** The facility agent has completed the facility configuration and submitted the master commitment for lender review and approval. The facility is now visible to the selected lenders, who can review the details and decide whether to approve.

**When This Occurs:**

* After the facility agent clicks **Create Facility** in the Draft stage
* All configured sections (Basic, Parties & Accounts, Conditions, Pricing, Covenants) have been completed

**What Lenders Can Do:**

* See the master commitment in their **Opportunities** section under Credit Facility
* Click **Review & Approve** to open the full facility details
* Review all configuration sections — basic information, parties, conditions, pricing, covenants
* Click **Approve & E-Sign** to formally approve and digitally sign the master commitment
* Choose to reject if the terms are not acceptable, providing a rejection reason

**What the Facility Agent Can Do:**

* View the submitted facility details (editing is no longer available)
* Monitor which lenders have reviewed and what their decisions are
* Wait for at least one lender to approve

**Per-Lender Approval Tracking:** Each lender in the master commitment has their own individual approval status:

| Lender Status | Meaning                                         |
| ------------- | ----------------------------------------------- |
| **pending**   | Lender has not yet made a decision              |
| **approved**  | Lender has approved and e-signed the commitment |
| **rejected**  | Lender has rejected the commitment              |

**What Happens Next:**

* **Any single lender approves** → The master commitment status changes to **Active**. The entire facility becomes operational even if other lenders have not yet decided. This is a key business rule: one lender's approval activates the facility.
* **A lender rejects** → That individual lender's status is marked as rejected, but this does not block other lenders from approving. The overall commitment status only changes to Active once any lender approves.

**Dashboard View (Lenders):**

* Appears in the **Opportunities** section
* Action column displays: **Review & Approve**

### Active

**What This Status Represents:** At least one lender has approved and e-signed the master commitment. The facility is now operational, and the next steps depend on whether deal modelling has been completed (tracked by the **Facility Setup Status**).

**When This Occurs:**

* After any one lender completes the **Approve & E-Sign** process, including successfully completing the e-signature via Adobe Sign or ZohoSign
* The lender's `approvedAt` timestamp is recorded

**What the Facility Agent Can Do:**

* **Set Up Deal** — Complete deal modelling (if Facility Setup Status is In Progress). This involves configuring Basic Details, Parties & Accounts, Fee Structure, Interest Rate, Covenants, Waterfall, and the Review section
* **Delegate Deal Modelling** — Transfer the deal modelling task to the admin role if needed
* **Review Funding Requests** — Once deal modelling is complete and borrowers submit funding requests, the facility agent reviews and makes decisions (approve, reject, or request changes)
* **Approve Funding Notices** — Approve generated funding notices and e-sign for each lender
* **Process Settlements** — Monitor and manage the settlement process

**What Borrowers Can Do (after Facility Setup Status is Completed):**

* **Map Loans** — Map NFT-minted loans to the credit facility
* **Create Funding Requests** — Submit drawdown requests specifying amount, purpose, drawdown date, maturity date, and supporting documentation

**What Lenders Can Do:**

* View the facility in their **Credit Facility** section
* **Review Funding Notices** — When the facility agent has generated and e-signed a funding notice for them
* **Confirm Fund Transfers** — After reviewing a funding notice and transferring funds, click Confirm and Settle

**Dashboard View (Facility Agent):**

* Appears in the **Active Facilities** tab
* Action displays: **Set Up Deal** (if Facility Setup In Progress), then **Review Funding Request** (after deal modelling is complete and requests are submitted)

**Dashboard View (Lenders):**

* Appears in the **Credit Facility** section
* Actions: **View Facility**, **Review Funding Notice** (when available)

**Dashboard View (Borrowers):**

* Actions: **Map Loans** and **Create Funding Request** (enabled only after Facility Setup Completed)

### InActive

**What This Status Represents:** The facility has been deactivated. This status is used when a credit facility is closed or administratively deactivated. No further operational actions can be performed on an inactive facility.

**When This Occurs:**

* Administrative or business-driven facility deactivation
* The facility is no longer operational

**What This Means:**

* No new funding requests can be created
* No new funding notices can be generated
* The facility data remains accessible for historical reference and audit purposes
* This is a terminal status for the facility

## Additional Status: Facility Setup Status

After a master commitment becomes Active, a secondary status — **Facility Setup Status** — tracks whether deal modelling has been completed. This status is critical because it gates borrower access to the funding workflow.

| Facility Setup Status | Meaning                         | Borrower Can Map Loans | Borrower Can Create Funding Request |
| --------------------- | ------------------------------- | ---------------------- | ----------------------------------- |
| **In Progress**       | Deal modelling not yet complete | No                     | No                                  |
| **Completed**         | Deal modelling complete         | Yes                    | Yes                                 |

For full details on the deal modelling process and Facility Setup Status, see the [Facility Setup Status](22_Facility_Setup_Status.md) article.

## What Each Status Indicates

### Complete Status Summary

| Status                    | Triggered By                       | Who Acts Next          | Key Actions Available                                                                   |
| ------------------------- | ---------------------------------- | ---------------------- | --------------------------------------------------------------------------------------- |
| **Draft**                 | Term sheet approved (auto-created) | Facility Agent         | Configure all sections, add lenders, create sub-facilities, Create Facility             |
| **PendingLenderApproval** | FA clicks Create Facility          | Lender(s)              | Review & Approve, Approve & E-Sign (or reject)                                          |
| **Active**                | Any one lender approves & e-signs  | FA → Borrower → Lender | Set Up Deal, Map Loans, Create Funding Request, Review Funding Notice, Confirm & Settle |
| **InActive**              | Administrative deactivation        | None                   | Read-only access for historical reference                                               |

### Key Business Rules

* **Auto-Creation** — Master commitments are automatically created when a term sheet is approved. There is no manual "create master commitment" step.
* **Single Lender Activation** — Any single lender's approval activates the entire facility. All lenders do not need to approve.
* **Individual Lender Tracking** — Each lender has their own approval status, e-sign status, and approval timestamp. One lender's rejection does not prevent other lenders from approving.
* **E-Signature Required** — Lender approval requires completing the e-signature process through Adobe Sign or ZohoSign. A verbal or informal approval is not sufficient.
* **Auto-Save During Configuration** — All data entered during the Draft stage auto-saves, allowing facility agents to work across multiple sessions.
* **Sub-Facilities for Multi-Branch** — Sub-facilities can only be created when the facility is configured as multi-branch. Each sub-facility has its own name, type, amount, and currency.
* **Facility Setup Gates Funding** — Even after the master commitment is Active, borrowers cannot raise funding requests until the facility agent completes deal modelling and the Facility Setup Status changes to Completed.
* **Delegation Available** — During the Active stage, the facility agent can delegate deal modelling to the admin role if assistance is needed.
