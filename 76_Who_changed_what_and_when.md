---
title: Who Changed What and When
description: Reference guide to the platform's audit and change-tracking capabilities — what information is recorded, how to access it, how to query the centralized audit log, and what the audit export contains
---

# Who Changed What and When

## Overview

Intain Markets records who did something, what they changed, when they did it, and the result. You can see that in two places. Each pool, term sheet, facility, funding request, funding notice, and deal has its own history. **Activity Audit** in the sidebar brings those events together so you can search, filter, and export them.

This guide describes what is stored and how to find an event on screen.

## Reference Details

### What is recorded on every action

| What you see | What it contains | Example |
|---|---|---|
| **Who** | The person, their email, their role, and their organization | jane.lee@lender.com, Lender, ABC Capital |
| **What** | The kind of action | Created, updated, approved, rejected, signed, or submitted |
| **Which item** | The record that was affected | A facility, a term sheet, a pool, or a deal, with its reference |
| **When** | The date and time, in UTC | 09/15/2026 - 14:23 UTC |
| **Result** | Whether it succeeded, failed, or was denied | Succeeded, failed, or denied |
| **Summary** | A sentence you can read | Term sheet approved by the facility agent |
| **Extra detail** | Comments, the reason, the old and new status, or a transaction reference when the step was on the blockchain | Previous status Draft, new status In review |

The activity log also keeps enough context to tie related steps from the same action together. You do not need to look up a request id. Open the event and read the summary, the person, and the item.

### Status history on the item

Every status change on an item records:

- **Who** changed it, by name and organization
- **When** it changed
- **The previous status**
- **The new status**
- **A comment or reason**, when one was entered

**Pools.** Created → Preview → Mandate Pending → Under Review → Deal. The history shows who created the pool, who shared it, and who accepted or declined the mandate.

**Term sheets.** Draft → Signed → In review → Accepted, Rejected, or Changes Requested. The history shows who signed, who submitted, and who approved, rejected, or asked for changes.

**Facilities.** Draft → Pending → Active. The history shows when the facility agent sent it to lenders and when a lender approved it.

**Funding requests.** Draft → In review → Approved, Rejected, or Changes Requested. The history shows when the borrower submitted it and how the facility agent responded.

**Funding notices.** Pending Token Generated, then approved by the facility agent, then signed for each lender. The history shows the facility agent’s approval and each lender signature.

**Asset Sale deals.** Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed. Each change names the person who made it.

### Other actions on the item

Status history is not the only list. The item also records actions such as:

- **Pools:** creating, sharing, sending for a mandate, accepting or declining the mandate, mapping loans, removing or putting back a loan, and feedback
- **Term sheets:** creating, editing, uploading documents, signing, submitting, approving, rejecting, and each round of requested changes
- **Facilities:** creation from an accepted term sheet, setup, adding lenders, and each lender’s signed approval
- **Funding requests:** creating, editing, uploading documents, submitting, approving, rejecting, and requested changes
- **Funding notices:** creation from an approved request, the facility agent’s approval, the facility agent’s signature for each lender, and each lender’s confirmation that funds were sent

### Document history

Uploaded files keep:

- **Who** uploaded the file
- **When** it was uploaded
- **A check** that the stored file is the one that was uploaded
- **Earlier versions**, which stay in the history

Files tracked this way include collateral profiles, financial statements, KYC documents, collateral data, funding sheets, collateral addendums, and other supporting documents.

### Activity Audit

Open **Activity Audit** in the sidebar. The screen is titled Audit & Activity. It has two tabs, **Activities** and **Audit**.

**How to find an event**

1. Choose **Activities** for a short summary of what happened, or **Audit** for the action and remarks.
2. Use **Module** to limit the list, for example to loans or pools. Choose **All** to clear that filter.
3. Search by words in the summary or by the item’s reference.
4. Read the row. Activities show the summary, the item, the module, the user, the time, and the result. Audit rows show the action, the item, the module, the user, the time, and remarks.
5. Choose **View** on an activity to open the detail. **Go to Entity** takes you to the related item.

You can sort the list and move through it page by page. Filter choices reflect values that exist in the activity you can see, such as the modules and people in your results.

**What an export contains**

Use **Export** and choose a spreadsheet (XLSX) or CSV. The file includes:

| Column | What it is |
|---|---|
| When | Date and time of the event |
| Event reference | The id of that activity line |
| What happened | The type of event |
| Category | The kind of activity, such as a data change or a signature |
| Action | Created, approved, rejected, and similar |
| Result | Succeeded, failed, denied, or pending |
| Email | The person who did it |
| Role | Their role at the time |
| Organization | Their organization |
| Item type | Pool, deal, term sheet, and similar |
| Item reference | Which record |
| Summary | A sentence describing the event |

One download includes up to **50,000** events. The spreadsheet keeps the header row in place while you scroll.

### How items connect

You can follow a chain without leaving the records:

| Starting point | Leads to |
|---|---|
| Accepted term sheet | The facility created from it |
| Facility | The funding requests made against it |
| Approved funding request | The funding notice created from it |
| Pool | The loans mapped to it |
| Asset Sale deal | The commitments investors made |

Open the later item to see the reference of the one that created it. That is how you walk from a term sheet to the facility, the draw, and the notice.

## Important Notes

**History stays.** Recorded changes are not deleted or edited afterward.

**A person is named.** Each change stores the email, role, and organization, not only a generic “user.”

**Your organization only.** If you are not an admin, Activity Audit shows your organization’s events. Admins see a wider set.

**View-as is labeled.** When an admin views the platform as another user, the activity log shows both the admin and the user they were viewing. The session is read-only.

**Times are in UTC.** A timestamp on screen is a UTC time, so teams in different places are looking at the same clock.

**Nothing expires the log.** Activity records are kept. They are not removed on a timer.
