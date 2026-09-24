---
title: Status or Logic Changes
description: Changes to statuses, signing, sign-in, and activity history in Intain Markets
---

# Status or Logic Changes

## Overview

This page records changes to statuses and to how a few workflows behave. If you have been away, or a label does not match what you remember, start here.

## What Changed

### Asset sale status names

Two deal statuses were renamed so the labels match the life of the sale.

| Previous status | New status | Meaning                                                                   |
| --------------- | ---------- | ------------------------------------------------------------------------- |
| **Closed**      | **Active** | The sale has settled and the investor holds the assets. The deal is live. |
| **Repaid**      | **Closed** | Repayment is finished. The deal is complete.                              |

A settled sale used to be called Closed, which sounded finished. A finished repayment used to be called Repaid. A deal now settles, becomes **Active**, and becomes **Closed** only after repayment is done.

Current asset sale path:

Draft → Pending Review → Approved → Published → Commit → Invest → Settlement In Progress → Settled → **Active** → Repayment In Progress → **Closed**

Cancelled and Defaulted still end a deal.

### E-signature providers

DocuSign has been replaced by **Adobe Sign** and **ZohoSign**.

When you sign a term sheet, master commitment, funding notice, investor agreement, or batch self-certification, the signing window is Adobe Sign or ZohoSign. The steps are the same for both. The window may look different from DocuSign.

### Sign-in

Microsoft Entra (formerly Azure AD) is available next to username and password.

If your organization uses Microsoft Entra, sign in with those credentials. If you have more than one role, choose one after Microsoft sign-in. Your session stays signed in without asking you to sign in again on every page.

### Activity history

Activity across the platform is kept in one place. Open **Activity Audit** in the sidebar to filter, sort, and export it. Records are kept permanently.

### Credit facility path

Credit facilities follow their own path, separate from securitization and pools:

Term Sheet → Master Commitment → Funding Request → Funding Notice

* Approving a term sheet (status **Accepted**) creates a master commitment in Draft, filled from the term sheet.
* Approving a funding request creates a funding notice in **Pending Token Generated**.
* The facility agent signs the funding notice once for each lender.

### Loans removed from a pool

Removed and reinstated loans stay visible.

* **Removed** stays on the loan and the loan stays on the list.
* **Reinstated** is shown when a removed loan is put back.
* The status history for the loan remains available.

### Status labels

Some labels were aligned:

* Term sheet **Approved** is now **Accepted**
* Master commitment **Active** is shown as **ACTIVE**
* Funding request statuses are **Draft**, **Approved**, **Rejected**, and **Changes Requested**

### One-time password

These actions ask you to confirm with a one-time password:

| Action                        | Role         |
| ----------------------------- | ------------ |
| NFT minting                   | Issuer       |
| NFT transfer on an asset sale | Issuer       |
| Token approval                | Issuer       |
| Fund transfer                 | Paying Agent |

If you cannot complete the code, you can request emergency access.

## Impact on Existing Users

* If you tracked asset sales as Closed or Repaid, read those as **Active** (sale complete and live) and **Closed** (repayment finished). The path is Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed.
* Signing windows use Adobe Sign or ZohoSign.
* Use **Activity Audit** for one history of what happened.
* Microsoft Entra sign-in is available when your organization is set up for it. Username and password still work.
* NFT minting, token approval, and fund transfers now ask for a one-time password before they continue.
