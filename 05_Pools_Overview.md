---
title: Pools Overview
description: Learn what pools are and how they work in structured finance transactions
---

# Pools Overview

## Overview

Pools are collections of loans grouped together for securitization, whole loan sales, or other structured finance transactions. They serve as the fundamental building blocks for presenting loan portfolios to investors, structuring deals, and managing transactions from creation through completion. Understanding pools helps you effectively organize loans and navigate the structured finance workflow.

## What Pools Are

A pool is essentially a container that holds multiple individual loans, organizing them into a single transaction unit. When you create a pool, you're grouping related loans together to present them as a cohesive investment opportunity or transaction package. Pools make it easier to manage, analyze, and present multiple loans as a unified whole rather than dealing with each loan individually.

Pools are dynamic entities—you can add loans to them, remove loans from them, and share them with other parties for review and collaboration. The platform automatically calculates aggregate metrics from all the loans in a pool, such as total balance, loan count, weighted average interest rates, and other characteristics that help investors and market makers understand the pool's composition and quality.

## Purpose and Use Cases

Pools serve several important purposes in structured finance:

**For Securitization Transactions** - Pools organize loans that will be packaged into securities and sold to investors. The pool structure helps investors understand the underlying assets and assess risk and return.

**For Whole Loan Sales** - Pools present loans as investment opportunities to potential buyers. Buyers can review pool characteristics and loan details to make purchase decisions.

**For Transaction Management** - Pools provide a structured way to manage the entire transaction process from initial creation through deal completion, tracking progress and coordinating with multiple parties.

**For Collaboration** - Pools enable collaboration between issuers, market makers, investors, and other parties. You can share pools for review, receive feedback, and work together to structure deals.

**For Analysis** - Pools aggregate loan data into meaningful metrics that help all parties understand pool characteristics, assess quality, and make informed decisions.

## Key Components

**Pool Information** - Basic details about the pool including pool name, asset class, transaction type, description, and closing deal indicator. The pool name must be unique and helps identify the pool throughout the transaction.

**Mapped Loans** - Individual loans that have been assigned to the pool. Loans can only belong to one pool at a time. When loans are mapped, they contribute their balance, characteristics, and data to pool-level metrics.

**Pool Metrics** - Aggregate statistics calculated automatically from mapped loans, including total balance, loan count, weighted average coupon, weighted average FICO scores, geographic distribution, and other characteristics. These metrics update automatically when loans are added or removed.

**Organization Assignments** - Organizations assigned to participate in the transaction, such as market makers for structuring, investors for funding, servicers for loan administration, paying agents for payment distributions, and rating agencies for analysis.

**Status** - The current stage of the pool in its workflow, such as Created, Preview, Mandate Pending, or Deal. Status determines what actions are available and what needs to happen next.

**Sharing Configuration** - Settings that control which organizations can see the pool and what they can do with it, such as viewing, providing feedback, downloading data, or requesting changes.

## How Pools Work

**Creation** - You create a pool by providing basic information like pool name, asset class, and transaction type. The pool starts in Created status, visible only to you, ready for loan mapping and configuration.

**Loan Mapping** - You map loans to the pool by selecting individual loans and assigning them to the pool. When loans are mapped, pool metrics calculate automatically. You can add or remove loans while the pool is in Created or Preview status.

**Pool Creation** - As an issuer, you create pools to group loans together for structured finance transactions. The pool creation process allows you to set up pools with all necessary information.

![Pool Creation - Issuer](imagesByMdFilesFolder/05/PoolCreation_Issuer.png)

**Sharing** - You share pools with other organizations for review and collaboration. When shared, pools become visible to those organizations, and recipients can view, analyze, and provide feedback based on sharing permissions.

![Pool Sharing - Issuer](imagesByMdFilesFolder/05/PoolSharing_Issuer.png)

**Pool Details** - When viewing pools, you can access detailed information including pool metrics, loan composition, and available actions. The pool details view provides comprehensive information for decision-making.

![Pool Details - Issuer](imagesByMdFilesFolder/05/Pool_Details_Issuer.png)

**Loan Mapping** - You map loans to pools to include them in the pool. Once mapped, loans contribute their characteristics to pool metrics.

![Loan Map to Pool - Issuer](imagesByMdFilesFolder/05/LoanMapToPoolIssuer.png)

**Status Progression** - Pools progress through statuses from Created to Preview to Mandate Pending to Deal. Each status represents a specific stage and determines what actions are available. Status changes happen when you take actions like sharing, submitting for mandate, or when market makers accept mandates.

**Collaboration** - Multiple parties can work together on pools. Issuers create and share, market makers review and structure, investors evaluate opportunities, and rating agencies analyze for ratings. Feedback and change requests enable iterative improvement.

**Finalization** - When market makers accept mandates, pools become Deals, representing finalized and committed transactions. At this stage, editing is restricted, and the pool is ready for execution.

## Important Points to Know

**Automatic Metric Calculation** - Pool metrics calculate automatically from mapped loans. You don't need to calculate them manually—total balance, loan count, weighted averages, and other statistics update automatically when loans are added or removed.

**One Pool Per Loan** - Loans can only belong to one pool at a time. If you want to move a loan to a different pool, you must unmap it from the current pool first. This ensures clear ownership and prevents conflicts.

**Status Controls Actions** - Pool status determines what actions are available. You can edit pools in Created or Preview status, but editing is restricted once pools become Deals. Understanding status helps you know what you can do.

**Removed Loans Are Excluded** - Removed loans are excluded from pool calculations but remain visible for tracking. This allows you to maintain pool quality while preserving complete records. Removed loans can be reinstated if needed.

**Sharing Enables Collaboration** - Sharing pools with other organizations enables collaboration and review. You can share with multiple parties simultaneously, and sharing permissions control what recipients can do.

**Complete Audit Trail** - All pool changes, status updates, and actions are recorded with who did what and when, ensuring complete transparency and accountability throughout the transaction lifecycle.

Understanding pools helps you effectively organize loans, present opportunities to investors, collaborate with other parties, manage transactions from creation to completion, and navigate the structured finance workflow successfully.
