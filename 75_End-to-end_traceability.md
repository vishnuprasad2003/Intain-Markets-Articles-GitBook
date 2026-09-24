---
title: End-to-End Traceability
description: >-
  How Intain Markets records every action, decision, and change — audit log, status history, and blockchain records
---

# End-to-End Traceability

Every meaningful action is recorded automatically: creates, status changes, approvals, rejections, document uploads, signatures, token transfers, and settlement confirmations. You cannot turn this off, and existing records cannot be edited.

## Activity Audit

**Sidebar → Activity Audit** — all events in one place.

| Field | What it shows |
|---|---|
| Reference | Unique event ID |
| When | Date and time (UTC) |
| Who | Person, role, and organisation |
| What happened | Plain-language description |
| Result | Succeeded, failed, denied, or pending |
| Which item | Pool, deal, term sheet, notice, etc. |

**Search and filter** by summary text, item reference, or module. **Export** to XLSX or CSV (up to 50,000 events per download). Click **View** on an event → **Go to Entity** to open the related item.

Non-admin users see their own organisation only. Admins see events across organisations.

## Status History on Each Item

Open any pool, term sheet, facility, funding request, or deal to see its full status trail — who changed each status, when, the previous value, the new value, and any comment.

## Documents

Document uploads record who uploaded the file and when. Earlier versions stay in the history alongside the current one.

## Signatures

Adobe Sign and ZohoSign evidence stays with the term sheet, commitment, or notice. Funding notice signatures are tracked per lender so you can see which lenders have a signed notice and which are still pending.

## Blockchain Records

Minting NFTs, transferring tokens, settlement, and repayment are also written to the blockchain. Each produces a transaction reference stored in the activity log alongside the platform event. This reference can be verified independently on a blockchain explorer.

## Key Notes

- Recording is automatic — no setting to enable
- Records are kept permanently; nothing expires
- Admin view-as sessions are labeled with both the admin and the viewed user
- The item's history, activity log, document history, signature record, and blockchain reference all describe the same event from different vantage points

→ See [Who Changed What and When](76_Who_changed_what_and_when.md) for Activity Audit usage.
→ See [Controls and Accountability](79_Controls_and_accountability.md) for how controls work.
