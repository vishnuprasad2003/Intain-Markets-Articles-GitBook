---
title: Status and Approval Philosophy
description: Understand how statuses and approvals work together to create structured workflows
---

# Status and Approval Philosophy

## Overview

Intain Markets uses statuses and approvals to ensure transactions progress through defined stages with proper authorization. Statuses control what actions are available, while approvals serve as quality gates before progression.

## Status-Based Control

Every item in the platform has a status that controls available actions:

### Pool Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| **Created** | Pool created, not shared | Edit, Add Loans, Share |
| **Preview** | Shared for review | Edit, Respond to Feedback, Start Deal |
| **Under Review** | Market maker accepted | View, Provide Feedback |
| **Deal** | Deal finalized | View only |

### Term Sheet Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| **Draft** | Being created | Edit, Sign (Create Draft) |
| **BorrowerSigned** | Borrower signed | Submit to FA |
| **FAReview** | FA reviewing | Approve/Reject/Request Changes (FA) |
| **CHANGES_REQUESTED** | Changes needed | Edit, Resubmit (Borrower) |
| **Accepted** | Approved | View, MC auto-created |
| **Rejected** | Declined | View only |

### Master Commitment Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| **Draft** | Being configured | Edit, Add Lenders, Create Facility |
| **PendingLenderApproval** | Awaiting lender | Approve & E-Sign (Lender) |
| **ACTIVE** | Facility operational | Set Up Deal, Create Funding Requests |

### Funding Request Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| **DRAFT** | Being created | Edit, Submit |
| **FAReview** | FA reviewing | Approve/Reject/Request Changes (FA) |
| **APPROVED** | Approved | Funding Notice auto-generated |
| **REJECTED** | Declined | View only |
| **CHANGES_REQUESTED** | Changes needed | Edit, Resubmit |

### Batch Verification Statuses

| Status | Meaning | Available Actions |
|--------|---------|-------------------|
| **Pending** | Not verified | Self Certify, Submit to Agent |
| **Reviewed** | Verification complete | Mint NFT (in Certificates) |
| **Certified** | Agent verified | View NFT |
| **Self Certified** | Self verified | View NFT |

## Approval Gates

Approvals are required at key workflow stages:

### Term Sheet Approval (Facility Agent)
- **Reviews:** Facility terms, documents, borrower information
- **Options:** Approve → MC created, Reject → Final, Request Changes → Borrower edits

### Master Commitment Approval (Lender)
- **Reviews:** Facility structure, terms, participation
- **Options:** Approve & E-Sign → Facility ACTIVE
- **Note:** One lender approval activates the facility

### Funding Request Approval (Facility Agent)
- **Reviews:** Draw amount, purpose, capacity, documentation
- **Options:** Approve → FN generated, Reject → Final, Request Changes → Borrower edits

### Pool Mandate (Market Maker)
- **Reviews:** Pool details, loans, terms
- **Options:** Accept → Deal, Reject → Pool remains in Preview

## Key Principles

**Status Controls Actions:**
- Buttons enabled/disabled based on status
- Cannot skip stages
- Sequential progression enforced

**Role-Based Authority:**
- Only certain roles can approve certain items
- FA approves term sheets and funding requests
- Lenders approve master commitments
- Market makers accept pool mandates

**Change Requests vs Rejection:**

| Aspect | Change Request | Rejection |
|--------|---------------|-----------|
| **Item editable?** | Yes | No |
| **Can resubmit?** | Yes | No |
| **Workflow** | Returns to submitter | Stops |
| **Next step** | Make changes, resubmit | Create new item |

**Complete Audit Trail:**
- Every status change recorded
- Who changed, when, why
- Approval decisions documented
- Cannot be modified after recording

## Platform Status Examples

**Example 1: Term Sheet Flow**
```
Draft → (Borrower signs) → BorrowerSigned → (Submit) → FAReview → (FA approves) → Accepted
```

**Example 2: Funding Request with Changes**
```
DRAFT → (Submit) → FAReview → (FA requests changes) → CHANGES_REQUESTED → (Edit, Resubmit) → FAReview → (FA approves) → APPROVED
```

**Example 3: Pool to Deal**
```
Created → (Share) → Preview → (MM accepts) → Under Review → (Start Deal) → Deal
```

Understanding statuses and approvals helps you navigate workflows effectively and know what actions are available at each stage.
