---
title: Loan Rejection and Reinstatement
description: Learn how to remove loans from pools and put them back when needed
---

# Loan Rejection and Reinstatement

## Overview

Sometimes loans need to be removed from pools temporarily or permanently, and later reinstated when appropriate. Understanding loan rejection and reinstatement helps you maintain pool quality, address data issues, and adjust pool composition as needed. This process allows you to manage pool composition flexibly while maintaining data integrity and ensuring pools meet quality standards.

## Possible Outcomes

When you remove a loan from a pool, the loan enters a "Removed" status. When you reinstate a loan, it returns to active participation in the pool. These are the two main outcomes for loan status management within pools. Understanding these outcomes helps you know what happens when you remove or reinstate loans and how these actions affect pool metrics and composition.

## What Each Outcome Means

**Removed Status** means the loan has been excluded from pool calculations but remains visible in the pool for tracking purposes. Pool metrics automatically recalculate to exclude the removed loan—total balance decreases, loan count decreases, and weighted averages recalculate without the removed loan. The loan is still visible in the pool list but marked as removed, allowing you to track what was excluded and why. This status is useful when loans don't meet pool criteria, have data quality issues, need correction, or when pool requirements change. Removed loans don't affect pool metrics but remain visible for audit and tracking purposes.

![Loan Rejection Request - From Market Maker](imagesByMdFilesFolder/12/Loan_Rejection_Request_From_MarketMaker.png)

**Reinstated Status** means a previously removed loan has been put back into the pool and is included in calculations again. Pool metrics automatically recalculate to include the reinstated loan—total balance increases, loan count increases, and weighted averages recalculate with the reinstated loan included. The loan fully participates in the pool again, and you can track that it was reinstated. This status is useful when issues with removed loans have been resolved, data has been corrected, pool requirements change, or you decide to include loans that were removed earlier. Reinstated loans fully participate in pool metrics and calculations.

## Next Steps for Users

**After Removing a Loan** - Review the updated pool metrics to ensure they reflect the removal correctly. Verify that the loan shows as "Removed" in the pool list. If the loan was removed due to data issues, correct the data. If it was removed because it doesn't meet criteria, determine if criteria can be adjusted or if the loan should remain removed. Consider whether other loans should also be removed for similar reasons. Track why loans were removed for future reference and audit purposes.

**After Reinstating a Loan** - Review the updated pool metrics to ensure they reflect the reinstatement correctly. Verify that the loan shows as active in the pool list. Confirm that the issues that caused removal have been resolved. Ensure the loan now meets pool criteria and requirements. Consider whether the reinstated loan affects pool characteristics in ways that are acceptable. Verify that reinstatement improves pool quality and meets requirements.

**Ongoing Management** - Monitor removed loans to see if they can be reinstated later. Track why loans were removed to help with future pool management decisions. Use removal and reinstatement to maintain pool quality and ensure pools meet requirements. Keep records of removal and reinstatement decisions for audit purposes. Regularly review removed loans to determine if they can be reinstated or should remain removed.

Understanding loan rejection and reinstatement helps you manage pool composition effectively, maintain pool quality, address data issues, adjust pools as requirements change, and ensure pools meet quality standards throughout their lifecycle.
