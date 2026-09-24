---
title: Pool Lifecycle and Statuses
description: >-
  Understand the different stages pools go through from creation to deal
  completion
---

# Pool Lifecycle & Statuses

## Overview

A pool moves through statuses from creation to a committed deal. The status controls who can see the pool, what they can do, and whether the issuer can still edit it.

## Lifecycle Overview

There are two ways to share a pool.

**Share Flow (Preview Sharing)**

* The issuer creates the pool. Its status is **Created**.
* The issuer clicks **Share**. Recipients see **Mandate Pending** and can **Accept** or **Reject**.
* After an underwriter / facility agent accepts, their view shows **Under Review**.
* If an underwriter / facility agent rejects, the pool leaves their dashboard.
* The issuer can still edit the pool, share it with more organizations, or click **Start Deal** when ready.

**Start Deal Flow**

* **Start Deal** turns on when the pool is ready, typically after every loan in the pool has an NFT.
* Recipients then see **Ready for Deal** and can **Accept** or **Reject**.
* When an underwriter / facility agent accepts, the status becomes **Deal** and structural editing stops.
* That underwriter / facility agent continues with deal structuring.

You prepare a pool in private, share it for review while you can still edit, then commit it when you are ready.

## Status Meanings

What you see depends on your role.

### For Issuers

**Created** — The pool exists with its name, asset class, transaction type, and organization assignments. Only you can see it. Add loans from the Asset Registry and finish setup before you share.

**Deal** — An underwriter / facility agent accepted **Start Deal**. Structural editing is restricted. That underwriter / facility agent continues deal structuring and later transaction steps.

### For Underwriters / Facility Agents, Investors, and Rating Agencies

**Mandate Pending** — Someone shared the pool with you using **Share**. You can **Accept** or **Reject**. Market makers cannot give feedback until they accept.

**Under Review** — You accepted a Mandate Pending pool. You can give feedback, review loans, and request loan removals. The issuer can still edit and respond.

**Ready for Deal** — The issuer clicked **Start Deal**. Loans are finalized, typically with NFTs minted. You can **Accept** or **Reject**.

**Deal** — You accepted Ready for Deal. Structural editing is restricted. The accepting underwriter / facility agent continues deal structuring.

## What Each Status Indicates

**Created** (issuer) — The pool is private. You can edit details, change organization assignments, map or unmap loans, upload loan tapes, and change settings. Finish setup and loan mapping before you share.

**Mandate Pending** (recipient) — You need to accept or reject. You can view details, metrics, and loans. Market makers cannot give feedback until they accept.

**Under Review** (underwriter / facility agent, after accept) — Feedback is available at pool level and loan level. You can request loan removals. The issuer may still change the pool.

**Ready for Deal** (recipient) — Start Deal has been clicked and the usual prerequisites, including NFT minting, are done. Accept commits you to the deal. Reject declines it.

**Deal** — The pool is committed. The structure is locked. The accepting underwriter / facility agent continues with structuring, investor allocations, and later steps.
