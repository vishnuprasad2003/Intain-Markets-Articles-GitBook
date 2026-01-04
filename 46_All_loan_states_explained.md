---
title: All Loan States Explained
description: Understand all possible loan statuses and what each means
---

# All Loan States Explained

## Overview

This comprehensive reference guide explains all possible loan statuses across different status fields. Loans have multiple status fields that track different aspects of their lifecycle, including mapping status, workflow status, and pool status.

## Lifecycle Overview

Loans progress through multiple status dimensions: they start as **Unmapped** when uploaded, move to **Mapped** when assigned to a pool, may progress through **Submitted** and **Verified** during processing, potentially reach **Minted** if tokenization is required, and may be **Removed** from pool calculations if needed, with the option to be **Reinstated** later. This progression ensures that loans move through proper stages with appropriate processing and validation at each step.

The lifecycle supports loan management—you upload loans, assign them to pools, they go through verification and processing, and they may be tokenized or removed as needed. Each stage has specific purposes and allows different types of actions.

## Status Meanings

**Unmapped** - The loan has been uploaded into the system but is not yet assigned to any pool. This is the initial stage where loans are available for mapping. Loans in Unmapped status are available for assignment but don't contribute to any pool metrics.

**Mapped** - The loan has been assigned to a pool and is included in pool calculations. The loan contributes to pool metrics and characteristics. Loans in Mapped status are actively participating in pools and affecting pool-level statistics.

**Submitted** - The loan has been included in a batch for verification or other processing. The loan is being reviewed or processed. Loans in Submitted status are moving through verification or processing workflows.

**Verified** - The loan has been verified and can proceed to next stages such as tokenization. The loan meets quality and compliance requirements. Loans in Verified status have passed verification and are ready for further processing.

**Minted** - An NFT (non-fungible token) has been created for the loan, and the loan is tokenized. This status only applies if tokenization is part of your workflow. Loans in Minted status are represented on the blockchain and ready for blockchain-based transactions.

**Removed** - The loan has been removed from pool calculations but remains visible in the pool. The loan is excluded from metrics but can be tracked. Loans in Removed status are temporarily or permanently excluded from pool calculations.

**Reinstated** - A previously removed loan has been put back into the pool and is included in calculations again. The loan fully participates in the pool. Loans in Reinstated status have been restored to active participation in pools.

## What Each Status Indicates

**Unmapped Status** indicates that the loan is available for assignment but hasn't been mapped to a pool yet. You can map it to a pool, edit information if allowed, or manage it independently.

**Mapped Status** indicates that the loan is part of a pool and contributing to pool calculations. Pool metrics include this loan, and you can unmap it if needed.

**Submitted Status** indicates that the loan is being processed or verified as part of a batch. You typically need to wait for processing to complete before taking further actions.

**Verified Status** indicates that the loan has passed verification and meets quality standards. The loan can proceed to tokenization or other next stages.

**Minted Status** indicates that the loan has been tokenized and an NFT has been created. The loan is now represented on the blockchain.

**Removed Status** indicates that the loan has been excluded from pool calculations, likely due to data quality issues, not meeting pool criteria, or errors needing correction. The loan remains visible for tracking but doesn't affect pool metrics.

**Reinstated Status** indicates that a previously removed loan has been put back into the pool. The loan is included in calculations again and fully participates in the pool.
