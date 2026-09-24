---
title: E-Signature Workflow
description: >-
  How electronic signatures work for term sheets, master commitments, and funding notices in credit facilities
---

# E-Signature Workflow

Intain Markets uses **Adobe Sign** or **ZohoSign** for binding e-signatures. DocuSign is no longer used. The signing window pattern is the same for both providers.

## Where Signatures Are Required

| Signing point | Who signs | When | Status after signing |
|---|---|---|---|
| **Term sheet** | Borrower | After clicking **Create Draft** | Draft → **Borrower signed** |
| **Master commitment** | Each lender | When clicking **Approve & E-Sign** | Pending → **Active** (first approver) |
| **Funding notice** | Facility agent (once per lender) | After approving the funding notice | **E-sign (0/n)** → **E-sign (n/n)** |

## Stage 1 — Term Sheet (Borrower)

1. Click **Create Draft** → signing window opens automatically
2. Review the document → sign
3. Signed PDF saved; status → **Borrower signed**
4. Borrower can now submit to the facility agent

> If changes are requested, the signature is cleared. Borrower must sign the updated document again before resubmitting.

## Stage 2 — Master Commitment (Lender)

1. **Opportunities** → **Review & Approve** → review all terms
2. Click **Approve & E-Sign** → signing window opens → sign
3. Signed PDF saved on lender's entry; status → **Active** (if first lender)
4. Each lender is tracked individually; one approval is enough to activate the facility

## Stage 3 — Funding Notice (Facility Agent, once per lender)

1. After approving the funding notice, action shows **E-sign (0/n)**
2. Open signing action → sign for first lender → counter updates to **E-sign (1/n)**
3. Repeat for each lender until **E-sign (n/n)**
4. Each lender can see and act on the notice as soon as their signature is complete — they do not wait for other lenders

| Counter | Meaning |
|---|---|
| E-sign (0/3) | No lender signed for yet |
| E-sign (1/3) | One lender can now see the notice |
| E-sign (3/3) | All lenders signed |

## Key Rules

- Term sheet cannot be submitted until the borrower signs
- Facility does not become **Active** until at least one lender signs
- A lender cannot see a funding notice until the facility agent signs for them
- Signed copies are stored permanently and available for download
- Status updates within seconds of signing; if not, refresh before signing again
- Test environments support practice signing mode (no Adobe Sign / ZohoSign account needed)
