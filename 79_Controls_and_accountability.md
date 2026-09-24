---
title: Controls and Accountability
description: >-
  How Intain Markets enforces controls — role-based access, status-driven
  workflows, approval gates, audit trails, blockchain immutability, MFA, rate
  limiting, and admin impersonation safeguards
---

# Controls & Accountability

## Overview

Intain Markets implements multiple layers of controls and accountability measures throughout the platform. These controls are not optional features that can be turned on or off — they are built into the platform's architecture and operate automatically. Every action is constrained by role-based access, governed by status-driven workflows, protected by approval gates, and recorded in permanent audit trails.

This document explains what those controls are, how they work, and why they exist.

## How the Platform Is Designed

### Role-Based Access Controls

Your role determines what you can see and what actions you can perform. The platform enforces these boundaries at the API level — not just in the UI — so they cannot be bypassed:

| Role                              | What They Can Do                                                                                                                | What They Cannot Do                                                                |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Issuer / Borrower**             | Create pools, upload loans, create term sheets, sign term sheets, submit funding requests                                       | Approve their own term sheets, approve funding requests, accept pool mandates      |
| **Facility Agent / Market Maker** | Approve or reject term sheets, configure master commitments, approve funding requests, accept pool mandates, e-sign for lenders | Create term sheets, create pools, submit funding requests                          |
| **Lender / Investor**             | Review and approve master commitments, review funding notices, confirm settlement, commit to asset sale deals                   | Create facilities, approve funding requests, publish deals                         |
| **Underwriter**                   | Review and approve/reject asset sale deals, manage investor allocation                                                          | Create deals, commit as an investor                                                |
| **Servicer**                      | Upload monthly loan tapes for assigned deals                                                                                    | Create deals, approve anything, access unassigned deals                            |
| **Rating Agency**                 | View shared pools, provide feedback, download data (if permitted)                                                               | Create pools, approve anything, request loan removal                               |
| **Paying Agent**                  | Execute fund transfers (FT transfer)                                                                                            | Create pools, approve term sheets                                                  |
| **Admin**                         | Manage organizations, approve KYC, process delegated LTS and deal modelling, view platform-wide analytics                       | Bypass approval workflows or act on behalf of users without impersonation controls |

The separation between roles follows the **maker-checker** principle: the person who creates or submits an item is never the same person who approves it.

### Status-Based Workflow Controls

Status controls what actions are available at any given moment. Items must progress through statuses in a defined order, and actions are enabled or disabled based on the current status:

**Pools:** Created → Preview → Mandate Pending → Under Review → Deal

* Editing is allowed in Created status; once a pool reaches Deal status, the structure is locked.

**Term Sheets:** Draft → BorrowerSigned → FAReview → Accepted / Rejected / CHANGES\_REQUESTED

* Editing is allowed in Draft; once submitted (BorrowerSigned), the borrower cannot edit until the facility agent responds.

**Master Commitments:** Draft → PendingLenderApproval → ACTIVE

* Configuration and lender additions are allowed in Draft; once submitted for lender approval, structural changes are locked.

**Funding Requests:** DRAFT → FAReview → APPROVED / REJECTED / CHANGES\_REQUESTED

* Editing is allowed in DRAFT; once submitted, the borrower cannot modify the request until the facility agent takes action.

**Funding Notices:** Pending Token Generated → FA Approved → E-signed (per lender)

* Lenders cannot see a funding notice until the facility agent has completed the e-signature for their specific lender entry.

**Asset Sale Deals:** Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed

* Each status transition unlocks the next set of actions and locks the previous ones.

Status progression cannot be skipped. A funding request cannot go from DRAFT directly to APPROVED — it must pass through FAReview. A term sheet cannot go from Draft directly to Accepted — it must pass through BorrowerSigned and FAReview.

### Approval Gates

Approvals are required at specific points before a workflow can advance. These gates ensure that an independent reviewer has evaluated and accepted the work before it creates obligations:

* **Term sheets** require facility agent approval before a master commitment is created
* **Master commitments** require at least one lender's approval (with e-signature) before the facility becomes active
* **Funding requests** require facility agent approval before a funding notice is generated
* **Funding notices** require the facility agent to e-sign for each lender individually before that lender can see the notice
* **Pool mandates** require market maker acceptance before the pool moves to Deal status
* **Asset sale deals** require underwriter approval before investors can commit
* **KYC submissions** require admin approval before users gain full platform access

### Multi-Factor Authentication (MFA) for Sensitive Operations

Beyond role-based access and approval gates, certain high-stakes operations require additional identity verification through MFA:

| Operation                            | Required Role | MFA Action     |
| ------------------------------------ | ------------- | -------------- |
| NFT Minting                          | Issuer        | `NFT_MINT`     |
| NFT Transfer (Asset Sale Settlement) | Issuer        | `NFT_TRANSFER` |
| FT Approval (Token Approval)         | Issuer        | `FT_APPROVE`   |
| FT Transfer (Fund Distribution)      | Paying Agent  | `FT_TRANSFER`  |

The `requireMfaForAction` middleware enforces this: it checks that the user has recently verified their identity via one-time password before the operation can proceed. This means that even if a user's session is compromised, blockchain operations cannot be executed without a fresh OTP verification.

### Data Validation Controls

The platform validates data before accepting it at every submission point:

**Required field validation:**

* Term sheets: requested commitment amount, advance rate, margin, pricing index, fixed rate, maturity date
* Pool fields: pool name, asset class, and required metadata
* Funding requests: draw amount, purpose of funds, funding date

**Required document validation:**

* Term sheets require: collateral profile, financial statements, KYC documents
* Funding requests require: collateral addendum, financial statements, KYC documents
* Missing documents prevent submission — the system will not accept a term sheet or funding request that lacks required documentation

**Business rule validation:**

* Borrowing capacity is validated against facility limits before a funding request can be approved
* Token allocations are calculated automatically based on lender voting percentages and must match the total drawdown amount
* Pool metrics calculate automatically from the mapped loans

Invalid data is rejected with clear error messages explaining what is missing or incorrect.

### Rate Limiting

All API endpoints are protected by tiered rate limiting. Requests are classified into tiers based on the endpoint's sensitivity and cost, and each tier has its own maximum request count and time window. If a user or client exceeds the allowed rate, subsequent requests are temporarily blocked with appropriate error responses.

Rate limiting uses Redis as the backing store. If Redis is unavailable, the rate limiter fails open (requests are allowed through) rather than blocking legitimate traffic — but the unavailability is logged and monitored.

### Admin Impersonation Controls (View-As)

Administrators can view the platform as another user for support and troubleshooting purposes. This capability is carefully controlled:

* **Read-only enforcement**: During an impersonation session, all write operations are blocked. The `requireWriteAccess` middleware intercepts any mutation attempt and returns an error. Administrators in view-as mode can see exactly what the user sees, but they cannot create, edit, approve, or change anything.
* **Audit trail transparency**: Every action during an impersonation session is tagged with `impersonatedBy` in the audit log, recording both the administrator's identity and the target user's identity.
* **No nested impersonation**: An administrator who is already in a view-as session cannot start another view-as session. This prevents impersonation chains.

## What This Enables for Users

### You Cannot Accidentally Bypass Controls

The controls described above operate at the API level, not just in the UI. Even if a UI element were to malfunction and present an action that should not be available, the backend would reject the request based on role, status, or prerequisite checks. This means the platform's integrity does not depend on the UI correctly hiding buttons.

### Every Decision Has an Audit Trail

All actions are tracked through the centralized audit module. Status changes record who changed the status, when, the previous value, and the new value. Approvals record the approver, timestamp, and comments. Rejections record the rejector, timestamp, and reason. Document uploads record the uploader, timestamp, and IPFS hash. This audit trail is permanent and cannot be modified.

### Blockchain Provides Independent Verification

For operations that touch the blockchain — NFT minting, token transfers, settlement, repayment — the on-chain record exists independently of the platform's database. Transaction hashes link platform events to their blockchain counterparts, providing an immutable, externally verifiable record that no single party controls.

## Key Principles to Understand

**Automatic enforcement** — Controls are enforced automatically by the platform. You do not need to enable them, and they cannot be disabled.

**Role-based access** — Your role determines your capabilities. The platform checks your role on every request, not just when you log in.

**Status-based control** — Status governs what actions are available. Status progression follows defined workflows and cannot be skipped.

**Accountability** — All actions are tracked with full attribution. Every change is recorded with who did it, when, and what changed.

**Permanent records** — Audit trails are permanent and cannot be modified or deleted. Blockchain records provide additional immutability.

**Validation before acceptance** — Data is validated before it is accepted. Invalid or incomplete submissions are rejected with clear error messages.

**Prerequisite enforcement** — Steps cannot be skipped. Each action has prerequisites that must be met before it is enabled.

**Defense in depth** — Multiple overlapping controls (roles, status, approval gates, MFA, rate limiting, validation) mean that no single failure can compromise the platform's integrity.
