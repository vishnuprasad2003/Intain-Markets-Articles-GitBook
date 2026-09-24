---
title: Master Commitment Statuses
description: >-
  Master commitment statuses from creation through lender approval and active use
---

# Master Commitment Statuses

→ Back to [Credit Facilities Overview](16_Credit_Facilities_Overview.md)

## Lifecycle

```
Term sheet approved → Master commitment created (Draft)
  → Facility agent configures → Create Facility (Pending Lender Approval)
    → Any one lender Approve & E-Sign → Active
      → Facility agent completes deal modelling (Facility Setup Completed)
        → Borrower can map loans and create funding requests
```

## Statuses

| Status | Who acts | What can be done |
|---|---|---|
| **Draft** | Facility agent | Edit all sections, add lenders, create sub-facilities, click Create Facility |
| **Pending Lender Approval** | Lender | Review & Approve (or decline); facility agent can view only |
| **Active** | Facility agent, then borrower, then lender | Set Up Deal; map loans and create funding requests (after setup complete); review funding notices and settle |
| **InActive** | None | View history only; no new funding requests |

## Lender Status (within Pending Lender Approval)

| Lender status | Meaning |
|---|---|
| **pending** | No decision yet |
| **approved** | Approved and e-signed |
| **rejected** | Declined |

> Any one lender's approval activates the facility. One rejection does not block others.

## Facility Setup Status (within Active)

| Setup status | Borrower can map loans? | Borrower can create funding request? |
|---|---|---|
| **In Progress** | No | No |
| **Completed** | Yes | Yes |

## Key Rules

- Master commitments are created automatically when a term sheet is approved — no separate create step
- Editing closes once the commitment moves to Pending Lender Approval
- Sub-facilities are only available on multiple-branch facilities
- Facility agent can delegate deal modelling to an admin
- Borrowers cannot request funds until setup is **Completed**, even if commitment is already **Active**

→ See [Facility Creation](50_Facility_Creation.md) for configuration steps.
→ See [Facility Approval](58_Facility_Approval.md) for lender approval process.
