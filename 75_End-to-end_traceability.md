---
title: End-to-End Traceability
description: >-
  How Intain Markets provides complete traceability for every action, decision,
  and change — from centralized audit logging and status history to blockchain
  records and e-signature evidence
---

# End-to-End Traceability

## Overview

Intain Markets keeps a record of meaningful actions: creating an item, changing a status, approving or rejecting, uploading a document, signing, transferring tokens, and confirming settlement. Each record says who did it, what they did, when it happened, and whether it succeeded.

That record is not optional. It is written as you work. You do not turn it on, and you cannot edit it later. The same history is available on the item itself and in the activity log for your organization.

## How the Platform Is Designed

### The activity log

Open **Activity Audit** from the left sidebar. It lists activity from across the platform in one place. Every event shows:

| What you see      | What it tells you                                                           |
| ----------------- | --------------------------------------------------------------------------- |
| **Reference**     | A unique id for that event, so you can find it again                        |
| **When**          | The date and time of the action                                             |
| **Who**           | The person, their role, and their organization                              |
| **What happened** | A short description written for people, such as a term sheet being approved |
| **Result**        | Succeeded, failed, denied, or still pending                                 |
| **Which item**    | The pool, deal, term sheet, notice, or other record the action was about    |

The log covers sign-in, permission checks, creates and updates, approvals and rejections, document access, blockchain steps, signatures, and platform jobs. You do not need to know internal category names. Use the description, the person, the item, and the result.

On the activity screen you can:

* Search by the summary or the item’s reference
* Filter by module, such as loans or pools
* Sort the list
* Move through the list page by page
* Export the current results to a spreadsheet or a CSV file
* Open an event and go to the related item

A single export is limited to 50,000 events so the file stays usable.

People who are not admins see only their own organization’s events. Admins can see activity across organizations. You cannot switch that scope yourself.

### History on the item

Each pool, term sheet, facility, funding request, funding notice, and deal also keeps its own history. Open the item to see how its status changed and what else was done to it.

**Status history** records each change of status: who changed it, when, the previous status, the new status, and any comment.

Typical paths:

* Pools: Created → Preview → Mandate Pending → Under Review → Deal
* Term sheets: Draft → Signed → In review → Accepted, Rejected, or Changes Requested
* Facilities: Draft → Pending → Active
* Funding requests: Draft → In review → Approved, Rejected, or Changes Requested
* Funding notices: Pending Token Generated → approved by the facility agent → signed for each lender
* Asset Sale deals: Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed

**Action history** records work that is not only a status change: edits, sharing, document uploads, signatures, loan mapping, and similar steps. Each line has the person, the time, and what they did.

### Documents

When someone uploads a file, the platform keeps who uploaded it and when. Earlier versions stay in the history. They are not replaced without a trace. You can use that history to see which file a reviewer actually had.

### Signatures

Adobe Sign and ZohoSign record that a person signed, and when. That evidence stays with the term sheet, facility, or notice. On a funding notice, the facility agent’s signature is tracked separately for each lender, so you can see which lenders have a signed notice and which are still waiting.

### Blockchain records

Minting a loan NFT, transferring tokens, settling, and recording repayment are also written to the blockchain. Each of those steps has a transaction reference. The activity log stores that reference next to the platform event, so you can connect what you see on screen with the blockchain record. The blockchain copy cannot be edited from inside Intain Markets.

## What This Enables for Users

### Rebuild what happened

For a pool, term sheet, funding request, or deal, you can follow who created it, what was edited, which statuses it passed through, who approved or rejected it, which documents were uploaded, who signed, and which blockchain steps completed. Start on the item. Use Activity Audit when you need a wider list than one item.

### See activity across modules

Activity Audit is a single feed instead of opening every deal and facility. Search or filter when you are looking for one event: a person’s name, an item reference, a module, or words from the summary. Export when you need the same list outside the platform. The export includes when it happened, the event reference, what happened, the result, the person’s email, role, and organization, the item, and the summary.

### View-as stays visible

An administrator can open the platform as another user to help with support. That session is read-only. The administrator can see what that user sees and cannot create, edit, approve, or submit. The activity log records both the administrator and the user they were viewing.

## Key Principles to Understand

### Recording is automatic

You do not enable an audit setting. Actions are recorded as part of normal work. The history cannot be switched off, and an existing line cannot be rewritten.

### Records are kept

Activity events are kept for the life of the data. They are not expired or deleted on a schedule.

### More than one record of the same event

The item’s own history, the activity log, the document history, the signature record, and the blockchain transaction reference describe the same work from different places. If you need to confirm a payment or a token transfer, the transaction reference is the record that sits outside the platform.

### You see your own organization

Unless you are an admin, the activity log is limited to your organization. Another organization’s users, approvals, and documents do not appear in your feed.
