# Funding & Approval Questions

## Overview

This guide answers common questions about credit facilities, funding requests, approvals, and the funding process. These FAQs help you understand the funding workflow.

## Term Sheet Questions

### Q: How long does term sheet review take?

**A:** Review time varies depending on facility agent workload and complexity. There's no fixed timeframe, but facility agents typically review promptly. You'll receive notifications when status changes.

---

### Q: What happens if my term sheet is rejected?

**A:** If rejected, the term sheet enters a final state. No master commitment is created. You can create a new term sheet to try again, addressing the issues that led to rejection.

---

### Q: Can I withdraw a term sheet after submitting?

**A:** Once submitted (FAReview status), you typically cannot withdraw. However, if the facility agent requests changes, you can edit and resubmit, or the term sheet may be rejected if you prefer not to proceed.

---

### Q: Do I need to re-sign if changes are requested?

**A:** Usually yes. When changes are requested, the DocuSign status may reset, requiring you to sign again after making changes. The system will indicate if re-signing is needed.

---

## Master Commitment Questions

### Q: Why was a master commitment created automatically?

**A:** Master commitments are automatically created when a term sheet is approved (via `POST /cf/acceptTermSheet/:termSheetId`):
- **Trigger**: Term sheet status changes to `'Accepted'`
- **Function**: System automatically calls `autoCreateMasterCommitment(termSheet, masterCommitmentId)` function
- **Database**: Creates document in `cf_master_commitments` collection with `status: 'DRAFT'`
- **Pre-population**: Pre-populates read-only fields from term sheet (`advanceRate`, `margin`, `pricingIndex`, etc.)
- **Empty fields**: Leaves facility agent-editable fields empty (`collateralRules: []`, `lenderGroups: []`, etc.)
- **No manual creation**: Cannot create via API - only auto-generated, no `POST /cf/createMasterCommitment` endpoint for manual creation (only for submitting to lenders)

---

### Q: How long does lender approval take?

**A:** Lender approval time varies. Lenders review at their own pace. Any lender approval activates the facility, so it depends on when the first lender approves. You'll be notified when the facility becomes ACTIVE.

---

### Q: What if no lender approves the master commitment?

**A:** The master commitment remains in PendingLenderApproval status. The facility agent may need to follow up with lenders or the facility may not proceed. Contact the facility agent if concerned about approval timing.

---

### Q: Can I see which lenders have approved?

**A:** Yes, you can typically see lender approval status in the master commitment details. Each lender's approval status is tracked individually, showing who has approved and when.

---

## Funding Request Questions

### Q: How much can I request in a funding request?

**A:** You can request up to the available borrowing capacity. The system shows available capacity, and you cannot request more than what's available based on the borrowing base calculation.

---

### Q: Can I create multiple funding requests?

**A:** Yes, you can create multiple funding requests against an active facility, as long as you don't exceed total facility limits and available borrowing capacity.

---

### Q: What happens if my funding request is rejected?

**A:** If rejected, no funding notice is created and the drawdown doesn't proceed. You can create a new funding request, potentially addressing the issues that led to rejection (like requesting a smaller amount if capacity was the issue).

---

### Q: How quickly will I receive funds after approval?

**A:** After funding request approval, the process involves token generation, facility agent signing, borrower token approval, lender review and approval, and fund transfers. Timing depends on how quickly each step completes. Lenders transfer funds after they approve.

---

## Funding Notice Questions

### Q: Why do I need to approve token transfer?

**A:** Borrower token approval enables lender visibility. Until you approve, lenders cannot see the funding notice. Approval authorizes the token transfer and makes the notice visible to lenders for their review.

---

### Q: What are FT tokens?

**A:** FT (Fungible Token) tokens represent the drawdown amount on the blockchain. They enable transparent tracking and distribution to lenders. Tokens are created for the borrower and then distributed to lenders based on their participation.

---

### Q: Why does the facility agent sign for each lender separately?

**A:** Each lender has a separate DocuSign envelope for the funding notice. This allows individual tracking of each lender's e-signature status and maintains clear records for each lender's participation.

---

### Q: Can I see which lenders have approved the funding notice?

**A:** Yes, you can see individual lender approval status in the funding notice details. Each lender's decision (APPROVED or REJECTED) is tracked separately in the token distribution array.

---

## Approval Process Questions

### Q: Why do I need to wait for approval?

**A:** Approvals ensure quality, compliance, and risk management. They protect all parties and ensure proper review before commitments are made. The approval process maintains standards and controls risk.

---

### Q: What if I disagree with a rejection?

**A:** Rejections are typically final decisions. However, you can:
- Review the rejection reason
- Create a new submission addressing issues
- Contact the reviewer for clarification
- Improve your submission for next time

---

### Q: How many times can changes be requested?

**A:** There's no fixed limit. The process can iterate multiple times until the item is approved or rejected. However, excessive iterations may indicate fundamental issues that need to be addressed.

---

### Q: Can I speed up the approval process?

**A:** You can:
- Submit complete, accurate information
- Provide all required documentation
- Respond promptly to change requests
- Ensure compliance with requirements
- Communicate clearly with reviewers

---

## Token Questions

### Q: What happens to tokens after I approve transfer?

**A:** After you approve token transfer, the funding notice becomes visible to lenders. Lenders can then review and approve the drawdown. Tokens are distributed to lenders based on their participation when they approve.

---

### Q: Can I see token IDs?

**A:** Yes, token IDs are typically visible in funding notice details and token distribution information. They enable tracking and provide blockchain references for audit purposes.

---

### Q: What if tokens aren't generated?

**A:** Contact the facility agent. Token generation is done by the facility agent via the `updateTokenDistribution` API. If tokens aren't generated, the facility agent needs to complete this step.

---

## Lender Questions

### Q: Do all lenders need to approve?

**A:** 
- **Master Commitments**: Any one lender approval activates the facility (via `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign`). When any lender in `lenderGroups` array approves, status changes from `'PendingLenderApproval'` to `'ACTIVE'`. Other lenders can still approve (for their own tracking), but facility is already ACTIVE.
- **Funding Notices**: Each lender makes their own decision independently (via `PATCH /cf/funding-notices/:fundingNoticeId/:lenderOrgId/status`). Some may approve (`lenderApprovalStatus: 'APPROVED'`), others may reject (`lenderApprovalStatus: 'REJECTED'`). Each lender's participation tracked separately in `tokenDistribution` array. One lender's decision doesn't affect others - each lender's `lenderApprovalStatus` is independent.

---

### Q: What if I reject a funding notice?

**A:** If you reject, you won't participate in that drawdown. Your portion won't be funded. Other lenders can still approve and participate. Your rejection doesn't affect other lenders' decisions.

---

### Q: When do I transfer funds?

**A:** After you approve a funding notice, you transfer funds to the borrower. Then you confirm the fund transfer in the system, which updates your status to show transfer is complete.

---

## Best Practices

1. **Complete submissions**: Provide all required information
2. **Respond promptly**: Address change requests quickly
3. **Monitor status**: Track approval progress
4. **Communicate clearly**: Maintain good communication
5. **Be patient**: Allow time for proper review

---

## Key Takeaways

1. **Approvals ensure quality**: Review process maintains standards
2. **Multiple steps**: Funding involves several approval steps
3. **Individual decisions**: Lenders decide independently
4. **Complete process**: From request to fund transfer
5. **Transparency**: All steps tracked and visible

These funding and approval questions cover typical concerns. For specific issues, check relevant documentation or contact support.
