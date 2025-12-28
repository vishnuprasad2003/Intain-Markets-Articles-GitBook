---
title: Term Sheet, Facility, and Funding Statuses
description: Understand all statuses for credit facility components
---

# Term Sheet, Facility, and Funding Statuses

## Overview

This comprehensive reference guide explains all statuses for credit facility components: Term Sheets, Master Commitments (Facilities), Funding Requests, and Funding Notices. Understanding these statuses helps you navigate the credit facility workflow and know what to expect at each stage. Each component has its own status progression that reflects where it is in the workflow, and understanding them helps you work effectively within the credit facility system.

## Lifecycle Overview

Credit facilities involve multiple components that progress through their own lifecycles: **Term Sheets** start as Draft, move through BorrowerSigned and FAReview, and reach Accepted (which triggers master commitment creation). **Master Commitments** are auto-created from approved term sheets, progress from Draft through PendingLenderApproval to Active. **Funding Requests** start as DRAFT, move through FAReview, and reach APPROVED (which triggers funding notice creation). **Funding Notices** are auto-created from approved funding requests, progressing from PENDING_TOKEN_GENERATION through TOKEN_GENERATED to TOKEN_APPROVED.

The lifecycle is designed to support the credit facility workflow—borrowers propose facilities through term sheets, facility agents structure facilities through master commitments, borrowers request funds through funding requests, and the system manages drawdowns through funding notices. Each component has specific purposes and allows different types of actions, ensuring that facilities progress correctly through the structured workflow. Understanding this lifecycle helps you know what to expect and how to navigate the credit facility process effectively.

## Status Meanings

### Term Sheet Statuses

**Draft** - The term sheet has been created and can be edited freely. It has not been signed or submitted yet. Term sheets in Draft status allow full editing and are not yet ready for submission.

**BorrowerSigned** - The borrower has electronically signed the term sheet. You can preview the signed version, and it's ready for submission. Term sheets in BorrowerSigned status have been signed and can be submitted for facility agent review.

**FAReview** - The term sheet has been submitted to the facility agent for review. The facility agent is evaluating it and will make a decision. Term sheets in FAReview status are under facility agent review and waiting for decisions.

**Accepted** - The facility agent has approved the term sheet. Master commitment is automatically created. Term sheets in Accepted status have been approved and trigger master commitment creation.

**Rejected** - The facility agent has rejected the term sheet. It cannot be resubmitted. Term sheets in Rejected status have been declined and cannot proceed further.

**CHANGES_REQUESTED** - The facility agent has requested modifications to the term sheet. You can edit and resubmit. Term sheets in CHANGES_REQUESTED status allow editing and resubmission after changes are made.

### Master Commitment Statuses

**Draft** - The master commitment has been automatically created from an approved term sheet. The facility agent is configuring it. Master commitments in Draft status are being configured and are not yet ready for lender review.

**PendingLenderApproval** - The facility agent has completed configuration and submitted the master commitment for lender approval. Waiting for at least one lender to approve. Master commitments in PendingLenderApproval status are ready for lender review and decision.

**Active** - At least one lender has approved the master commitment, and the facility is operational. Borrowers can create funding requests. Master commitments in Active status are operational and ready for use.

### Funding Request Statuses

**DRAFT** - The funding request has been created but not yet submitted for review. You can edit freely. Funding requests in DRAFT status allow full editing and are not yet ready for submission.

**FAReview** - The funding request has been submitted to the facility agent for review. Waiting for facility agent decision. Funding requests in FAReview status are under facility agent review and waiting for decisions.

**APPROVED** - The facility agent has approved the funding request. Funding notice is automatically created. Funding requests in APPROVED status have been approved and trigger funding notice creation.

**REJECTED** - The facility agent has rejected the funding request. It cannot be resubmitted. Funding requests in REJECTED status have been declined and cannot proceed further.

**CHANGES_REQUESTED** - The facility agent has requested modifications to the funding request. You can edit and resubmit. Funding requests in CHANGES_REQUESTED status allow editing and resubmission after changes are made.

### Funding Notice Statuses

**PENDING_TOKEN_GENERATION** - The funding notice has been automatically created from an approved funding request. Waiting for facility agent to generate tokens. Funding notices in PENDING_TOKEN_GENERATION status are waiting for token generation.

**TOKEN_GENERATED** - Tokens have been created and distributed. Facility agent can sign for lenders, and borrower can approve token transfer. Funding notices in TOKEN_GENERATED status have tokens created and are ready for signing and approval.

**TOKEN_APPROVED** - The borrower has approved token transfer. Funding notice is visible to lenders, and lenders can review and approve drawdowns. Funding notices in TOKEN_APPROVED status are visible to lenders and ready for lender review.

## What Each Status Indicates

**Term Sheet Statuses** indicate where term sheets are in the proposal and approval process. Draft means you're still preparing, BorrowerSigned means it's ready for submission, FAReview means it's under facility agent review, Accepted means it's approved and triggers master commitment creation, Rejected means it's been declined, and CHANGES_REQUESTED means modifications are needed before approval. Understanding term sheet statuses helps you know where proposals are in the approval process.

**Master Commitment Statuses** indicate where facilities are in the setup and activation process. Draft means facility agent is configuring, PendingLenderApproval means it's waiting for lender approval, and Active means the facility is operational and ready for funding requests. Understanding master commitment statuses helps you know where facilities are in the setup and activation process.

**Funding Request Statuses** indicate where funding requests are in the review and approval process. DRAFT means you're still preparing, FAReview means it's under facility agent review, APPROVED means it's approved and triggers funding notice creation, REJECTED means it's been declined, and CHANGES_REQUESTED means modifications are needed before approval. Understanding funding request statuses helps you know where drawdown requests are in the approval process.

**Funding Notice Statuses** indicate where funding notices are in the token generation and lender approval process. PENDING_TOKEN_GENERATION means tokens haven't been created yet, TOKEN_GENERATED means tokens exist and signing can occur, and TOKEN_APPROVED means borrowers have approved and lenders can review. Understanding funding notice statuses helps you know where drawdowns are in the token and approval process.

Understanding all credit facility statuses helps you track progress through the workflow, know what actions are available at each stage, understand why certain actions are disabled, know what to expect at each status, and work effectively within the credit facility system.
