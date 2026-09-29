---
title: Securitization Roles & Permissions
description: Complete role permissions reference for the Securitization module — what each role can do, when actions are blocked, and MFA requirements.
---

# Securitization Roles & Permissions

This article summarizes what each role can do in a Securitization deal, when actions are blocked by deal status, and which actions require MFA.

---

## Role Permissions Overview

### Issuer

| Action | Requirement |
|--------|-------------|
| Create a deal from a pool | Pool must be in Deal status |
| View deal details and tranches | Any deal they created |
| Approve FT contract per tranche | MFA + on-chain wallet signing required |
| Close a deal | Deal must be Open |

### Underwriter

| Action | Requirement |
|--------|-------------|
| Create a deal from a pool | Pool must be in Deal status |
| Add tranches to a deal | Deal must be in Created status |
| Delete tranches | Deal must be in Created status |
| Approve deal (Awaiting Approval → Open) | Deal must be in Awaiting Approval status |
| Reject deal | Deal must be in Awaiting Approval status |
| Open Commit phase | Deal must be Open |
| Switch to Invest phase + select payment mode | Deal must be Open and in Commit phase |
| View all deal details | Any deal assigned to them |

### Investor

| Action | Requirement |
|--------|-------------|
| View deal details and tranches | Deal must be Open |
| Commit to a tranche | Deal must be in Open/Commit phase; tranche must be Approved; Available Commitments > 0 |
| Invest in a committed tranche | Deal must be in Invest phase; investor must have a commitment |
| View their FT token balance | After FTs are delivered |

### Paying Agent

| Action | Requirement |
|--------|-------------|
| Deliver FTs to investors | FT contract must be approved by Issuer; MFA required |
| Deliver FTs to one investor | Specific investor must have completed investment |
| Create and manage accounts | Deal must be Open |
| Record transactions in ledger | Any Open deal account |
| View all deal and investor details | Any deal assigned to them |

### Rating Agency

| Action | Requirement |
|--------|-------------|
| View deal details | Pool/deal must be shared with them |
| View tranche information | Read-only access |

> **Note:** Rating Agency cannot commit, invest, create deals, manage accounts, or perform any write action.

---

## Permissions by Deal Status

| Action | Created | Awaiting Approval | Open | Closed |
|--------|---------|-------------------|------|--------|
| Edit deal fields | ✓ | ✗ | ✗ | ✗ |
| Add/delete tranches (Underwriter) | ✓ | ✗ | ✗ | ✗ |
| Approve deal (Underwriter) | ✗ | ✓ | ✗ | ✗ |
| Open Commit phase (Underwriter) | ✗ | ✗ | ✓ | ✗ |
| Switch to Invest phase (Underwriter) | ✗ | ✗ | ✓ | ✗ |
| Investor commit | ✗ | ✗ | ✓ (Commit phase only) | ✗ |
| Investor invest | ✗ | ✗ | ✓ (Invest phase only) | ✗ |
| Issuer FT approval | ✗ | ✗ | ✓ | ✗ |
| Paying Agent FT delivery | ✗ | ✗ | ✓ | ✗ |
| Manage accounts/transactions | ✗ | ✗ | ✓ | ✓ (read-only) |

---

## Actions Blocked by Phase

| Action | Blocked When |
|--------|-------------|
| Investor commit | Deal is in Invest phase, Awaiting Approval, Created, or Closed |
| Investor invest | Deal is in Commit phase, Awaiting Approval, Created, or Closed |
| Commit exceeding Available Commitments | Available Commitments = 0 for that tranche |
| Second commitment by same investor to same tranche | One commitment per investor per tranche — enforced by system |
| FT delivery | FT contract not yet approved by Issuer |
| FT approval | No investors have completed investment in the tranche |

---

## MFA Requirements

Two actions in Securitization require Multi-Factor Authentication (MFA):

| Action | Role | MFA Type |
|--------|------|----------|
| **FT contract approval** | Issuer | One-time password (OTP) + on-chain wallet signature |
| **FT delivery to investors** | Paying Agent | One-time password (OTP) |

MFA codes expire after a short window. If you enter an invalid or expired code, the action is rejected and you must generate a new code.

---

## Related Articles

→ See [Securitization Overview](88_Securitization_Overview.md) for a summary of all roles in context.  
→ See [Token Approval & FT Delivery](93_Token_Approval_and_FT_Delivery.md) for the MFA-gated FT workflow.  
→ See [Deal Lifecycle & Statuses](89_Securitization_Deal_Lifecycle_and_Statuses.md) for status definitions.
