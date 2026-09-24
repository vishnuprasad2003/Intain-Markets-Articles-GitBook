---
title: Asset Sale Deal Lifecycle and Statuses
description: >-
  Complete lifecycle progression of asset sale deals — from creation through
  closure, with exact status names, transition triggers, and what happens at
  each stage
---

# Asset Sale Deal Lifecycle & Statuses

## Overview

Asset sale deals progress through several statuses from initial creation to final closure. Each status represents a specific stage in the deal's journey and determines what actions are available, who can act, and what the deal's current state means. Understanding the lifecycle helps you navigate the workflow and know what to expect at each stage.

## Lifecycle Overview

Asset sale deals follow a linear lifecycle with clear progression through stages:

**Pre-Sale Phase**

* The deal starts as **Draft** when first created by the issuer via the three-step deal creation wizard (Basics → Pool Selection → Sale Terms)
* After loan assignment, sale terms configuration, and optional recourse profile setup, the issuer publishes the deal
* The deal moves to **Pending Review** for the underwriter (Market Maker) to evaluate
* The underwriter reviews the deal package — loans, terms, documentation — and makes a decision:
  * **Approve** → the deal becomes **Approved**, then **Published** and is visible to investors
  * **Reject** → the deal reverts to **Draft** for the issuer to revise
* If the issuer or underwriter cancels at any point during pre-sale, the deal moves to **Cancelled**

**Commitment Phase**

* Investors review the published deal and submit commitments
* The deal enters the **Commit** stage as investors formalize their participation
* The underwriter manages allocation across investors — distributing the deal capacity among committed investors
* Once allocation is finalized, the deal moves to **Invest**
* During the Invest stage, investor agreements are executed (via Adobe Sign or manual upload)
* The backend enforces that agreement signing is only permitted when the deal status is exactly **Invest**

**Settlement Phase**

* Settlement begins once agreements are signed and the fund transfer process is initiated
* The deal enters **Settlement In Progress** while transfers are being confirmed
* Settlement progress is tracked as **Created** → **Funded** → **Settled**
* Once all parties confirm, the deal becomes **Settled**

**Post-Sale Phase**

* After settlement, receivables NFTs are minted and transferred to investor wallets
* The NFT status becomes **Transferred**
* The deal status becomes **Active** — the primary operational status for live deals
* The issuer manages ongoing loan tape uploads and monitors the underlying loans
* When the issuer initiates repayment, the deal moves to **Repayment In Progress**
* A repayment settlement is created with transaction type `Whole Loan Sale Repayment`
* The investor reviews and accepts (or rejects) the repayment declaration
* After acceptance, the investor retires (burns) their receivables NFTs on-chain
* The NFT status progresses: **Transferred** → **Retirement pending** → **Retired**
* Once all NFTs are retired, the deal becomes **Closed**
* If the deal encounters issues, it may move to **Defaulted** (via the issuer's "Declare Default" action)

The lifecycle is designed to ensure proper review, approval, and documentation at each stage before progressing to the next.

![Deal Lifecycle Stepper](.gitbook/assets/deal-lifecycle-stepper.png)

## Status Meanings

### Draft

The deal has been created by the issuer with basic information and is being prepared for publication. In this status, the issuer can edit all deal details through the three-step wizard: deal basics (name, sale route, target settlement date, governing law, buyer visibility, arranger, servicing setup, servicing fee), pool/loan selection (individual assets or entire pools), and sale terms (purchase price basis, price, cutoff date, settlement date, minimum pool size, commit window, recourse profile). The issuer can also upload or replace the sale agreement document. The deal is visible only to the issuer at this stage. The editable status set in the code is `["Draft", "Cancelled"]`.

### Pending Review

The issuer has submitted the deal for underwriter review. The underwriter can view all deal details, review the loan portfolio, examine documentation, and make an approval decision. The issuer can no longer edit deal fundamentals while the deal is under review. The underwriter has three options: approve (→ Published), reject (→ Draft for revision), or cancel.

### Published

The underwriter has approved the deal and it is now visible to investors (according to the buyer visibility setting: All investors or Selected investors). Investors can review deal details, loan portfolios, and documentation. This is the stage where investor interest is gathered and commitments begin.

### Cancelled

The deal has been cancelled by either the issuer or the underwriter. Cancelled deals are retained for audit purposes. Interestingly, deals in Cancelled status are still in the editable set alongside Draft, meaning limited editing may be possible, but the deal cannot re-enter the active lifecycle. This is a terminal status.

### Commit

Investors have begun submitting commitments for the deal. The underwriter reviews and manages the allocation of commitments across investors. Deal terms are locked at this stage — no further edits to sale terms, recourse profile, or loan assignments are permitted.

### Invest

Investor commitments have been finalized and the deal is ready for settlement preparation. This is the critical stage where investor agreements must be executed. The backend enforces a strict gate: investor agreement signing (via Adobe Sign or manual upload) is only allowed when the deal status is exactly **Invest**. If the deal is in any other status, the signing endpoint rejects the request with: "Investor agreement signing is only allowed when deal status is Invest."

### Settlement In Progress

The settlement process has been initiated. Fund transfers are being processed via bank wire, and the platform is recording settlement events on the blockchain. The settlement engine manages its own status lifecycle:

| Settlement Status | Meaning                               |
| ----------------- | ------------------------------------- |
| Created           | Settlement initialized                |
| Funded            | Payer confirmed funding               |
| Settled           | Rail delivered and assets transferred |

This is a transitional status that resolves once all transfers are confirmed and the settlement rail completes delivery.

### Settled

All fund transfers have been confirmed and recorded. The settlement is complete, and the deal is ready for NFT transfer to finalize investor ownership of the loan receivables. The platform mints receivables NFTs and transfers them to investor wallets; the NFT status becomes **Transferred**.

### Active

NFT transfer is complete — investors now hold receivables NFTs representing their ownership of the loan assets. This is the primary operational status for live deals. The issuer manages ongoing loan tape updates and monitors the underlying loans. Analytics dashboards are available to all parties.

Available issuer actions at this stage:

* Upload latest loan tape (Edit Loan Tape → field mapping → save)
* Initiate repayment (opens the four-step repayment wizard)
* Monitor deal performance

### Repayment In Progress

The issuer has initiated a repayment to investors. This happens through the repayment modal, where the issuer:

1. Selects the payment rail (currently Bank Wire/ACH)
2. Chooses the repayment type (Full, Partial, or Declare Default)
3. Enters payment details (date, amount, wire reference) and uploads wire confirmation
4. Confirms the repayment

The deal remains in this status until all investors respond:

* **Accept** → leads to NFT burn and eventual closure
* **Reject** → the settlement reverts, the issuer can record a new repayment attempt
* For **partial repayment**, the settlement status becomes **Partially Settled**, and additional installments can be recorded
* For **declared default**, the settlement status becomes **Defaulted**

### Closed

The deal has been fully repaid and all receivables NFTs have been retired by investors. This is the final terminal status indicating successful completion of the entire asset sale lifecycle. The deal shows as 100% repaid, the NFT status is **Retired**, and all settlement and repayment audit trails are preserved.

### Defaulted

The deal has encountered a default condition. This status is reached when the issuer declares default through the repayment modal's "Declare Default" option. The settlement overall status is set to **Defaulted**. The investor must confirm the default declaration (rejection of a declared default is not permitted). Declaring default is permanent — no further repayment can be recorded after this action.

## What Each Status Indicates

**Draft** indicates the deal is still being prepared. The issuer has full control over all aspects of the deal — basics, loan assignment, sale terms, recourse profile, and documents — and should complete everything before publishing.

**Pending Review** indicates the deal is awaiting underwriter evaluation. The underwriter should review the deal promptly and communicate any issues. No edits are possible during review.

**Published** indicates the deal is live and available to investors. This is the stage where market interest is tested and investor commitments are gathered.

**Commit and Invest** indicate progressive investor participation. During Commit, investors are submitting and the underwriter is managing allocation. During Invest, allocation is finalized and the focus shifts to agreement execution — the only stage where investor agreement signing is permitted.

**Settlement In Progress and Settled** indicate the financial exchange is happening or complete. Fund transfers, blockchain recording, and NFT preparation occur during these stages. The settlement engine manages a separate set of statuses (Created → Funded → Settled) that track the mechanics of fund delivery.

**Active** indicates the deal is fully settled with NFTs transferred to investors. This is the operational steady-state where loan tape management, monitoring, and repayment initiation occur.

**Repayment In Progress** indicates an active repayment cycle. The issuer has declared a repayment outcome (full, partial, or default) and the investor must respond. The settlement tracks additional statuses: Partially Settled for partial repayment, Defaulted for declared default, and NFT statuses (**Transferred** → **Retirement pending** → **Retired**) for the token retirement flow.

**Closed** indicates successful deal completion. All financial obligations have been met, all NFTs have been retired on-chain, and the deal is archived with a complete, immutable audit trail covering every event from creation through closure.
