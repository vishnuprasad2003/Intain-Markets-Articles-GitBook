---
title: Status Qualifiers Explained
description: Understand status qualifiers that provide additional context about item states
---

# Status Qualifiers Explained

## Overview

Statuses in Intain Markets often include qualifiers that provide additional context about the state of an item. Understanding these qualifiers helps you better understand what a status means, what actions are available, and what needs to happen next in the workflow. Qualifiers add meaning to base statuses, clarifying workflow position and indicating what's needed.

## Reference Details

**"Pending" Qualifier** - Examples include Mandate Pending, Pending Lender Approval, Pending Token Generation. This qualifier means the item is waiting for someone to take action. It's in a holding state, waiting for a decision or action from another party. Common scenarios include pools that are "Mandate Pending" waiting for market maker to accept or reject, master commitments that are "Pending Lender Approval" waiting for lender to approve, and funding notices that are "Pending Token Generation" waiting for facility agent to generate tokens.

**"Review" Qualifier** - Examples include FAReview, Under Review, Pending Review. This qualifier means the item is being reviewed by someone. A reviewer is evaluating it and will make a decision. Common scenarios include term sheets that are "FAReview" where facility agent is reviewing, funding requests that are "FAReview" where facility agent is evaluating, and pools that are "Under Review" where market maker or investor is reviewing.

**"Requested" Qualifier** - Examples include Changes Requested, Updates Requested. This qualifier means changes or modifications have been requested. The item needs to be updated before it can proceed. Common scenarios include term sheets with "CHANGES_REQUESTED" status where facility agent requests modifications, and funding requests with "CHANGES_REQUESTED" status where facility agent needs changes before approval.

**"Active" Qualifier** - Examples include Active status for master commitments. This qualifier means the item is operational and ready for use. Common scenarios include master commitments that are "Active" meaning the facility is operational and borrowers can create funding requests.

**"Approved" Qualifier** - Examples include Approved status for funding requests. This qualifier means the item has been approved and can proceed. Common scenarios include funding requests that are "APPROVED" meaning facility agent has approved and funding notice is created.

**"Rejected" Qualifier** - Examples include Rejected status for term sheets and funding requests. This qualifier means the item has been rejected and cannot proceed. Common scenarios include term sheets that are "Rejected" meaning facility agent has declined, and funding requests that are "REJECTED" meaning facility agent has declined the request.

## Important Notes

**Qualifiers Clarify Workflow Position** - Qualifiers tell you where the item is in its workflow and what's happening. They help you understand the current state more precisely than base statuses alone.

**Qualifiers Indicate What's Needed** - Qualifiers show what action is required or what's waiting to happen. They guide you on what needs to happen next for the workflow to progress.

**Qualifiers Explain Action Availability** - Qualifiers help explain why certain actions are enabled or disabled. Understanding qualifiers helps you know what you can and cannot do.

**Qualifiers Guide Next Steps** - Qualifiers indicate what needs to happen next for the workflow to progress. They help you understand what to expect and what to prepare for.

**Multiple Qualifiers Possible** - Some statuses may have multiple qualifiers or be combined with other status information. Understanding how qualifiers combine helps you interpret statuses accurately.

**Qualifiers Are Consistent** - The same qualifiers mean the same thing across different item types. Once you understand a qualifier, you can apply that understanding to other contexts.

Understanding status qualifiers helps you interpret statuses more accurately, know what actions are available, understand what needs to happen next, and navigate workflows more effectively.
