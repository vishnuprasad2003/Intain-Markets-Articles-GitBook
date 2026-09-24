---
title: New Features
description: Learn about new features and capabilities added to Intain Markets
---

# New Features

## Overview

This page lists capabilities that are available in Intain Markets, and a few that are still being added. Use it to see what you can do now and what to watch for next.

## What Changed

### Credit facilities

**Master commitments are created for you.** When a term sheet is approved, a master commitment is created in Draft and filled from the term sheet. The facility agent then configures it and sends it to lenders.

**Funding notices are signed per lender.** The facility agent signs once for each lender. Progress shows as E-sign (0/n) through (n/n). A lender sees the notice after their signature is done.

**One lender can activate the facility.** Each lender’s decision is tracked separately, including when they approved. The facility becomes ACTIVE when the first lender approves.

**Tokens for a draw.** When a funding notice is ready, tokens are created and split by each lender’s share.

### E-signature

Signing uses Adobe Sign for term sheets, master commitment approval, and funding notices. After a borrower signs a term sheet, the status becomes Signed by the borrower. Lender signatures and funding-notice signatures are tracked one lender at a time.

Adobe Sign and ZohoSign are both supported. DocuSign is no longer available. In a test environment, signing can be simulated.

### Status history

Status changes record who acted, when, and why. You can review that history on the item.

Typical paths:

- Term sheets: Draft → Signed by the borrower → Under Review → Accepted
- Master commitments: Draft → Pending Lender Approval → Active
- Funding requests: DRAFT → Under Review → APPROVED
- Funding notices: Pending Token Generated → approved by the facility agent → e-signed for lenders

### Pools

Select loans in the Loan Registry and click Map to Pool. A loan can be in only one pool. Share a pool with market makers, investors, and rating agencies, and set feedback and download permissions on each share. NFT minting stays in Certificates, after batch verification.

### Loans

Upload a loan tape in Imports. Use Basic or Intelligent AI mapping, or save a mapping to reuse. In Batch Verification you can Self Certify or send the batch to a verification agent. Batch status moves from Pending to Reviewed, then to Certified when verification is complete.

IDA suggests field matches while you standardize a tape. You can also upload tapes for past reporting periods.

You can send a batch to a verification agent from Batch Verification. The result is recorded on the batch. You and the verification agent both get an email when it is submitted and when it is finished.

### Asset sale (February–September 2026)

You can create a deal, send it for underwriter review, take investor commitments, and settle. Settlement transfers ownership with NFTs.

After the sale, repayment uses a loan tape upload, a bank wire, investor confirmation of receipt, and an NFT burn when the deal closes.

Analytics inside an asset sale deal include:

- Asset Analysis: Overview, Strats, Performance, Receivables
- Risk Surveillance: Overview, Concentration, Data Checks, Exceptions, Performance Triggers
- Reports for the deal

From March 2026, an investor can burn receivables NFTs on a repaid asset sale. The burn finishes in the background.

### Credit facility deal setup (September 2026)

Facility agents set up a deal in a wizard with these sections: General, Facilities, Fees, Expenses, Manual Inputs, Accounts, Triggers, Borrowing Base, Calculations, Waterfall, and Review.

### Sign-in with Microsoft (February 2026)

If your organization uses Microsoft Entra (formerly Azure AD), click **Sign in with Microsoft**. If you have more than one role, choose a role before you enter.

### View As (February 2026)

Admins can open the platform as another user for support. The view is read-only, so the admin cannot change that user’s data.

### Activity Audit (March 2026)

**Activity Audit** in the sidebar shows activity across the platform. You can filter it and export it.

### Modelling workbench (January–February 2026)

Market makers and investors can set up cashflow models for a pool and compare scenarios.

### Updated issuer screens (January 2026)

Issuer dashboard, pool details, batches, and profile use an updated layout.

### Pool analysis (September 2026)

On a pool preview, market makers and investors can open IDA analytics.

### Participation Agreements (2026)

Participation Agreements appear alongside Asset Sale, Credit Facilities, and Securitization in the sidebar and on dashboard tiles. Issuers, market makers, and investors use them for participation workflows. Deal counts and statuses appear with the other product lines.

### Delegation (2026)

You can send a task, such as field mapping or deal setup, to an admin to finish for you.

### Too many requests (2026)

If too many requests are sent in a short time, the platform pauses them briefly.

### Wallet setup (2026)

Each organization can set up a wallet. The platform screens the wallet before it can be used.

### Notifications (March 2026)

The notification drawer updates while you work, so new alerts appear without a refresh.

### Search and filter (March–September 2026)

You can search and filter large lists, including batches, NFTs, pools, and admin lists.

## Impact on Existing Users

- Sign term sheets, commitments, funding notices, and investor agreements with Adobe Sign or ZohoSign.
- Use **Sign in with Microsoft** if your organization uses Entra. Direct username and password sign-in is still available.
- Open **Activity Audit** for a single activity history.
- Admins who need to see another user’s screen should use **View As**. It does not change that user’s data.
- For an asset sale, follow the deal through settlement, then repayment, receipt confirmation, and NFT burn.
- Facility agents should use the deal setup wizard before borrowers map loans or request funds.
- Issuers can self-certify a batch or send it to a verification agent.
- Kinexys and Circle fund transfers are still being added. When they are available, you will choose them during **Confirm and Settle**.
- A choice of Avalanche or Solana for token transfer is still being added.

Check release notes and in-product notifications when something new appears.
