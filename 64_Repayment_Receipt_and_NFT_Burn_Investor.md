---
title: Repayment Receipt and NFT Burn
description: How the investor accepts or rejects repayment and burns the receivables NFT
---

# Repayment Receipt & NFT Burn

## Overview

When the issuer records repayment, the investor reviews the declaration, accepts or rejects it, and — after a full accept — burns the receivables NFT to close the position. Match the on-screen amount to the wire you received before you accept. Accepting is a confirmation of receipt, not a request to send more funds. Burn is on-chain and cannot be undone.

## Who Can Use This

- **Investors** who are the payee on the repayment

Other roles can view status but cannot accept, reject, or burn. If you are not the payee on the settlement, the platform returns access denied. Use the same organization that received the allocation. A different investor login will not see Confirm Repayment Receipt on that specific Asset Sale deal.

## When This Is Used

Use this when the deal is **Repayment In Progress**, or when the issuer has declared default and you must confirm it.

## Step-by-Step Process

### Review the declaration

1. Open **Asset Sale** and the deal showing **Repayment In Progress**.
2. **Investment Operations** → **Confirm Repayment Receipt**.
3. Check the issuer’s values (read-only):

| Field | Shown |
|-------|--------|
| **Repayment Type** | Full, Partial, or Defaulted |
| **Repayment Date** | Hidden for default |
| **Repayment Amount** | Hidden for default |
| **Wire Reference** | Issuer’s memo or transaction ID |

You cannot edit these fields. Your job is to verify and respond. If the wire reference on screen does not match your bank memo, treat that as a reject reason rather than accepting and reconciling later.

### Respond

| Response | Effect |
|----------|--------|
| **Accept Repayment** | Confirms receipt. Default selection. |
| **Reject Repayment** | Reason required (up to 1,000 characters). Balance unchanged; issuer can resubmit. |
| **Confirm Default** | Only option when the issuer declared default. Cannot reject. Permanent. |

Click **Review & Confirm** (or **Review Rejection**), read the summary, then submit.

- Accept: you confirm receipt as declared.
- Reject: figures do not change; the issuer is notified with your reason.
- Default: no further repayment can be recorded.

### Burn the NFT

Burn appears after accept, when NFT status is **Retirement pending** and the token is **Transferred** to you.

1. **Asset Analysis** → **Receivables**.
2. Click **Burn**. You can select one or more asset IDs.
3. Confirm **Yes, Burn NFT**.

On a partial repayment, only assets with zero outstanding can be burned. When every NFT on the deal is burned, NFT status becomes **Retired** and the deal is **Closed** (Fully Repaid). If you burn only some tokens, status stays **Retirement pending**.

## Rules & Validations

- Only the investor on the settlement can accept, reject, or burn.
- Reject needs a written reason.
- Declared default cannot be rejected.
- The deal closes only after all NFTs are retired.
- Burn is irreversible.
- **Burn** stays hidden until repayment is accepted and NFT status is **Retirement pending**.

### If something looks wrong

If the amount does not match your bank receipt, reject and explain the difference. Do not accept “to keep the deal moving.” If **Burn** is missing after accept, refresh Receivables and confirm status is **Retirement pending**, not still **Transferred**.

## What Happens Next

A closed deal stays on the dashboard for reporting. Settlement Details keep the trail from settlement through burn. If you rejected, the issuer records a new repayment. Issuer steps: [Repayment Initiation](47_Repayment_Initiation_Issuer.md). What the token is: [Receivables & NFT Burn](38_Receivables_and_NFT_Burn.md).
