---
title: Status Qualifiers Explained
description: Understand status qualifiers that provide additional context about item states
---

# Status Qualifiers Explained

## Overview

Statuses in Intain Markets often include qualifiers that provide additional context about the state of an item. Understanding these qualifiers helps you better understand what a status means, what actions are available, and what needs to happen next in the workflow.

## What This Means for the User

When you see statuses with qualifiers like "Pending," "Review," or "Requested," these qualifiers add meaning to the base status:

- **They clarify workflow position** - Qualifiers tell you where the item is in its workflow and what's happening.

- **They indicate what's needed** - Qualifiers show what action is required or what's waiting to happen.

- **They explain action availability** - Qualifiers help explain why certain actions are enabled or disabled.

- **They guide next steps** - Qualifiers indicate what needs to happen next for the workflow to progress.

Understanding qualifiers helps you interpret statuses more accurately and know what to expect.

## Key Concepts Explained

### "Pending" Qualifier

**Examples**: Mandate Pending, Pending Lender Approval, Pending Token Generation

**What It Means**: The item is waiting for someone to take action. It's in a holding state, waiting for a decision or action from another party.

**What You Can Do**:
- View the item
- See what's pending
- Wait for the required action
- Monitor progress

**What You Cannot Do**:
- Usually limited actions available
- Cannot proceed until pending action is completed
- May not be able to edit

**Common Scenarios**:
- Pool is "Mandate Pending" - waiting for market maker to accept or reject
- Master commitment is "Pending Lender Approval" - waiting for lender to approve
- Funding notice is "Pending Token Generation" - waiting for facility agent to generate tokens

### "Review" Qualifier

**Examples**: FAReview, Under Review, Pending Review

**What It Means**: The item is being reviewed by someone. A reviewer is evaluating it and will make a decision.

**What You Can Do**:
- View the item (usually read-only)
- See review status
- Wait for review decision
- Monitor review progress

**What You Cannot Do**:
- Cannot edit while under review
- Cannot proceed until review is complete
- Must wait for reviewer decision

**Common Scenarios**:
- Term sheet is "FAReview" - facility agent is reviewing
- Funding request is "FAReview" - facility agent is evaluating
- Pool is "Under Review" - market maker or investor is reviewing

### "Requested" Qualifier

**Examples**: Changes Requested, Updates Requested

**What It Means**: Changes or modifications have been requested. The item needs to be updated before it can proceed.

**What You Can Do**:
- Edit the item
- Make requested changes
- Address all requested modifications
- Resubmit when complete

**What You Cannot Do**:
- Cannot proceed until changes are made
- Must address all requested changes
- Cannot skip requested modifications

**Common Scenarios**:
- Term sheet has "CHANGES_REQUESTED" - facility agent wants modifications
- Funding request has "CHANGES_REQUESTED" - facility agent needs updates
- Pool has change requests - market maker or investor requested improvements

### "Approved" Qualifier

**Examples**: Approved, Accepted, Token Approved

**What It Means**: The item has been approved and can proceed to the next phase. Approval indicates the item meets requirements.

**What You Can Do**:
- Proceed to next phase
- Take next steps in workflow
- Move forward with process

**What You Cannot Do**:
- Usually cannot edit after approval
- Cannot undo approval easily
- Must proceed to next phase

**Common Scenarios**:
- Term sheet is "Accepted" - approved by facility agent, master commitment created
- Funding request is "APPROVED" - approved by facility agent, funding notice created
- Token transfer is "TOKEN_APPROVED" - borrower approved, lenders can review

### "Rejected" Qualifier

**Examples**: Rejected

**What It Means**: The item has been rejected and will not proceed. Rejection is a final decision.

**What You Can Do**:
- View the rejected item
- See rejection reason
- Create new item to try again
- Learn from rejection

**What You Cannot Do**:
- Cannot edit rejected item
- Cannot resubmit same item
- Cannot proceed with rejected item
- Cannot appeal rejection

**Common Scenarios**:
- Term sheet is "Rejected" - facility agent rejected, must create new term sheet
- Funding request is "REJECTED" - facility agent rejected, must create new request
- Pool mandate is rejected - market maker declined, can share with another

## Important Points to Know

- **Qualifiers provide context** - They add meaning to base statuses, helping you understand what's happening.

- **They help explain action availability** - Qualifiers indicate why certain actions are enabled or disabled.

- **They indicate what needs to happen next** - Qualifiers show what action is required for workflow to progress.

- **They show workflow progression** - Qualifiers help you understand where items are in their workflow journey.

- **They help interpret statuses** - Understanding qualifiers helps you better understand what each status means.

- **Multiple qualifiers possible** - Some statuses may have multiple qualifiers (for example, "Pending - Under Review").

- **Qualifiers are consistent** - Same qualifiers mean the same thing across different item types.

- **Status badges show qualifiers** - Status displays include qualifiers, so you can see them at a glance.

- **Complete context** - Qualifiers provide complete context about item state, not just the base status.

- **Workflow guidance** - Qualifiers guide you on what to do next and what to expect.

Understanding status qualifiers helps you better interpret statuses, know what actions are available, understand why actions are disabled, and know what needs to happen next in your workflow.
