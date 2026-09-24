---
title: Controls and Accountability
description: >-
  How Intain Markets enforces role-based access, status-driven approvals, audit trails, and blockchain immutability
---

# Controls & Accountability

Controls are automatic. You do not switch them on. Your role, the item's status, and any outstanding approvals decide which actions are available.

## Role-Based Access

The person who prepares an item is never the person who approves it.

| Role | Cannot |
|---|---|
| Issuer / Borrower | Approve own term sheet or funding request; accept pool mandate |
| Facility Agent / Market Maker | Create term sheets, pools, or funding requests |
| Lender / Investor | Create a facility, approve a funding request, or publish a deal |
| Underwriter | Create a deal or commit as an investor |
| Admin | Skip an approval; change data while viewing as another user |

## Status-Driven Workflow

Items move through statuses in order. Buttons match the current status. Steps cannot be skipped.

- **Pools:** Created → Preview → Mandate Pending → Under Review → Deal
- **Term sheets:** Draft → Signed → In review → Accepted / Rejected / Changes Requested
- **Facilities:** Draft → Pending → Active
- **Funding requests:** Draft → In review → Approved / Rejected / Changes Requested
- **Asset Sale deals:** Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed

## Required Approvals Before Proceeding

- Term sheet approval → facility created
- Lender signed approval → facility becomes Active
- Funding request approval → funding notice created
- Funding notice signed per lender → lender can see the notice
- Market maker mandate acceptance → pool moves to Deal
- Underwriter approval → investors can commit
- Admin KYC approval → new user gets full access

## One-Time Code (OTP) for Sensitive Steps

| Action | Who |
|---|---|
| Mint NFTs | Issuer |
| Transfer NFTs during settlement | Issuer |
| Approve a token transfer | Issuer |
| Move funds in a distribution | Paying Agent |

A saved sign-in is not enough. If the code is missing or expired, the action stops.

## Validation Before Submission

Required fields and documents are checked before any submission is accepted. Missing items are rejected with a specific message — nothing is half-saved.

- Term sheets: commitment amount, advance rate, margin, pricing index / fixed rate, maturity date
- Funding requests: draw amount, purpose, funding date, required documents
- Funding requests are checked against the facility's remaining capacity

## Admin Impersonation (View As)

- **Read-only.** Admin sees the same screens but cannot create, edit, approve, or submit.
- **Activity log names both.** It records the admin and the user being viewed.
- **One session at a time.** A second view-as session cannot be started on top of the first.

## What Gets Recorded

Every status change stores: who changed it, when, old value, new value. Approvals store: who approved, when, any comments. Rejections store: who rejected, when, reason. Document uploads store: who uploaded, when.

Blockchain steps (minting, token transfer, settlement, repayment) also produce an on-chain transaction reference that can be verified outside the platform.

→ See [End-to-End Traceability](75_End-to-end_traceability.md) for audit trail details.
→ See [Who Can Do What](74_Who_can_do_what.md) for the full role-permission matrix.
