---
title: Funding and Approval Questions
description: Frequently asked questions about credit facility funding and approvals
---

# Funding & Approval Questions

## Term Sheets

**How do I create a term sheet?**
Credit Facility → Term Sheet Setup → Create Via Wizard → fill in details → Create Draft.
→ [Term Sheet Submission](43_Term_Sheet_Submission.md)

**Do I need to sign it?**
Yes — Adobe Sign opens after Create Draft. Signature is required before submitting.

**Can I edit after submitting?**
No — only when the facility agent sets status to **Changes Requested**.

**Term sheet approved — what happens?**
A master commitment is created in **Draft** automatically.

**Term sheet rejected — what now?**
Create a new term sheet; the rejected one cannot be sent again.

---

## Master Commitments

**How is a master commitment created?**
Automatically when the facility agent approves a term sheet. Cannot be created manually.

**Who configures it?**
The facility agent adds lenders and completes all sections → **Create Facility**.

**When does the facility become Active?**
When any one lender approves and e-signs it.
→ [Master Commitment Statuses](21_Master_Commitment_Statuses.md)

---

## Deal Modelling

**What is deal modelling?**
Facility agent setup of operating terms (fees, interest, covenants, waterfall) after the master commitment is **Active**. Required before borrowers can raise funding requests.

**Can I delegate deal modelling?**
Yes — click **Delegation** in the deal modelling screen to let an admin finish it.

**Why can't I raise a funding request?**
Check: (1) master commitment is **Active**, and (2) Facility Setup Status is **Completed**.
→ [Facility Setup Status](22_Facility_Setup_Status.md)

---

## Funding Requests

**What do I need to create one?**
Active master commitment + Completed facility setup + draw amount, date, purpose, and collateral addendum.

**Is a signature required to approve a funding request?**
No — the facility agent approves without e-signing. Signatures apply on the funding notice.

**After approval — what happens?**
A funding notice is created. Facility agent approves it and e-signs for each lender. Lenders send funds and click Confirm and Settle.

**Can I resubmit a rejected funding request?**
No — create a new one.

---

## Funding Notices

**How is a funding notice created?**
Automatically when a funding request is approved.

**What does "E-sign (0/n)" mean?**
The facility agent signs once for each lender. 0/n = none signed yet; n/n = all signed.

**When do lenders see the notice?**
After the facility agent completes the e-signature for their portion.

**How do lenders finish?**
Review the notice → send funds by wire → fill in wire details → **Confirm and Settle**.
→ [Funds Transfer Confirmation](31_Funds_Transfer_Confirmation.md)

---

## Roles

**Role names in a credit facility:**
- Issuer = **Borrower**
- Market Maker = **Facility Agent**
- Investor = **Lender**

**Where do lenders approve a master commitment?**
In **Opportunities**.

→ [Roles in Credit Facilities](17_Roles_in_Credit_Facilities.md)
