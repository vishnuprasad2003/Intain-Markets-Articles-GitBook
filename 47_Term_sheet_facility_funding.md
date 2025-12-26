---
title: Term Sheet, Facility, and Funding Statuses
description: Understand all statuses for credit facility components
---

# Term Sheet, Facility, and Funding Statuses

## Overview

This reference guide explains all statuses for credit facility components: Term Sheets, Master Commitments (Facilities), Funding Requests, and Funding Notices. Understanding these statuses helps you navigate the credit facility workflow and know what to expect at each stage.

## Reference Details

### Term Sheet Statuses

#### Draft Status

**What It Means**: The term sheet has been created and can be edited freely. It has not been signed or submitted yet.

**What You Can Do**:
- Edit all term sheet fields
- Upload or modify documents
- Save changes multiple times
- Sign the term sheet when ready

**What You Cannot Do**:
- Cannot submit until signed
- Cannot proceed to review until submitted

**Who Can See It**: Only you, the borrower who created it.

**Typical Duration**: This status lasts until you sign and submit the term sheet.

**What Happens Next**: Term sheet moves to BorrowerSigned status when signed, then to FAReview when submitted.

#### BorrowerSigned Status

**What It Means**: The borrower has electronically signed the term sheet. You can preview the signed version, and it's ready for submission.

**What You Can Do**:
- Preview the signed version
- Review signed term sheet
- Submit for facility agent review

**What You Cannot Do**:
- Cannot edit (must request changes if needed)
- Cannot proceed until submitted

**Who Can See It**: Only you, the borrower.

**Typical Duration**: This status lasts until you submit for facility agent review.

**What Happens Next**: Term sheet moves to FAReview status when submitted.

#### FAReview Status

**What It Means**: The term sheet has been submitted to the facility agent for review. The facility agent is evaluating it and will make a decision.

**What You Can Do**:
- View the term sheet (read-only)
- Wait for facility agent decision
- Cannot edit while under review

**What Facility Agent Can Do**:
- Review term sheet details
- Approve, reject, or request changes

**Who Can See It**: You (the borrower) and the facility agent.

**Typical Duration**: This status lasts until facility agent makes a decision (typically a few days).

**Possible Outcomes**:
- **Accepted**: Term sheet is approved, master commitment is automatically created.
- **Rejected**: Term sheet is rejected, you must create a new one.
- **CHANGES_REQUESTED**: Facility agent requests modifications, you can update and resubmit.

**What Happens Next**: Term sheet moves to Accepted, Rejected, or CHANGES_REQUESTED based on facility agent decision.

#### Accepted Status

**What It Means**: The facility agent has approved the term sheet. Master commitment is automatically created.

**What You Can Do**:
- View the approved term sheet
- Monitor master commitment creation
- Track facility setup progress

**What Happens Next**: Master commitment is automatically created with Draft status, and facility agent configures it.

**Typical Duration**: This is a final status for term sheets. The process moves to master commitment configuration.

#### Rejected Status

**What It Means**: The facility agent has rejected the term sheet. It cannot be resubmitted.

**What You Can Do**:
- View the rejected term sheet
- Review rejection reason
- Create a new term sheet

**What You Cannot Do**:
- Cannot edit or resubmit
- Cannot proceed with this term sheet

**What Happens Next**: You create a new term sheet addressing the rejection reasons.

**Typical Duration**: This is a final status. You must create a new term sheet to proceed.

#### CHANGES_REQUESTED Status

**What It Means**: The facility agent has requested modifications to the term sheet. You can edit and resubmit.

**What You Can Do**:
- Edit the term sheet
- Make requested changes
- Re-sign if required
- Resubmit for review

**What You Cannot Do**:
- Cannot proceed until changes are made
- Must address all requested changes

**What Happens Next**: You make changes and resubmit, moving back to FAReview status.

**Typical Duration**: This status lasts until you make changes and resubmit.

### Master Commitment Statuses

#### Draft Status

**What It Means**: The master commitment has been automatically created from your approved term sheet. The facility agent is configuring it.

**What Facility Agent Can Do**:
- Configure facility rules and parameters
- Set up borrowing base calculations
- Define collateral eligibility rules
- Add and configure lender groups
- Edit all fields and settings
- Save changes multiple times

**What You Can Do**:
- View the master commitment (read-only)
- Monitor configuration progress

**Who Can See It**: Facility agent (who configures it) and borrower (who can view it).

**Typical Duration**: This status lasts until facility agent completes configuration and submits for lender approval.

**What Happens Next**: Master commitment moves to PendingLenderApproval status when facility agent submits.

#### PendingLenderApproval Status

**What It Means**: The facility agent has completed configuration and submitted the master commitment for lender approval. Waiting for at least one lender to approve.

**What Lenders Can Do**:
- Review the complete master commitment
- Approve the facility via electronic signature
- Reject the facility (if allowed)

**What Facility Agent Can Do**:
- View the master commitment
- Monitor approval status
- Cannot edit (configuration is complete)

**What You Can Do**:
- View the master commitment (read-only)
- Monitor approval progress
- Cannot create funding requests yet (facility not active)

**Who Can See It**: Facility agents, borrowers, and lenders who are configured in the facility.

**Typical Duration**: This status lasts until at least one lender approves the facility.

**Possible Outcomes**:
- **Approved**: At least one lender approves, facility becomes Active.
- **Rejected**: All lenders reject (rare), facility may return to Draft for reconfiguration.

**What Happens Next**: Facility moves to Active status when at least one lender approves.

#### Active Status

**What It Means**: At least one lender has approved the master commitment, and the facility is operational. Borrowers can create funding requests.

**What Borrowers Can Do**:
- View the active facility
- Create funding requests
- Monitor borrowing capacity
- Track drawdowns

**What Facility Agents Can Do**:
- View the active facility
- Review funding requests
- Manage facility operations
- Monitor borrowing activity

**What Lenders Can Do**:
- View the active facility
- Review and approve funding notices
- Monitor facility activity
- Track borrowing and repayments

**Who Can See It**: All parties involved in the facility (facility agents, borrowers, and lenders).

**Typical Duration**: This is the operational status. The facility remains active until it expires, is closed, or is terminated.

**What Happens Next**: Borrowers create funding requests, facility agents review them, funding notices are generated, lenders approve drawdowns, and funds are disbursed.

### Funding Request Statuses

#### DRAFT Status

**What It Means**: The funding request has been created but not yet submitted for review. You can edit freely.

**What You Can Do**:
- Edit all request fields
- Modify amount, purpose, date, or documents
- Save changes multiple times
- Submit when ready

**What You Cannot Do**:
- Cannot proceed until submitted
- Cannot be reviewed until submitted

**Typical Duration**: This status lasts until you submit for facility agent review.

**What Happens Next**: Funding request moves to FAReview status when submitted.

#### FAReview Status

**What It Means**: The funding request has been submitted to the facility agent for review. Waiting for facility agent decision.

**What You Can Do**:
- View the request (read-only)
- Wait for facility agent decision
- Cannot edit while under review

**What Facility Agent Can Do**:
- Review request details
- Approve, reject, or request changes

**Typical Duration**: This status lasts until facility agent makes a decision (typically a few days).

**Possible Outcomes**:
- **APPROVED**: Request is approved, funding notice is automatically created.
- **REJECTED**: Request is rejected, you must create a new one.
- **CHANGES_REQUESTED**: Facility agent requests modifications, you can update and resubmit.

**What Happens Next**: Request moves to APPROVED, REJECTED, or CHANGES_REQUESTED based on facility agent decision.

#### APPROVED Status

**What It Means**: The facility agent has approved the funding request. Funding notice is automatically created.

**What You Can Do**:
- View the approved request
- Monitor funding notice progress
- Approve token transfer when ready

**What Happens Next**: Funding notice is automatically created, tokens are generated, and drawdown process proceeds.

**Typical Duration**: This is a final status for funding requests. The process moves to funding notice workflow.

#### REJECTED Status

**What It Means**: The facility agent has rejected the funding request. It cannot be resubmitted.

**What You Can Do**:
- View the rejected request
- Review rejection reason
- Create a new funding request

**What You Cannot Do**:
- Cannot edit or resubmit
- Cannot proceed with this request

**What Happens Next**: You create a new funding request addressing the rejection reasons.

**Typical Duration**: This is a final status. You must create a new request to proceed.

#### CHANGES_REQUESTED Status

**What It Means**: The facility agent has requested modifications to the funding request. You can edit and resubmit.

**What You Can Do**:
- Edit the request
- Make requested changes
- Resubmit for review

**What You Cannot Do**:
- Cannot proceed until changes are made
- Must address all requested changes

**What Happens Next**: You make changes and resubmit, moving back to FAReview status.

**Typical Duration**: This status lasts until you make changes and resubmit.

### Funding Notice Statuses

#### PENDING_TOKEN_GENERATION Status

**What It Means**: The funding notice has been automatically created from an approved funding request. Waiting for facility agent to generate tokens.

**What Facility Agent Can Do**:
- Generate tokens
- Configure token distribution
- Initialize tokenDistribution array

**What You Can Do**:
- View the funding notice (read-only)
- Wait for token generation

**Typical Duration**: This status lasts until facility agent generates tokens.

**What Happens Next**: Status moves to TOKEN_GENERATED when tokens are created.

#### TOKEN_GENERATED Status

**What It Means**: Tokens have been created and distributed. Facility agent can sign for lenders, and borrower can approve token transfer.

**What Facility Agent Can Do**:
- Sign funding notice for each lender individually
- Track per-lender signature status

**What You Can Do**:
- Review token allocation
- Approve token transfer when ready

**What Happens Next**: After borrower approves, status moves to TOKEN_APPROVED, and lenders can review.

**Typical Duration**: This status lasts until borrower approves token transfer.

#### TOKEN_APPROVED Status

**What It Means**: The borrower has approved token transfer. Funding notice is visible to lenders, and lenders can review and approve drawdowns.

**What Lenders Can Do**:
- Review funding notice
- Approve or reject drawdowns
- Confirm fund transfers

**What You Can Do**:
- View funding notice
- Track lender decisions
- Monitor fund transfers

**What Happens Next**: Lenders review and approve, transfer funds, and confirm transfers.

**Typical Duration**: This status lasts until all lenders make decisions and confirm transfers.

## Important Notes

- **Status Progression**: Each component has its own status flow. Term sheets progress from Draft → BorrowerSigned → FAReview → Accepted. Master commitments progress from Draft → PendingLenderApproval → Active. Funding requests progress from DRAFT → FAReview → APPROVED. Funding notices progress from PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED.

- **Status Controls Actions**: The current status determines what actions are available. You can only take actions allowed by the current status.

- **Some Statuses Trigger Automatic Actions**: Accepted term sheets automatically create master commitments. APPROVED funding requests automatically create funding notices.

- **Status Changes Are Recorded**: Every status change is recorded with who changed it and when, creating a complete audit trail.

- **Status History**: You can view the complete history of status changes, including who changed them and when, by viewing the item's audit trail or history.

- **Status Badges**: Statuses are displayed as badges or labels, often color-coded for easy identification.

Understanding all credit facility statuses helps you track progress through the workflow, know what actions are available at each stage, and understand why certain actions are disabled.
