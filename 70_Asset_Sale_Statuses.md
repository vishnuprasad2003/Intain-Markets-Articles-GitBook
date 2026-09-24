---
title: Asset Sale Statuses
description: >-
  Canonical reference for all asset sale deal statuses — exact status values
  from the codebase, their meanings, who can act, available actions, and
  transitions
---

# Asset Sale Statuses

## Overview

Asset sale deals progress through a series of statuses that represent the deal's current state in its lifecycle. Each status determines what actions are available, who can act, and what the deal's operational state means. This reference document provides a complete explanation of every status in the asset sale workflow, verified against the actual status values used in the platform's code.

## Lifecycle Overview

Asset sale deals follow a linear progression through statuses:

**Draft** → **Pending Review** → **Approved** → **Published** → **Commit** → **Invest** → **Settlement In Progress** → **Settled** → **Active** → **Repayment In Progress** → **Closed**

Alternative terminal statuses: **Cancelled**, **Defaulted**

Settlement statuses shown to users:

* Settlement: **Created**, **Funded**, **Settled**, **Repayment Initiated**, **Partially Settled**, **Defaulted**
* NFT: **Transferred**, **Retirement pending**, **Retired**

The lifecycle moves from deal preparation (Draft) through market distribution (Published), investor participation (Commit/Invest), financial exchange (Settlement), active management (Active), and finally repayment and closure (Closed).

## Status Meanings

### Draft

**What it means:** The deal has been created by the issuer and is being prepared. This is the initial status assigned when the deal creation API returns successfully.

**Who sees it:** Issuer only.

**Available actions:**

* Edit deal details (name, sale route, dates, governing law, buyer visibility, servicing setup)
* Assign or remove loans (via the Pool Selection tab)
* Configure sale terms (purchase price basis, price, dates, minimum pool size, commit window)
* Configure recourse options (type, triggers, thresholds, holdback, replacement right)
* Upload sale agreement document
* Publish for underwriter review
* Cancel the deal

**Code reference:** Deals are created with `status: 'Draft'`. The editable status set is `["Draft", "Cancelled"]`.

**Transitions to:** Pending Review (on publish), Cancelled (on cancel)

***

### Pending Review

**What it means:** The issuer has submitted the deal for underwriter (Market Maker) evaluation. The deal package is locked for issuer editing while under review.

**Who sees it:** Issuer (read-only), Underwriter (review actions).

**Available actions:**

* Underwriter: Review deal package (terms, loan portfolio, documentation), approve, or reject
* Issuer: View deal status (no edits permitted)

**Transitions to:** Published (on approve), Draft (on reject for revision), Cancelled (on cancel)

***

### Published

**What it means:** The underwriter has approved the deal and it is available to investors. The deal is now visible to the investor audience configured during deal creation (All or Selected).

**Who sees it:** Issuer, Underwriter, Investors (based on buyer visibility setting).

**Available actions:**

* Investors: View deal details, submit commitments
* Underwriter: Monitor commitments
* Issuer: Monitor deal progress

**Code reference:** After underwriter approval, `status` is set to `'Published'`.

**Transitions to:** Commit (when commitments begin), Cancelled (on cancel)

***

### Commit

**What it means:** Investors are actively submitting commitments for the deal. The underwriter reviews incoming commitments and manages allocation.

**Who sees it:** All parties.

**Available actions:**

* Investors: Submit or update commitments
* Underwriter: Review and manage allocation

**Transitions to:** Invest (when allocation is finalized)

***

### Invest

**What it means:** Investor allocation is finalized and the deal is preparing for settlement. This is when investor agreements must be executed.

**Who sees it:** All parties.

**Available actions:**

* Investor agreement signing via Adobe Sign or manual upload (backend enforces that signing is only allowed when deal status is **Invest**)
* Preparation for fund transfer

**Code reference:** The backend validates `dealStatus !== 'Invest'` and blocks agreement signing for any other status.

**Transitions to:** Settlement In Progress (when settlement begins)

***

### Settlement In Progress

**What it means:** Fund transfers and settlement recording are underway. The platform's settlement engine is processing the financial exchange.

**Who sees it:** All parties.

**Available actions:**

* Investors: Confirm fund transfer (bank wire sent)
* Issuer: Confirm payment receipt
* Platform: Record settlement events on blockchain

**Settlement statuses during this phase:**

* **Created** → **Funded** → **Settled**

**Transitions to:** Settled (when all transfers confirmed)

***

### Settled

**What it means:** All fund transfers are confirmed and recorded. The settlement is complete and ready for NFT transfer to finalize investor ownership.

**Who sees it:** All parties.

**Available actions:**

* Platform: Mint and transfer receivables NFTs to investor wallets
* NFT status becomes **Transferred**

**Transitions to:** Active (after NFT transfer completes)

***

### Active

**What it means:** NFT transfer is complete. Investors hold receivables NFTs representing loan ownership. This is the primary operational status for live deals.

**Who sees it:** All parties.

**Available actions:**

* Issuer: Upload loan tapes, initiate repayment
* Investors: View receivables, monitor analytics
* All: Access asset sale analytics dashboard

**Transitions to:** Repayment In Progress (when issuer initiates repayment), Defaulted (on default)

***

### Repayment In Progress

**What it means:** The issuer has initiated repayment to investors. A repayment settlement has been created with the transaction type `Whole Loan Sale Repayment`.

**Who sees it:** All parties.

**Settlement statuses during repayment:**

* Overall status: **Created** (initial) → **Funded** (after issuer confirms payment) → **Settled** (after investor accepts)
* If investor rejects: overall status reverts to **Created** for a retry
* For partial repayment: **Partially Settled** allows additional installments
* NFT status: **Transferred** → **Retirement pending** (after repayment accepted) → **Retired** (after all NFTs retired)

**Available actions:**

* Investors: Review repayment details, accept or reject, retire NFTs
* Issuer: Monitor investor confirmations, record additional installments for partial repayment

**Transitions to:** Closed (after all NFTs retired and repayment confirmed)

***

### Closed

**What it means:** The deal is fully repaid and all receivables NFTs have been retired. This is the successful terminal status.

**Who sees it:** All parties (read-only).

**Available actions:**

* View audit trail and settlement history
* Access reports and compliance documentation
* No operational actions available

**Terminal status** — no further transitions.

***

### Cancelled

**What it means:** The deal has been cancelled by the issuer or underwriter before settlement. Deals in **Draft** or early statuses can be cancelled.

**Who sees it:** Issuer, Underwriter.

**Available actions:**

* View deal history for audit purposes
* No reactivation possible
* Deals in Cancelled status can still be edited (the editable status set includes both Draft and Cancelled)

**Terminal status** — no further transitions.

***

### Defaulted

**What it means:** The deal has encountered a default condition. In the repayment context, the issuer declares default using the "Declare Default" option in the repayment modal. The settlement overall status is set to **Defaulted**.

**Who sees it:** All parties.

**Available actions:**

* Investor: Confirm the default declaration (cannot reject a declared default)
* Audit trail review

**Code reference:** `OVERALL_STATUS.DEFAULTED = 'Defaulted'`. Declaring default is permanent — no further repayment can be recorded.

**Terminal status** — requires administrative intervention for resolution.

***

## What Each Status Indicates

| Status                 | Phase      | Key Indicator                                   | Editable?                         |
| ---------------------- | ---------- | ----------------------------------------------- | --------------------------------- |
| Draft                  | Pre-Sale   | Deal is being prepared privately                | Yes                               |
| Pending Review         | Pre-Sale   | Awaiting underwriter evaluation                 | No (issuer)                       |
| Approved               | Pre-Sale   | Underwriter approved; preparing for publication | No                                |
| Published              | Pre-Sale   | Available for investor participation            | No                                |
| Commit                 | Commitment | Investors are committing capital                | No                                |
| Invest                 | Commitment | Allocation finalized, agreements signing        | No (deal terms), Yes (agreements) |
| Settlement In Progress | Settlement | Fund transfers underway                         | No                                |
| Settled                | Settlement | Transfers confirmed, NFT minting next           | No                                |
| Active                 | Post-Sale  | Live deal, investors hold NFTs                  | Loan tape uploads only            |
| Repayment In Progress  | Closure    | Repayment sent, awaiting confirmation           | No                                |
| Closed                 | Terminal   | Fully repaid, NFTs retired                      | No                                |
| Cancelled              | Terminal   | Deal cancelled before settlement                | Limited editing                   |
| Defaulted              | Terminal   | Default condition encountered                   | No                                |

### Settlement Statuses

| Settlement Status   | Meaning                                     |
| ------------------- | ------------------------------------------- |
| Created             | Settlement initialized, awaiting funding    |
| Funded              | Payer has confirmed funding                 |
| Settled             | Settlement complete; assets transferred     |
| Repayment Initiated | Issuer initiated repayment                  |
| Partially Settled   | Partial repayment accepted, balance remains |
| Defaulted           | Default declared                            |

### NFT Statuses

| NFT Status         | Meaning                                      |
| ------------------ | -------------------------------------------- |
| Transferred        | NFTs transferred to investor wallet          |
| Retirement pending | Repayment accepted; NFT retirement available |
| Retired            | All NFTs retired; deal closure complete      |
