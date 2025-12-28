---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where each loan is in the process, know what actions are available, and understand why certain actions are disabled. Each status represents a specific stage in the loan's journey from upload to final state, and understanding these statuses helps you manage loans effectively throughout the structured finance workflow.

## Lifecycle Overview

Loans typically start as **Unmapped** when first uploaded into the system, progress to **Mapped** when assigned to a pool, may move to **Submitted** when included in a batch, advance to **Verified** after verification, potentially reach **Minted** if tokenization is required, and may be **Removed** from pool calculations if needed, with the option to be **Reinstated** later. This progression ensures that loans move through proper stages with appropriate processing and validation at each step.

The lifecycle is designed to support loan management—you upload loans, assign them to pools, they go through verification and processing, and they may be tokenized or removed as needed. Each stage has specific purposes and allows different types of actions, ensuring that loans progress correctly through the structured finance workflow. Understanding this lifecycle helps you know what to expect and how to navigate loan management effectively.

## Status Meanings

**Unmapped** - The loan has been uploaded into the system but is not yet assigned to any pool. This is the initial stage where loans are available for mapping. Loans in Unmapped status are available for assignment but don't contribute to any pool metrics.

**Mapped** - The loan has been assigned to a pool and is included in pool calculations. The loan contributes to pool metrics and characteristics. Loans in Mapped status are actively participating in pools and affecting pool-level statistics.

**Submitted** - The loan has been included in a batch for verification or other processing. The loan is being reviewed or processed. Loans in Submitted status are moving through verification or processing workflows.

**Verified** - The loan has been verified and can proceed to next stages such as tokenization. The loan meets quality and compliance requirements. Loans in Verified status have passed verification and are ready for further processing.

**Minted** - An NFT (non-fungible token) has been created for the loan, and the loan is tokenized. This status only applies if tokenization is part of your workflow. Loans in Minted status are represented on the blockchain and ready for blockchain-based transactions.

**Removed** - The loan has been removed from pool calculations but remains visible in the pool. The loan is excluded from metrics but can be tracked. Loans in Removed status are temporarily or permanently excluded from pool calculations.

**Reinstated** - A previously removed loan has been put back into the pool and is included in calculations again. The loan fully participates in the pool. Loans in Reinstated status have been restored to active participation in pools.

## What Each Status Indicates

**Unmapped Status** indicates that the loan is available for assignment but hasn't been mapped to a pool yet. You can map it to a pool, edit information if allowed, or manage it independently. This status tells you that the loan is ready to be included in a pool. You have full control over unmapped loans and can assign them to pools when ready.

**Mapped Status** indicates that the loan is part of a pool and contributing to pool calculations. Pool metrics include this loan, and you can unmap it if needed. This status tells you that the loan is actively participating in a pool. The loan affects pool-level statistics and characteristics.

**Submitted Status** indicates that the loan is being processed or verified as part of a batch. The loan is in a review or processing stage. This status tells you that the loan is moving through verification or processing workflows. You typically need to wait for processing to complete before taking further actions.

**Verified Status** indicates that the loan has passed verification and meets quality standards. The loan can proceed to tokenization or other next stages. This status tells you that the loan is ready for further processing. The loan has met quality and compliance requirements.

**Minted Status** indicates that the loan has been tokenized and an NFT has been created. The loan is now represented on the blockchain. This status tells you that tokenization is complete and the loan is ready for blockchain-based transactions. The loan is fully tokenized and ready for blockchain operations.

**Removed Status** indicates that the loan has been excluded from pool calculations, likely due to data quality issues, not meeting pool criteria, or errors needing correction. The loan remains visible for tracking but doesn't affect pool metrics. This status tells you that the loan is temporarily or permanently excluded from calculations. You can track removed loans and reinstate them when appropriate.

**Reinstated Status** indicates that a previously removed loan has been put back into the pool. The loan is included in calculations again and fully participates in the pool. This status tells you that issues have been resolved and the loan is active again. The loan fully contributes to pool metrics and characteristics.

Understanding loan lifecycle and statuses helps you track where loans are in the process, know what actions are available, understand why certain actions are disabled, manage loans effectively throughout the structured finance workflow, and work efficiently within the loan management system.
