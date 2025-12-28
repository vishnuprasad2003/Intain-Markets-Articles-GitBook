---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where each loan is in the process, know what actions are available, and understand why certain actions are disabled. Each status represents a specific stage in the loan's journey from upload to final state.

## Lifecycle Overview

Loans typically start as **Unmapped** when first uploaded into the system, progress to **Mapped** when assigned to a pool, may move to **Submitted** when included in a batch, advance to **Verified** after verification, potentially reach **Minted** if tokenization is required, and may be **Removed** from pool calculations if needed, with the option to be **Reinstated** later. This progression ensures that loans move through proper stages with appropriate processing and validation at each step.

The lifecycle is designed to support loan management—you upload loans, assign them to pools, they go through verification and processing, and they may be tokenized or removed as needed. Each stage has specific purposes and allows different types of actions, ensuring that loans progress correctly through the structured finance workflow.

## Status Meanings

**Unmapped** - The loan has been uploaded into the system but is not yet assigned to any pool. This is the initial stage where loans are available for mapping.

**Mapped** - The loan has been assigned to a pool and is included in pool calculations. The loan contributes to pool metrics and characteristics.

**Submitted** - The loan has been included in a batch for verification or other processing. The loan is being reviewed or processed.

**Verified** - The loan has been verified and can proceed to next stages such as tokenization. The loan meets quality and compliance requirements.

**Minted** - An NFT (non-fungible token) has been created for the loan, and the loan is tokenized. This status only applies if tokenization is part of your workflow.

**Removed** - The loan has been removed from pool calculations but remains visible in the pool. The loan is excluded from metrics but can be tracked.

**Reinstated** - A previously removed loan has been put back into the pool and is included in calculations again. The loan fully participates in the pool.

## What Each Status Indicates

**Unmapped Status** indicates that the loan is available for assignment but hasn't been mapped to a pool yet. You can map it to a pool, edit information if allowed, or manage it independently. This status tells you that the loan is ready to be included in a pool.

**Mapped Status** indicates that the loan is part of a pool and contributing to pool calculations. Pool metrics include this loan, and you can unmap it if needed. This status tells you that the loan is actively participating in a pool.

**Submitted Status** indicates that the loan is being processed or verified as part of a batch. The loan is in a review or processing stage. This status tells you that the loan is moving through verification or processing workflows.

**Verified Status** indicates that the loan has passed verification and meets quality standards. The loan can proceed to tokenization or other next stages. This status tells you that the loan is ready for further processing.

**Minted Status** indicates that the loan has been tokenized and an NFT has been created. The loan is now represented on the blockchain. This status tells you that tokenization is complete and the loan is ready for blockchain-based transactions.

**Removed Status** indicates that the loan has been excluded from pool calculations, likely due to data quality issues, not meeting pool criteria, or errors needing correction. The loan remains visible for tracking but doesn't affect pool metrics. This status tells you that the loan is temporarily or permanently excluded from calculations.

**Reinstated Status** indicates that a previously removed loan has been put back into the pool. The loan is included in calculations again and fully participates in the pool. This status tells you that issues have been resolved and the loan is active again.

Understanding loan lifecycle and statuses helps you track where loans are in the process, know what actions are available, understand why certain actions are disabled, and manage loans effectively throughout the structured finance workflow.
