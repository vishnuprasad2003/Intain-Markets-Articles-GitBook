---
title: Asset Sale Deal Lifecycle and Statuses
description: Understand the different stages asset sale deals go through from creation to closure
---

# Asset Sale Deal Lifecycle & Statuses

## Overview

Asset sale deals progress through several statuses from initial creation to final closure. Each status represents a specific stage in the deal's journey and determines what actions are available, who can act, and what the deal's current state means. Understanding the lifecycle helps you navigate the workflow and know what to expect at each stage.

## Lifecycle Overview

Asset sale deals follow a linear lifecycle with clear progression through stages:

**Pre-Sale Phase**
- Deal starts as **Draft** when first created by the issuer
- After loan assignment and deal preparation, the issuer publishes the deal
- The deal moves to **Pending Review** for the underwriter to evaluate
- The underwriter approves or rejects; if approved, the deal becomes **Published**
- If the issuer or underwriter cancels, the deal moves to **Cancelled**

**Commitment Phase**
- Investors review the published deal and submit commitments
- The underwriter manages allocation across investors
- The deal moves through **Commit** and **Invest** stages as investors formalize their participation

**Settlement Phase**
- Settlement begins with fund transfer and NFT minting
- The deal enters **Settlement In Progress** while transfers are being confirmed
- Once all parties confirm, the deal becomes **Settled**

**Post-Sale Phase**
- After NFT transfer to investors, the deal becomes **Active**
- When the issuer initiates repayment, the deal moves to **Repayment In Progress**
- After investors confirm receipt and burn NFTs, the deal becomes **Closed**
- If the deal encounters issues, it may move to **Defaulted** or **Inactive**

The lifecycle is designed to ensure proper review, approval, and documentation at each stage before progressing to the next.

![Deal Lifecycle Stepper](images/33-asset-sale-deal-lifecycle-and-statuses/deal-lifecycle-stepper.png)

## Status Meanings

### Draft

The deal has been created by the issuer with basic information and is being prepared for publication. In this status, the issuer can edit all deal details, assign or remove loans, configure sale terms and recourse options, upload documents, and prepare investor agreements. The deal is visible only to the issuer at this stage.

### Pending Review

The issuer has submitted the deal for underwriter review. The underwriter can view all deal details, review the loan portfolio, examine documentation, and make an approval decision. The issuer can no longer edit deal fundamentals while the deal is under review.

### Published

The underwriter has approved the deal and it is now visible to investors. Investors can review deal details, loan portfolios, and documentation. This is the stage where investor interest is gathered and commitments begin.

### Cancelled

The deal has been cancelled by either the issuer or the underwriter. Cancelled deals are retained for audit purposes but cannot be reactivated. This is a terminal status.

### Commit

Investors have begun submitting commitments for the deal. The underwriter reviews and manages the allocation of commitments across investors. Deal terms are locked at this stage.

### Invest

Investor commitments have been finalized and the deal is ready for settlement preparation. Investor agreements must be executed before proceeding to settlement.

### Settlement In Progress

The settlement process has been initiated. Fund transfers are being processed via bank wire, and the platform is recording settlement events on the blockchain. This is a transitional status that resolves once all transfers are confirmed.

### Settled

All fund transfers have been confirmed and recorded. The settlement is complete, and the deal is ready for NFT transfer to finalize investor ownership of the loan receivables.

### Active

NFT transfer is complete — investors now hold receivables NFTs representing their ownership of the loan assets. The deal is in its active post-sale lifecycle. The issuer manages ongoing loan tape updates and monitors the underlying loans. This is the primary operational status for live deals.

### Repayment In Progress

The issuer has initiated a repayment to investors, typically triggered by borrower payments on the underlying loans. The issuer has uploaded the latest loan tape, selected the payment rail (bank wire), and submitted repayment details. The deal remains in this status until all investors confirm receipt.

### Closed

The deal has been fully repaid and all receivables NFTs have been burned by investors. This is the final terminal status indicating successful completion of the entire asset sale lifecycle. The deal shows as 100% repaid, and all settlement and repayment audit trails are preserved.

### Defaulted

The deal has encountered a default condition. This status is set when the underlying loan portfolio fails to perform according to the deal terms. Defaulted deals require special handling and may trigger different workflows.

### Inactive

The deal has been marked as inactive, typically due to administrative reasons or extended periods without activity. Inactive deals are retained for reference but are not part of active operations.

## What Each Status Indicates

**Draft** indicates the deal is still being prepared. The issuer has full control over all aspects of the deal and should complete loan assignment, sale terms configuration, and document preparation before publishing.

**Pending Review** indicates the deal is awaiting underwriter evaluation. The underwriter should review the deal promptly and communicate any issues. No edits are possible during review.

**Published** indicates the deal is live and available to investors. This is the stage where market interest is tested and investor commitments are gathered.

**Commit and Invest** indicate progressive investor participation. The deal is moving toward settlement as commitments are finalized and agreements are signed.

**Settlement In Progress and Settled** indicate the financial exchange is happening or complete. Fund transfers, blockchain recording, and NFT preparation occur during these stages.

**Active** indicates the deal is fully settled with NFTs transferred to investors. This is the operational steady-state where loan tape management and monitoring occur.

**Repayment In Progress** indicates an active repayment cycle. The issuer has initiated repayment and is awaiting investor confirmation.

**Closed** indicates successful deal completion. All financial obligations have been met, NFTs have been burned, and the deal is archived with a complete audit trail.
