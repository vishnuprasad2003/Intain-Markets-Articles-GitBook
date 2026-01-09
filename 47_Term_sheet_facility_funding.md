---
title: Term Sheet, Facility, and Funding
description: Complete guide to the credit facility workflow from term sheet to funding
---

# Term Sheet, Facility, and Funding

## Overview

This guide provides a complete walkthrough of the credit facility workflow, from creating a term sheet through facility setup to funding. It covers all three major phases: Term Sheet, Facility (Master Commitment), and Funding.

## Phase 1: Term Sheet

### What Is a Term Sheet

A term sheet defines the preliminary terms of the credit facility agreement between the borrower and lenders.

### Term Sheet Flow

```
Borrower creates Term Sheet (Draft)
       ↓
Borrower signs via Adobe Sign (BorrowerSigned)
       ↓
Borrower submits to FA (FAReview)
       ↓
FA reviews → Approve / Reject / Request Changes
       ↓
If Approved → Accepted → Master Commitment auto-created
```

### Term Sheet Statuses

| Status | Description |
|--------|-------------|
| **Draft** | Created, can be edited |
| **BorrowerSigned** | Signed, ready to submit |
| **FAReview** | Under facility agent review |
| **Accepted** | Approved, MC created |
| **Rejected** | Declined (final) |
| **CHANGES_REQUESTED** | FA requested modifications |

---

## Phase 2: Facility (Master Commitment)

### What Is a Master Commitment

A master commitment is the formal facility agreement that defines the terms, lenders, and commitment amounts.

### Facility Flow

```
Term Sheet Accepted → MC auto-created (Draft)
       ↓
FA configures facility details
       ↓
FA adds lenders and allocations
       ↓
FA clicks Create Facility (PendingLenderApproval)
       ↓
Lender reviews → E-Sign approval
       ↓
Any lender approves → MC becomes Active
       ↓
FA completes Deal Modelling (Set Up Deal → Create)
```

### Master Commitment Statuses

| Status | Description |
|--------|-------------|
| **Draft** | FA configuring facility |
| **PendingLenderApproval** | Awaiting lender review |
| **Active** | Approved, operational |

### Facility Setup Status

| Status | Description | Borrower Can Request Funding |
|--------|-------------|------------------------------|
| **In Progress** | Deal modelling not complete | No |
| **Completed** | Deal modelling complete | Yes |

---

## Phase 3: Funding

### What Is Funding

Funding is the process by which borrowers request and receive funds from lenders through the facility.

### Funding Flow

```
Borrower maps loans to facility
       ↓
Borrower creates Funding Request (Draft)
       ↓
Borrower submits to FA (FAReview)
       ↓
FA reviews → Approve / Reject / Request Changes
       ↓
If Approved → Funding Notice auto-created
       ↓
FA approves Funding Notice
       ↓
FA e-signs for each lender (0/n → n/n)
       ↓
Each lender sees notice once signed for
       ↓
Lenders review → Transfer funds → Confirm and Settle
       ↓
Tokens transferred to Borrower
```

### Funding Request Statuses

| Status | Description |
|--------|-------------|
| **DRAFT** | Created, can be edited |
| **FAReview** | Under FA review |
| **APPROVED** | Approved, notice generated |
| **REJECTED** | Declined (final) |
| **CHANGES_REQUESTED** | FA requested modifications |

### Funding Notice Process

| Step | Who Acts | Action |
|------|----------|--------|
| 1 | System | Auto-generate notice |
| 2 | FA | Approve |
| 3 | FA | E-sign for each lender |
| 4 | Lender | Review and transfer funds |
| 5 | Lender | Confirm and Settle |

---

## Complete End-to-End Flow

```
TERM SHEET PHASE
1. Borrower: Create Term Sheet
2. Borrower: Sign via Adobe Sign
3. Borrower: Submit to FA
4. FA: Review → Approve

FACILITY PHASE
5. System: Auto-create Master Commitment
6. FA: Configure facility details
7. FA: Add lenders and allocations
8. FA: Create Facility
9. Lender: Review & Approve (E-Sign)
10. FA: Complete Deal Modelling

FUNDING PHASE
11. Borrower: Map loans to facility
12. Borrower: Create Funding Request → Submit
13. FA: Review → Approve
14. System: Auto-create Funding Notice
15. FA: Approve → E-sign for each lender
16. Lender: Review → Transfer funds → Confirm and Settle
17. Tokens transferred to Borrower
```

## Role Actions Summary

### Borrower Actions

| Phase | Actions |
|-------|---------|
| Term Sheet | Create, Sign, Submit |
| Facility | Wait for activation |
| Funding | Map loans, Create request, Submit |

### Facility Agent Actions

| Phase | Actions |
|-------|---------|
| Term Sheet | Review, Approve/Reject/Request Changes |
| Facility | Configure, Add lenders, Create, Deal modelling |
| Funding | Review request, Approve, E-sign for lenders |

### Lender Actions

| Phase | Actions |
|-------|---------|
| Term Sheet | None |
| Facility | Review & Approve (E-Sign) |
| Funding | Review notice, Transfer funds, Confirm and Settle |

## Key Points

**Sequential Phases** - Each phase must complete before the next can begin.

**Auto-Creation** - Master commitments and funding notices are auto-created from approvals.

**E-Sign Integration** - Adobe Sign is used for legal signatures throughout.

**Multiple Approvals** - Different parties approve at different stages.

**Funding Cycle** - Funding requests can be repeated multiple times within an active facility.
