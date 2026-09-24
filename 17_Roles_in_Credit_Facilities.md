---
title: Roles in Credit Facilities
description: >-
  Comprehensive guide to all credit facility roles — Borrower, Facility Agent,
  Lender, Servicer, and Paying Agent — their responsibilities, dashboard views,
  and stage-specific capabilities
---

# Roles in Credit Facilities

## Overview

Credit facility transactions involve multiple parties with distinct roles and responsibilities. Understanding these roles helps you navigate the workflow and know what actions each party can take at every stage. In the Credit Facility module, roles have different names compared to other modules on the platform: the Issuer becomes the Borrower, the Market Maker becomes the Facility Agent, and the Investor becomes the Lender. This mapping reflects the distinct terminology used in institutional credit facility transactions.

## Roles Covered

The Credit Facility module recognizes five distinct roles:

| Platform Role | CF Role Name       | Primary Function                              |
| ------------- | ------------------ | --------------------------------------------- |
| Issuer        | **Borrower**       | Seeks funds through the credit facility       |
| Market Maker  | **Facility Agent** | Structures, reviews, and manages the facility |
| Investor      | **Lender**         | Provides funding and approves facility terms  |
| Servicer      | **Servicer**       | Manages ongoing loan administration           |
| Paying Agent  | **Paying Agent**   | Manages payment distribution to lenders       |

## What Each Role Can Do

### Borrower (Issuer)

The Borrower initiates and manages credit facility requests. They are the party seeking funds through the credit facility. The Borrower is the starting point for the entire credit facility workflow.

**Capabilities by Stage:**

* **Term Sheet Creation**: Create new term sheets proposing credit facility terms. Enter facility details including amounts, rates, tenors, and conditions. Sign the term sheet via Adobe Sign before submission.
* **Term Sheet Submission**: Submit signed term sheets to the Facility Agent for review. If the Facility Agent requests changes, edit the term sheet based on feedback and resubmit.
* **Post-Approval (Facility Active)**: View the approved master commitment and facility terms. Map NFT-minted loans to the active facility for funding eligibility.
* **Funding**: Create funding requests to draw down funds from the facility. Each funding request specifies the draw amount, purpose, and supporting documentation. If the Facility Agent requests changes, edit and resubmit.
* **Token Approval**: Approve token transfers when funding notices are ready for settlement.
* **Ongoing Monitoring**: Track facility utilization, available capacity, and funding history.

**Dashboard View:**

* Access the **Credit Facility** section from the left expandable menu
* See term sheets created by them
* See master commitments under approved term sheets
* Available actions: Submit Term Sheet, Edit Term Sheet (when changes requested), View Term Sheet, Map Loans, Create Funding Request

### Facility Agent (Market Maker)

The Facility Agent reviews, structures, and manages credit facilities. They act as the intermediary between Borrowers and Lenders — the central orchestrator of the credit facility lifecycle.

**Capabilities by Stage:**

* **Term Sheet Review**: Review term sheets submitted by Borrowers. Examine facility terms, documentation, borrower information, and supporting materials. Three decision options:
  * **Approve** — the term sheet is accepted and a Master Commitment is automatically created
  * **Reject** — the term sheet is permanently declined (final, cannot be resubmitted)
  * **Request Changes** — the term sheet returns to the Borrower for revision and resubmission
* **Master Commitment Configuration**: After approving a term sheet, configure the Master Commitment. Add lenders to the facility. Set up facility rules and participation structures. Create sub-facilities for multiple-lender arrangements if needed. Submit the configured Master Commitment to Lenders for approval.
* **Deal Modelling**: After the Master Commitment is activated (at least one Lender has approved), set up deal modelling for the facility.
* **Funding Request Review**: Review funding requests submitted by Borrowers. Examine draw amounts, purpose, capacity, and documentation. Three decision options:
  * **Approve** — a Funding Notice is automatically generated for each Lender
  * **Reject** — the funding request is permanently declined
  * **Request Changes** — the funding request returns to the Borrower for revision
* **Funding Notice Management**: E-sign funding notices for each Lender via Adobe Sign.
* **Facility Oversight**: Monitor facility operations, compliance, and utilization across all facilities.

**Dashboard View:**

* Access the **Credit Facility** section from the left expandable menu
* See the **Set-up** tab with term sheets and master commitments awaiting setup
* See the **Active Facilities** tab with active master commitments
* Available actions: Review Term Sheet, Create Facility, Set Up Deal, Review Funding Request, E-sign Funding Notice

### Lender (Investor)

Lenders provide the capital for credit facilities. They review and approve facilities, and transfer funds for approved drawdowns. Lenders are the funding counterparty in the credit facility structure.

**Capabilities by Stage:**

* **Master Commitment Review**: Review master commitments (or sub-master commitments) shared with them in the Opportunities section. Examine the facility structure, terms, participation amounts, and conditions. Approve and e-sign the master commitment via Adobe Sign.
  * **Important**: A single Lender's approval is sufficient to activate the facility — the Master Commitment status changes to **ACTIVE** upon the first Lender approval.
* **Facility Participation**: View approved facilities in the Credit Facility section. Monitor their committed amounts and available capacity.
* **Funding Notice Review**: Review funding notices generated after the Facility Agent approves a Borrower's funding request. The funding notice specifies the draw amount allocated to this Lender.
* **Fund Transfer**: Select the payment method and initiate fund transfer for approved funding notices. Confirm and settle the transfer once the wire is sent.
* **Ongoing Monitoring**: Track their participation, commitments, and funding history across all facilities.

**Dashboard View:**

* Access the **Opportunities** section to see pending master commitments for approval
* Access the **Credit Facility** section to see approved facilities and funding notices
* Available actions: Review & Approve Master Commitment, Review Funding Notice, Confirm and Settle Fund Transfer

### Servicer

The Servicer manages ongoing loan administration for active facilities. This role focuses on the operational aspects of loan management after the facility is live and loans are mapped.

**Capabilities:**

* Upload monthly loan tapes for facility loans to keep performance data current
* Monitor loan performance metrics and portfolio health
* Provide servicing reports to the Facility Agent and other stakeholders
* Access deal details for facilities they service

**Dashboard View:**

* Access the **Servicer** dashboard showing active deals they service
* View deal details and loan-level data
* Upload recurring loan tape data

### Paying Agent

The Paying Agent is designated on the Master Commitment by the Facility Agent during facility setup. The Facility Agent selects the Paying Agent organization from a dropdown when configuring the Master Commitment. In the current platform implementation, the Paying Agent is recorded as an organizational reference on the facility rather than having its own dedicated Credit Facility dashboard or workflow actions. The Paying Agent's identity is captured for legal and operational documentation purposes and may be used for integration with external payment administration systems.

## Important Access Notes

### Role-Based Access Matrix

| Action                                       | Borrower | Facility Agent | Lender | Servicer | Paying Agent |
| -------------------------------------------- | -------- | -------------- | ------ | -------- | ------------ |
| Create Term Sheet                            | ✓        | —              | —      | —        | —            |
| Sign Term Sheet (Adobe Sign)                 | ✓        | —              | —      | —        | —            |
| Submit Term Sheet                            | ✓        | —              | —      | —        | —            |
| Review Term Sheet                            | —        | ✓              | —      | —        | —            |
| Approve/Reject/Request Changes on Term Sheet | —        | ✓              | —      | —        | —            |
| Configure Master Commitment                  | —        | ✓              | —      | —        | —            |
| Add Lenders to Facility                      | —        | ✓              | —      | —        | —            |
| Submit MC for Lender Approval                | —        | ✓              | —      | —        | —            |
| Approve & E-Sign Master Commitment           | —        | —              | ✓      | —        | —            |
| Set Up Deal Modelling                        | —        | ✓              | —      | —        | —            |
| Map Loans to Facility                        | ✓        | —              | —      | —        | —            |
| Create Funding Request                       | ✓        | —              | —      | —        | —            |
| Review Funding Request                       | —        | ✓              | —      | —        | —            |
| Approve/Reject/Request Changes on FR         | —        | ✓              | —      | —        | —            |
| E-Sign Funding Notice                        | —        | ✓              | —      | —        | —            |
| Review Funding Notice                        | —        | —              | ✓      | —        | —            |
| Confirm Fund Transfer                        | —        | —              | ✓      | —        | —            |
| Upload Monthly Loan Tapes                    | —        | —              | —      | ✓        | —            |
| Designated on MC (org field)                 | —        | —              | —      | —        | ✓            |

### Key Access Principles

**Role determines visibility.** Each role only sees the sections, tabs, and actions relevant to their responsibilities. A Borrower will not see the Facility Agent's review actions, and a Lender will not see term sheet creation options.

**Status determines action availability.** Even within a role, actions are only available at the appropriate workflow stage. For example, a Borrower can only edit a term sheet when its status is **Draft** or **CHANGES\_REQUESTED** — not when it is under Facility Agent review.

**One Lender approval activates the facility.** Unlike other approval workflows that may require all parties, a single Lender approval is sufficient to move the Master Commitment to **ACTIVE** status. This enables the Facility Agent to proceed with deal modelling and the Borrower to begin mapping loans.

**Change Requests preserve the workflow.** When the Facility Agent requests changes on a term sheet or funding request, the item returns to the Borrower for revision. The Borrower can edit and resubmit without starting over. Rejection, by contrast, is final.

**Adobe Sign is integrated for key approvals.** Both term sheet signing (Borrower) and master commitment approval (Lender) use Adobe Sign for legally binding e-signatures. Funding notice signing by the Facility Agent also uses Adobe Sign.

### Workflow Summary by Role

**Borrower**: Create term sheet → Sign → Submit → (If changes requested: Edit → Resubmit) → Wait for approval → Map loans → Create funding requests → Approve tokens → Receive funds

**Facility Agent**: Review term sheets → Approve/Reject/Request Changes → Configure MC → Submit to Lenders → Set up deal modelling → Review funding requests → E-sign funding notices

**Lender**: Review MC in Opportunities → Approve & E-Sign → View facility → Review funding notices → Transfer funds → Confirm settlement

**Servicer**: Access active deals → Upload monthly loan tapes → Monitor loan performance

**Paying Agent**: Designated on the Master Commitment by the Facility Agent during facility setup (organizational reference for legal and payment administration purposes)
