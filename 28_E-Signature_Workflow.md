---
title: E-Signature Workflow
description: >-
  Understand how electronic signatures work across credit facility workflows,
  including provider integration, per-lender tracking, and document lifecycle
---

# E-Signature Workflow

## Overview

Electronic signatures are used in the credit facility so people can sign binding documents on the platform. Each signature records who signed, when they signed, and which document they signed. Signed copies stay available for people who are allowed to download them.

The platform uses **Adobe Sign** or **ZohoSign**. In a test environment, a practice signing mode can complete the signature immediately so teams can rehearse the steps. The signing windows follow the same pattern at each step, whichever service your organization uses. DocuSign is no longer used.

## Workflow Overview

Signatures are required at three points. Each point has a different signer and a different result:

| Signing Point                 | Who Signs                       | What Is Signed                 | When It Happens                                      | Status After Signing                      |
| ----------------------------- | ------------------------------- | ------------------------------ | ---------------------------------------------------- | ----------------------------------------- |
| **Term Sheet Signing**        | Borrower                        | Term sheet                     | After the borrower clicks **Create Draft**           | **Draft** → **Borrower signed**           |
| **Master Commitment Signing** | Lender                          | Master commitment              | When the lender clicks **Approve & E-Sign**          | Pending lender approval → **Active**      |
| **Funding Notice Signing**    | Facility agent, once per lender | Funding notice for that lender | After the facility agent approves the funding notice | **E-sign (0/n)** through **E-sign (n/n)** |

## Key Stages

### Stage 1: Term Sheet E-Signature (Borrower)

**When it happens:** After the borrower finishes the term sheet and clicks **Create Draft**, signing starts on its own.

**How it works:**

1. The borrower clicks **Create Draft**
2. A signing window opens with the term sheet
3. The borrower reviews the document and signs
4. The signed copy is saved on the platform
5. The status changes from **Draft** to **Borrower signed**

**What this means:**

* The borrower has signed the term sheet
* The borrower can now submit it to the facility agent
* Authorized users can download the signed copy
* Without this signature, the term sheet cannot be submitted

### Stage 2: Master Commitment E-Signature (Lender)

**When it happens:** A lender opens the master commitment under **Opportunities** and clicks **Approve & E-Sign**.

**How it works:**

1. The lender opens **Opportunities** in Credit Facility
2. The lender clicks **Review & Approve**
3. The lender reviews the facility details: basic information, parties, conditions, pricing, and covenants
4. The lender clicks **Approve & E-Sign**
5. A signing window opens
6. The lender reviews and signs
7. The signed copy is saved
8. That lender's decision is recorded as approved, with the date and time
9. The master commitment status changes to **Active**, even if other lenders have not approved yet

**What this means:**

* The lender commits to the credit facility
* **One lender's approval makes the facility active.** The other lenders do not all have to approve first.
* Each lender's decision is tracked on its own
* The facility agent can continue facility setup once the commitment is active
* The signed commitment is the lender's formal approval

Each lender is tracked separately. A lender can be waiting, approved, or rejected. Their signature is either still pending or signed, and the approval time is shown after they approve.

### Stage 3: Funding Notice E-Signature (Facility Agent)

**When it happens:** After a funding request is approved, a funding notice is created. The facility agent signs that notice once for each lender.

**How it works:**

1. The funding request is approved and a funding notice is created with status **Pending token generation**
2. The facility agent clicks **Approve** on the funding notice
3. The action shows **E-sign (0/n)**. The number n is the count of lenders on the notice.
4. The facility agent opens the signing action
5. A signing window opens for the next lender who is not yet signed
6. The facility agent signs for that lender
7. The counter updates, for example **E-sign (1/n)**
8. The facility agent repeats this until every lender is signed
9. A lender can see and act on the notice as soon as their own signature is done. They do not wait for the other lenders.
10. When every lender is signed, the action shows **E-sign (n/n)**

**What this means:**

* The facility agent signs a copy for each lender
* Each lender has their own signature record, including when it was completed
* That lender can review the notice as soon as their signature is done

**Signature progress:**

| Counter          | Meaning                                              |
| ---------------- | ---------------------------------------------------- |
| **E-sign (0/3)** | None of the 3 lenders is signed yet                  |
| **E-sign (1/3)** | Signed for 1 lender. That lender can see the notice. |
| **E-sign (2/3)** | Signed for 2 lenders. Both can see the notice.       |
| **E-sign (3/3)** | All lenders are signed                               |

Until a lender is signed, their signature status stays **pending signature**. After the facility agent signs for them, that lender's status is **signed**.

## How the Workflow Progresses

### E-Signature Provider Architecture

Your organization uses one signing service for these steps: **Adobe Sign** or **ZohoSign**. You do not choose a different service at each step.

**Adobe Sign:**

1. A signing window opens with your document
2. You review and sign
3. When signing is finished, the signed copy is saved on the platform
4. The related status updates, such as **Borrower signed** or the **E-sign** count

**ZohoSign:**

1. A signing window opens with your document
2. You review and sign
3. When signing is finished, the signed copy is saved on the platform
4. The related status updates in the same way as Adobe Sign

**Practice signing in a test environment:**

* Test environments can complete the signature immediately
* No Adobe Sign or ZohoSign account is required for that practice mode
* The document is marked signed so you can continue the workflow

### Document Lifecycle

```
Document prepared → Signing window opens → You sign → Signed copy is saved → You can download it
```

## Important Points to Know

**The signature is binding** — Signatures completed in Adobe Sign or ZohoSign are the formal sign-off for that document.

**The workflow waits for the signature:**

* A term sheet cannot be submitted until the borrower has signed
* A master commitment does not become **Active** until at least one lender has signed
* A lender cannot see or act on a funding notice until the facility agent has signed for that lender

**Each lender is separate on a funding notice** — The facility agent signs once per lender. That lender gets access as soon as their own signature is complete.

**One signing service at a time** — The platform uses Adobe Sign or ZohoSign. DocuSign is retired.

**You can see who signed** — The record shows who signed, when they signed, and which service was used. Authorized users can download the signed document.

**The status updates after you finish** — When the signing window is complete, the term sheet, commitment, or funding notice updates to the next status.

**Signed copies stay available** — Authorized users can download signed documents later for their records.
