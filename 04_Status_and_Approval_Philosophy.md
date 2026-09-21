---
title: Status and Approval Philosophy
description: Why Intain Markets uses status-driven workflows and approval gates to ensure trust, accountability, and structured progression across every transaction
---

# Status and Approval Philosophy

## Overview

Intain Markets is built on a foundational principle: every transaction should progress through clearly defined stages, with proper authorization at each transition. This is not merely a technical design choice — it reflects a deliberate philosophy rooted in how institutional financial markets operate. In traditional capital markets, deals move through stages of preparation, review, commitment, execution, and settlement, with checks and sign-offs at every boundary. Intain Markets brings this same rigor to a digital platform, ensuring that no action happens without the right person authorizing it at the right time.

Statuses and approvals are the two mechanisms that enforce this philosophy. Statuses represent where an item is in its journey — they control what actions are available and who can act. Approvals are the gates between stages — they ensure that a qualified party has reviewed and authorized the transition before it happens.

Together, these mechanisms create workflows that are predictable, auditable, and resistant to errors or unauthorized actions.

## How the Platform Is Designed

### Status-Driven Workflows

Every major item on the platform — pools, loans, term sheets, master commitments, funding requests, asset sale deals — carries a status that defines its current state. This status is the single source of truth for what can happen next.

The platform enforces strict rules based on status:

- **Action availability is status-dependent.** Buttons and actions are enabled or disabled based on the item's current status. For example, a term sheet in **Draft** status can be edited, but once it moves to **FAReview**, editing is locked until the facility agent makes a decision. A deal in **Active** status allows repayment initiation, but a deal in **Settlement In Progress** does not.

- **Sequential progression is enforced.** Items cannot skip stages. A pool must move from **Created** to **Preview** to **Under Review** to **Deal** — there is no shortcut from Created directly to Deal. An asset sale deal must progress through Draft, Pending Review, Published, Commit, Invest, Settlement In Progress, Settled, and Active in order. Each status transition is a deliberate, recorded event.

- **Backward movement is controlled.** When an item moves backward (for example, a term sheet returning from **FAReview** to **CHANGES_REQUESTED**), it is always the result of an explicit decision by an authorized party, never an automatic or accidental regression.

- **Terminal statuses are final.** Statuses like **Cancelled**, **Rejected**, and **Closed** are endpoints. Once an item reaches a terminal status, it cannot be reactivated or re-entered into the workflow. This prevents confusion about whether a cancelled or rejected item might still be acted upon.

### The Maker-Checker Principle

At the heart of the approval philosophy is the **maker-checker** pattern — a well-established control principle in financial services. The idea is simple but powerful: the person who creates or initiates something should not be the same person who approves it.

On Intain Markets, this principle appears throughout:

- **Borrowers create** term sheets; **Facility Agents review** and approve them.
- **Issuers create** asset sale deals; **Underwriters (Market Makers) review** and approve them.
- **Borrowers submit** funding requests; **Facility Agents review** and approve them.
- **Issuers initiate** repayment; **Investors confirm** receipt.
- **Facility Agents configure** master commitments; **Lenders approve** and e-sign them.

This separation ensures that no single party can unilaterally advance a transaction. Every progression requires at least two parties to agree, reducing the risk of errors, fraud, or miscommunication.

### Role-Based Action Controls

The platform does not merely check whether an action is available — it also checks whether the current user has the authority to perform it. Actions are gated by both status and role:

- Only **Facility Agents** can approve or reject term sheets and funding requests.
- Only **Lenders** can approve master commitments.
- Only **Market Makers** can accept or reject pool mandates.
- Only **Issuers** can publish deals, initiate repayment, and upload loan tapes.
- Only **Investors** can confirm repayment receipt and burn receivables NFTs.

Even if an item is in a status that theoretically allows an action, the action will not appear unless the logged-in user holds the correct role. This means a borrower viewing a term sheet in **FAReview** status will not see approval buttons — only the facility agent will.

### Change Requests vs. Rejection

The platform distinguishes between two types of negative decisions:

- **Change Requests** return the item to the submitter for revision. The item remains editable, and the submitter can make modifications and resubmit. The workflow continues. This is a collaborative mechanism that allows iterative refinement.

- **Rejection** is final. The item cannot be edited or resubmitted. The workflow stops. If the submitter wants to try again, they must create a new item from scratch.

This distinction matters because it preserves workflow integrity while enabling practical collaboration. Most real-world negotiations involve back-and-forth refinement, and change requests accommodate that. Rejection is reserved for situations where the submission is fundamentally unsuitable.

| Aspect | Change Request | Rejection |
|--------|---------------|-----------|
| **Item editable?** | Yes | No |
| **Can resubmit?** | Yes | No |
| **Workflow** | Returns to submitter for revision | Stops permanently |
| **Next step** | Make changes, resubmit | Create a new item |

## What This Enables for Users

### Predictability

Because workflows follow fixed status progressions, users always know what to expect. When you see a deal in **Published** status, you know it has already been created, reviewed, and approved — and you know the next stage is investor commitment. There are no surprises about what comes next or what has already happened.

### Accountability

Every status change is recorded with a timestamp, the identity of the user who triggered it, and any associated notes or decisions. This creates a complete, immutable audit trail. If a term sheet was rejected, you can see who rejected it, when, and why. If a funding request was approved, the approval decision and the approver's identity are permanently recorded.

This audit trail is not just for compliance — it gives all participants confidence that the process is transparent and that every decision can be traced back to a specific person and moment.

### Safety and Error Prevention

The combination of status controls, role-based gates, and maker-checker separation creates multiple layers of protection against errors:

- An issuer cannot accidentally publish an incomplete deal because the platform validates that loans are assigned and terms are configured before allowing publication.
- A facility agent cannot accidentally approve a term sheet they haven't reviewed because the approval action requires an explicit decision.
- An investor cannot burn a receivables NFT before confirming repayment receipt because the burn action is only available after repayment confirmation.

### Trust Between Parties

In multi-party financial transactions, trust is essential but difficult to establish. The platform's structured workflows create trust by ensuring that every party's interests are protected by the process itself. Investors know that deals have been reviewed by underwriters before they see them. Lenders know that facility terms have been reviewed by facility agents. Issuers know that their deals will proceed in an orderly fashion once approved.

## Key Principles to Understand

**Every item has exactly one status at any time.** There is no ambiguity about where something stands. The status is the definitive answer to "What is happening with this item right now?"

**Status controls everything.** Available actions, visible buttons, permitted edits, and allowed transitions are all determined by the current status. The status is not just a label — it is a control mechanism.

**Approvals are gates, not rubber stamps.** Every approval point exists because there is a genuine business need for review at that stage. Approvals require an authorized party to make an active decision — there is no automatic approval or timeout-based progression.

**The audit trail is permanent and complete.** Every status change, every approval decision, every action is recorded. This trail cannot be modified after the fact and serves as the authoritative record of what happened.

**Separation of duties is enforced by the platform.** The maker-checker principle is not a guideline — it is a technical enforcement. The platform will not allow a user to both create and approve the same item, regardless of their role.

**Forward momentum is the default.** The workflow is designed to move items forward through their lifecycle. Backward movement (change requests) is an exception that requires an explicit decision. This keeps transactions progressing toward completion.

Understanding these principles helps you navigate the platform with confidence. When you encounter a disabled button or an unavailable action, it is not a bug — it is the platform enforcing the structured workflow that protects all participants.
