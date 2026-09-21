---
title: Asset Sale Statuses
description: Canonical reference for all asset sale deal statuses and their meanings
---

# Asset Sale Statuses

## Overview

Asset sale deals progress through a series of statuses that represent the deal's current state in its lifecycle. Each status determines what actions are available, who can act, and what the deal's operational state means. This reference document provides a complete explanation of every status in the asset sale workflow.

## Lifecycle Overview

Asset sale deals follow a linear progression through statuses:

**Draft** → **Pending Review** → **Published** → **Commit** → **Invest** → **Settlement In Progress** → **Settled** → **Active** → **Repayment In Progress** → **Closed**

Alternative terminal statuses: **Cancelled**, **Defaulted**, **Inactive**

The lifecycle moves from deal preparation (Draft) through market distribution (Published), investor participation (Commit/Invest), financial exchange (Settlement), active management (Active), and finally repayment and closure (Closed).

## Status Meanings

### Draft

**What it means:** The deal has been created by the issuer and is being prepared.

**Who sees it:** Issuer only.

**Available actions:**
- Edit deal details (name, description, dates)
- Assign or remove loans
- Configure sale terms and recourse options
- Upload documents
- Prepare investor agreements
- Publish for underwriter review
- Cancel the deal

**Transitions to:** Pending Review (on publish), Cancelled (on cancel)

---

### Pending Review

**What it means:** The issuer has submitted the deal for underwriter evaluation.

**Who sees it:** Issuer (read-only), Underwriter (review actions).

**Available actions:**
- Underwriter: Review deal package, approve, or reject
- Issuer: View deal status (no edits)

**Transitions to:** Published (on approve), Draft (on reject for revision), Cancelled (on cancel)

---

### Published

**What it means:** The underwriter has approved the deal and it is available to investors.

**Who sees it:** Issuer, Underwriter, Investors.

**Available actions:**
- Investors: View deal details, submit commitments
- Underwriter: Monitor commitments
- Issuer: Monitor deal progress

**Transitions to:** Commit (when commitments begin), Cancelled (on cancel)

---

### Commit

**What it means:** Investors are actively submitting commitments for the deal.

**Who sees it:** All parties.

**Available actions:**
- Investors: Submit or update commitments
- Underwriter: Review and manage allocation

**Transitions to:** Invest (when allocation is finalized)

---

### Invest

**What it means:** Investor allocation is finalized and the deal is preparing for settlement.

**Who sees it:** All parties.

**Available actions:**
- Investor agreement signing (Adobe Sign or manual upload)
- Preparation for fund transfer

**Transitions to:** Settlement In Progress (when settlement begins)

---

### Settlement In Progress

**What it means:** Fund transfers and settlement recording are underway.

**Who sees it:** All parties.

**Available actions:**
- Investors: Confirm fund transfer (bank wire sent)
- Issuer: Confirm payment receipt
- Platform: Record settlement on blockchain

**Transitions to:** Settled (when all transfers confirmed)

---

### Settled

**What it means:** All fund transfers are confirmed and recorded. Ready for NFT transfer.

**Who sees it:** All parties.

**Available actions:**
- Platform: Mint and transfer receivables NFTs to investor wallets

**Transitions to:** Active (after NFT transfer completes)

---

### Active

**What it means:** NFT transfer is complete. Investors hold receivables NFTs representing loan ownership. This is the primary operational status for live deals.

**Who sees it:** All parties.

**Available actions:**
- Issuer: Upload loan tapes, initiate repayment
- Investors: View receivables, monitor analytics
- All: Access asset sale analytics dashboard

**Transitions to:** Repayment In Progress (when issuer initiates repayment), Defaulted (on default), Inactive (on administrative action)

---

### Repayment In Progress

**What it means:** The issuer has initiated repayment to investors. Wire transfer has been sent and awaiting investor confirmation.

**Who sees it:** All parties.

**Available actions:**
- Investors: Review repayment details, confirm receipt, burn NFTs
- Issuer: Monitor investor confirmations

**Transitions to:** Closed (after all NFTs burned and repayment confirmed)

---

### Closed

**What it means:** The deal is fully repaid and all receivables NFTs have been burned. This is the successful terminal status.

**Who sees it:** All parties (read-only).

**Available actions:**
- View audit trail and settlement history
- Access reports and compliance documentation
- No operational actions available

**Terminal status** — no further transitions.

---

### Cancelled

**What it means:** The deal has been cancelled by the issuer or underwriter before settlement.

**Who sees it:** Issuer, Underwriter.

**Available actions:**
- View deal history for audit purposes
- No reactivation possible

**Terminal status** — no further transitions.

---

### Defaulted

**What it means:** The deal has encountered a default condition based on underlying loan performance.

**Who sees it:** All parties.

**Available actions:**
- Special handling workflows as applicable
- Audit trail review

**Terminal status** — requires administrative intervention for resolution.

---

### Inactive

**What it means:** The deal has been administratively marked as inactive.

**Who sees it:** All parties (read-only).

**Available actions:**
- View deal history
- Administrative reactivation if applicable

---

## What Each Status Indicates

| Status | Phase | Key Indicator |
|--------|-------|---------------|
| Draft | Pre-Sale | Deal is being prepared privately |
| Pending Review | Pre-Sale | Awaiting underwriter evaluation |
| Published | Pre-Sale | Available for investor participation |
| Commit | Commitment | Investors are committing capital |
| Invest | Commitment | Allocation finalized, agreements signing |
| Settlement In Progress | Settlement | Fund transfers underway |
| Settled | Settlement | Transfers confirmed, NFT minting next |
| Active | Post-Sale | Live deal, investors hold NFTs |
| Repayment In Progress | Closure | Repayment sent, awaiting confirmation |
| Closed | Terminal | Fully repaid, NFTs burned |
| Cancelled | Terminal | Deal cancelled before settlement |
| Defaulted | Terminal | Default condition encountered |
| Inactive | Terminal | Administratively deactivated |
