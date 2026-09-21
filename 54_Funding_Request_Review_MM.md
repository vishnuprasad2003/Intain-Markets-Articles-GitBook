---
title: Funding Request Review (Facility Agent)
description: Complete guide for facility agents on how to review, evaluate, and make decisions on funding requests submitted by borrowers
---

# Funding Request Review (Facility Agent)

## Overview

This guide covers the end-to-end process by which facility agents review funding requests submitted by borrowers in the Credit Facility module. When a borrower submits a drawdown request, the facility agent is responsible for evaluating the request against the facility terms, available capacity, and collateral requirements — then making one of three decisions: approve, reject, or request changes. This review step is a critical control point in the credit facility workflow, as approval triggers the automatic generation of a funding notice and begins the token issuance process.

## Who Can Use This

- **Facility Agents (Market Makers with Underwriter role)** — Only users with the Underwriter role permission can review and act on funding requests. The system enforces this through the `requireRole('Underwriter')` middleware, ensuring that only authorized facility agents can approve, reject, or request changes on funding requests.

## When This Is Used

This review process is triggered when:
- A borrower has submitted a funding request and its status shows **FAReview**
- The facility agent needs to evaluate a drawdown request against the facility's terms and available capacity
- A previously returned funding request (after a change request) has been resubmitted by the borrower and is again in **FAReview** status

Funding requests can only be acted upon when they are in **FAReview** status. The system enforces this rule — attempts to approve, reject, or request changes on a funding request in any other status will fail with an error message indicating the current status.

## Review Process

### Step 1: Access the Funding Request

1. Navigate to **Credit Facility** from the left expandable menu
2. Go to the **Active Facilities** tab
3. Locate the relevant master commitment
4. Find the funding request under that commitment — it will show **FAReview** status
5. Click the **Review Funding Request** action button

### Step 2: Evaluate the Request Details

When reviewing a funding request, the facility agent should examine the following areas:

**Request Details:**

| Field | What to Check |
|-------|---------------|
| `fundingRequestId` | Unique identifier in the format **FR-MMDDYYYY-xxxx** (auto-generated) |
| Draw Amount | The amount the borrower is requesting to draw down |
| Funding Date | The date the borrower needs the funds |
| Purpose of Funds | The stated reason for the drawdown |
| Draw Currency | The currency of the requested draw |

**Facility Terms and Capacity:**

| Field | What to Check |
|-------|---------------|
| Available Borrowing Capacity | Whether the requested draw amount fits within the remaining facility capacity |
| Facility Utilization | Current utilization level of the overall credit facility |
| Advance Rate | Whether the draw is within the approved advance rate |
| Commitment Amount | Total commitment amount from the master commitment |

**Documentation:**

| Document | What to Verify |
|----------|----------------|
| Collateral Addendum | Review the collateral addendum document and its history (`collateralAddendumHistory`) |
| Supporting Documents | Any additional documents uploaded by the borrower |
| Funding Sheet | If applicable, the funding sheet supporting the request |

**Lender Participation:**
The system automatically includes only lenders with `esignature_completed` status from the master commitment's lender groups. Review the lender participation breakdown to ensure the allocation percentages and commitment amounts are correct.

### Step 3: Review Status History and Action History

Each funding request maintains two audit trails:
- **statusHistory** — records every status transition with timestamps and actors
- **actionHistory** — records every action taken (submit, approve, reject, request changes) with comments

Review these histories if the funding request has been through previous review cycles (e.g., returned via a change request and resubmitted).

## Evaluation Criteria

When evaluating a funding request, consider:

1. **Capacity compliance** — Does the draw amount fit within the available borrowing capacity?
2. **Terms alignment** — Are the request terms (rate, date, currency) consistent with the master commitment?
3. **Documentation completeness** — Has the borrower provided all required collateral and supporting documents?
4. **Lender readiness** — Are participating lenders in the correct status to support the drawdown?
5. **Prior feedback** — If this is a resubmission, has the borrower addressed all previously requested changes?

## Making Decisions

Three decision options are available to the facility agent:

### Option 1: Approve

**When to Use:** The funding request meets all requirements and the drawdown can proceed.

**What Happens:**
- Status changes from **FAReview** to **APPROVED**
- The system records `approvedAt` (timestamp) and `approvedBy` (user ID)
- A **funding notice** is automatically generated with status `PENDING_TOKEN_GENERATION`
- The funding notice includes a `tokenDistribution` array with one entry per eligible lender
- A notification is sent to the borrower's organization via SSE and email confirming the approval
- The approval is logged in both `statusHistory` and `actionHistory` with comments (e.g., "Funding request approved by market maker, pending e-signature")

**After Approval — What Follows:**
1. The auto-generated funding notice appears with `PENDING_TOKEN_GENERATION` status
2. The facility agent clicks **Approve** on the funding notice to trigger FT token deployment
3. Status advances to `TOKEN_GENERATED` once the FT contract is deployed on-chain
4. The borrower approves the token transfer
5. The facility agent initiates e-signature for each lender (progress shown as **E-sign 0/n → n/n**)
6. Each lender receives visibility into the funding notice after their e-sign is complete
7. Lenders transfer funds and click **Confirm and Settle**
8. When all lenders complete, tokens are transferred to the borrower and status becomes `TOKEN_TRANSFERRED`

### Option 2: Reject

**When to Use:** The funding request cannot be approved — for example, it exceeds capacity, lacks sufficient collateral, or the borrower does not qualify for the requested terms.

**What Happens:**
- Facility agent must provide a `rejectionReason` explaining why the request was declined
- Status changes from **FAReview** to **REJECTED**
- The system records `rejectedAt`, `rejectedBy`, and `rejectionReason`
- The action is logged with comments (e.g., "Funding request rejected by market maker")
- A notification is sent to the borrower
- An audit event `credit_facility.funding_request.rejected` is recorded with the summary: "Funding request {id} rejected and closed; no further changes allowed"

**Important:** Rejection is **final**. The rejected funding request becomes read-only. The borrower cannot edit or resubmit it. To try again, the borrower must create an entirely new funding request.

### Option 3: Request Changes

**When to Use:** The funding request is close to acceptable but needs modifications — for example, reduce the draw amount, change the funding date, or provide additional documentation.

**What Happens:**
- Facility agent provides specific comments describing what changes are needed
- A change request record is created with a unique `requestId` in the format **CR-{fundingRequestId}-{sequenceNumber}** (sequence increments with each change request)
- Status changes from **FAReview** to **CHANGES_REQUESTED**
- The system captures a version snapshot of the current funding request state before the change request
- The borrower can now edit the funding request and resubmit it
- Upon resubmission, the status returns to **FAReview** for another review cycle
- An audit event `credit_facility.funding_request.changes_requested` is recorded

**Note:** If the funding request is already in `CHANGES_REQUESTED` status (e.g., the borrower has not yet resubmitted), the system prevents duplicate change requests.

## Rules & Validations

| Rule | Details |
|------|---------|
| **Status Gate** | Only funding requests in `FAReview` status can be approved, rejected, or have changes requested |
| **Role Gate** | Only users with the `Underwriter` role can perform review actions |
| **Rejection Finality** | Rejected requests are permanently closed — no edits or resubmission |
| **Duplicate Prevention** | Already-approved or already-rejected requests return an informational response instead of re-processing |
| **Change Request Tracking** | Each change request is numbered sequentially and preserves a version snapshot for audit purposes |
| **No E-Signature Required** | Funding request approval does not require an e-signature (unlike term sheet signing) |
| **Auto-Generation** | Approval automatically creates a funding notice — no separate action needed |

## What Happens Next

| Your Decision | Borrower's Next Step | System's Next Step |
|---------------|----------------------|--------------------|
| **Approve** | Wait for funding notice process | Funding notice auto-generated, token workflow begins |
| **Reject** | Create a new funding request | Request archived as read-only |
| **Request Changes** | Edit and resubmit the request | Request returns to FAReview after resubmission |

After approval, the workflow continues through the funding notice lifecycle: token generation → borrower token approval → facility agent e-signature per lender → lender fund transfer → settlement. Each of these stages has its own documentation and is covered in separate articles.
