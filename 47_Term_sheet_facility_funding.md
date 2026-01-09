---
title: All Credit Facility Statuses Explained
description: Comprehensive reference for all statuses in the credit facility module
---

# All Credit Facility Statuses Explained

## Overview

This comprehensive reference guide explains all statuses for credit facility components: Term Sheets, Master Commitments, Funding Requests, and Funding Notices. Use this guide to understand what each status means and what actions are available.

## Term Sheet Statuses

### Status Flow

```
Draft → BorrowerSigned → FAReview → Accepted
                                   ↓
                         Auto-Create Master Commitment

Alternative from FAReview:
FAReview → Rejected (final)
FAReview → CHANGES_REQUESTED → BorrowerSigned → FAReview
```

### Status Definitions

| Status | Meaning | Who Acts | Available Actions |
|--------|---------|----------|-------------------|
| **Draft** | Created, can be edited | Borrower | Edit, sign via Adobe Sign |
| **BorrowerSigned** | Signed, ready to submit | Borrower | Submit to FA |
| **FAReview** | Under facility agent review | Facility Agent | Approve, Reject, Request Changes |
| **Accepted** | Approved, MC auto-created | - | View only |
| **Rejected** | Declined (final) | - | View only, create new term sheet |
| **CHANGES_REQUESTED** | FA requested modifications | Borrower | Edit, sign, resubmit |

### Key Points

- **Signing Required**: Must sign via Adobe Sign before submitting
- **Auto-Create MC**: When approved, master commitment is automatically created
- **Rejected Is Final**: Cannot resubmit; must create new term sheet

---

## Master Commitment Statuses

### Status Flow

```
Term Sheet Accepted → Auto-Create → Draft → FA Configures → PendingLenderApproval → Any Lender Approves → Active
```

### Status Definitions

| Status | Meaning | Who Acts | Available Actions |
|--------|---------|----------|-------------------|
| **Draft** | Auto-created, FA configuring | Facility Agent | Configure facility, add lenders, Create Facility |
| **PendingLenderApproval** | Submitted, awaiting lender | Lender | Review & Approve, E-Sign |
| **Active** | Lender approved, operational | FA, Borrower, Lender | Set Up Deal, Map Loans, Funding Request |

### Facility Setup Status (Within Active)

| Status | Meaning | Borrower Can Raise Funding Request |
|--------|---------|-------------------------------------|
| **In Progress** | Deal modelling not complete | No |
| **Completed** | Deal modelling complete | Yes |

### Key Points

- **Auto-Created Only**: Cannot create manually; only from approved term sheets
- **Any Lender Activates**: One lender approval makes it Active
- **Deal Modelling Required**: FA must complete before borrower can raise funding requests

---

## Funding Request Statuses

### Status Flow

```
DRAFT → FAReview → APPROVED → Funding Notice Generated

Alternative from FAReview:
FAReview → REJECTED (final)
FAReview → CHANGES_REQUESTED → DRAFT → FAReview
```

### Status Definitions

| Status | Meaning | Who Acts | Available Actions |
|--------|---------|----------|-------------------|
| **DRAFT** | Created, can be edited | Borrower | Edit, Submit |
| **FAReview** | Under FA review | Facility Agent | Approve, Reject, Request Changes |
| **APPROVED** | Approved, notice generated | - | View |
| **REJECTED** | Declined (final) | - | View only, create new request |
| **CHANGES_REQUESTED** | FA requested modifications | Borrower | Edit, resubmit |

### Key Points

- **No E-Sign for Approval**: FA doesn't sign to approve funding requests
- **Auto-Generate Notice**: Approved requests automatically create funding notices
- **Rejected Is Final**: Cannot resubmit; must create new request

---

## Funding Notice Statuses

### Status Flow

```
Funding Request APPROVED → Auto-Create → Pending Token Generated → FA Approves → FA E-signs (0/n) → Visible to Lenders → Lenders Confirm and Settle
```

### Status Definitions

| Status | Meaning | Who Acts | Available Actions |
|--------|---------|----------|-------------------|
| **Pending Token Generated** | Notice created, awaiting FA approval | Facility Agent | Approve |
| **E-sign (0/n)** | FA needs to sign for each lender | Facility Agent | E-sign for each lender |
| **Visible to Lenders** | Individual e-sign complete | Lender | Review, Confirm and Settle |

### E-Sign Progress

The E-sign counter shows progress:
- **E-sign (0/3)**: None signed yet (3 lenders total)
- **E-sign (1/3)**: Signed for 1 lender
- **E-sign (2/3)**: Signed for 2 lenders
- **E-sign (3/3)**: All signed, visible to lenders

### Key Points

- **Auto-Created Only**: Cannot create manually; only from approved funding requests
- **FA Approves First**: FA clicks Approve before e-signing
- **E-Sign Per Lender**: FA signs for each lender individually
- **Lender Visibility**: Each lender sees the notice once their e-sign is complete
- **Confirm and Settle**: Lenders transfer funds and click Confirm and Settle

---

## Complete Credit Facility Workflow

```
1. Borrower: Create Term Sheet → Sign (Adobe Sign) → Submit
2. FA: Review Term Sheet → Approve
3. System: Auto-create Master Commitment (Draft)
4. FA: Configure Facility → Add Lenders → Create Facility
5. Lender: Review & Approve → E-Sign (Adobe Sign)
6. System: Master Commitment becomes Active
7. FA: Complete Deal Modelling (Set Up Deal → Create)
8. Borrower: Map Loans → Create Funding Request → Submit
9. FA: Review Funding Request → Approve
10. System: Auto-create Funding Notice (Pending Token Generated)
11. FA: Approve Funding Notice → E-sign for each lender (0/n → n/n)
12. Lender: Review Funding Notice → Transfer Funds → Confirm and Settle
13. Funds disbursed to Borrower
```
