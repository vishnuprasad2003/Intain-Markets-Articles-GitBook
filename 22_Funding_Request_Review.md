---
title: Funding Request Review
description: Learn how facility agents review funding requests and make approval decisions
---

# Funding Request Review

## Overview

When borrowers submit funding requests, facility agents review them and decide whether to approve, reject, or request changes. No e-signature is required for funding request approval. This guide explains the review process for facility agents.

## Who Can Use This

- **Facility Agents**: Review funding requests and make approval decisions

## When This Is Used

Use funding request review when:
- A funding request is submitted with **FAReview** status
- You need to evaluate a borrower's drawdown request
- You want to make an approval decision

## Step-by-Step Process

### Step 1: Access the Funding Request

1. **Navigate to Credit Facility**
   - Log in with your Facility Agent credentials
   - From the left expandable menu, click on **Credit Facility**
   - Go to the **Active Facilities** tab

2. **Find the Funding Request**
   - Locate the funding request under the relevant master commitment
   - Status shows **FAReview**
   - Action column shows **Review Funding Request**

3. **Click Review Funding Request**
   - Click **Review Funding Request** to open the review popup

![Review Funding Request - Review](imagesByMdFilesFolder/22/review_funding_request_review.png)

### Step 2: Evaluate the Request

1. **Review Request Details**
   - Check the draw amount
   - Verify the funding date
   - Review the purpose of funds
   - Check the draw currency

2. **Review Documentation**
   - Check the uploaded Collateral Addendum
   - Verify documentation is complete

3. **Verify Capacity**
   - Ensure the draw amount is within available borrowing capacity
   - Check facility utilization

### Step 3: Make Your Decision

The review popup shows three buttons:

#### Option 1: Approve

**When to Approve:**
- Request meets all requirements
- Draw amount is within capacity
- Documentation is complete
- No compliance issues

**What Happens:**
- Click **Approve**
- Status changes to **APPROVED**
- Funding notice is automatically generated (Pending Token Generated)
- Proceed to funding notice processing

**No e-signature is required for funding request approval.**

#### Option 2: Reject

**When to Reject:**
- Request doesn't meet requirements
- Insufficient capacity
- Documentation issues
- Compliance problems

**What Happens:**
- Click **Reject**
- Provide rejection reason
- Status changes to **REJECTED** (final)
- Borrower must create a new request

#### Option 3: Request Changes

**When to Request Changes:**
- Minor issues need addressing
- Additional documentation needed
- Clarifications required

**What Happens:**
- Click **Request Changes**
- Enter details about needed changes
- Status changes to **CHANGES_REQUESTED**
- Borrower can edit and resubmit

## What Happens After Approval

After you approve a funding request:

1. **Funding Notice Generated**
   - Status: Pending Token Generated

2. **Approve Funding Notice**
   - Click **Approve** on the funding notice

3. **E-Sign for Each Lender**
   - Action shows **E-sign (0/n)**
   - Sign for each lender individually via Adobe Sign
   - Count updates as you sign (1/n, 2/n, etc.)

4. **Lender Visibility**
   - Each lender can see the funding notice once their e-sign is complete

5. **Lender Fund Transfer**
   - Lenders review funding notice
   - Lenders transfer funds and click Confirm and Settle

## Rules & Validations

- **FAReview Status Required**: You can only review requests in FAReview status.

- **No E-Sign for Approval**: Unlike term sheets, funding requests don't require e-signature for approval.

- **Rejected Is Final**: Rejected requests cannot be resubmitted; borrower creates new request.

- **Auto-Generate Notice**: Approved requests automatically generate funding notices.

## Decision Summary

| Decision | Status Change | Funding Notice | Next Steps |
|----------|---------------|----------------|------------|
| Approve | APPROVED | Auto-generated | Process funding notice, e-sign |
| Reject | REJECTED | Not created | Borrower creates new request |
| Request Changes | CHANGES_REQUESTED | Not created | Borrower edits and resubmits |
