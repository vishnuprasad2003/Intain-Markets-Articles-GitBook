---
title: Funding and Approval Questions
description: Frequently asked questions about the credit facility funding and approval process
---

# Funding and Approval Questions

## Overview

This guide answers common questions about the credit facility funding and approval process. Use this as a quick reference for understanding how different parts of the workflow operate.

## Term Sheet Questions

### Q: How do I create a term sheet?

Navigate to **Credit Facility** from the left menu, click **Term Sheet Setup** at the top right, select **Create Via Wizard**, fill in the details, and click **Create Draft**.

### Q: Do I need to sign the term sheet?

Yes. After clicking Create Draft, an Adobe Sign popup opens automatically. You must complete the electronic signature before you can submit to the facility agent.

### Q: Can I edit a term sheet after submitting?

No. Once submitted (FAReview status), you cannot edit. You can only edit if the facility agent requests changes (CHANGES_REQUESTED status).

### Q: What happens when my term sheet is approved?

A master commitment is automatically created with Draft status. The facility agent then configures the facility.

### Q: What if my term sheet is rejected?

Rejected term sheets cannot be resubmitted. You must create a new term sheet.

## Master Commitment Questions

### Q: How is a master commitment created?

Master commitments are automatically created when term sheets are approved. You cannot create them manually.

### Q: Who configures the master commitment?

The facility agent configures the master commitment by adding lenders, setting up facility rules, and completing all required sections.

### Q: What are sub-facilities?

For multiple-branch master commitments, sub-facilities allow the facility agent to assign different lender groups. Each sub-facility has its own lenders, and no two sub-facilities can have the same lenders.

### Q: When does the facility become active?

The facility becomes Active when any one lender approves and e-signs the master commitment.

## Deal Modelling Questions

### Q: What is deal modelling?

Deal modelling is when the facility agent configures operational parameters after the master commitment becomes Active. This must be completed before borrowers can raise funding requests.

### Q: Can I delegate deal modelling?

Yes. Facility agents can click the **Delegation** button to ask the admin to complete deal modelling on their behalf.

### Q: Why can't I raise a funding request?

Check if:
1. The master commitment is Active
2. Deal modelling is complete (Facility Setup Status: Completed)

You can only raise funding requests after both conditions are met.

## Funding Request Questions

### Q: What do I need to create a funding request?

You need:
- Active master commitment
- Completed deal modelling
- NFT-minted loans mapped to the facility (if required)
- Draw amount, funding date, purpose, and collateral addendum

### Q: Is e-signature required for funding requests?

No. Unlike term sheets, facility agents don't need to e-sign to approve funding requests.

### Q: What happens after my funding request is approved?

A funding notice is automatically generated. The facility agent approves it and e-signs for each lender individually. Each lender can see the notice once their e-sign is complete and can then transfer funds.

### Q: Can I resubmit a rejected funding request?

No. Rejected funding requests cannot be resubmitted. You must create a new funding request.

## Funding Notice Questions

### Q: How is a funding notice created?

Funding notices are automatically created when funding requests are approved. You cannot create them manually.

### Q: What does E-sign (0/n) mean?

The facility agent must e-sign the funding notice for each lender individually. The count shows progress (0/n means none signed, n/n means all signed).

### Q: When do lenders see the funding notice?

Lenders see funding notices after:
1. Facility agent approves the funding notice
2. Facility agent e-signs for each lender individually

### Q: How do lenders complete the process?

Lenders review the funding notice in their Credit Facility section, select a payment method, transfer funds, and click **Confirm and Settle**.

## Role-Related Questions

### Q: What are the role names in credit facility?

- Issuer → **Borrower**
- Market Maker → **Facility Agent**
- Investor → **Lender**

### Q: Where do lenders see pending facilities?

Lenders see master commitments awaiting approval in their **Opportunities** section from the left menu.

### Q: Where do lenders see approved facilities?

Lenders see approved facilities and funding notices in their **Credit Facility** section from the left menu.
