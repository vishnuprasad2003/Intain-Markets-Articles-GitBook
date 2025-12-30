---
title: Loans Overview
description: Learn what loans are and how they work in the platform
---

# Loans Overview

## Overview

Loans are individual credit agreements representing money lent to borrowers. In Intain Markets, loans are the building blocks of pools—you group multiple loans together to create pools for securitization, whole loan sales, or credit facilities. Understanding loans helps you effectively manage your loan portfolios and create successful pools.

## What Loans Are

A loan represents a single credit agreement where money has been lent to a borrower. Each loan contains detailed information about the borrower, the loan amount, interest rates, payment terms, loan characteristics, and performance data. Loans are the fundamental units that make up larger transactions—you organize multiple loans into pools to present them to investors or use them in credit facilities.

Loans have their own lifecycle within the platform. They start as uploaded data, get processed and standardized, can be mapped to pools, go through verification and processing, may be tokenized, and can be removed or reinstated as needed. Each loan contributes its characteristics to pool-level metrics when mapped to a pool.

## Purpose and Use Cases

Loans serve as the foundation for structured finance transactions:

**For Pool Creation** - Loans are the building blocks of pools. You map multiple loans to a pool to create investment opportunities or transaction packages. Pool metrics aggregate individual loan characteristics.

**For Investment Analysis** - Investors and market makers review individual loan details to assess quality, evaluate risk, and make investment decisions. Loan characteristics help determine pool quality and attractiveness.

**For Loan Servicing** - After deals are completed, servicers manage individual loans, tracking payments, updating statuses, and handling ongoing administration. Each loan requires individual attention for servicing.

**For Quality Management** - Loans can be removed from pools if they don't meet quality standards or have data issues. Removed loans are excluded from calculations but can be reinstated when issues are resolved.

**For Portfolio Management** - Issuers manage loan portfolios, organizing loans into pools, tracking loan status, and ensuring data quality throughout the transaction lifecycle.

## Key Components

**Borrower Information** - Details about the borrower including name, contact information, and other identifying information. This helps understand who the loan is with and enables borrower-level analysis.

**Financial Details** - Loan amount, interest rate (coupon), payment terms, maturity date, and other financial characteristics. These details determine the loan's financial profile and contribution to pool metrics.

**Loan Characteristics** - FICO scores, loan-to-value ratios, geographic location, loan type, and other characteristics that help assess loan quality and risk. These characteristics aggregate to create pool-level statistics.

**Status Information** - Current status showing where the loan is in its lifecycle, such as Unmapped, Mapped, Submitted, Verified, Minted, Removed, or Reinstated. Status tracks loan progression through the workflow.

**Performance Data** - Payment history, current balance, outstanding amounts, and other performance metrics. This data helps assess loan quality and track performance over time.

**Pool Assignment** - Which pool the loan is mapped to (if any). Loans can only belong to one pool at a time, ensuring clear ownership and preventing conflicts.

## How Loans Work

**Upload and Processing** - You upload loan data into the platform, typically through file upload. The system processes and standardizes the data, validates loan information, and makes loans available for mapping to pools or individual management.

![Loans Onboarding - Uploading - Issuer](imagesByMdFilesFolder/10/Loans_Onboarding_Uploading_Issuer.png)

**Mapping to Pools** - You assign loans to pools by mapping them. When loans are mapped, they contribute their balance and characteristics to pool metrics. Pool metrics calculate automatically to include the mapped loan.

![Loan Map to Pool - Issuer](imagesByMdFilesFolder/10/LoanMapToPoolIssuer.png)

**Batch Verification and NFT Minting** - After mapping loans to pools, loans are added to batches for verification and NFT minting. Batches group multiple loans together for efficient processing. During verification, the system validates loan data and ensures everything is correct. Once verified, loans can be minted as NFTs (Non-Fungible Tokens) on the blockchain, creating a digital representation of each loan that enables secure tracking, ownership, and transfer. The batch process ensures loans are properly verified and tokenized before they can be used in transactions.

**Status Progression** - Loans progress through statuses from Unmapped to Mapped to Submitted to Verified, and potentially to Minted if tokenization is required. Status shows where each loan is in its lifecycle and what actions are available.

**Removal and Reinstatement** - Loans can be removed from pools if they don't meet criteria or have issues. Removed loans are excluded from pool calculations but remain visible. They can be reinstated when issues are resolved, and metrics recalculate to include them.

**Contribution to Pool Metrics** - Individual loan characteristics aggregate to create pool-level statistics. Loan balances sum to total pool balance, loan counts aggregate, and weighted averages calculate from individual loan rates and scores.

**Individual Management** - Each loan can be managed individually—you can view loan details, update information, track status, and manage loans independently of pools when needed.

## Important Points to Know

**One Pool Per Loan** - Loans can only belong to one pool at a time. If you want to move a loan to a different pool, you must unmap it from the current pool first. This ensures clear ownership and prevents conflicts.

**Automatic Pool Calculations** - When you map loans to pools, pool metrics calculate automatically. Total balance, loan count, weighted averages, and other statistics update immediately to reflect the mapped loans.

**Removed Loans Are Excluded** - Removed loans don't affect pool calculations but remain visible for tracking purposes. This allows you to maintain pool quality while preserving complete records. Removed loans can be reinstated when issues are resolved.

**Loan Characteristics Aggregate** - Individual loan characteristics (FICO scores, interest rates, etc.) aggregate to create pool-level statistics that help investors assess opportunities. Understanding loan characteristics helps you create better pools.

**Status Tracks Lifecycle** - Loan status shows where each loan is in its lifecycle, from upload through mapping, processing, verification, and potentially tokenization. Understanding status helps you track loan progress.

**Complete History** - The platform maintains history of loan status changes, mappings, and other actions, ensuring complete traceability. You can see how loans have progressed and who made changes.

Understanding loans helps you effectively manage loan portfolios, create successful pools, ensure loan data quality, track loans throughout their lifecycle, and understand how individual loans contribute to pool-level metrics and transactions.
