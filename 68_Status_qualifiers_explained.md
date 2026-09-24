---
title: Status Qualifiers Explained
description: Understand status qualifiers that show who needs to act and what happens next
---

# Status Qualifiers Explained

→ Back to [Status & Approval Philosophy](04_Status_and_Approval_Philosophy.md)

A qualifier is the word after a status — **Pending**, **In review**, **Changes Requested** — that tells you who acts next. The meaning is the same regardless of which item type shows it.

## Quick Reference

| Qualifier | You're waiting? | Next action by |
|---|---|---|
| **Pending** | Yes | The other party |
| **In review** | Yes | The reviewer |
| **Changes Requested** | No | You — edit and resubmit |
| **Active** | No | Ready for the next operating step |
| **Approved / Accepted** | No | Continue to the next stage |
| **Rejected** | No | Create a new item |
| **Signed** | No | Submit, if you are the signer |

## Qualifier Meanings

**Pending** — waiting for someone to act.

| Status | Waiting on |
|---|---|
| Mandate Pending | Market maker to accept or decline |
| Pending (facility) | Lender to approve |
| Pending Token Generated | Facility agent to finish processing tokens |

**In review** — a reviewer has it and has not decided yet. You cannot edit while in review.

| Status | Reviewer |
|---|---|
| In review (term sheet / funding request) | Facility agent |
| Under Review (pool) | Market maker or investor |
| Pending Review (Asset Sale deal) | Underwriter |

**Changes Requested** — reviewer sent it back. Edit, re-sign (if term sheet), and resubmit. The same item stays open.

**Active** — in force and usable. For a facility it means loans can be mapped and funding requests created. For an Asset Sale deal it means repayment can be initiated.

**Approved / Accepted** — reviewer said yes; the next item is created automatically (funding notice after request approval; facility after term sheet acceptance).

**Rejected** — final. Read the reason, create a new item. The rejected item is read-only.

**Signed** — e-signature is complete. Submit the item if you are the signer.

## Loan Qualifier: Mapped / Unmapped

| Status | Meaning |
|---|---|
| **Mapped** | Loan is assigned to a pool |
| **Unmapped** | Loan exists in registry but not in any pool |

## Batch Verification Qualifiers

| Status | Meaning |
|---|---|
| **Pending** | Not yet verified; Mint NFT disabled |
| **Reviewed** | Verification complete; Mint NFT enabled |
| **Certified** | Third-party verification agent certified |
| **Self Certified** | Issuer verified in verification agent role |
| **Self Certify (Data Only)** | Issuer self-certified via Self Certify button |

## Asset Sale Deal Statuses

| Status | Meaning |
|---|---|
| **Draft** | Issuer is setting up the deal |
| **Pending Review** | Sent to underwriter |
| **Published** | Approved; investors can commit |
| **Commit / Invest** | Commitments open / allocated |
| **Settlement In Progress** | Funds and NFTs being exchanged |
| **Active** | Post-settlement; repayment can begin |
| **Repayment In Progress** | Issuer initiated repayment |
| **Closed** | Fully repaid |
| **Defaulted** | Default declared and confirmed |
| **Cancelled** | Cancelled before progressing |
