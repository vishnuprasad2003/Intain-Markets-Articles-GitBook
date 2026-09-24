---
title: Who Changed What and When
description: >-
  How to find audit records — what is logged, where to find it, and what the Activity Audit export contains
---

# Who Changed What and When

## What Is Recorded on Every Action

| Field | What it contains |
|---|---|
| **Who** | Person's name, email, role, and organisation |
| **What** | Action type (created, approved, rejected, signed, submitted) |
| **Which item** | Record affected (pool, term sheet, facility, deal) with its reference |
| **When** | Date and time in UTC |
| **Result** | Succeeded, failed, or denied |
| **Detail** | Comments, old/new status, or blockchain transaction reference |

## Status History on Each Item

Every status change records who changed it, when, the previous status, the new status, and any comment. Open an item and view its history to trace the full lifecycle.

| Item | Status trail |
|---|---|
| Pool | Created → Preview → Mandate Pending → Under Review → Deal |
| Term sheet | Draft → Signed → In review → Accepted / Rejected / Changes Requested |
| Facility | Draft → Pending → Active |
| Funding request | Draft → In review → Approved / Rejected / Changes Requested |
| Asset Sale deal | Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Closed |

## Activity Audit

**Sidebar → Activity Audit** — search, filter, and export all events across your organisation.

**How to find an event:**
1. Choose **Activities** tab (readable summaries) or **Audit** tab (action + remarks)
2. Use **Module** filter to narrow by loans, pools, facilities, etc.
3. Search by event summary text or item reference
4. Click **View** on a row for full detail; **Go to Entity** opens the related item

**Connected items** — open a later item to see the reference of the one that created it:

| Start from | Leads to |
|---|---|
| Accepted term sheet | The facility created from it |
| Approved funding request | The funding notice created from it |
| Pool | The loans mapped to it |

## Activity Audit Export

Click **Export** → choose XLSX or CSV. The file includes: When, Event reference, What happened, Category, Action, Result, Email, Role, Organisation, Item type, Item reference, Summary. Up to 50,000 events per download.

## Key Notes

- Activity records are kept permanently — nothing expires
- Timestamps are in UTC
- Non-admin users see their organisation's events only; admins see a wider set
- Admin view-as sessions are labeled with both the admin and the viewed user
- Document uploads record who uploaded the file, when, and which version

→ See [End-to-End Traceability](75_End-to-end_traceability.md) for blockchain audit details.
→ See [Controls and Accountability](79_Controls_and_accountability.md) for how controls work.
