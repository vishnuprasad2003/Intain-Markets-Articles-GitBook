---
title: End-to-End Traceability
description: How Intain Markets provides complete traceability for every action, decision, and change — from centralized audit logging and status history to blockchain records and e-signature evidence
---

# End-to-End Traceability

## Overview

Intain Markets is designed so that every meaningful action — creating an item, changing a status, approving or rejecting a request, uploading a document, signing an agreement, transferring tokens, or confirming settlement — is recorded with full attribution. The platform provides multiple, overlapping layers of traceability: per-item status and action histories, a centralized audit module that spans all modules, document storage with hash verification, e-signature evidence, and blockchain records for on-chain operations.

This is not a feature that was added after the fact. Traceability is built into the platform's architecture. Every module writes to the same centralized audit trail, every status change is captured with who made it and when, and blockchain operations produce immutable records that exist independently of the platform's database.

## How the Platform Is Designed

### Centralized Audit Module

The platform includes a centralized audit module that consolidates activity from every module into a single, queryable log. All modules write to this log through a single function — `audit.helper.record()` — which ensures that every event follows the same structure and meets the same quality standards.

**What every audit event contains:**

| Field | Description |
|---|---|
| **Audit ID** | A unique identifier for the event (format: `AUD-<uuid>`) |
| **Occurred At** | Timestamp of when the action happened |
| **Actor** | Who performed the action — user ID, email, role, and organization ID |
| **Event Type** | What kind of action occurred (e.g., `credit_facility.term_sheet.created`, `whole_loan_sale.deal.approved`) |
| **Category** | The concern the event belongs to — Authentication, Authorization, Data Mutation, Data Access, Chain, Integration, or System |
| **Outcome** | Whether the action succeeded, failed, was denied, or is pending |
| **Resource** | What the action was performed on — resource type and resource ID |
| **Summary** | A human-readable sentence describing what happened, written for the activity feed |
| **Request Context** | The HTTP request that triggered the action — request ID, IP address, method, path |
| **Metadata** | Additional details specific to the event — change details, blockchain transaction hashes, related entity IDs |

**Resource types tracked across the platform:**

The audit module defines a fixed set of resource types that cover every module: `auth`, `mfa`, `user`, `organization`, `pool`, `batch`, `loan`, `dataroom`, `delegation`, `settlement`, `securitization`, `whole_loan_sale`, `credit_facility`, `adobesign`, `zohosign`, `notification`, `feedback`, `wallet_onboarding`, `xft`, `nft`, `blob_files`, `ipfs_files`, `receivables_rnft`, `blockchain`, `deal`, and more. Every audit event must specify one of these types, ensuring that the log is consistently categorized and filterable.

**Event categories provide a second dimension of organization:**

- **Authentication** — Sign-in attempts, SSO logins, token refreshes, session management
- **Authorization** — Access grants, role checks, permission denials
- **Data Mutation** — Creations, updates, status changes, approvals, rejections
- **Data Access** — Reads, exports, downloads
- **Chain** — Blockchain operations — NFT minting, token transfers, settlement events
- **Integration** — E-signature events, external system interactions
- **System** — Platform-level operations, migrations, background jobs

### Per-Item Status and Action History

In addition to the centralized audit log, each item in the platform maintains its own status history and action history directly on the item record:

**Status history** records every status transition with attribution:
- Pools: Created → Preview → Mandate Pending → Under Review → Deal
- Term Sheets: Draft → BorrowerSigned → FAReview → Accepted / Rejected / CHANGES_REQUESTED
- Master Commitments: Draft → PendingLenderApproval → ACTIVE
- Funding Requests: DRAFT → FAReview → APPROVED / REJECTED / CHANGES_REQUESTED
- Funding Notices: Pending Token Generated → FA Approved → E-signed for each lender
- Asset Sale Deals: Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed

Each status history entry records who changed the status, when, the previous status, the new status, and any comments or reasons.

**Action history** records every operation performed on an item — creation, editing, sharing, submission, approval, rejection, document uploads, e-signature events, loan mapping, and more. Each entry includes the actor, timestamp, action type, and relevant details.

### Document Traceability

Documents uploaded to the platform are stored with IPFS hash verification. Each upload generates a content-addressable hash that serves as proof of the document's contents at the time of upload. Document history arrays maintain the complete upload history with timestamps, uploader attribution, and IPFS hashes, so you can trace every version of every document back to who uploaded it and when.

### E-Signature Evidence

E-signatures (via Adobe Sign or ZohoSign) create formal, timestamped records of consent. The platform tracks the e-signature lifecycle — envelope creation, signing events, completion — and stores this evidence alongside the item being signed. For credit facility workflows, the facility agent's e-signature for each lender on a funding notice is tracked individually, providing per-lender evidence of authorization.

### Blockchain Records

Operations that involve the blockchain — NFT minting, token transfers, settlement, repayment — produce on-chain records with transaction hashes. These records are immutable and exist independently of the platform's database. The audit module captures blockchain transaction hashes (`metadata.chain.txHash`) alongside the platform event, creating a link between the platform's audit trail and the blockchain's permanent record.

Settlement events in the asset sale workflow record on-chain delivery and payment confirmations, each with its own transaction hash. Repayment events are similarly recorded on-chain, ensuring that the complete financial lifecycle of a deal has permanent, tamper-proof evidence.

## What This Enables for Users

### Complete Reconstruction of Any Transaction

For any item in the system — a pool, a term sheet, a funding request, a deal — you can reconstruct the complete history: who created it, every edit made, every status change, every approval or rejection, every document uploaded, every signature completed, and every blockchain transaction. This history is available on the item's detail page and through the centralized audit log.

### Cross-Module Activity View

The centralized audit module provides a unified view across all modules. Rather than checking individual items, you can access the Activity Audit from the sidebar to see a chronological feed of all actions taken across the platform. This feed supports:

- **Filtering** by event type, category, outcome, actor, resource type, organization, and more
- **Sorting** by time, event type, category, or outcome
- **Cursor-based pagination** for efficient browsing through large activity logs
- **Distinct-value lookups** for building filter dropdowns dynamically

### Compliance Exports

The audit module supports exporting the activity log to CSV or XLSX format for compliance and reporting needs. Exports follow a fixed column template that includes: Occurred At, Audit ID, Event Type, Category, Action, Outcome, Actor Email, Actor Role, Actor Org ID, Resource Type, Resource ID, and Summary. Exports are capped at 50,000 rows per download to maintain performance, and the exported file is generated as a streaming download.

### Impersonation Transparency

When an administrator uses the view-as (impersonation) feature for support or troubleshooting, the audit trail records both the administrator's identity and the impersonated user's identity. View-as mode is strictly read-only — no mutations are allowed — and every action taken during an impersonation session is tagged with the `impersonatedBy` field, ensuring complete transparency.

## Key Principles to Understand

### Traceability Is Automatic

You do not need to enable logging or opt into audit tracking. Every action is recorded automatically as part of the platform's normal operation. The audit trail cannot be turned off, and it cannot be modified after the fact.

### Audit Records Are Retained Indefinitely

Audit events are stored permanently. There is no expiration or automatic deletion of audit records. The platform maintains the complete history of every action for the lifetime of the data.

### Multiple Layers Provide Redundancy

The combination of per-item history (embedded in the item record), centralized audit log (queryable across modules), document hashes (content-addressable proof), e-signature records (legally binding evidence), and blockchain records (immutable on-chain proof) means that traceability does not depend on any single system. Even if one layer were compromised, the others would provide independent evidence.

### Non-Admin Users Are Auto-Scoped

When non-Admin users query the audit log, they automatically see only events related to their own organization. This scoping is applied server-side and cannot be bypassed, ensuring that organizations cannot see each other's activity while still having full visibility into their own.
