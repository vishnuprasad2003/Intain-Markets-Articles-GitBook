---
title: Repayment Flow
description: >-
  Step-by-step guide for asset sale repayment — loan tape upload, repayment initiation, investor confirmation, NFT burn, and deal closure
---

# Repayment Flow

Covers Full Repayment, Partial Repayment, and Declare Default on active asset sale deals.

## Repayment Types

| Type | Amount | Deal outcome |
|---|---|---|
| **Full Repayment** | Must equal outstanding balance | Deal closes after NFT burn |
| **Partial Repayment** | > 0 and ≤ outstanding balance | Deal stays Active; repeat for next instalment |
| **Declare Default** | Not required | Deal moves to **Defaulted** after investor confirms |

## Phase 1 — Upload Loan Tape (Issuer)

1. **Asset Sale → Deal ID** (deal must be **Active**)
2. **Deal Operations → Edit Loan Tape** → choose file → set **As Of Date** → **Upload**
3. Map loan tape columns to platform fields → **Save Mapping**

> The Intain internal team can upload the loan tape on the issuer's behalf; the issuer still reviews and records repayment.

## Phase 2 — Initiate Repayment (Issuer)

1. **Deal Operations → Initiate Repayment**
2. Fill in:
   - **Repayment Type** — Full, Partial, or Declare Default
   - **Repayment Date** — today or a past date (no future dates)
   - **Repayment Amount** — equals outstanding balance for Full; any amount ≤ balance for Partial; not required for Default. For receivables deals the amount is auto-calculated from the loan tape.
   - **Wire Reference** — required for Full and Partial
   - **Wire Confirmation Document** — PNG, JPEG, or PDF, max 10 MB
3. **Next → Review & Confirm** → deal status changes to **Repayment In Progress**

## Phase 3 — Confirm Receipt (Investor)

1. **Asset Sale → deal with repayment pending**
2. **Investment Operations → Confirm Repayment Receipt** → review details and wire document
3. Choose:

| Decision | Action | Outcome |
|---|---|---|
| **Accept** (Full) | Confirm | Investor can now burn the NFT; deal closes |
| **Accept** (Partial) | Confirm | Status shows **Installment Recorded**; issuer records next instalment |
| **Reject** | Enter reason (required, ≤ 1,000 chars) | Issuer re-submits repayment |
| **Confirm Default** | Confirm | Deal status → **Defaulted** |

## Phase 4 — Burn the NFT (Investor, Full Repayment only)

1. **Asset Analysis → Receivables tab**
2. Click **Burn** next to the receivables NFT → **Yes, Burn NFT**
3. NFT status: **Transferred → Retirement pending → Retired**

> NFT burn is irreversible. Once burned, the tokenised position is permanently closed.

## Phase 5 — Deal Closure

After NFT burn: deal status → **Closed** (Fully Repaid, 100% repaid). All events are preserved in the settlement audit trail (**Settlement Details → View details**).

## Status Summary

| Status step shown | Meaning |
|---|---|
| **Awaiting Investor Confirmation** | Issuer submitted; investor has not responded |
| **Installment Recorded** | Partial repayment accepted; issuer can record next |
| **Repayment Complete** | Full repayment accepted |
| **Default Declared** | Investor confirmed the default |

## Deal Status Transitions

| Deal status | When |
|---|---|
| **Active** | Before any repayment |
| **Repayment In Progress** | After issuer initiates |
| **Active** (Partially Repaid) | After partial repayment confirmed |
| **Closed** (Fully Repaid) | After full repayment confirmed and NFT burned |
| **Defaulted** | After default declared and confirmed |

## Key Rules

- Deal must be **Active** before repayment can be initiated
- Loan tape must be uploaded and mapped first
- Repayment date cannot be a future date
- Wire reference and document are required for Full and Partial types
- **Default cannot be rejected** — investor can only confirm
- **Record Next Instalment** is only available after a partial repayment is confirmed
