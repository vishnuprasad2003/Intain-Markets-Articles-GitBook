---
title: Signature Visibility
description: >-
  When and where electronic signatures are visible across term sheets, facilities, funding notices, and batch certification
---

# Signature Visibility

Intain Markets uses **Adobe Sign** or **ZohoSign** (set by the platform). The steps are the same: a signing window opens, you sign, the signed document is stored with the item.

## Term Sheet (borrower signs)

1. **Create Draft** → Adobe Sign / ZohoSign window opens → borrower signs → status → **Signed**
2. Signed PDF is saved and attached to the term sheet

| Who | Can see? | When |
|---|---|---|
| Borrower | Yes | As soon as signature is recorded |
| Facility Agent | Yes | When term sheet is signed and In review |

> If changes are requested, the signature is cleared. Borrower must sign the updated term sheet again before resubmitting.

## Facility (each lender signs)

1. Lender opens **Opportunities → Approve & E-Sign** → signs → saved on their entry

| Lender status | Meaning |
|---|---|
| **Pending** | Lender has not signed yet |
| **Approved** | Lender approved (may precede signature completion) |
| **Signed** | Electronic signature complete |

| Who | Can see? | When |
|---|---|---|
| Lender | Their own signature | After they finish |
| Facility Agent | All lenders | As each lender finishes |
| Borrower | All signatures | After facility is **Active** |

> Facility becomes **Active** when at least one lender has signed.

## Funding Notice (facility agent signs for each lender)

The action shows signing progress: **E-sign (0 of n)** → **E-sign (n of n)**

| What you see | Meaning |
|---|---|
| E-sign (0 of 3) | No lender signed for yet |
| E-sign (1 of 3) | Facility agent signed for 1 of 3 |
| E-sign (3 of 3) | All lenders signed |

| Who | Can see? | When |
|---|---|---|
| Facility Agent | All lender signatures | As each is signed |
| Lender | Their own signature | After facility agent signs for them |
| Borrower | All signatures | After all lenders signed |

> A lender cannot see the funding notice until the facility agent has signed for them.

## Batch Self-Certification (issuer signs)

1. Issuer clicks **Self Certify** → certificate prepared → Adobe Sign opens → issuer signs
2. Batch status → **Reviewed**; loans marked **Self Certify (Data Only)**

## Helpful Tips

- Check the item's status before looking for a signature — a **Draft** term sheet has no signed document yet
- Expect a short delay after signing before the status updates in Intain Markets
- Signed documents are never replaced — a new round of changes adds a new signature alongside the earlier one
- Signatures appear in the item's history, status history, and Activity Audit
