---
title: Funding Request Review (Facility Agent)
description: Complete guide for facility agents on how to review, evaluate, and make decisions on funding requests submitted by borrowers
---

# Funding Request Review (Facility Agent)

## Overview

This guide explains how a facility agent reviews a funding request. When a borrower asks to draw funds, you check the request against the facility terms, the capacity that is still available, and the collateral. You then approve, reject, or ask for changes. Approval creates a funding notice and starts the token steps for that draw.

## Who Can Use This

- **Facility agents**: Only a facility agent can review a funding request and approve it, reject it, or ask for changes.

## When This Is Used

Review a funding request when:
- A borrower has submitted one and the status is **In review (facility agent)**
- You need to check the draw against the facility terms and the remaining capacity
- A borrower has sent the request back after you asked for changes, and the status is **In review (facility agent)** again

You can act only while the status is **In review (facility agent)**. If the status is something else, the approve, reject, and request-changes actions are not available.

## Review Process

### Step 1: Access the Funding Request

1. Open **Credit Facility** from the left menu
2. Open the **Active Facilities** tab
3. Find the master commitment
4. Find the funding request. It shows **In review (facility agent)**.
5. Click **Review Funding Request**

### Step 2: Evaluate the Request Details

Check these areas:

**Request details:**

| What you see | What to check |
|--------------|----------------|
| Funding request ID | The identifier for this request, so you are reviewing the right one |
| Draw amount | The amount the borrower wants to draw |
| Funding date | The date the borrower needs the funds |
| Purpose of funds | Why they want the draw |
| Draw currency | The currency of the request |

**Facility terms and capacity:**

| What you see | What to check |
|--------------|----------------|
| Available borrowing capacity | Whether the draw fits the amount still available |
| Facility utilization | How much of the facility is already in use |
| Advance rate | Whether the draw stays within the approved advance rate. The advance rate is the share of collateral value that can be borrowed. |
| Commitment amount | The total commitment on the master commitment |

**Documents:**

| Document | What to verify |
|----------|----------------|
| Collateral addendum | The collateral document, including earlier versions if they are shown |
| Supporting documents | Any other files the borrower uploaded |
| Funding sheet | The funding sheet, if one was provided |

**Lender participation:**
The request includes lenders who have finished signing the master commitment. Check that their shares and commitment amounts look right.

### Step 3: Review Status History and Action History

The request keeps a history you can read:
- **Status history** shows each status change, when it happened, and who did it
- **Action history** shows submit, approve, reject, and change-request actions, including comments

Read the history when the request was sent back for changes and then submitted again. Confirm the borrower addressed the earlier comments.

## Evaluation Criteria

When you evaluate a funding request, consider:

1. **Capacity** — Does the draw amount fit the borrowing capacity that is still available?
2. **Terms** — Do the date, currency, and other terms match the master commitment?
3. **Documents** — Did the borrower provide the collateral and other required files?
4. **Lenders** — Are the participating lenders ready for this draw?
5. **Earlier comments** — If this is a resubmission, did the borrower make the changes you asked for?

## Making Decisions

You have three choices.

### Option 1: Approve

**When to use it:** The request meets the requirements and the draw can continue.

**What happens:**
- The status changes from **In review (facility agent)** to **Approved**
- The screen records who approved it and when
- A funding notice is created with status **Pending token generation**
- The notice lists one share for each eligible lender
- The borrower is notified by email and in the platform
- Your approval and any comments are saved on the request history

**After you approve:**
1. The funding notice shows **Pending token generation**
2. Click **Approve** on the funding notice to create the tokens
3. The status becomes **Tokens generated**
4. The borrower approves the token transfer
5. You sign for each lender. The action shows **E-sign (0/n)** and moves toward **E-sign (n/n)**.
6. Each lender can see the notice after their signature is done
7. Lenders send funds and click **Confirm and Settle**
8. When every lender is finished, the status becomes **Tokens transferred**

### Option 2: Reject

**When to use it:** You cannot approve the request. Examples include a draw that is too large, collateral that is not enough, or terms the borrower does not qualify for.

**What happens:**
- You must enter a rejection reason
- The status changes from **In review (facility agent)** to **Rejected**
- The screen records who rejected it, when, and the reason
- The borrower is notified
- The request is closed. No further changes are allowed.

Rejection is final. The request becomes view only. The borrower cannot edit it or send it again. They must create a new funding request.

### Option 3: Request Changes

**When to use it:** The request is close, but something must change. Examples include a lower draw amount, a different funding date, or another document.

**What happens:**
- You enter comments that say what must change
- The status changes from **In review (facility agent)** to **Changes Requested**
- The comments are saved with the request so the borrower can see them
- The borrower can edit the request and submit it again
- After they resubmit, the status returns to **In review (facility agent)**
- Each time you ask for changes, that round is kept on the request history

If the status is already **Changes Requested**, you cannot send another change request until the borrower resubmits.

## Rules & Validations

| Rule | Details |
|------|---------|
| **Status** | You can approve, reject, or request changes only when the status is **In review (facility agent)** |
| **Who can review** | Only a facility agent can take these actions |
| **Rejection is final** | A rejected request stays closed. It cannot be edited or resubmitted. |
| **Do not decide twice** | If the request is already approved or rejected, the action is not repeated |
| **Change requests are kept** | Each request for changes is saved in order, with your comments |
| **No signature on this step** | Approving a funding request does not require a signature. Signatures happen later on the funding notice. |
| **The notice is created for you** | Approval creates the funding notice. You do not create it as a separate form. |

## What Happens Next

| Your decision | What the borrower does | What happens on the platform |
|---------------|------------------------|------------------------------|
| **Approve** | Waits for the funding notice | A funding notice is created and the token steps begin |
| **Reject** | Creates a new funding request | This request stays view only |
| **Request Changes** | Edits the request and submits it again | The status returns to **In review (facility agent)** after they resubmit |

After approval, the notice continues in this order: tokens are created, the borrower approves the transfer, you sign for each lender, lenders send funds, and settlement is confirmed. Those later steps are covered in the funding notice and token approval guides.
