---
title: Common User Questions
description: Answers to frequently asked questions about Intain Markets platform usage
---

# Common User Questions

## Overview

This guide answers common questions about using Intain Markets.

## Pool Questions

**Q: How do I create a pool?**

A: Navigate to Pools from the left menu, click **Set-up Pool** button at top right, fill in the pool details (name, asset class, transaction type, organizations to share with), and click **Create**.

**Q: Can I edit a pool after creating it?**

A: Yes, you can edit pools while in Created status. Click **Edit** button at top right of pool details. Once shared (Preview status) or in Deal status, some editing is restricted.

**Q: How do I add loans to a pool?**

A: Go to **Loan Registry** from the left menu, select the loans you want to add, click **Map to Pool**, and select the pool from the dropdown.

**Q: What do the tick and cross icons mean on loans?**

A: When a market maker or investor requests loan removal, the tick and cross appear. **Tick** = accept the removal request (loan marked as Removed). **Cross** = reject the removal request (loan stays in pool).

**Q: How do I share a pool?**

A: Click the **Share** button at top right of pool details, select recipient type (Market Maker, Investor, Rating Agency), select organizations, set permissions (feedback, download), and share.

## Loan Questions

**Q: How do I upload loans?**

A: Go to **Imports** from the left menu, select as of date, select asset class, choose file, and click **Submit**. The file is uploaded and a job is created.

**Q: What is Trigger LTS?**

A: LTS (Loan Tape Standardization) maps your loan file columns to Intain standard fields. Click **Trigger LTS** to start the mapping process. You can use Basic or Intelligent AI mapping.

**Q: What's the difference between Mapped and Unmapped status?**

A: **Mapped** = loan is assigned to a pool. **Unmapped** = loan exists but is not assigned to any pool. The Status column in Loan Registry shows this.

**Q: How do I verify loans?**

A: Add loans to a batch from Loan Registry, go to **Batch Verification**, enter the batch, and either Self Certify or submit to a verification agent. After verification, batch status changes to Reviewed.

**Q: When can I mint NFTs?**

A: After batch verification is complete (status: Reviewed). Go to **Certificates**, find the batch, and click **Mint NFT**. Select loans and click **Mint Selected**.

## Credit Facility Questions

**Q: How do I create a term sheet?**

A: Go to **Credit Facility** from the left menu, click **Term Sheet Setup** at top right, select **Create via Wizard**, fill in the details, and click **Create Draft**. An Adobe Sign popup opens for signing.

**Q: What happens after I sign and submit a term sheet?**

A: The facility agent reviews it and can Approve, Reject, or Request Changes. If approved, a master commitment is automatically created.

**Q: Why can't I create a funding request?**

A: Check two things: (1) Master commitment must be **Active** (at least one lender approved), and (2) Deal modelling must be **Completed** (facility agent did Set Up Deal).

**Q: How do lenders see funding notices?**

A: After the facility agent approves the funding notice and e-signs for each lender individually, each lender can see the funding notice in their Credit Facility section once their e-sign is complete.

**Q: What is Confirm and Settle?**

A: After lenders review the funding notice and transfer funds, they click **Confirm and Settle** to finalize their participation. Tokens are then transferred to the borrower.

## General Platform Questions

**Q: How do I switch roles?**

A: Log out and log back in. Select your role during login from the dropdown.

**Q: Why are some buttons disabled?**

A: Buttons are disabled when:
- Item isn't in the right status
- Your role doesn't have permission
- Prerequisites aren't met
- Waiting for another party to act

**Q: How do I provide feedback on a pool?**

A: Open the pool details, go to the **Feedback** section, and add your comments. Pool-level feedback is visible to the issuer. Loan-level feedback uses the chat box icon on individual loans.

**Q: What's the difference between feedback and rejection?**

A: **Feedback** allows the issuer to make changes. **Rejection** (for term sheets, funding requests) is final - a new item must be created.

**Q: How do I track my submissions?**

A: Check the item's status in the dashboard. Status shows where it is in the workflow. Status history shows all changes.
