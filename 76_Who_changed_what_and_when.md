---
title: Who Changed What and When
description: >-
  Reference guide to the platform's audit and change-tracking capabilities —
  what information is recorded, how to access it, how to query the centralized
  audit log, and what the audit export contains
---

# Who Changed What and When

## Overview

Intain Markets records every action with details about who performed it, what was affected, and when it happened. This tracking operates at two levels: per-item history embedded in each pool, term sheet, master commitment, funding request, funding notice, and deal; and a centralized audit module that consolidates activity from every module into a single, searchable log with export capabilities.

This reference guide explains what information is recorded, where to find it, and how to use the audit module.

## Reference Details

### What Gets Recorded on Every Action

Every action in the platform captures the following information:

| Field               | What It Contains                                                                      | Example                                                             |
| ------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Actor**           | User ID, email address, role, and organization ID                                     | `john.doe@lender.com`, Role: Lender, Org: ABC Capital               |
| **Action**          | What type of action was performed                                                     | `created`, `updated`, `approved`, `rejected`, `signed`, `submitted` |
| **Resource**        | What the action was performed on — resource type and ID                               | Type: `credit_facility`, ID: `MC-09152026-a3f2`                     |
| **Timestamp**       | When the action occurred (UTC)                                                        | `2026-09-15T14:23:07.000Z`                                          |
| **Outcome**         | Whether the action succeeded, failed, or was denied                                   | `SUCCESS`, `FAILURE`, `DENIED`                                      |
| **Summary**         | A human-readable sentence describing what happened                                    | `Term sheet "TS-09102026-b7c1" approved by facility agent`          |
| **Metadata**        | Additional context — change details, comments, reasons, blockchain transaction hashes | Previous status, new status, rejection reason, `txHash`             |
| **Request Context** | The HTTP request that triggered the action — request ID, IP address, method, path     | `POST /cf/:id/term-sheets/:id/approve`                              |

### Per-Item Status History

Each item type maintains its own status history directly on the record. Every status transition records:

* **Who changed the status** (user name and organization)
* **When the change occurred** (timestamp)
* **Previous status** (what it was before)
* **New status** (what it changed to)
* **Comments or reason** (why the change was made, if provided)

**Pool Status History:** Tracks progression through: Created → Preview → Mandate Pending → Under Review → Deal. Records who created the pool, who shared it, who accepted or rejected the mandate, and who moved it through each stage.

**Term Sheet Status History:** Tracks progression through: Draft → BorrowerSigned → FAReview → Accepted / Rejected / CHANGES\_REQUESTED. Records who signed the term sheet, who submitted it, and who approved, rejected, or requested changes.

**Master Commitment Status History:** Tracks progression through: Draft → PendingLenderApproval → ACTIVE. Records when the facility agent submitted for approval and when each lender approved.

**Funding Request Status History:** Tracks progression through: DRAFT → FAReview → APPROVED / REJECTED / CHANGES\_REQUESTED. Records when the borrower submitted the request and how the facility agent responded.

**Funding Notice Status History:** Tracks progression through: Pending Token Generated → FA Approved → E-signed (per lender). Records the facility agent's approval and each individual lender e-signature event.

**Asset Sale Deal Status History:** Tracks the full lifecycle: Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed. Records every status transition with attribution.

### Per-Item Action History

In addition to status history, items maintain an action history that records operations beyond status changes:

* **Pool actions**: Creation, sharing, mandate submission, mandate acceptance/rejection, loan mapping, loan removal, loan reinstatement, feedback submission
* **Term sheet actions**: Creation, editing, document uploads, signing, submission, approval, rejection, change requests, change request responses
* **Master commitment actions**: Auto-creation from term sheet, facility configuration, lender group additions, lender approvals with e-signature
* **Funding request actions**: Creation, editing, document uploads, submission, approval, rejection, change requests
* **Funding notice actions**: Auto-generation from approved funding request, FA approval, FA e-sign for each lender, lender fund transfer confirmations

### Document History

Documents uploaded to the platform are tracked with:

* **Uploader** — who uploaded the document
* **Timestamp** — when it was uploaded
* **IPFS hash** — content-addressable hash for verification
* **History arrays** — previous versions are preserved, not overwritten

Document types tracked include: collateral profiles, financial statements, KYC documents, collateral data, funding sheets, collateral addendums, and supporting documents.

### The Centralized Audit Module

The Activity Audit module consolidates all of the above into a single, cross-module activity log. It is accessible via the **Activity Audit** item in the sidebar.

**How to query the audit log:**

The audit log supports filtering on the following fields:

* `occurredAt` — when the event happened (date range)
* `event.type` — the specific event type (e.g., `credit_facility.term_sheet.created`)
* `event.category` — the broad category (Authentication, Authorization, Data Mutation, Data Access, Chain, Integration, System)
* `event.action` — the action performed
* `event.outcome` — SUCCESS, FAILURE, DENIED, or PENDING
* `actor.userId`, `actor.email`, `actor.role`, `actor.orgId` — who performed the action
* `resource.type`, `resource.id` — what the action was performed on
* `metadata.chain.txHash` — blockchain transaction hash (for on-chain events)
* `metadata.issuerOrgId`, `metadata.assetClass` — additional context filters
* `request.correlationId` — link related events from the same request

The log supports sorting by time, event type, category, outcome, actor, or resource type. Results are cursor-paginated (up to 200 events per page) for efficient browsing of large activity histories.

**Distinct-value lookups:**

For building filter dropdowns, the audit module provides a distinct-values endpoint that returns unique values for any filterable column. This powers the filter chips in the UI — for example, showing all unique event types or all unique actor emails present in the current data.

**What the audit export contains:**

The audit module supports exporting to CSV or XLSX format. Each export contains the following columns:

| Column        | Description                                         |
| ------------- | --------------------------------------------------- |
| Occurred At   | Timestamp of the event                              |
| Audit Id      | Unique event identifier (AUD-)                      |
| Event Type    | Specific event type                                 |
| Category      | Event category                                      |
| Action        | Action performed                                    |
| Outcome       | SUCCESS, FAILURE, DENIED, or PENDING                |
| Actor Email   | Email of the person who performed the action        |
| Actor Role    | Role of the person who performed the action         |
| Actor Org Id  | Organization of the person who performed the action |
| Resource Type | Type of resource affected                           |
| Resource Id   | Identifier of the resource affected                 |
| Summary       | Human-readable description of what happened         |

Exports are capped at **50,000 rows** per download. XLSX exports include a frozen header row for easy scrolling. CSV exports include a UTF-8 BOM for correct Excel rendering.

### Relationship Tracking

The audit log and item histories also track relationships between items:

| From              | To                | Tracked Via                                  |
| ----------------- | ----------------- | -------------------------------------------- |
| Term Sheet        | Master Commitment | `termSheetId` on the master commitment       |
| Master Commitment | Funding Requests  | `masterCommitmentId` on each funding request |
| Funding Request   | Funding Notice    | `fundingRequestId` on the funding notice     |
| Pool              | Loans             | `poolid` on each loan mapping                |
| Deal              | Commitments       | `dealId` on each commitment                  |

This means you can trace a complete chain from a borrower's original term sheet through to the final funding notice and settlement.

## Important Notes

**Complete history** — All changes are recorded permanently. History cannot be deleted or modified after the fact.

**User attribution** — Every change is attributed to a specific user, with their email, role, and organization recorded.

**Organization scoping** — Non-Admin users automatically see only events related to their own organization. This scoping is applied server-side and cannot be bypassed.

**Impersonation transparency** — When an admin uses view-as mode, actions are tagged with the `impersonatedBy` field, recording both the admin's identity and the target user's identity.

**Timestamps** — All timestamps are recorded in UTC for consistency across time zones.

**Indefinite retention** — Audit records are retained permanently. There is no automatic deletion or expiration of audit data.

**Catalog discovery** — The audit module provides a catalog endpoint that exposes all available categories, resource types, outcomes, filterable fields, sortable fields, and export format options. The UI uses this catalog to build its filter and sort menus dynamically.
