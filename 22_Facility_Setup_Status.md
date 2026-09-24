---
title: Facility Setup Status
description: >-
  Understand the facility setup status lifecycle, deal modelling process, and
  what each status means for credit facility participants
---

# Facility Setup Status

## Overview

After a master commitment becomes **Active** (when at least one lender approves and e-signs), the facility agent must complete **deal modelling** before borrowers can raise funding requests or map loans. The **Facility Setup Status** is a secondary status on the master commitment that tracks whether this critical configuration step is complete. Understanding this status is essential because it directly controls what actions borrowers and other participants can perform on the facility.

## Lifecycle Overview

The facility setup status has a straightforward two-state lifecycle:

```
Master Commitment becomes Active
  → Facility Setup Status: In Progress (default)
    → FA completes deal modelling
      → Facility Setup Status: Completed
```

This lifecycle is linear — once the status reaches **Completed**, it does not revert. Deal modelling is a one-time configuration process per facility.

## Status Meanings

### In Progress

**What This Status Represents:** The facility is active but deal modelling has not been completed yet. This is the **default status** automatically assigned when a master commitment first transitions to Active.

**When This Occurs:**

* Immediately after any lender approves the master commitment, transitioning it to Active
* The facility agent has not yet opened or completed the deal modelling process

**What This Means for Each Role:**

| Role               | Impact                                                                                                                                    |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Facility Agent** | Must complete deal modelling. The **Set Up Deal** action is available in the Active Facilities tab.                                       |
| **Borrower**       | **Cannot** map loans to the facility. **Cannot** create funding requests. These actions remain disabled until deal modelling is complete. |
| **Lender**         | Can view the facility details but no funding-related actions are available yet.                                                           |

**Dashboard View:**

* The facility appears in the Active Facilities tab for the facility agent
* The action column displays **Set Up Deal**
* Borrowers see the facility but with disabled action buttons for Map Loans and Create Funding Request

### Completed

**What This Status Represents:** Deal modelling is complete and the facility is fully operational. All workflow actions are now available to the appropriate roles.

**When This Occurs:**

* After the facility agent (or admin, if delegated) completes all deal modelling sections and clicks **Create** in the Review section

**What This Means for Each Role:**

| Role               | Impact                                                                                                                                                           |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Facility Agent** | Deal modelling is finished. **Review Funding Request** action becomes available when borrowers submit requests.                                                  |
| **Borrower**       | **Map Loans** action is now enabled — can map NFT-minted loans to the facility. **Create Funding Request** action is now enabled — can submit drawdown requests. |
| **Lender**         | Can view the facility and will see **Review Funding Notice** when funding notices are generated and e-signed by the facility agent.                              |

## What is Deal Modelling

Deal modelling is the process where the facility agent configures all the operational parameters needed for the credit facility to function. This includes setting up the financial structure, parties, fees, interest rates, covenants, and payment waterfalls. The platform provides a multi-section configuration interface with auto-save functionality, so data is preserved as the facility agent works through each section.

### Deal Modelling Sections

The deal modelling screen contains the following sections, accessible through a left-side navigation menu:

1. **Basic Details** — Core deal information including deal name, deal type, currency, closing date, maturity date, payment frequency, day count convention (e.g., 30/360, Actual/360), and business day convention.
2. **Parties & Accounts** — Configuration of all parties involved in the facility, including borrower details, facility agent details, individual lender details, bank account information for each party, and payment instructions for wire transfers.
3. **Fee Structure** — All fee configurations for the facility, including upfront fees, commitment fees, agent fees, and any other applicable fees.
4. **Interest Rate** — Interest rate parameters including rate type (fixed or floating), base rate reference (e.g., SOFR), spread over the base rate, margin, default interest rate, and interest period configuration.
5. **Covenants** — Definition of all covenant requirements, organized into financial covenants, reporting covenants, and other covenant categories.
6. **Waterfall** — Payment priority configuration including waterfall steps (the order in which payments are distributed) and distribution rules that govern how cash flows are allocated among participants.
7. **Review** — The final section that presents a summary of all configured sections. This section contains the **Create** button that completes deal modelling.

### Auto-Save Behavior

As the facility agent enters data in each section, the platform auto-saves the information. This means the facility agent can work through the sections over multiple sessions without losing progress. Data is preserved even if the browser is closed and the facility agent returns later.

### Delegation to Admin

A **Delegation** button is available at the top of the deal modelling screen. If the facility agent needs assistance or wants the platform admin to complete the configuration:

1. Click the **Delegation** button
2. The deal modelling responsibility is transferred to the admin role
3. The admin can now access and complete all deal modelling sections
4. Once the admin clicks **Create** in the Review section, the facility setup status changes to **Completed**

Delegation can only be initiated when the facility setup status is **In Progress**. Once delegated, the admin takes over the configuration responsibility.

## What Each Status Indicates

### Actions Available at Each Status

| Facility Setup Status | FA Action                               | Borrower: Map Loans | Borrower: Create Funding Request | Lender Actions                         |
| --------------------- | --------------------------------------- | ------------------- | -------------------------------- | -------------------------------------- |
| **In Progress**       | Set Up Deal                             | Disabled            | Disabled                         | View only                              |
| **Completed**         | Review Funding Request (when submitted) | Enabled             | Enabled                          | Review Funding Notice (when available) |

### Validation Rules

* **Active Master Commitment Required** — Deal modelling can only be initiated and completed for master commitments in Active status. Draft or PendingLenderApproval commitments do not have the Set Up Deal action.
* **All Sections Required** — All deal modelling sections must be completed before the Create button becomes active in the Review section.
* **One-Time Process** — Deal modelling is completed once per facility. After the status changes to Completed, the configuration cannot be re-opened or modified through the deal modelling interface.
* **Delegation is One-Way** — Once deal modelling is delegated to admin, the facility agent cannot reclaim the configuration task.
* **No Duplicate Creation** — The platform prevents creating a deal model if one already exists for the master commitment, ensuring the process runs exactly once.

## What Happens After Completion

Once the facility setup status changes to **Completed**, the full credit facility funding workflow becomes available:

1. **Borrower Maps Loans** — The borrower can map NFT-minted loans to the facility using the now-enabled Map Loans action
2. **Borrower Creates Funding Request** — The borrower can submit drawdown requests specifying the amount, purpose, and supporting documentation
3. **Facility Agent Reviews** — The facility agent reviews funding requests and can approve, reject, or request changes
4. **Funding Notice Generated** — Upon approval, a funding notice is automatically generated and progresses through e-signature
5. **Lenders Transfer Funds** — Lenders review the funding notice, transfer funds, and click Confirm and Settle
6. **Settlement Complete** — Tokens are transferred and the drawdown is finalized

The facility setup status serves as the critical gate between facility activation and the start of the funding workflow.
