---
title: Funding and Approval Questions
description: Frequently asked questions about credit facility funding and approvals
---

# Funding & Approval Questions

## Term Sheets

**Q1. How do I create a term sheet?**
Credit Facility → Term Sheet Setup → Create Via Wizard → fill in details → Create Draft. Adobe Sign opens automatically; signature is required before submitting.
→ See [Term Sheet Submission](43_Term_Sheet_Submission.md)

**Q2. Do I need to sign the term sheet?**
Yes — Adobe Sign opens after Create Draft. You must sign before the **Submit to FA** button becomes available.
→ See [Term Sheet Workflow](18_Term_Sheet_Workflow.md)

**Q3. Can I edit after submitting?**
No — the term sheet is locked while **In review**. You can only edit when the facility agent sets status to **Changes Requested**.
→ See [Term Sheet Workflow](18_Term_Sheet_Workflow.md)

**Q4. What happens after the term sheet is approved?**
A master commitment is created automatically in **Draft** status. The facility agent then configures it and adds lenders.
→ See [Master Commitment Overview](20_Master_Commitment_Overview.md)

**Q5. What do I do if the term sheet is rejected?**
Create a new term sheet; the rejected one cannot be sent again. Use the rejection comments to address the issues before resubmitting.
→ See [What Happens After Rejection](72_What_happens_after_rejection.md)

---

## Master Commitments

**Q6. How is a master commitment created?**
Automatically when the facility agent approves a term sheet. You cannot create one manually.
→ See [Master Commitment Overview](20_Master_Commitment_Overview.md)

**Q7. Who configures the master commitment?**
The facility agent adds lenders and completes all sections → **Create Facility**. Borrowers cannot configure it.
→ See [Facility Creation](50_Facility_Creation.md)

**Q8. When does the facility become Active?**
When any one lender approves and e-signs it. Other lenders can approve later; each is tracked independently.
→ See [Master Commitment Statuses](21_Master_Commitment_Statuses.md)

---

## Deal Modelling

**Q9. What is deal modelling?**
Facility agent setup of operating terms (fees, interest, covenants, waterfall) after the master commitment is **Active**. Required before borrowers can raise funding requests.
→ See [Facility Setup Status](22_Facility_Setup_Status.md)

**Q10. Can I delegate deal modelling?**
Yes — click **Delegation** in the deal modelling screen to let an admin finish it. Delegation is only available while Facility Setup Status is **In Progress**.
→ See [Facility Setup Status](22_Facility_Setup_Status.md)

**Q11. Why can't I raise a funding request?**
Check two things: (1) master commitment must be **Active**, and (2) Facility Setup Status must be **Completed**. Both conditions must be met.
→ See [Facility Setup Status](22_Facility_Setup_Status.md)

---

## Funding Requests

**Q12. What do I need to create a funding request?**
Active master commitment + Completed facility setup + draw amount, date, purpose, and collateral addendum document.
→ See [Funding Requests](44_Funding_Requests.md)

**Q13. Is a signature required to approve a funding request?**
No — the facility agent approves without e-signing. Signatures apply on the funding notice, not the funding request.
→ See [Funding Request Review (Facility Agent)](54_Funding_Request_Review_MM.md)

**Q14. What happens after a funding request is approved?**
A funding notice is created automatically. The facility agent approves it and e-signs for each lender. Lenders then see the notice, send funds, and click Confirm and Settle.
→ See [Funding Notices Overview](26_Funding_Notices_Overview.md)

**Q15. Can I resubmit a rejected funding request?**
No — create a new funding request. The rejected one is final and cannot be reopened.
→ See [Funding Request Outcomes](25_Funding_Request_Outcomes.md)

---

## Funding Notices

**Q16. How is a funding notice created?**
Automatically when a funding request is approved. You cannot create one manually.
→ See [Funding Notices Overview](26_Funding_Notices_Overview.md)

**Q17. What does "E-sign (0/n)" mean?**
The facility agent signs once for each lender. 0/n = none signed yet; n/n = all signed. A lender can only see and act on the notice after the facility agent signs for their portion.
→ See [E-Signature Workflow](28_E-Signature_Workflow.md)

**Q18. When do lenders see the notice?**
After the facility agent completes the e-signature for their specific portion. Each lender is handled independently.
→ See [Funding Notice Review](59_Funding_Notice_Review.md)

**Q19. How do lenders complete settlement?**
Review the notice → send funds by wire → fill in wire details → **Confirm and Settle**.
→ See [Funds Transfer Confirmation](31_Funds_Transfer_Confirmation.md)

---

## Roles

**Q20. What are the role names in a credit facility?**
Platform role names differ in the credit facility context:
- Issuer = **Borrower**
- Underwriter / Facility Agent = **Facility Agent**
- Investor = **Lender**
→ See [Roles in Credit Facilities](17_Roles_in_Credit_Facilities.md)

**Q21. Where do lenders approve a master commitment?**
In **Opportunities**. Lenders see pending master commitments there and click **Approve & E-Sign**.
→ See [Facility Approval](58_Facility_Approval.md)
