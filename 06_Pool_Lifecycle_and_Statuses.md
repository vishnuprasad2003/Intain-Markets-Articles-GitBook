---
title: Pool Lifecycle and Statuses
description: Understand the different stages pools go through from creation to deal completion
---

# Pool Lifecycle and Statuses

## Overview

Pools progress through several statuses from creation to final deal completion. Each status represents a specific stage in the pool's journey and determines what actions are available, who can see the pool, and what editing is permitted. Understanding the lifecycle helps you navigate the workflow and know what to expect at each stage.

## Lifecycle Overview

Pools follow two distinct flows depending on how you share them:

**Share Flow (Preview Sharing)**
- Pool starts as **Created** when first created by the issuer
- When shared using the **Share** button, recipients see the pool as **Mandate Pending** with Accept/Reject actions
- When a market maker accepts, their view shows **Under Review**
- When a market maker rejects, they no longer see the pool in their dashboard
- Throughout this phase, the issuer retains full editing capabilities
- The issuer can continue to share with additional organizations or proceed to Start Deal when ready

**Start Deal Flow**
- When prerequisites are met (typically all pool loans NFT-minted), the **Start Deal** button becomes enabled
- When the issuer clicks Start Deal, recipients see the pool as **Ready for Deal** with Accept/Reject actions
- When a market maker accepts, the pool status becomes **Deal** and structural editing is restricted
- The accepting market maker proceeds with deal structuring and downstream activities

The lifecycle is designed to support collaboration—you create and prepare pools privately, share them for review and feedback while retaining editing rights, then finalize them as committed deals when ready.

## Status Meanings

The statuses you see depend on your role and where you are in the workflow:

### For Issuers

**Created** - The pool has been created with basic information (pool name, asset class, transaction type, organization assignments) and is visible only to you. This is the initial stage where you prepare the pool, add loans from the Loan Registry, and configure settings before sharing. Pools in Created status are completely private—no other organization can see them until you share.

**Deal** - The pool has reached its final committed state after a market maker accepted via Start Deal. Structural editing is restricted at this stage. The accepting market maker proceeds with deal structuring, and downstream transaction activities continue from here.

### For Market Makers / Investors / Rating Agencies (Recipients)

**Mandate Pending** - This is what you see when a pool has been shared with you through the Share button. You have **Accept** and **Reject** action buttons. Before accepting the mandate, market makers cannot provide feedback on the pool—feedback functionality becomes available only after acceptance.

**Under Review** - This is what market makers see after they click Accept on a Mandate Pending pool. You can now provide feedback, review loan details, request loan removals, and prepare for the next steps. The issuer can still edit the pool and respond to your feedback during this phase.

**Ready for Deal** - This is what you see when the issuer has initiated Start Deal. The pool is finalized (all loans NFT-minted) and ready for deal commitment. You have **Accept** and **Reject** action buttons to decide whether to commit to the deal.

**Deal** - After you accept a Ready for Deal pool, the status becomes Deal. Structural editing is restricted. The accepting market maker proceeds with deal structuring, and downstream transaction activities continue.

## What Each Status Indicates

**Created Status** (Issuer view) indicates that you're still preparing the pool privately. You have full control: you can edit pool details, add or remove organization assignments, map or unmap loans from the Loan Registry, upload recurring loan tapes, and configure all settings. The pool is not visible to any other organization. Complete pool setup and loan mapping before sharing.

**Mandate Pending** (Recipient view) indicates that you have received a share and need to decide whether to accept or reject. You can view pool details, metrics, and loan information, but market makers cannot provide feedback until they accept. Your Accept or Reject decision affects your view of the pool and enables or disables subsequent actions.

**Under Review** (Market Maker view after accepting) indicates that you have accepted a mandate. Feedback functionality is now available—you can provide pool-level and loan-level feedback, request loan removals, and collaborate with the issuer. The issuer may continue making changes based on your input.

**Ready for Deal** (Recipient view) indicates that the issuer has initiated Start Deal, meaning prerequisites (such as NFT minting for all pool loans) are complete and the pool is finalized. Your Accept or Reject decision here commits (or declines) the deal.

**Deal Status** indicates that the transaction is finalized and committed. The pool structure is locked, and structural editing is restricted. The accepting market maker proceeds with deal structuring, investor allocations, and other downstream activities.
