---
title: Funding and Approval Questions
description: >-
  Frequently asked questions about the credit facility funding and approval
  process
---

# Funding & Approval Questions

## Overview

Answers to common questions about credit facility funding and approvals, plus a short comparison with asset sale settlement.

## Frequently Asked Questions

### Term sheets

**How do I create a term sheet?**

Open **Credit Facility**, click **Term Sheet Setup**, choose **Create Via Wizard**, enter the details, and click **Create Draft**.

→ [Term Sheet Submission](43_Term_Sheet_Submission.md)
**Do I need to sign the term sheet?**

Yes. Adobe Sign opens after Create Draft. You must finish the signature before you can submit to the facility agent.

→ [E-Signature Workflow](28_E-Signature_Workflow.md)
**Can I edit a term sheet after I submit it?**

No. In **Under Review** you cannot edit. You can edit again only if the facility agent requests changes (**Changes Requested**).

→ [Term Sheet Change Requests](19_Term_Sheet_Change_Requests.md)
**What happens when my term sheet is approved?**

A master commitment is created in **Draft**. The facility agent then configures the facility.

→ [Master Commitment Overview](20_Master_Commitment_Overview.md)
**What if my term sheet is rejected?**

You cannot send the same term sheet again. Create a new one.

→ [What Happens After Rejection](72_What_happens_after_rejection.md)
### Master commitments

**How is a master commitment created?**

It is created when a term sheet is approved. You cannot create one on your own.

→ [Master Commitment Overview](20_Master_Commitment_Overview.md)
**Who configures it?**

The facility agent adds lenders, sets the facility rules, and completes the required sections.

→ [Facility Creation](50_Facility_Creation.md)
**What are sub-facilities?**

On a multiple-branch commitment, sub-facilities let the facility agent assign different groups of lenders. Two sub-facilities cannot share the same lenders.

→ [Facility Creation](50_Facility_Creation.md)
**When does the facility become active?**

When any one lender approves and e-signs the master commitment.

→ [Facility Setup Status](22_Facility_Setup_Status.md)
### Deal modelling

**What is deal modelling?**

It is the facility agent’s setup of operating terms after the master commitment is **Active**. Borrowers cannot raise funding requests until it is finished.

→ [Deal Setup and Calculations](51_Deal_Setup_and_Calculations.md)
**Can I delegate deal modelling?**

Yes. The facility agent can click **Delegation** and ask an admin to finish it.

**Why can’t I raise a funding request?**

Check both of these:

1. The master commitment is **Active**.
2. Facility Setup Status is **Completed**.

### Funding requests

**What do I need to create a funding request?**

* An active master commitment
* Completed deal modelling
* Loans with NFTs mapped to the facility, when mapping is required
* Draw amount, funding date, purpose, and a collateral addendum

**Is a signature required to approve a funding request?**

No. The facility agent does not e-sign to approve the request.

**What happens after approval?**

A funding notice is created. The facility agent approves it and e-signs for each lender. A lender sees the notice after their signature is done, then sends funds.

**Can I resubmit a rejected funding request?**

No. Create a new funding request.

### Funding notices

**How is a funding notice created?**

It is created when a funding request is approved. You cannot create one on your own.

**What does E-sign (0/n) mean?**

The facility agent signs once for each lender. 0/n means none are signed. n/n means all are signed.

**When do lenders see the funding notice?**

After the facility agent approves the notice and completes the e-signature for that lender.

**How do lenders finish?**

Open the notice in **Credit Facility**, choose a payment method, send the funds, and click **Confirm and Settle**.

### Roles

**What are the role names in a credit facility?**

* Issuer is the **Borrower**
* Market Maker is the **Facility Agent**
* Investor is the **Lender**

**Where do lenders see facilities waiting for approval?**

In **Opportunities**.

**Where do lenders see approved facilities?**

In **Credit Facility**, along with funding notices.

### Asset sale settlement

**How does settlement work in an asset sale?**

Investors send funds to the issuer by bank wire. Both sides confirm the transfer on the platform. The platform then mints receivables NFTs and transfers them to investor wallets. See [Settlement and NFT Transfer](36_Settlement_and_NFT_Transfer.md).

**How is that different from credit facility funding?**

A credit facility draw is a request against an approved facility, reviewed by the facility agent. An asset sale settlement is a one-time purchase of loan assets. Both use signatures and approvals. The steps are different.
