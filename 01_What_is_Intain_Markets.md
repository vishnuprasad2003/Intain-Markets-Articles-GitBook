---
title: What is Intain Markets
description: >-
  Comprehensive introduction to the Intain Markets platform — blockchain-based
  digital infrastructure for structured finance transactions across
  securitization, credit facilities, asset sales, and parti
---

# What is Intain Markets

## Overview

[Intain Markets](https://intainft.com/intainmarkets) is a blockchain-based digital infrastructure platform for structured finance transactions. The platform enables issuers, investors, market makers, servicers, borrowers, facility agents, lenders, and other participants to collaborate on structured finance workflows with complete transparency, traceability, and automation.

Built on blockchain technology, Intain Markets provides a secure, auditable environment for managing the entire lifecycle of structured finance transactions — from loan onboarding and pool creation through deal structuring, investor commitment, tokenized settlement, repayment, and deal closure. Every action taken on the platform is recorded with an immutable audit trail, providing institutional-grade accountability for all participants.

Intain Markets is not a single-purpose tool. It is a comprehensive platform that supports four distinct product lines — **Securitization**, **Credit Facilities**, **Asset Sale**, and **Participation Agreements** — each with its own workflows, roles, statuses, and analytics. Whether you are structuring an asset-backed securitization, managing a revolving credit facility, executing a whole loan sale, or creating a participation agreement, the platform provides end-to-end digital infrastructure for the transaction.

## How the Platform Is Designed

### Four Product Lines

Intain Markets is organized around four major product lines, each designed for a specific type of structured finance transaction:

**Securitization** — The platform's foundational product line for structuring and managing securitization deals. Issuers create pools of loans, share them with market makers for review, structure deals with tranching and waterfall calculations, and distribute to investors. The securitization module includes pool creation, loan management, deal setup, waterfall calculations, investor distribution, recurring calculations, and ESMA regulatory reporting for European securitizations.

**Credit Facilities** — A complete lifecycle management system for credit facilities. Borrowers submit term sheets, facility agents configure master commitments, lenders approve and e-sign commitments, and the platform manages the entire funding cycle from deal modelling through funding requests, funding notices, lender fund transfers, and settlement. Credit facilities support revolving and term structures, multi-branch sub-facilities, and delegation workflows.

**Asset Sale** — Whole loan sale transaction management from deal creation through investor commitment, blockchain-based settlement, post-sale repayment (full, partial, or default declaration), and deal closure. The asset sale module supports loan tape upload and field mapping, NFT-based receivables, and a complete repayment lifecycle including investor confirmation and NFT burn.

**Participation Agreements** — Creation and management of participation agreement transactions between originators and participants, enabling shared ownership and risk distribution of loan assets.

### Blockchain-Based Tokenization

At the core of the platform is blockchain-based tokenization. Loans and receivables are tokenized as NFTs (Non-Fungible Tokens) on the blockchain, while participation and settlement use Fungible Tokens (FT). Each deal receives a unique contract address, and every token has a unique identifier. This tokenization provides:

* **Immutable ownership records** — Token transfers on-chain permanently record who holds what
* **Transparent settlement** — Settlement is recorded on the blockchain, not just in a database
* **NFT lifecycle tracking** — After settlement, receivables NFTs are **Transferred** to investors; during repayment they move to **Retirement pending** and then **Retired** when burned on-chain
* **Document hash verification** — Documents stored on-chain have hash verification for integrity

### Workflow-Driven Architecture

Every transaction type on the platform follows a defined workflow with clear stages, status transitions, and approval gates. The platform enforces that actions can only be taken by the right person at the right time:

* **Status-based action controls** — What you can do depends on the current status of the item and your role
* **Approval gates** — Critical transitions require explicit approval from authorized participants
* **Automated transitions** — Many status changes happen automatically (e.g., funding notice auto-generated on funding request approval)
* **Role-based visibility** — Each role sees only the actions and data relevant to their participation

### Multi-Party Collaboration

Structured finance involves multiple organizations working together. The platform supports this through:

* **Role-based participation** — Each organization operates in its designated role with appropriate capabilities
* **Cross-organization sharing** — Pools, deals, and facilities can be shared with specific organizations
* **Feedback workflows** — Structured feedback and comment workflows between parties
* **Per-participant tracking** — Individual status, actions, and signatures tracked for each participant

## What This Enables for Users

### For Issuers or Borrowers

* Create and manage loan pools, term sheets, and funding requests from a single platform
* Submit for review with complete documentation and supporting materials
* Track the status of every submission through clear, defined lifecycle stages
* Receive structured feedback or approvals with full audit trails
* Initiate repayments and manage post-transaction obligations

### For Market Makers or Facility Agents

* Review submissions with all relevant data in one place
* Structure deals with configurable parameters, waterfall calculations, and fee structures
* Approve, reject, or request changes with documented reasoning
* E-sign documents individually per participant using Adobe Sign or ZohoSign
* Run recurring calculations and manage ongoing deal operations

### For Investors or Lenders

* Browse opportunities and review detailed deal information
* Commit to deals and approve master commitments with legally binding e-signatures
* Transfer funds and confirm settlement with blockchain-recorded transactions
* Receive repayments and manage receivable positions
* Access complete settlement and repayment audit trails

### For Servicers, Paying Agents, and Rating Agencies

* Upload data files and manage ongoing administration
* Manage payment distributions across participants
* Access read-only views for review, analysis, and reporting

### For Administrators

* Manage organizations, users, and role assignments
* Support delegation workflows where facility agents can delegate tasks to admin
* Use impersonation ("view as") for read-only support operations
* Configure platform settings and manage system operations

## Key Principles to Understand

### User Roles

The platform defines the following roles, each with specific capabilities and responsibilities:

| Role               | Context                    | Primary Responsibility                                                         |
| ------------------ | -------------------------- | ------------------------------------------------------------------------------ |
| **Issuer**         | Securitization, Asset Sale | Create and manage assets, pools, and deals; submit for review                  |
| **Market Maker**   | Securitization             | Structure deals, review submissions, run calculations, facilitate transactions |
| **Investor**       | Securitization, Asset Sale | Review opportunities, commit to deals, confirm settlements, receive repayments |
| **Servicer**       | Securitization             | Ongoing administration, data uploads                                           |
| **Paying Agent**   | Securitization             | Manage payment distributions                                                   |
| **Rating Agency**  | Securitization             | Review and analyze (read-only access)                                          |
| **Borrower**       | Credit Facilities          | Submit term sheets, create funding requests, map loans                         |
| **Facility Agent** | Credit Facilities          | Configure facilities, review requests, approve notices, e-sign per lender      |
| **Lender**         | Credit Facilities          | Approve commitments, transfer funds, confirm settlement                        |
| **Admin**          | All                        | Platform administration, user management, delegation support                   |

### Authentication and Security

Intain Markets implements enterprise-grade security:

* **Microsoft Entra SSO** — Single sign-on through Microsoft identity platform for enterprise login
* **Multi-Factor Authentication (MFA)** — Required for sensitive actions
* **Role-Based Access Control (RBAC)** — Fine-grained permissions based on role and context
* **Rate Limiting** — API rate limiting to prevent abuse
* **Session Management** — Configurable session expiry and concurrent session controls
* **Input Validation** — All inputs validated using schema validation (Zod) to prevent invalid data
* **Security Headers** — Industry-standard security headers via Helmet.js
* **Encryption** — Sensitive data encrypted at rest and in transit

### Analytics and Reporting

The platform provides comprehensive analytics and reporting capabilities:

* **Portfolio Analytics** — Dashboard views of pool performance, loan metrics, and risk indicators
* **IDA Dashboard** — The Intain Digital Analyst dashboard for advanced analytics
* **Credit Facility Analytics** — Facility utilization, commitment tracking, and funding metrics
* **Asset Sale Analytics** — Deal performance, settlement tracking, and repayment metrics
* **ESMA Reporting** — Automated generation of Annex 2, 12, and 14 reports for European regulatory compliance in Excel, XML, and CSV formats
* **Document Management** — Centralized document storage with blockchain hash verification

### Complete Traceability

Every action on the platform is recorded with full traceability:

* **Audit Module** — Every action recorded with user identity and timestamp
* **Status History** — Full change tracking for all items showing every status transition
* **Blockchain Records** — Settlement, token transfers, and NFT burns recorded immutably on-chain
* **E-Signature Trails** — Complete signing records with provider details, timestamps, and stored signed documents

## Getting Started

1. **Login** — Access the platform via Microsoft Entra SSO or direct login, then select your role from the available options
2. **Dashboard** — View items relevant to your role across pools, credit facilities, asset sales, and participation agreements
3. **Actions** — Perform actions based on your role and the current status of each item — the platform shows only the actions available to you
4. **Track Progress** — Monitor the lifecycle of every item through its defined status stages with complete visibility

For detailed information on specific features, roles, workflows, and statuses, refer to the relevant documentation sections throughout this guide.
