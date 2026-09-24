---
title: Status and Approval Philosophy
description: >-
  Why Intain Markets uses status-driven workflows and approval gates to ensure
  trust, accountability, and structured progression across every transaction
---

# Status & Approval Philosophy

## Overview

Every transaction on Intain Markets moves through defined stages. A qualified person must authorize each move to the next stage. That matches how institutional deals work: preparation, review, commitment, execution, and settlement, with a sign-off at each boundary.

A **status** shows where an item is and which actions are available. An **approval** is the gate between stages. Together they keep the workflow predictable and make every decision traceable.

## How the Platform Is Designed

### Status-Driven Workflows

Pools, loans, term sheets, master commitments, funding requests, and asset sale deals each have one status. That status decides what can happen next.

* **Actions follow the status.** Buttons turn on or off with the status. A term sheet in **Draft** can be edited. In **Under Review**, editing stays locked until the facility agent decides. A deal in **Active** can start repayment. A deal in **Settlement In Progress** cannot.
* **Stages stay in order.** A pool moves from **Created** to **Preview** to **Under Review** to **Deal**. It cannot jump from Created to Deal. An asset sale deal moves through Draft, Pending Review, Published, Commit, Invest, Settlement In Progress, Settled, and Active in that order. Each change is recorded.
* **Moving backward takes a decision.** A term sheet returns from **Under Review** to **Changes Requested** only when an authorized person asks for changes. It does not slip backward on its own.
* **Some statuses are final.** **Cancelled**, **Rejected**, and **Closed** end the workflow. The item cannot re-enter it. If you need to try again, create a new item.

### The Maker-Checker Principle

The person who creates an item is not the person who approves it.

* **Borrowers** create term sheets. **Facility Agents** review and approve them.
* **Issuers** create asset sale deals. **Underwriters** review and approve them.
* **Borrowers** submit funding requests. **Facility Agents** review and approve them.
* **Issuers** start repayment. **Investors** confirm receipt.
* **Facility Agents** set up master commitments. **Lenders** approve and e-sign them.

No single party can move a transaction forward alone.

### Role-Based Action Controls

The platform checks the status and your role.

* Only **Facility Agents** can approve or reject term sheets and funding requests.
* Only **Lenders** can approve master commitments.
* Only **Market Makers** can accept or reject pool mandates.
* Only **Issuers** can publish deals, start repayment, and upload loan tapes.
* Only **Investors** can confirm repayment receipt and burn receivables NFTs.

If you do not hold the role, the action is not shown. A borrower looking at a term sheet in **Under Review** does not see approval buttons. The facility agent does.

### Change Requests vs. Rejection

* A **change request** sends the item back to the submitter. They can edit it and send it again. The workflow continues.
* A **rejection** is final. The item cannot be edited or sent again. To try again, create a new item.

| Aspect             | Change Request       | Rejection         |
| ------------------ | -------------------- | ----------------- |
| **Item editable?** | Yes                  | No                |
| **Can resubmit?**  | Yes                  | No                |
| **Workflow**       | Returns for revision | Stops             |
| **Next step**      | Edit and resubmit    | Create a new item |

## What This Enables for Users

### Predictability

A deal in **Published** has already been created, reviewed, and approved. The next stage is investor commitment. You can tell what has happened and what comes next from the status.

### Accountability

Each status change records the time, the person, and any notes. If a term sheet is rejected, you can see who rejected it, when, and why. The same record exists for an approved funding request.

### Safety and Error Prevention

* An issuer cannot publish a deal until loans are assigned and the required terms are set.
* A facility agent approves a term sheet only by making an explicit decision.
* An investor cannot burn a receivables NFT until repayment receipt is confirmed.

### Trust Between Parties

Investors see asset sale deals after an underwriter has reviewed them. Lenders see facility terms after a facility agent has reviewed them. Issuers know an approved deal continues in a set order.

## Key Principles to Understand

**Every item has one status.** That status answers where the item stands right now.

**Status controls actions.** Buttons, edits, and allowed moves all follow the current status.

**Approvals are active decisions.** Someone with the right role must choose. Nothing is approved automatically because time passed.

**The history stays on the record.** Status changes, approvals, and actions stay available to review.

**Duties stay separate.** The platform does not let the same person both create and approve the same item.

**The usual direction is forward.** A change request is the exception, and it requires an explicit decision.

A disabled button is the workflow protecting the parties. It is not a broken control.
