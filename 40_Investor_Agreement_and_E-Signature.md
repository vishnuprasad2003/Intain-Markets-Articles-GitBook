---
title: Investor Agreement and E-Signature
description: >-
  How the Asset Sale investor agreement is uploaded, signed, and used as the
  settlement gate
---

# Investor Agreement & E-Signature

## Overview

The investor agreement is the legal document between the issuer and the selected investor. It can be signed in the platform with **Adobe Sign** (ZohoSign is also supported) or uploaded as a signed PDF. Settlement cannot start until the agreement status is **Signed**. This workflow is specific to Asset Sale; credit-facility signing is covered separately.

## Workflow Overview

1. The issuer uploads the sale agreement PDF during the create-deal wizard or from deal details.
2. The underwriter finalizes allocation and the deal moves to **Invest**.
3. The selected investor signs in the embedded e-sign view, or the issuer uploads a signed copy.
4. Status becomes **Signed** and the deal advances to **Settlement In Progress**.

Signing is allowed only when deal status is exactly **Invest**. In any other status the action is blocked.

## Key Stages

### Sale agreement upload

Upload a PDF on the **Sale Terms** tab or later from deal documents. That file is the agreement for the selected (winning) investor on the deal. You can replace it before signing starts.

### Record creation

When allocation is confirmed, the platform creates an agreement record with status **Not Signed**, tied to that investor. Deal details show **Not Signed** or **Signed**.

### Electronic signature

1. The investor opens the agreement from deal details.
2. Adobe Sign opens inside the platform — no separate Adobe account is required.
3. After signing, the signed PDF is stored. The record updates to **Signed**, including signing method, organization, and timestamp.

ZohoSign follows the same path. DocuSign is not used.

### Manual upload

If the agreement was signed outside the platform, the issuer uploads the signed PDF from deal details. Status is still **Signed**. This also moves the deal to **Settlement In Progress**. Use this when wet-ink or an external process was required.

### Settlement gate

If the agreement is still **Not Signed**, Confirm and Settle stays blocked. Both e-sign and upload count as executed.

## How the Workflow Progresses

Issuer uploads the template → investors commit → underwriter allocates → deal is **Invest** → investor signs or issuer uploads → **Settlement In Progress**.

The agreement is tied to the selected investor. You do not sign a separate copy per unallocated party.

## Important Points to Know

* **Adobe Sign** is the primary provider; **ZohoSign** is supported.
* Signed files are stored with version history for audit.
* Attempts to sign outside **Invest** are rejected with a clear error.
* Upload and e-sign are equivalent for the settlement gate.
* Replacing the PDF after **Signed** is not a normal path; treat the stored signed file as the executed copy.

If signing fails, confirm the deal is still **Invest** and that you are the selected investor. Re-open the agreement from deal details rather than a stale email link.

See [Deal Creation & Publishing](34_Deal_Creation_and_Publishing.md) for the upload step and [Settlement](36_Settlement_and_NFT_Transfer.md) for what follows.
