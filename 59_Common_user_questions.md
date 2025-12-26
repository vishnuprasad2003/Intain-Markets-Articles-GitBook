# Common User Questions

## Overview

This guide answers common questions users have about pools, loans, and general platform usage. These FAQs help you quickly find answers to typical questions.

## Pool Questions

### Q: Can I edit a pool after sharing it?

**A:** Yes, you can usually edit pools in Preview status. However, once a pool reaches Deal status, editing is typically restricted. Check the pool status to see what editing options are available.

---

### Q: How many loans can I add to a pool?

**A:** There's no specific limit on the number of loans you can add to a pool. Add as many loans as needed for your transaction. The system will calculate metrics automatically.

---

### Q: What happens if I remove a loan from a pool?

**A:** When you remove a loan (via `GET /updateLoanStatus` with `loanPoolStatus: 'Removed'`), it's excluded from pool calculations:
- **MongoDB calculations**: `numberofloans`, `originalbalance`, `currentbalance` in `pool_detail` collection updated immediately via `CalculateNoofLoansAndBalanceRefactored()` function
- **PostgreSQL analytics**: Loan deleted from `poolloantape` table via `deleteLoansFromPoolInPostgres()` function, WAC, FICO, LTV, DTI/DSCR calculations exclude removed loans
- The loan status changes to `'Removed'` (`loanPoolStatus: 'Removed'` in `previewstdloantape` collection) but remains visible in database
- You can reinstate it later (via `GET /updateLoanStatus` with `loanPoolStatus: ''` (empty string)) - but may need manual PostgreSQL sync for analytics to include it again

---

### Q: Can I share a pool with multiple market makers?

**A:** This depends on system configuration. Typically, you can share with multiple parties, but only one market maker can accept a mandate at a time. Check sharing options for your specific situation.

---

### Q: How do I know if my pool is ready to share?

**A:** Your pool is ready when:
- All required information is filled
- Loans are mapped (if applicable)
- Metrics look accurate
- Documents are uploaded
- You're satisfied with the pool

---

## Loan Questions

### Q: Can a loan be in multiple pools?

**A:** No, a loan belongs to one pool at a time. To move a loan to another pool, you must first remove it from the current pool, then map it to the new pool.

---

### Q: What's the difference between unmapped and mapped loans?

**A:** 
- **Unmapped**: Loan exists in system but not assigned to any pool
- **Mapped**: Loan is assigned to a specific pool and included in pool calculations

---

### Q: Can I delete a loan?

**A:** You can usually delete unmapped loans that haven't been verified. Once a loan is verified or mapped to a pool, deletion may be restricted. Check loan status to see deletion options.

---

### Q: What does "Reconsider" status mean for a loan?

**A:** "Reconsider" means the loan needs review. It may have issues identified or need attention. You can review the loan, address issues, and either return it to normal status or remove it from the pool.

---

### Q: How do I know if a loan is verified?

**A:** Check the `verificationSource` field in `previewstdloantape` collection:
- **`'No'`**: Loan not verified yet (initial state)
- **`'Self Certified'`**: Loan verified by issuer via batch self-certification (via `POST /batch/self-certify`)
- **`'Certified'`**: Loan verified by Verification Agent (VA) via batch verification (via `POST /batch/verify`)
- **`'Self Certified (Data Only)'`**: Loan self-certified via e-signature (DocuSign/ZohoSign completion updates this)
- Also check `workflow_status` field: `'VERIFIED'` means verification complete, `'SUBMITTED'` means submitted for verification, `'STANDARDISED'` means processed but not verified

---

## General Platform Questions

### Q: How do I switch between roles?

**A:** Log out and log back in with a different role. Each role has its own view and permissions. You select your role during login.

---

### Q: Why are some buttons disabled?

**A:** Buttons are disabled when:
- Wrong status for the action
- Missing required information
- Waiting for another party to act
- You don't have permission
- Action already completed

Hover over disabled buttons to see tooltips explaining why.

---

### Q: How do I know what status my item is in?

**A:** Status is displayed prominently on item details pages. Look for status badges, labels, or status sections. Status history shows all status changes.

---

### Q: Can I undo an action?

**A:** Most actions cannot be undone once completed. However, some statuses allow editing (like Draft or CHANGES_REQUESTED). Check the item status to see if editing is available.

---

### Q: How do I get help if I'm stuck?

**A:** 
- Check tooltips and help text
- Review status messages
- Read relevant documentation
- Contact support
- Check FAQs and troubleshooting guides

---

## Status Questions

### Q: Why did my status change unexpectedly?

**A:** Some status changes are automatic (like when DocuSign completes or when approvals trigger next steps). Check notifications and status history to see who or what changed the status and why.

---

### Q: Can I change a status back?

**A:** Usually not. Statuses typically progress forward. Some statuses allow limited backward movement (like Mandate Pending → Preview if rejected), but most status changes are one-way.

---

### Q: What does "Pending" mean?

**A:** "Pending" means waiting for action. Something needs to happen before the item can proceed. Check who needs to act and what action is needed.

---

## Sharing and Collaboration Questions

### Q: Who can see my pools?

**A:** 
- **Created status**: Only you (the issuer)
- **Preview status**: You and organizations you've shared with
- **Mandate Pending**: You and the market maker reviewing
- **Deal status**: All relevant parties

---

### Q: Can I stop sharing a pool?

**A:** Usually yes, if the pool status allows it. You can typically remove sharing with specific organizations. However, some sharing may be required for workflow progression.

---

### Q: How do I know who has viewed my pool?

**A:** Check the sharing section of your pool. Many systems show view activity, including who viewed and when. Look for activity tracking or view history.

---

## Troubleshooting Questions

### Q: Why can't I submit my term sheet?

**A:** Common reasons:
- Status is not BorrowerSigned (must sign first)
- Required fields not filled
- Documents not uploaded
- Validation errors present

Check status and validation messages.

---

### Q: Why can't I create a funding request?

**A:** Common reasons:
- Master commitment is not ACTIVE
- Facility not operational
- No available borrowing capacity
- Missing required information

Check master commitment status and facility availability.

---

### Q: Why is my pool not visible to investors?

**A:** Common reasons:
- Pool is not in Preview status
- Pool hasn't been shared with investors
- Sharing permissions not set correctly
- Investors not logged in with correct role

Check pool status and sharing settings.

---

## Key Takeaways

1. **Check status first**: Many questions relate to status
2. **Read messages**: Status messages explain situations
3. **Check permissions**: Verify you have permission
4. **Review history**: Status history shows what happened
5. **Contact support**: Ask for help when needed

These common questions cover typical user concerns. For specific issues, check relevant documentation or contact support.
