---
title: Asset Sale Overview
description: Learn what asset sales are and how they work on the Intain Markets platform
---

# Asset Sale Overview

## Overview

An asset sale is a transaction where a financial institution (the issuer) sells a portfolio of loans or receivables to one or more investors. On Intain Markets, the Asset Sale module enables issuers to package loans into deals, publish them for underwriter review, allocate to investors, settle the transaction with NFT-based ownership transfer, and manage the post-sale lifecycle including repayment and deal closure. This module covers the complete asset sale workflow from deal creation to final repayment.

## What Asset Sale Is

An asset sale — also referred to internally as a Whole Loan Sale — is a structured transaction where loan assets change ownership from the issuer (seller) to investors (buyers). Unlike securitization where loans are pooled into tranches with different risk profiles, an asset sale transfers the actual loan assets directly.

Asset sales involve multiple components that progress through a structured workflow:

* **Deals** package loans with sale terms for investor review
* **Commitments** capture investor interest and allocation
* **Settlement** handles the financial exchange and NFT ownership transfer
* **Repayment** manages the post-sale lifecycle when borrowers repay the underlying loans
* **Receivables** represent the tokenized loan assets that investors hold after settlement

## Purpose and Use Cases

**For Loan Portfolio Sales** — Issuers who want to sell a portfolio of loans to investors use asset sales to package, price, and transfer the assets with full transparency and blockchain-based traceability.

**For Institutional Investment** — Investors gain access to loan portfolios through a structured review, commitment, and settlement process with complete documentation and agreement signing.

**For Underwriter Oversight** — Underwriters (market makers) review deal terms, manage investor allocation, and oversee the settlement process to ensure compliance and proper execution.

**For Post-Sale Lifecycle Management** — After settlement, the platform manages ongoing repayment flows between issuers and investors, including loan tape updates, repayment initiation, receipt confirmation, and NFT burn on deal closure.

**For Servicing Operations** — Servicers can upload and manage loan tapes throughout the deal lifecycle, ensuring that loan-level data stays current for all parties.

## Key Components

**Deals** — The core unit of an asset sale. A deal packages a set of loans with sale terms (pricing, recourse options, settlement dates) and progresses through a lifecycle from draft to closed. Deals are created by the issuer, reviewed by the underwriter, and made available to investors.

**Loan Assignment** — Issuers assign loans to a deal either individually by loan ID or by mapping an entire pool. Assigned loans become part of the deal's asset portfolio and are visible to all deal participants once published.

**Sale Terms** — Configuration that defines the economics of the deal, including pricing methodology, recourse type, and settlement terms. Sale terms can be set as optional or required depending on the deal structure.

**Investor Agreements** — Legal documentation between the issuer and each investor. Agreements can be signed electronically via Adobe Sign or uploaded manually as pre-signed documents. Each investor must have a signed agreement before settlement can proceed.

**Commitments** — Investor expressions of interest in purchasing a portion of the deal. Commitments capture the investment amount each investor is willing to allocate. The underwriter manages and finalizes the allocation across investors.

**Settlement** — The financial exchange where investors pay for the loan assets and receive NFT-based ownership tokens in return. Settlement uses bank wire transfers (off-chain) and records the transaction on the blockchain for immutable traceability.

**Repayment** — The post-sale process where the issuer repays investors when the underlying loan borrowers make payments. Repayment involves uploading the latest loan tape, initiating repayment with wire confirmation, and investor receipt confirmation.

**Receivables & NFT Burn** — After settlement, investors hold receivables NFTs representing their ownership of the loan assets. When a deal is fully repaid, investors burn these NFTs to close out their position, and the deal status moves to Closed.

**Asset Sale Analytics** — A comprehensive analytics dashboard embedded within each deal, providing asset analysis, risk surveillance, and performance tracking across the deal's loan portfolio.

![Deal Details Page](.gitbook/assets/deal-details-page.png)

![Asset Sale Deal Details](.gitbook/assets/issuer-deal-details.png)

## How Asset Sale Works

**1. Deal Creation (Issuer)**

The issuer navigates to the **Asset Sale** section from the left sidebar menu (under Transactions). The Asset Sale dashboard displays summary tiles (Total Deals, Draft Deals, Submitted Deals, Active Deals) and a searchable, filterable deal table showing Deal ID, Deal Name, Sale Route, Servicing Setup, Current Balance, Price, Status, and Last Updated. The issuer clicks **Create Deal** to open a 3-step wizard (Basics → Pool Selection → Sale Terms), configures the deal, and saves it in Draft status.

![Asset Sale Dashboard - Issuer View](.gitbook/assets/issuer-asset-sale-dashboard.png)

**2. Loan Assignment (Issuer)**

The issuer assigns loans to the deal by selecting from available loans or mapping an entire pool. Loan details including balances, rates, and collateral information become part of the deal package. The issuer also configures sale terms and recourse options.

**3. Publishing for Review (Issuer)**

When the deal package is ready, the issuer publishes the deal to the underwriter. The deal status changes from Draft to Pending Review, and the underwriter receives the deal for evaluation.

**4. Underwriter Review**

The underwriter reviews the deal terms, loan portfolio, and documentation. They can approve or reject the deal. If approved, the deal becomes Published and is made available to investors. If changes are needed, the deal can be sent back for revision.

**5. Investor Commitment**

Investors view the published deal and submit commitments indicating how much they want to invest. The underwriter reviews all commitments and finalizes the allocation, determining how much each investor will receive.

**6. Agreement Signing**

Before settlement, investor agreements must be executed. The issuer can upload a sale agreement for electronic signing via Adobe Sign, or upload manually signed documents. Each investor's agreement status is tracked independently.

**7. Settlement**

Once commitments are finalized and agreements are signed, the settlement process begins. Investors transfer funds via bank wire, and the platform records the settlement on the blockchain. NFTs representing the loan receivables are transferred to investors, and the deal status moves to Active.

**8. Post-Sale Lifecycle**

After settlement, the deal enters its active lifecycle. The issuer manages ongoing loan tape updates, and when borrowers make payments on the underlying loans, the issuer initiates repayment to investors. Investors confirm receipt and, when the deal is fully repaid, burn their receivables NFTs to close the deal.

## Important Points to Know

**Role-Based Access** — Each role sees a different view of the Asset Sale dashboard. Issuers see all their deals (including Draft) with the Create Deal button. Underwriters (labeled "Facility Agent" in the sidebar) see deals from Pending Review onward with Accept/Reject actions and an Investor(s) column. Investors see deals from Published onward — Draft, Pending Review, and Approved deals are hidden from their view.

**Status-Driven Workflow** — The deal lifecycle is strictly status-driven. Each status determines what actions are available and who can perform them. Actions that are not available at the current status are disabled in the interface.

**Blockchain Traceability** — Every significant action in the asset sale lifecycle is recorded on the blockchain, providing an immutable audit trail. NFT transfers, settlement confirmations, and repayment events are all traceable.

**E-Signature Integration** — Investor agreements support electronic signatures via Adobe Sign, providing legally binding documentation within the platform workflow.

**Loan Tape Management** — Throughout the deal lifecycle, loan tapes can be updated to reflect the latest loan-level data. This is particularly important during the repayment phase, where the latest loan tape determines repayment amounts.
