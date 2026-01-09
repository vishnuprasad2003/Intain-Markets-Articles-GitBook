---
title: Pools Overview
description: Learn what pools are and how they work in structured finance transactions
---

# Pools Overview

## Overview

Pools are collections of loans grouped together for securitization, whole loan sales, or other structured finance transactions. They serve as the fundamental building blocks for presenting loan portfolios to market makers, investors, and rating agencies. As an issuer, you create pools, map loans from your Loan Registry, and share them with other organizations for review and deal progression.

## What Pools Are

A pool is a container that holds multiple individual loans, organizing them into a single transaction unit. When you create a pool, you group related loans together to present them as a cohesive investment opportunity or transaction package. Pools aggregate loan-level data into meaningful metrics that help all parties understand the pool's characteristics, risk profile, and investment potential.

Pools are dynamic—you can add loans, remove loans, and share them with other parties for review and collaboration. The platform automatically calculates aggregate metrics from all loans in a pool, and these metrics update automatically when loans are added or removed.

## Purpose and Use Cases

Pools serve several important purposes in structured finance:

**For Securitization Transactions** - Pools organize loans that will be packaged into securities and sold to investors. By grouping loans into pools, you can present a defined set of collateral for securitization structures.

**For Whole Loan Sales** - Pools present loans for potential buyers. Investors can review pool characteristics and individual loan details.

**For Transaction Management** - Pools provide a structured way to manage the entire transaction process from creation through deal completion. Status progression tracks where each pool is in the workflow.

**For Collaboration** - Pools enable collaboration between issuers, market makers, investors, and rating agencies. Sharing controls determine what each party can see and do.

**For Analysis** - Pools aggregate loan data into meaningful metrics that help all parties understand pool characteristics, assess quality, and make informed decisions.

## Key Components

**Pool Information** - Basic details about the pool including pool name (must be unique), asset class (auto loans, personal loans, mortgages, commercial mortgages, etc.), transaction type (securitization, whole loan sale, etc.), description, and closing deal indicator. These details are entered when you set up the pool and can be edited while in Created or Preview status.

**Organization Assignments** - Organizations assigned to participate in the transaction: market makers for structuring, investors for funding, servicers for loan administration, paying agents for payment distributions, rating agencies for analysis, and verification agents for loan verification. You select these organizations during pool setup, and only assigned organizations appear as options when you share the pool.

**Mapped Loans** - Individual loans that have been assigned to the pool from the Loan Registry. Loans can only belong to one pool at a time. When loans are mapped, they contribute their balance, characteristics, and data to pool-level metrics. The Loans tab in pool details shows all mapped loans with action icons for feedback and loan rejection handling.

**Pool Metrics** - Aggregate statistics calculated automatically from mapped loans. These metrics are displayed in summary tiles at the top of the pool details page and update automatically when loans are added, removed, or reinstated.

**Pool Details Sections** - Within the pool details page, you have access to:
- **Summary Section**: Charts and analytics showing pool composition and loan distributions
- **Loans Tab**: All mapped loans with their key fields and action icons (tick, cross, chat box for feedback and loan rejection handling)
- **Loan Tape Section**: Detailed loan-level data for both mapped and unmapped columns (unmapped columns show headers in italic). You can select different "As Of Date" values to view loan data for different reporting periods and download loan data in XLSX or CSV format
- **Strats Section**: Stratification analytics showing distributions by various loan characteristics
- **Performance Section**: Performance analytics for loans in the pool
- **Feedback Section**: Pool-level feedback from market makers, investors, and other shared parties (issuers can view but not add pool-level feedback themselves)
- **Sharing Tab**: Shows all organizations shared with and their current permissions (feedback, download)

**Status** - The current stage of the pool in its workflow. Pool status progresses through Created → Preview → Deal. Status determines what actions are available and what editing is permitted.

**Sharing Configuration** - Settings that control which organizations can see the pool and what they can do with it. Permissions include view access, feedback capability, and download capability. Permissions are set per organization and can be adjusted in the Sharing tab.

## How Pools Work

**Creation** - You create a pool by clicking **Set-up Pool** in the Pools dashboard and entering basic information: pool name, asset class, transaction type, description, and closing deal indicator. You also select organizations (market makers, investors, servicers, paying agents, rating agencies, verification agents) that will be available for sharing later. The pool starts in Created status, visible only to you, ready for loan mapping and configuration.

![Pool Creation - Issuer](imagesByMdFilesFolder/05/PoolCreation_Issuer.png)

**Loan Mapping** - You map loans to the pool from the **Loan Registry** section (not from within pool details). In Loan Registry, you select unmapped loans and click **Map to Pool**, then choose the target pool from a dropdown. When loans are mapped, pool metrics calculate automatically. You can view mapped loans in the pool's Loans tab.

![Loan Map to Pool - Issuer](imagesByMdFilesFolder/05/LoanMapToPoolIssuer.png)

**Sharing (Preview Flow)** - You share pools with other organizations by clicking **Share** in pool details. You select recipient type, choose from assigned organizations, and set permissions (feedback, download). When shared, the pool status becomes Preview (if it was Created). Recipients see the pool as **Mandate Pending** with Accept/Reject actions. Before accepting, market makers cannot provide feedback. After a market maker accepts, their view shows **Under Review** and feedback becomes available.

![Pool Sharing - Issuer](imagesByMdFilesFolder/05/PoolSharing_Issuer.png)

**Pool Details** - When viewing pools, you access comprehensive information: pool metrics in summary tiles, loan composition in the Loans tab, detailed loan data in the Loan Tape section (with As Of Date selection and download), stratification analytics in Strats, performance analytics in Performance, pool-level feedback in Feedback, and sharing configuration in Sharing. The Edit button provides options to edit pool details or upload recurring loan tapes.

![Pool Details - Issuer](imagesByMdFilesFolder/05/Pool_Details_Issuer.png)

**Start Deal Flow** - When prerequisites are met (typically all pool loans NFT-minted), the **Start Deal** button becomes enabled. Start Deal sends the pool to recipients with status **Ready for Deal**. When a market maker accepts, the pool becomes a **Deal** and structural editing is restricted.

**Status Progression** - Pools progress through statuses: Created → Preview (when shared) → Deal (when accepted via Start Deal). Each status represents a specific stage with appropriate controls. In Created and Preview, you can edit the pool. In Deal, editing is restricted.

**Collaboration** - Multiple parties work together on pools. Issuers create and share; market makers review, accept mandates, and can share further with investors; investors evaluate and provide feedback; rating agencies analyze for ratings. Each role sees appropriate views and actions.

## Important Points to Know

**Automatic Metric Calculation** - Pool metrics calculate automatically from mapped loans and update automatically when loans are added, removed, or reinstated.

**One Pool Per Loan** - Loans can only belong to one pool at a time. To move a loan to a different pool, unmap it from the current pool first.

**Status Controls Actions** - Pool status determines what actions are available. You can edit pools in Created or Preview status, but editing is restricted once pools become Deals.

**Sharing Permissions** - Permissions (feedback, download) are set per organization and control what recipients can do. You can adjust permissions in the Sharing tab.

**Preview vs Start Deal** - Preview sharing allows recipients to review and accept/reject mandates while you retain editing rights. Start Deal sends a finalized pool (after NFT minting) and results in Deal status when accepted.

**Loan Rejection Handling** - In the Loans tab, action icons allow handling of loan rejection requests from market makers. Tick accepts the rejection (loan marked as Removed); cross rejects the rejection request.

**Loan Tape Downloads** - The Loan Tape section allows selecting different As Of Date values for periodic loan data and downloading in XLSX or CSV format.

**Feedback Levels** - Feedback can be pool-level (in the Feedback section) or loan-level (via chat box icon in Loans tab). Issuers can view pool-level feedback but add comments through loan-level feedback.
