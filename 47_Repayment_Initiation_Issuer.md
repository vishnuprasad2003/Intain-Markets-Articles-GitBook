---
title: Repayment Initiation
description: How the issuer uploads a loan tape and records Asset Sale repayment in the four-step wizard
---

# Repayment Initiation

## Overview

On an **Active** deal, the issuer uploads the latest loan tape and records repayment so investors can confirm receipt. The repayment modal is a four-step wizard: rail, payment details, review, status. This page is the issuer click-path. The shared repayment picture is in [Repayment Flow](37_Repayment_Flow.md).

## Who Can Use This

- **Issuers**

If you do not see **Initiate Repayment**, the deal is not **Active**, or you are not the issuer on that deal.

## When This Is Used

Use this when borrowers have paid on the underlying loans and you need to pass funds through — full payoff, a partial installment, or declare default.

## Step-by-Step Process

### 1. Open the Active deal

**Asset Sale** → click the Deal ID. Confirm status is **Active**.

### 2. Upload the loan tape

**Deal Operations** → **Edit Loan Tape**. Upload the Excel file, set **As Of Date**, map columns, and **Save Mapping**.

On receivables deals, the amount is taken from the tape’s invoice totals. If that total is 0, the platform shows an error and you must re-upload before continuing.

### 3. Open the wizard

Click **Initiate Repayment**. Steps: **Select Rail** → **Record Payment** → **Review** → **Status**. A tracker at the top shows the current step.

### 4. Select the rail

Choose **Bank (Wire/ACH)**. Kinexys and Stablecoin cards are visible but disabled. Hover text explains that repayment supports bank wire only.

### 5. Record payment

| Type | What happens |
|------|----------------|
| **Full Repayment** | Amount fills with the outstanding balance. You can edit it except on receivables deals. |
| **Partial Repayment** | You enter the amount. Remaining balance stays open. |
| **Declare Default** | Amount fields hide. A warning states default is permanent. |

If the outstanding balance is zero, all type cards are disabled.

Required for Full or Partial:

| Field | Rule |
|-------|------|
| **Repayment Method** | Bank (Wire/ACH) — read-only |
| **Repayment Date** | MM/DD/YYYY; future dates are disabled |
| **Repayment Amount** | Greater than zero; not above outstanding on a full repayment |
| **Wire Reference** | Required memo or transaction ID |
| **Wire Confirmation** | PNG, JPEG, JPG, or PDF, max 10 MB |

Click **Next**. Missing fields show a tooltip (type, amount, date, reference, or document).

### 6. Review and confirm

The summary shows method, type, amount, date, deal name, Deal ID, and wire reference. Confirm that the wire has been initiated. For default, confirm that the investor will be asked to acknowledge and that no further repayment can be recorded.

### 7. Watch status

The last step shows awaiting investor confirmation, repayment complete, default declared, or installment recorded. The modal refreshes while it is open.

- **Partial** — after the investor accepts, **Record Next Installment** restarts the wizard with a blank form.
- **Rejected** — the wizard returns to Record Payment. Re-enter details and upload a new confirmation.

## Rules & Validations

- Only **Active** deals.
- Loan tape mapping must be saved first.
- One repayment in progress at a time.
- Default cannot be undone.
- Amounts accept up to four decimal places.

## What Happens Next

The deal is **Repayment In Progress**. The investor accepts or rejects. You cannot burn the NFT — that is the investor’s step. After a full accept and NFT burn, the deal is **Closed**. After a partial accept, use **Record Next Installment**. After a reject, open the wizard again with a new confirmation file.

See [Repayment Receipt & NFT Burn](64_Repayment_Receipt_and_NFT_Burn_Investor.md).
