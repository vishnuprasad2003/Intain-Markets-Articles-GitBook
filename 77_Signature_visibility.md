---
title: Signature Visibility
description: Comprehensive guide to understanding when and where electronic signatures are visible across roles and workflows in Intain Markets
---

# Signature Visibility

## Overview

Electronic signatures are used on term sheets, facilities, funding notices, and batch self-certification. Intain Markets uses **Adobe Sign** and **ZohoSign**. Which provider you see is set for the platform. You do not choose it, and the steps are the same either way: a signing window opens, you sign, and the signed document is stored with the item.

Who can see a signed document depends on your role and on how far the item has progressed. A signature that is not finished yet is not shown as complete.

## How to Navigate Signature Information

**Term sheets**

- Go to **Credit Facility** and open the term sheet
- Open the term sheet details
- In **Documents**, open the signed PDF after the borrower has signed
- The status moves to **Signed** once that signature is recorded. Until then, there is no signed copy to view

**Facilities**

- Go to **Credit Facility** and open **Active Facilities**, or open the facility while it is still **Pending**
- Open the facility details
- In **Documents**, open the signed commitment documents
- Each lender has their own signature status. You can see who has finished and who has not

**Funding notices**

- Go to **Credit Facility** and open the funding notice under its facility
- The action shows signature progress, such as **E-sign (0 of 3)** moving toward **E-sign (3 of 3)**
- Each lender’s row shows whether their signature is still pending or complete

**Batch self-certification**

- Go to **Batches**
- A self-certified batch shows the signed certificate
- The batch is marked self-certified (data only) after the issuer signs

## What You Will See

### Term Sheet Signatures

**Who signs:** The borrower.

**How it works:**

1. The borrower chooses **Create Draft**. Adobe Sign or ZohoSign opens.
2. The borrower reviews the term sheet produced from the facility terms, collateral, and financial information.
3. The borrower signs in that window.
4. The signed PDF is saved and attached to the term sheet.
5. The term sheet status becomes **Signed**.

There can be a short pause after you finish in the signing window before Intain Markets shows the new status.

**Who can see the signed document**

| Party | Can see it? | When |
|-------|-------------|------|
| **Borrower** | Yes | As soon as the signature is recorded |
| **Facility Agent** | Yes | When the term sheet has been signed or submitted and is **In review** |

The platform stores the signed PDF, the signing provider’s reference for that envelope, whether signing is complete, and the time it was completed. That signing event is also written to the term sheet’s history and to the activity log.

**If changes are requested**

When the facility agent asks for changes on a signed term sheet, the signature is cleared. The borrower must sign the updated term sheet again before submitting it. The earlier signed file remains part of the history of that round.

### Facility Signatures (each lender)

**Who signs:** Each lender.

**How it works:**

1. After the term sheet is accepted, the facility is created and lenders are asked to sign.
2. The lender opens **Opportunities** and chooses **Approve & E-Sign**.
3. Adobe Sign or ZohoSign opens.
4. The lender signs.
5. The signed document is saved on that lender’s entry in the facility.

**What each lender’s status means**

| What you see | Meaning |
|--------------|---------|
| Pending | The lender has not finished |
| Approved | The lender has approved. In some cases this is recorded before the signature itself is complete |
| Signed | The lender has finished the electronic signature and is committed |

**Who can see the signed documents**

| Party | Can see them? | When |
|-------|---------------|------|
| **Lender** | Their own signature | As soon as they finish |
| **Facility Agent** | Every lender’s signature | As each lender finishes |
| **Borrower** | The signatures | After the facility is **Active** |

The facility becomes **Active** when at least one lender has finished signing. Only lenders who have finished are included when the platform later builds a funding notice.

If the facility has sub-facilities, the signature is recorded on both the parent facility and the sub-facility.

### Funding Notice Signatures (the facility agent signs for each lender)

**Who signs:** The facility agent, once for each lender.

**How it works:**

1. The notice action shows **E-sign (0 of n)** before anyone is signed.
2. The facility agent opens the signing window and signs for the first lender.
3. The count moves to **1 of n**.
4. The facility agent repeats this for each remaining lender.
5. The count shows **n of n** when every lender is signed.

| What you see | Meaning |
|--------------|---------|
| E-sign (0 of 3) | No lender has been signed for yet |
| E-sign (1 of 3) | The facility agent has signed for 1 of 3 lenders |
| E-sign (2 of 3) | Signed for 2 of 3 |
| E-sign (3 of 3) | Every lender is signed |

The notice shows how many lenders need a signature, how many are still waiting, and whether signing overall is still pending or complete. Each lender’s row moves from pending to signed on its own.

**Who can see the signed documents**

| Party | Can see them? | When |
|-------|---------------|------|
| **Facility Agent** | All of them | As soon as they sign for that lender |
| **Lender** | Their own | Only after the facility agent has signed for that lender |
| **Borrower** | All of them | After the facility agent has signed for every lender |

A lender does not see the funding notice, and cannot act on it, until the facility agent has signed for them. That way the lender receives the notice together with the signed agreement.

### Batch Self-Certification Signatures

**Who signs:** The issuer.

**How it works:**

1. The issuer starts self-certification on the batch.
2. A certificate is prepared from the batch.
3. Adobe Sign or ZohoSign opens, and the issuer signs.
4. The signed certificate is saved on the batch.
5. Loans in the batch are marked self-certified (data only).
6. The batch status becomes **Reviewed**.

The relevant organizations are notified when this finishes. You confirm the step with a one-time code when the platform asks for one.

## Helpful Tips

**Check the status before you look for a file.** A term sheet still in **Draft** has no signature yet. A notice that shows **E-sign (0 of 3)** has no lender signatures yet.

**A finished signature is kept.** Once Adobe Sign or ZohoSign returns the signed PDF, that file stays with the item. It is not edited or replaced. A later round of changes adds a new signature. It does not rewrite the earlier one.

**The provider does not change the rules.** Adobe Sign and ZohoSign follow the same pattern: you sign in their window, the status updates in Intain Markets, and the signed file is stored on the item.

**Expect a short delay.** Completion is picked up from the signing provider. The status in Intain Markets usually updates within seconds. If it does not, refresh the item before you sign a second time.

**You are notified.** When a signature is recorded, the signer and the other parties who need to know get a notification in the platform and an email.

**The history is in more than one place.** The item’s action history, its status history, and Activity Audit all record the signature. Use those if you need to show who signed and when.
