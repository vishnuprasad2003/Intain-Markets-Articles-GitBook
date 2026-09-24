---
title: Controls and Accountability
description: >-
  How Intain Markets enforces controls — role-based access, status-driven
  workflows, approval gates, audit trails, blockchain immutability, MFA, rate
  limiting, and admin impersonation safeguards
---

# Controls & Accountability

## Overview

Intain Markets limits what each person can do, and it keeps a record of what they did. Those limits are part of normal use. You do not switch them on. Your role, the item’s status, and the approvals still outstanding decide whether an action is available. When you do act, the activity log stores who did it, what changed, and the result.

This article explains those controls and why they are there.

## How the Platform Is Designed

### Role-based access

Your role decides what you can see and which actions you can take. The platform checks the role on the action itself, not only by hiding a button.

| Role                              | What they can do                                                                                                                   | What they cannot do                                                         |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **Issuer / Borrower**             | Create pools, upload loans, create and sign term sheets, submit funding requests                                                   | Approve their own term sheet or funding request, or accept a pool mandate   |
| **Facility Agent / Market Maker** | Approve or reject term sheets, set up facilities, approve funding requests, accept pool mandates, sign funding notices for lenders | Create term sheets, create pools, or submit funding requests                |
| **Lender / Investor**             | Approve a facility, review funding notices, confirm settlement, commit to an Asset Sale deal                                       | Create a facility, approve a funding request, or publish a deal             |
| **Underwriter**                   | Approve or reject an Asset Sale deal, and manage investor allocation                                                               | Create a deal, or commit as an investor                                     |
| **Servicer**                      | Upload monthly loan tapes for assigned deals                                                                                       | Create deals, approve items, or open deals that are not assigned            |
| **Rating Agency**                 | View pools shared with them, leave feedback, and download data when that was allowed                                               | Create pools, approve items, or request loan removal                        |
| **Paying Agent**                  | Move funds when a distribution is ready                                                                                            | Create pools or approve term sheets                                         |
| **Admin**                         | Manage organizations, approve KYC, complete delegated loan-tape work and deal modelling, and view platform-wide analytics          | Skip an approval, or change data while viewing the platform as another user |

The person who prepares an item is not the person who approves it. A borrower submits a term sheet. A facility agent decides it. An issuer publishes a deal. An underwriter approves it before investors commit.

### Status controls the next action

An item moves through statuses in order. Buttons match the status you are in. You cannot skip ahead.

**Pools:** Created → Preview → Mandate Pending → Under Review → Deal. You can edit while the pool is Created. At Deal, the structure is locked.

**Term sheets:** Draft → Signed → In review → Accepted, Rejected, or Changes Requested. You can edit in Draft, and again if changes were requested. After you submit, you wait for the facility agent.

**Facilities:** Draft → Pending → Active. Lender names and setup can change in Draft. After the facility is sent for lender approval, those structural edits stop.

**Funding requests:** Draft → In review → Approved, Rejected, or Changes Requested. You can edit in Draft, and again after changes are requested. You cannot edit while the request is in review.

**Funding notices:** Pending Token Generated, then approved by the facility agent, then signed for each lender. A lender does not see the notice until the facility agent has signed for them.

**Asset Sale deals:** Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed. Each status opens the next actions and closes the earlier ones.

A funding request does not go from Draft straight to Approved. It has to be in review first. A term sheet does not go from Draft straight to Accepted. It has to be signed and then reviewed.

### Approvals that must happen first

* A term sheet needs the facility agent’s approval before a facility is created
* A facility needs at least one lender’s signed approval before it becomes **Active**
* A funding request needs the facility agent’s approval before a funding notice is created
* A funding notice needs the facility agent’s signature for a lender before that lender can see it
* A pool needs the market maker to accept the mandate before it moves to Deal
* An Asset Sale deal needs the underwriter’s approval before investors commit
* A new user’s KYC needs an admin’s approval before they have full access

### A one-time code for sensitive steps

Some actions also ask you to confirm with a one-time code. The platform checks that you have just completed that code before it continues.

| Action                                     | Who          |
| ------------------------------------------ | ------------ |
| Mint NFTs                                  | Issuer       |
| Transfer NFTs during Asset Sale settlement | Issuer       |
| Approve a token transfer                   | Issuer       |
| Move funds in a distribution               | Paying Agent |

A saved sign-in is not enough for these steps. If the code is missing or expired, the action stops until you enter a new one.

### Checks before something is accepted

The platform checks required information before it accepts a submission.

**Required details**

* Term sheets need the commitment amount, advance rate, margin, pricing index or fixed rate, and maturity date
* Pools need a name, an asset class, and the other required details on the form
* Funding requests need the draw amount, the purpose of the funds, and the funding date

**Required documents**

* Term sheets need a collateral profile, financial statements, and KYC documents
* Funding requests need a collateral addendum, financial statements, and KYC documents

If a required document is missing, submission is refused and the message says what is missing.

**Other rules**

* A funding request is checked against the facility’s remaining capacity
* Each lender’s token amount is calculated from their share and must add up to the draw
* Pool figures are calculated from the loans mapped to the pool

If something does not pass, you get an error that says what to correct. The item is not half-saved as if it had been accepted.

### Too many requests

If you or your session send too many requests in a short time, further requests are blocked for a while. Wait and try again. The block is temporary. It is there to protect the platform. It is not a change to your role or to the item’s status.

### Viewing the platform as another user

Administrators can open the platform as another user for support.

* **Read-only.** While they are viewing as that user, they cannot create, edit, approve, or submit. They see the same screens. Actions that would change data are refused.
* **The activity log names both people.** It shows the administrator and the user they were viewing.
* **One view at a time.** An administrator who is already viewing as someone cannot start a second view-as session on top of it.

## What This Enables for Users

### An action can be refused even if you see it

The platform checks your role, the status, and any approval or one-time code that is still required. If a button were shown by mistake, the action would still be refused. Your work does not depend on the screen hiding every unavailable button.

### Decisions stay on the record

Status changes store who changed them, when, the old value, and the new value. Approvals store the approver, the time, and any comments. Rejections store who rejected the item, when, and the reason. Document uploads store who uploaded the file and when. This history is kept and is not edited later.

### Blockchain steps can be checked outside the platform

Minting an NFT, transferring tokens, settling, and recording repayment also produce a transaction reference. That reference ties the on-screen event to the blockchain. The blockchain record does not sit under any one party’s control inside Intain Markets.

## Key Principles to Understand

**Controls run on their own.** You do not enable them, and you cannot turn them off for your account.

**Your role is checked every time.** It is not checked only at sign-in.

**Status decides what is open.** The path is fixed. Steps are not skipped.

**Someone is accountable.** Each change records who did it, when, and what changed.

**The record remains.** Activity history is kept. Blockchain references add a copy you can check outside the platform.

**Incomplete submissions are stopped.** Missing fields or documents are rejected with a message, before the item is treated as submitted.

**Earlier steps are required.** An action stays unavailable until the status, the approval, or the one-time code it depends on is in place.

**Several checks overlap.** Role, status, approval, the one-time code, the request limit, and the field checks all apply. Missing one of them is enough to stop the action.
