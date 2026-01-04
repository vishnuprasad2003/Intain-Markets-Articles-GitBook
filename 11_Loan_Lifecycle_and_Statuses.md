---
title: Loan Lifecycle and Statuses
description: Understand the different stages loans go through and what each status means
---

# Loan Lifecycle and Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Each status represents a specific stage in the loan's journey from upload to final state.

## Lifecycle Overview

Loans progress through a sequence: **Unmapped** when first uploaded (Status: "Unmapped", poolid: null/empty, loanPoolStatus: null/empty), **Mapped** when assigned to a pool (Status: "Mapped", loanPoolStatus: "Pending"), **Submitted** when included in a batch, **Verified** after verification, **Minted** if tokenization is required, and may be **Removed** from pool calculations if needed (loanPoolStatus: "Removed", loan remains in pool but excluded from calculations), with the option to be **Reinstated** later (loanPoolStatus: "Reinstated"). Loans also have a **Reconsider** status (loanPoolStatus: "Reconsider") when market makers or investors reject specific loans.

The lifecycle supports loan management—you upload loans, assign them to pools, they go through verification and processing, and they may be tokenized or removed as needed. Each stage has specific purposes and allows different types of actions.

## Status Meanings

**Unmapped** - The loan has been uploaded into the system but is not yet assigned to any pool. Status field: "Unmapped", poolid field: null or empty string, loanPoolStatus field: null or empty string. This is the initial stage where loans are available for mapping. Loans in Unmapped status are available for assignment but don't contribute to any pool metrics. When loans are unmapped from pools, system clears poolid field, sets Status to "Unmapped", clears loanPoolStatus field, and recalculates pool metrics via CalculateNoofLoansAndBalanceRefactored function.

**Mapped** - The loan has been assigned to a pool and is included in pool calculations. Status field: "Mapped", loanPoolStatus field: "Pending", poolid field: poolId. System updates loan via mapLoansToPoolRefactored function: sets poolid to poolId, sets Status to "Mapped", sets loanPoolStatus to "Pending", pushes loan data to PostgreSQL via postgresDataPush function, recalculates pool metrics via CalculateNoofLoansAndBalanceRefactored function. The loan contributes to pool metrics and characteristics. Loans in Mapped status are actively participating in pools and affecting pool-level statistics.

**Submitted** - The loan has been included in a batch for verification or other processing. The loan is being reviewed or processed. Loans in Submitted status are moving through verification or processing workflows.

**Verified** - The loan has been verified and can proceed to next stages such as tokenization. The loan meets quality and compliance requirements. Loans in Verified status have passed verification and are ready for further processing.

**Minted** - An NFT (non-fungible token) has been created for the loan, and the loan is tokenized. This status only applies if tokenization is part of your workflow. Loans in Minted status are represented on the blockchain and ready for blockchain-based transactions.

**Removed** - The loan has been removed from pool calculations but remains visible in the pool. loanPoolStatus field: "Removed", Status field remains "Mapped", poolid field remains set (loan stays in pool). System updates loan via updatePreviewLoanStatus function: sets loanPoolStatus to "Removed", recalculates pool metrics via CalculateNoofLoansAndBalanceRefactored function (excludes removed loan), deletes loan from PostgreSQL via deleteLoansFromPoolInPostgres function. The loan is excluded from metrics but can be tracked. Loans in Removed status are temporarily or permanently excluded from pool calculations.

**Reinstated** - A previously removed loan has been put back into the pool and is included in calculations again. loanPoolStatus field: "Reinstated", Status field remains "Mapped", poolid field remains set. System updates loan via updatePreviewLoanStatus function: sets loanPoolStatus to "Reinstated", recalculates pool metrics via CalculateNoofLoansAndBalanceRefactored function (includes reinstated loan). The loan fully participates in the pool. Loans in Reinstated status have been restored to active participation in pools.

## What Each Status Indicates

**Unmapped Status** indicates that the loan is available for assignment but hasn't been mapped to a pool yet. You can map it to a pool, edit information if allowed, or manage it independently.

**Mapped Status** indicates that the loan is part of a pool and contributing to pool calculations. Pool metrics include this loan, and you can unmap it if needed.

**Submitted Status** indicates that the loan is being processed or verified as part of a batch. You typically need to wait for processing to complete before taking further actions.

**Verified Status** indicates that the loan has passed verification and meets quality standards. The loan can proceed to tokenization or other next stages.

**Minted Status** indicates that the loan has been tokenized and an NFT has been created. The loan is now represented on the blockchain.

**Removed Status** indicates that the loan has been excluded from pool calculations, likely due to data quality issues, not meeting pool criteria, or errors needing correction. The loan remains visible for tracking but doesn't affect pool metrics.

**Reinstated Status** indicates that a previously removed loan has been put back into the pool. The loan is included in calculations again and fully participates in the pool.
