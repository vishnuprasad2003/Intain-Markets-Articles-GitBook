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

→ [Pools Overview](05_Pools_Overview.md)
**Q: Can I edit a pool after creating it?**

A: Yes, you can edit pools while in Created status. Click **Edit** button at top right of pool details. Once shared (Preview status) or in Deal status, some editing is restricted.

→ [Pool Lifecycle & Statuses](06_Pool_Lifecycle_and_Statuses.md)
**Q: How do I add loans to a pool?**

A: Go to **Loan Registry** from the left menu, select the loans you want to add, click **Map to Pool**, and select the pool from the dropdown.

→ [Loan Management](42_Loan_Management.md)
**Q: What do the tick and cross icons mean on loans?**

A: When a market maker or investor requests loan removal, the tick and cross appear. **Tick** = accept the removal request (loan marked as Removed). **Cross** = reject the removal request (loan stays in pool).

→ [Pool & Loan Review](57_Pool_and_Loan_Review.md)
**Q: How do I share a pool?**

A: Click the **Share** button at top right of pool details, select recipient type (Market Maker, Investor, Rating Agency), select organizations, set permissions (feedback, download), and share.

→ [Pool Creation & Sharing](41_Pool_Creation_and_Sharing.md)
## Loan Questions

**Q: How do I upload loans?**

A: Go to **Imports** from the left menu, select as of date, select asset class, choose file, and click **Submit**. The file is uploaded and a job is created.

→ [Loan Management](42_Loan_Management.md)
**Q: What is Trigger LTS?**

A: LTS (Loan Tape Standardization) maps your loan file columns to Intain standard fields. Click **Trigger LTS** to start the mapping process. You can use Basic or Intelligent AI mapping.

→ [Loan Management](42_Loan_Management.md)
**Q: What's the difference between Mapped and Unmapped status?**

A: **Mapped** = loan is assigned to a pool. **Unmapped** = loan exists but is not assigned to any pool. The Status column in Loan Registry shows this.

→ [Loan Lifecycle & Statuses](11_Loan_Lifecycle_and_Statuses.md)
**Q: How do I verify loans?**

A: Add loans to a batch from Loan Registry, go to **Batch Verification**, enter the batch, and either Self Certify or submit to a verification agent. After verification, batch status changes to Reviewed.

→ [Loan Management](42_Loan_Management.md)
**Q: When can I mint NFTs?**

A: After batch verification is complete (status: Reviewed). Go to **Certificates**, find the batch, and click **Mint NFT**. Select loans and click **Mint Selected**.

→ [Token Generation & Issuance](27_Token_Generation_and_Issuance.md)
## Credit Facility Questions

**Q: How do I create a term sheet?**

A: Go to **Credit Facility** from the left menu, click **Term Sheet Setup** at top right, select **Create via Wizard**, fill in the details, and click **Create Draft**. An Adobe Sign popup opens for signing.

→ [Term Sheet Submission](43_Term_Sheet_Submission.md)
**Q: What happens after I sign and submit a term sheet?**

A: The facility agent reviews it and can Approve, Reject, or Request Changes. If approved, a master commitment is automatically created.

→ [Term Sheet Workflow](18_Term_Sheet_Workflow.md)
**Q: Why can't I create a funding request?**

A: Check two things: (1) Master commitment must be **Active** (at least one lender approved), and (2) Deal modelling must be **Completed** (facility agent did Set Up Deal).

→ [Funding Requests](44_Funding_Requests.md)
**Q: How do lenders see funding notices?**

A: After the facility agent approves the funding notice and e-signs for each lender individually, each lender can see the funding notice in their Credit Facility section once their e-sign is complete.

→ [Funding Notices Overview](26_Funding_Notices_Overview.md)
**Q: What is Confirm and Settle?**

A: After lenders review the funding notice and transfer funds, they click **Confirm and Settle** to finalize their participation. Tokens are then transferred to the borrower.

→ [Funds Transfer Confirmation](31_Funds_Transfer_Confirmation.md)
## General Platform Questions

**Q: How do I switch roles?**

A: Log out and log back in. Select your role during login from the dropdown.

→ [Login & Navigation](03_Login_and_Navigation.md)
**Q: Why are some buttons disabled?**

A: Buttons are disabled when:
- Item isn't in the right status
- Your role doesn't have permission
- Prerequisites aren't met
- Waiting for another party to act

→ [Enabled vs Disabled Actions](69_Enabled_vs_Disabled_actions.md)
**Q: How do I provide feedback on a pool?**

A: Open the pool details, go to the **Feedback** section, and add your comments. Pool-level feedback is visible to the issuer. Loan-level feedback uses the chat box icon on individual loans.

→ [Pool Feedback Workflow](09_Pool_Feedback_Workflow.md)
**Q: What's the difference between feedback and rejection?**

A: **Feedback** allows the issuer to make changes. **Rejection** (for term sheets, funding requests) is final - a new item must be created.

→ [Feedback vs Rejection](73_Feedback_vs_rejection.md)
**Q: How do I track my submissions?**

A: Check the item's status in the dashboard. Status shows where it is in the workflow. Status history shows all changes.

→ [Status & Approval Philosophy](04_Status_and_Approval_Philosophy.md)
## Asset Sale Questions

**Q: How do I access the Asset Sale module?**

A: Navigate to **Asset Sale** from the left sidebar menu. The Asset Sale dashboard shows all deals relevant to your role — issuers see deals they created, underwriters see deals for review, and investors see published deals available for commitment.

→ [Asset Sale Overview](32_Asset_Sale_Overview.md)
## Activity & Audit Questions

**Q: Where can I see my audit trail?**

A: The platform provides a centralized **Activity Audit** accessible from the left sidebar. This shows a chronological feed of all actions across modules including who performed each action, what changed, and when.

→ [Who Changed What and When](76_Who_changed_what_and_when.md)
## Login & Authentication Questions

**Q: How do I log in with Microsoft SSO?**

A: Click the **Sign in with Microsoft** button on the login page. You will be redirected to Microsoft's authentication flow. After authentication, if your account has multiple roles, select your role on the role selection page.

→ [Login & Navigation](03_Login_and_Navigation.md)
