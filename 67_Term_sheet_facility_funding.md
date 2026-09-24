---
title: Term Sheet, Facility, and Funding
description: Complete guide to the credit facility workflow from term sheet to funding
---

# Term Sheet, Facility & Funding Statuses

## Overview

This guide walks through a credit facility from the first proposal to the moment funds are paid. The work happens in three phases: the term sheet, the facility (also called the master commitment), and funding. Each phase has to finish before the next one starts. Borrowers propose terms and request draws. The facility agent reviews and sets up the facility. Lenders approve the facility and pay the draws.

## Phase 1: Term Sheet

### What Is a Term Sheet

A term sheet is the preliminary agreement between the borrower and the lenders. It sets the proposed terms of the credit facility before anyone is formally committed.

### Term Sheet Flow

```
Borrower creates the term sheet (Draft)
       ↓
Borrower signs with Adobe Sign (Signed)
       ↓
Borrower submits it to the facility agent (In review)
       ↓
Facility agent approves, rejects, or requests changes
       ↓
If approved → Accepted → the facility is created automatically
```

### Term Sheet Statuses

| Status                | Description                                                                  |
| --------------------- | ---------------------------------------------------------------------------- |
| **Draft**             | Created and still editable                                                   |
| **Signed**            | The borrower has signed and can submit it                                    |
| **In review**         | Waiting for the facility agent                                               |
| **Accepted**          | Approved. The facility is created from this term sheet                       |
| **Rejected**          | Declined. This term sheet cannot be reused                                   |
| **Changes Requested** | The facility agent asked for edits. The borrower can update and submit again |

***

## Phase 2: Facility (Master Commitment)

### What Is a Master Commitment

A master commitment is the formal facility. It records the agreed terms, the lenders, and how much each lender has committed. It is created automatically when the facility agent accepts the term sheet.

### Facility Flow

```
Term sheet accepted → facility created (Draft)
       ↓
Facility agent sets the facility details
       ↓
Facility agent adds lenders and their shares
       ↓
Facility agent clicks Create Facility (Pending)
       ↓
Each lender reviews and signs
       ↓
When any lender approves → the facility becomes Active
       ↓
Facility agent finishes deal modelling (Set Up Deal → Create)
```

### Master Commitment Statuses

| Status      | Description                                                |
| ----------- | ---------------------------------------------------------- |
| **Draft**   | The facility agent is still setting up the facility        |
| **Pending** | Waiting for lenders to review and sign                     |
| **Active**  | At least one lender has approved. The facility can be used |

### Facility Setup Status

| Status          | Description                    | Borrower Can Request Funding |
| --------------- | ------------------------------ | ---------------------------- |
| **In Progress** | Deal modelling is not finished | No                           |
| **Completed**   | Deal modelling is finished     | Yes                          |

The borrower cannot map loans or create a funding request until the facility is **Active** and setup is **Completed**.

***

## Phase 3: Funding

### What Is Funding

Funding is how the borrower asks for money under an active facility and how lenders pay that draw. A borrower can request funding more than once while the facility stays active, as long as each request fits the remaining capacity.

### Funding Flow

```
Borrower maps loans to the facility
       ↓
Borrower creates a funding request (Draft)
       ↓
Borrower submits it to the facility agent (In review)
       ↓
Facility agent approves, rejects, or requests changes
       ↓
If approved → a funding notice is created automatically
       ↓
Facility agent approves the funding notice
       ↓
Facility agent signs for each lender (0 of n, then all of n)
       ↓
Each lender sees the notice only after it is signed for them
       ↓
Lenders review, transfer funds, then Confirm and Settle
       ↓
Tokens are recorded to the borrower
```

### Funding Request Statuses

| Status                | Description                                                                  |
| --------------------- | ---------------------------------------------------------------------------- |
| **Draft**             | Created and still editable                                                   |
| **In review**         | Waiting for the facility agent                                               |
| **Approved**          | Approved. A funding notice has been created                                  |
| **Rejected**          | Declined. This request cannot be reused                                      |
| **Changes Requested** | The facility agent asked for edits. The borrower can update and submit again |

### Funding Notice Process

| Step | Who Acts       | Action                                          |
| ---- | -------------- | ----------------------------------------------- |
| 1    | Platform       | Creates the notice when the request is approved |
| 2    | Facility agent | Approves the notice                             |
| 3    | Facility agent | Signs for each lender, one at a time            |
| 4    | Lender         | Reviews the notice and transfers funds          |
| 5    | Lender         | Confirms and settles                            |

A lender does not see the notice until the facility agent has signed for that lender. Other lenders may already see theirs.

***

## Complete End-to-End Flow

```
TERM SHEET
1. Borrower: Create the term sheet
2. Borrower: Sign with Adobe Sign
3. Borrower: Submit to the facility agent
4. Facility agent: Review and approve

FACILITY
5. Platform: Create the master commitment
6. Facility agent: Set facility details
7. Facility agent: Add lenders and their shares
8. Facility agent: Create the facility
9. Lender: Review and approve by signing
10. Facility agent: Finish deal modelling

FUNDING
11. Borrower: Map loans to the facility
12. Borrower: Create a funding request and submit it
13. Facility agent: Review and approve
14. Platform: Create the funding notice
15. Facility agent: Approve the notice and sign for each lender
16. Lender: Review, transfer funds, then Confirm and Settle
17. Tokens are recorded to the borrower
```

## Role Actions Summary

### Borrower Actions

| Phase      | Actions                                                 |
| ---------- | ------------------------------------------------------- |
| Term Sheet | Create, sign, and submit                                |
| Facility   | Wait until the facility is active and setup is complete |
| Funding    | Map loans, create a request, and submit it              |

### Facility Agent Actions

| Phase      | Actions                                                                        |
| ---------- | ------------------------------------------------------------------------------ |
| Term Sheet | Review, then approve, reject, or request changes                               |
| Facility   | Configure details, add lenders, create the facility, and finish deal modelling |
| Funding    | Review the request, approve the notice, and sign for each lender               |

### Lender Actions

| Phase      | Actions                                                    |
| ---------- | ---------------------------------------------------------- |
| Term Sheet | None                                                       |
| Facility   | Review and approve by signing                              |
| Funding    | Review the notice, transfer funds, then Confirm and Settle |

## Key Points

**One phase at a time.** The facility does not exist until the term sheet is accepted. Funding does not start until the facility is active and deal modelling is complete.

**Some records are created for you.** Accepting a term sheet creates the facility. Approving a funding request creates the funding notice.

**Signatures are part of the workflow.** Adobe Sign is used for the borrower’s term sheet, each lender’s facility approval, and the facility agent’s signature on the funding notice.

**Different people approve different steps.** The borrower cannot approve their own term sheet or funding request. Lenders approve the facility and pay the draw. The facility agent stands between them.

**Funding can repeat.** An active facility can support more than one funding request over its life.

> **Note:** These statuses apply to the **Credit Facility** workflow. Asset Sale deals follow a different path (Draft → Published → Active → Closed). See [Asset Sale Statuses](70_Asset_Sale_Statuses.md).
