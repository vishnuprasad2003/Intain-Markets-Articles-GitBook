---
title: Loan Rejection and Reinstatement
description: Learn how loan removal requests work and how issuers handle them
---

# Loan Rejection and Reinstatement

## Overview

When pools are shared with market makers and investors, they can request removal of specific loans they believe shouldn't be in the pool. The issuer then decides whether to accept or reject these removal requests. This process allows collaborative pool refinement while keeping the issuer in control of pool composition.

## How Loan Rejection Works

**Market Maker / Investor Requests Removal**

When a market maker or investor reviews a pool and believes a loan should be removed, they can request removal by clicking the **cross icon** next to that loan in the Loans tab of the pool details page.

- The removal request is sent to the issuer
- The market maker/investor sees the loan status change to **Under Reconsider**
- The loan remains in pool calculations until the issuer makes a decision

![Loan Rejection Request - From Market Maker](imagesByMdFilesFolder/12/Loan_Rejection_Request_From_MarketMaker.png)

**Issuer Reviews the Request**

The issuer sees the loan with **Reconsider** status in the Loans tab. Two action icons appear next to that loan:

- **Tick icon**: Accept the removal request (loan will be removed)
- **Cross icon**: Reject the removal request (loan stays in pool)

## Possible Outcomes

### Removal Accepted (Tick Icon)

When the issuer clicks the **tick icon**, accepting the removal request:

**What Happens:**
- The loan status changes to **Removed**
- The loan is excluded from pool calculations
- Pool metrics recalculate automatically (total balance decreases, loan count decreases)
- The loan remains visible in the pool list for tracking purposes
- Both issuer and market maker/investor see the loan as "Removed"

**What This Means:**
- The loan no longer contributes to pool metrics
- The pool composition has been adjusted based on feedback
- The loan is still tracked but not counted in calculations
- The loan can potentially be reinstated later if needed

### Removal Rejected (Cross Icon)

When the issuer clicks the **cross icon**, rejecting the removal request:

**What Happens:**
- The loan remains in the pool
- The loan status returns to normal (Accepted/Mapped)
- Pool calculations continue to include this loan
- The market maker/investor is informed the request was rejected

**What This Means:**
- The issuer has decided to keep the loan in the pool
- Pool composition remains unchanged
- The loan continues to contribute to pool metrics

## Reinstatement

If a removed loan needs to be added back to the pool, the issuer can reinstate it.

**What Happens When Reinstated:**
- The loan status changes from **Removed** to **Reinstated**
- The loan is included in pool calculations again
- Pool metrics recalculate automatically (total balance increases, loan count increases)
- The loan fully participates in the pool

**When to Reinstate:**
- Issues that caused removal have been resolved
- Pool requirements have changed
- The loan was removed in error
- Circumstances have changed and the loan should be included

## Next Steps for Users

### For Market Makers / Investors (Requesting Removal)

1. **Identify Loans for Removal**
   - Review the loans in the pool's Loans tab
   - Identify loans you believe should not be in the pool
   - Consider your reasoning (data quality, criteria mismatch, risk concerns)

2. **Submit Removal Request**
   - Click the **cross icon** next to the loan you want removed
   - The request is sent to the issuer
   - The loan shows as "Under Reconsider" in your view

3. **Wait for Issuer Decision**
   - The issuer reviews your request
   - You will see the outcome: either "Removed" (accepted) or the loan returns to normal status (rejected)

4. **Continue Review**
   - If accepted, pool metrics update to exclude the loan
   - If rejected, the loan remains in the pool
   - You can provide feedback through the chat box if you want to discuss further

### For Issuers (Handling Removal Requests)

1. **Review the Request**
   - Go to the pool's Loans tab
   - Look for loans with "Reconsider" status
   - Understand why the removal was requested (check feedback/comments)

2. **Make Your Decision**
   - Click **tick icon** to accept: Loan is removed from calculations
   - Click **cross icon** to reject: Loan stays in pool

3. **After Accepting Removal**
   - Verify pool metrics updated correctly
   - Consider if the loan should be fixed and reinstated later
   - Track removed loans for record-keeping

4. **After Rejecting Removal**
   - Consider providing feedback explaining your decision
   - The loan continues to be part of the pool
   - Address any underlying concerns through the feedback mechanism

5. **Reinstatement (When Needed)**
   - If issues are resolved, you can reinstate removed loans
   - Pool metrics will update to include the reinstated loan
   - The loan returns to full participation in the pool

## Important Notes

**Issuer Has Final Say** - The issuer decides whether to accept or reject removal requests. Market makers and investors can request, but the issuer controls pool composition.

**Automatic Metric Updates** - Pool metrics recalculate automatically when loans are removed or reinstated. You don't need to manually update anything.

**Loans Remain Visible** - Removed loans stay visible in the pool list with "Removed" status. This maintains a complete record of what happened.

**Feedback for Communication** - Use the chat box icon in the Loans tab to communicate about specific loans. This provides context for removal requests and decisions.

**Reinstatement Is Possible** - Removal is not permanent. Loans can be reinstated when appropriate.

**All Actions Are Tracked** - Removal requests, decisions, and reinstatements are recorded for audit purposes.
