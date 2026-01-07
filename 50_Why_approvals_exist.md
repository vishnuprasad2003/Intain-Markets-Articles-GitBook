---
title: Why Approvals Exist
description: Understand the purpose and importance of approvals in Intain Markets
---

# Why Approvals Exist

## Overview

Approvals are fundamental to how Intain Markets operates. They serve as quality gates, compliance checkpoints, and authorization mechanisms that ensure transactions progress correctly while protecting all parties involved. Every approval in the platform has a specific purpose and protects specific interests.

## Platform-Specific Approval Workflows

### Term Sheet Approval

**Who Approves:** Facility agents approve term sheets submitted by borrowers.

**What Gets Approved:** Term sheets proposing new credit facilities with facility terms, amounts, interest rates, and repayment terms.

**Why Approval Exists:**
- Ensures facility terms meet requirements before commitment
- Verifies borrower documentation is complete and accurate
- Validates facility structure is feasible and compliant
- Protects lenders by ensuring quality proposals
- Enables iterative improvement through change requests

**What Happens After Approval:**
- Term sheet status changes to "Accepted"
- Master commitment is automatically created with Draft status
- Facility agent can configure the complete facility structure
- Facility becomes available for lender approval

### Master Commitment Approval

**Who Approves:** Lenders approve master commitments configured by facility agents.

**What Gets Approved:** Complete facility structures including lender groups, collateral rules, borrowing base calculations, and facility parameters.

**Why Approval Exists:**
- Ensures lenders agree to facility terms before activation
- Verifies facility structure meets lender requirements
- Validates lender groups and commitment amounts are correct
- Protects borrowers by ensuring lender commitment
- Creates formal agreement between parties

**What Happens After Approval:**
- Master commitment status changes to "ACTIVE"
- Facility agent can set up deal modelling

### Funding Request Approval

**Who Approves:** Facility agents approve funding requests submitted by borrowers.

**What Gets Approved:** Requests to draw down funds from active facilities, including drawdown amounts, purposes, funding dates, and supporting documentation.

**Why Approval Exists:**
- Ensures drawdown requests comply with facility rules
- Verifies borrowing capacity is available
- Validates supporting documentation is complete
- Protects lenders by ensuring proper use of funds
- Maintains facility compliance

**What Happens After Approval:**
- Funding request status changes to "APPROVED"
- Funding notice is automatically generated with PENDING_TOKEN_GENERATION status
- Facility agent can generate tokens and configure token distribution
- Process moves to token generation and lender approval

### Funding Notice Approval

**Who Approves:** Lenders approve funding notices after borrower token approval.

**What Gets Approved:** Individual drawdowns with token allocations, funding amounts, and lender-specific details.

**Why Approval Exists:**
- Ensures lenders agree to individual drawdowns
- Allows lenders to evaluate each drawdown independently
- Protects lenders by enabling independent decisions
- Validates token allocations are correct
- Creates formal agreement for fund transfer

**What Happens After Approval:**
- Lender's approval status in tokenDistribution array changes to "APPROVED"
- Lender can confirm fund transfer
- Other lenders can still approve or reject independently
- Process continues with fund transfer confirmation

### Pool Mandate Acceptance

**Who Approves:** Market makers accept mandates to structure deals for pools.

**What Gets Approved:** Pools submitted by issuers for deal structuring and completion.

**Why Approval Exists:**
- Ensures market makers commit to structuring deals
- Verifies pools meet structuring requirements
- Protects issuers by ensuring market maker commitment
- Creates formal relationship for deal completion
- Enables deal progression

**What Happens After Acceptance:**
- Pool status changes to "Deal"
- Market maker proceeds with deal structuring
- Pool is finalized and committed
- Editing is restricted

## Key Principles

**Quality Assurance** - Approvals ensure quality by requiring review before proceeding. Facility agents review term sheets, lenders review master commitments, and all parties review funding requests.

**Compliance and Risk Management** - Approvals ensure compliance by verifying transactions meet regulatory requirements and business rules. Reviewers assess risk before commitment, protecting all parties.

**Transparency and Accountability** - Approvals provide transparency by creating visible decision points. All approval decisions are documented with who approved, when, and why, creating accountability.

**Workflow Control** - Approvals control workflow progression by acting as gates. Items cannot proceed without required approvals, ensuring proper order and sequence.

**Protection for All Parties** - Approvals protect all parties by ensuring agreement before commitment. Borrowers know their requests are reviewed, lenders can ensure quality, and facility agents can structure properly.

**Collaboration Enablement** - Approvals enable collaboration by creating structured opportunities for feedback. Reviewers can request changes, submitters can respond, and items can be improved iteratively.

**Role-Based Authority** - Different roles have authority to approve different items. Facility agents approve term sheets and funding requests, lenders approve master commitments and funding notices, market makers accept pool mandates.

**Documented Decisions** - All approval decisions are recorded with timestamps, reviewer information, and comments. This creates complete audit trails for compliance and accountability.

**Change Requests vs. Rejection** - Reviewers can request changes (allowing improvement) or reject items (stopping the workflow). This distinction enables iterative improvement while maintaining quality standards.

Understanding why approvals exist helps you navigate the platform effectively, know what to expect at each stage, and understand how approvals protect all parties while ensuring quality and compliance.
