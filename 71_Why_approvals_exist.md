---
title: Why Approvals Exist
description: Understand why Intain Markets requires approvals at every critical step, the maker-checker philosophy that drives them, and how each approval gate protects all parties in a transaction
---

# Why Approvals Exist

## Overview

Approvals are one of the most visible design decisions in Intain Markets. Every transaction of consequence — from a borrower proposing a term sheet to a lender funding a drawdown — passes through at least one explicit approval gate before it can take effect. This is not accidental. The platform is built on the principle that no single party should be able to advance a financial commitment without independent review and consent from the party who bears the risk or responsibility.

This document explains the philosophy behind that design, the pattern it follows, and the specific approval points you encounter across the platform.

## How the Platform Is Designed

### The Maker-Checker Pattern

At the heart of every approval in Intain Markets is the **maker-checker** principle, a well-established control in financial services. The idea is straightforward:

- **The maker** initiates or prepares something — a term sheet, a funding request, a pool mandate, a deal.
- **The checker** is a different person (and typically a different organization) who reviews the work and decides whether to approve, reject, or request changes.

The platform enforces this separation structurally. A borrower who creates a term sheet cannot approve it — only the facility agent can. An issuer who publishes an asset sale deal cannot approve it — only the underwriter can. The person who submits is never the person who approves. This is not a policy guideline; it is enforced in code. The system checks the caller's role before allowing any approval action, and the role of the submitter is always different from the role of the approver.

### Why Not Just Let Things Proceed?

In principle, a platform could allow items to move through a workflow automatically. But in structured finance, each progression represents a financial or legal commitment:

- Approving a term sheet means the facility agent is satisfied the borrower qualifies and the terms are viable.
- Approving a master commitment means a lender is legally committing capital.
- Approving a funding request means the facility agent confirms the draw complies with facility rules.
- Accepting a pool mandate means the market maker is committing to structure the deal.

Without explicit approval gates, errors, incomplete documentation, or unacceptable terms could propagate through the system and create obligations that are difficult or impossible to unwind.

## What This Enables for Users

### Protection for Every Party

Each approval gate exists because a specific party needs the opportunity to review before they are affected:

| Approval Gate | Who Approves | Who Is Protected |
|---|---|---|
| Term Sheet Approval | Facility Agent | Lenders (ensures viable terms before commitment creation) |
| Master Commitment Approval | Lender | Lender (ensures they agree before capital commitment) |
| Funding Request Approval | Facility Agent | Lenders (ensures draw complies with facility rules) |
| Funding Notice E-Signature | Facility Agent (signs for each lender) | Lender (formal documentation before fund transfer) |
| Pool Mandate Acceptance | Market Maker | Market Maker (ensures pool quality before structuring commitment) |
| Asset Sale Deal Approval | Underwriter | Investors (ensures deal quality before investor visibility) |
| Token Approval (FT) | Issuer | All parties (MFA-gated confirmation before token distribution) |
| KYC Approval | Admin | Platform (ensures identity verification before access) |

### Accountability and Auditability

Every approval decision is recorded permanently. The platform captures who approved (or rejected), when they did it, and any comments or reasons they provided. This creates a complete decision trail that can be reviewed at any time — for compliance, dispute resolution, or simply understanding how a transaction progressed.

### Three Possible Outcomes

At most approval points, the reviewer has three options:

| Action | What It Means | What Happens |
|---|---|---|
| **Approve** | The reviewer is satisfied and the item advances | Status changes to the next stage; downstream processes may trigger automatically (e.g., master commitment auto-created after term sheet approval) |
| **Request Changes** | The reviewer sees issues that can be corrected | The item returns to the submitter for modification; the submitter can edit and resubmit |
| **Reject** | The reviewer determines the item cannot proceed | The item is finalized as rejected; the submitter cannot resubmit the same item but can create a new one |

Not every approval point supports all three outcomes. For instance, pool mandate acceptance is a binary accept/reject decision with no "request changes" option. Master commitment approval is also binary — the lender either approves and e-signs, or they do not act.

## Key Principles to Understand

### Approvals Are Not Bottlenecks — They Are Safeguards

Every approval gate exists because removing it would expose one or more parties to unreviewed risk. The platform is designed so that each approval step takes the minimum information needed for a sound decision, and the reviewer sees all relevant details in a single view.

### Separation of Roles Is Enforced, Not Suggested

The platform does not rely on organizational policies to maintain maker-checker separation. Role checks are built into every approval endpoint. An issuer literally cannot call the "approve term sheet" endpoint — the system rejects the request before it reaches the business logic.

### Automatic Consequences Follow Approvals

Approvals are not just status changes — they trigger downstream automation:

- **Term sheet approved** → Master commitment is auto-created in Draft status, pre-populated with term sheet data.
- **Funding request approved** → Funding notice is auto-generated with status Pending Token Generated.
- **Asset sale deal approved** → Deal becomes visible to investors for commitment.
- **Lender approves master commitment** → If this is the first lender approval, the facility status changes to Active, enabling deal modelling and funding requests.

### Multi-Factor Authentication for High-Stakes Actions

Certain approval actions are additionally protected by multi-factor authentication (MFA). Before an issuer can approve a token transfer or mint NFTs, or before a paying agent can execute a fund transfer, they must verify their identity with a one-time password. This adds a second layer of confirmation beyond role-based access, ensuring that sensitive blockchain operations are authorized by the right person at the right moment.

### E-Signature as Formal Commitment

Several approvals are paired with electronic signatures (via Adobe Sign or ZohoSign), which serve as legally binding records of consent. Lender approval of a master commitment, for example, requires the lender to complete an e-signature process — not just click an "Approve" button. This means the approval is not just a system action but a formal, signed commitment.
