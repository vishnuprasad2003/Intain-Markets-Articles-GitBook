---
title: Status Qualifiers Explained
description: Understand status qualifiers that provide additional context about item states
---

# Status Qualifiers Explained

## Overview

Statuses in Intain Markets often include qualifiers that provide additional context about the state of an item. Qualifiers add meaning to base statuses, clarifying workflow position and indicating what's needed for progression.

## Reference Details

**"Pending" Qualifier** - Examples include Mandate Pending, Pending Lender Approval, Pending Token Generation. This qualifier means the item is waiting for someone to take action. It's in a holding state, waiting for a decision or action from another party. Common scenarios include pools that are "Mandate Pending" waiting for market maker to accept or reject, master commitments that are "Pending Lender Approval" waiting for lender to approve, and funding notices that are "Pending Token Generation" waiting for facility agent to generate tokens. When you see "Pending", it means you're waiting for another party to act.

**"Review" Qualifier** - Examples include FAReview, Under Review, Pending Review. This qualifier means the item is being reviewed by someone. A reviewer is evaluating it and will make a decision. Common scenarios include term sheets that are "FAReview" where facility agent is reviewing, funding requests that are "FAReview" where facility agent is evaluating, and pools that are "Under Review" where market maker or investor is reviewing. When you see "Review", it means someone is actively evaluating the item.

**"Requested" Qualifier** - Examples include Changes Requested, Updates Requested. This qualifier means changes or modifications have been requested. The item needs to be updated before it can proceed. Common scenarios include term sheets with "CHANGES_REQUESTED" status where facility agent requests modifications, and funding requests with "CHANGES_REQUESTED" status where facility agent needs changes before approval. When you see "Requested", it means you need to make changes before proceeding.

**"ACTIVE" Qualifier** - Examples include ACTIVE status for master commitments. This qualifier means the item is operational and ready for use. Common scenarios include master commitments that are "ACTIVE" meaning the facility is operational and borrowers can create funding requests. When you see "ACTIVE", it means the item is fully operational and ready for use.

**"Approved" Qualifier** - Examples include Approved status for funding requests. This qualifier means the item has been approved and can proceed. Common scenarios include funding requests that are "APPROVED" meaning facility agent has approved and funding notice is created. When you see "Approved", it means the item has passed review and can proceed to the next stage.

**"Rejected" Qualifier** - Examples include Rejected status for term sheets and funding requests. This qualifier means the item has been rejected and cannot proceed. Common scenarios include term sheets that are "Rejected" meaning facility agent has declined, and funding requests that are "REJECTED" meaning facility agent has declined the request. When you see "Rejected", it means the item has been declined and cannot proceed further.

**"Signed" Qualifier** - Examples include BorrowerSigned status for term sheets. This qualifier means the item has been electronically signed. Common scenarios include term sheets that are "BorrowerSigned" meaning the borrower has signed electronically. When you see "Signed", it means electronic signatures have been completed.

**"Generated" Qualifier** - Examples include TOKEN_GENERATED status for funding notices. This qualifier means something has been generated or created. Common scenarios include funding notices that are "TOKEN_GENERATED" meaning tokens have been created. When you see "Generated", it means the system has created something needed for the process.

## Important Notes

**Qualifiers Clarify Workflow Position** - Qualifiers tell you where the item is in its workflow and what's happening. They help you understand the current state more precisely than base statuses alone.

**Qualifiers Indicate What's Needed** - Qualifiers show what action is required or what's waiting to happen. They guide you on what needs to happen next for the workflow to progress.

**Qualifiers Explain Action Availability** - Qualifiers help explain why certain actions are enabled or disabled. When actions are disabled, qualifiers often explain why.

**Qualifiers Guide Next Steps** - Qualifiers indicate what needs to happen next for the workflow to progress. They help you understand what to expect and what to prepare for.

**Multiple Qualifiers Possible** - Some statuses may have multiple qualifiers or be combined with other status information. Some items may have complex statuses with multiple qualifiers.

**Qualifiers Are Consistent** - The same qualifiers mean the same thing across different item types. Once you understand a qualifier, you can apply that understanding to other contexts.

**Qualifiers Change with Workflow** - Qualifiers change as items progress through workflows. Status progression often involves qualifier changes.

**Qualifiers Support Decision Making** - Qualifiers provide information that helps you make decisions about what actions to take.
