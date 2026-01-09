---
title: Funding Request Outcomes
description: Understand what happens after your funding request is reviewed
---

# Funding Request Outcomes

## Overview

When you submit a funding request, the facility agent reviews it and makes a decision: Approve, Reject, or Request Changes. This guide explains what each outcome means and what happens next.

## Possible Outcomes

After you submit a funding request to the facility agent, there are three possible outcomes:

1. **Approved** - Your request meets all requirements
2. **Rejected** - Your request doesn't meet requirements
3. **Changes Requested** - Your request needs modifications

![Funding Request Review - FA](imagesByMdFilesFolder/23/review_funding_request_FAReview.png)

## Approved

**What It Means:**
- Your funding request meets all requirements
- The facility agent has approved your drawdown
- The funding process proceeds

**Status Change:**
- Status changes to **APPROVED**

**What Happens Next:**

1. **Funding Notice Generated**
   - The system automatically generates a funding notice
   - Status: Pending Token Generated

2. **Facility Agent Approves Notice**
   - The facility agent clicks Approve on the funding notice

3. **Facility Agent E-Signs for Each Lender**
   - The facility agent signs the funding notice for each lender individually
   - Progress shows as E-sign (0/n), (1/n), (2/n), etc.

4. **Lenders See the Notice**
   - Each lender can see the funding notice once the FA has e-signed for them

5. **Lenders Transfer Funds**
   - Lenders review the funding notice
   - Lenders select payment method
   - Lenders transfer funds and click **Confirm and Settle**

6. **Funds Disbursed**
   - Tokens are transferred
   - You receive the funds

## Rejected

**What It Means:**
- Your funding request doesn't meet requirements
- The facility agent has declined your request
- The rejection reason is provided

**Status Change:**
- Status changes to **REJECTED** (final state)

**What Happens Next:**

1. **Review Rejection Reason**
   - Read the reason provided by the facility agent
   - Understand what requirements were not met

2. **Create New Request**
   - Rejected requests cannot be resubmitted
   - You must create a new funding request
   - Address the rejection reasons in your new request

**Important:** You cannot edit or resubmit a rejected funding request. You must start fresh with a new request.

## Changes Requested

**What It Means:**
- Your request needs modifications before approval
- The facility agent has specified what needs to change
- You can edit and resubmit

**Status Change:**
- Status changes to **CHANGES_REQUESTED**

**What Happens Next:**

1. **Review Change Request**
   - Read the details provided by the facility agent
   - Understand what modifications are needed

2. **Edit Your Request**
   - Your funding request becomes editable again
   - Make the requested changes
   - Update documentation if needed

3. **Resubmit**
   - Submit the updated request
   - Status changes back to **FAReview**
   - Facility agent reviews again

4. **Await New Decision**
   - The facility agent may:
     - Approve (funding notice generated)
     - Reject (create new request)
     - Request more changes (repeat process)

## Summary

| Outcome | Status | Funding Notice | Next Steps |
|---------|--------|----------------|------------|
| Approved | APPROVED | Auto-generated | FA e-signs, lenders transfer funds |
| Rejected | REJECTED | Not created | Create new request |
| Changes Requested | CHANGES_REQUESTED | Not created | Edit and resubmit |

## Tips

**For Approved Requests:**
- Monitor the funding notice progress
- Funds will be disbursed after lenders Confirm and Settle

**For Rejected Requests:**
- Carefully read the rejection reason
- Ensure your new request addresses all issues
- Verify capacity and documentation before submitting

**For Change Requests:**
- Address all requested changes
- Double-check before resubmitting
- The process may repeat until approved or rejected
