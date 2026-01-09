---
title: Why Approvals Exist
description: Understand the purpose and importance of approvals in Intain Markets
---

# Why Approvals Exist

## Overview

Approvals are quality gates that ensure transactions progress correctly while protecting all parties involved.

## Platform Approval Points

### 1. Term Sheet Approval

**Who Approves:** Facility Agent

**What Gets Approved:** Term sheets proposing new credit facilities

**Why It Exists:**
- Ensures facility terms meet requirements
- Verifies borrower documentation is complete
- Validates facility structure is feasible
- Protects lenders by ensuring quality proposals

**What Happens After:**
- Status changes to Accepted
- Master commitment auto-created (Draft status)
- FA can configure facility structure

### 2. Master Commitment Approval

**Who Approves:** Lender (via Approve & E-Sign)

**What Gets Approved:** Complete facility structure configured by FA

**Why It Exists:**
- Ensures lenders agree to terms before activation
- Creates formal commitment between parties
- Validates lender participation amounts

**What Happens After:**
- Status changes to Active (one lender approval activates)
- FA can complete deal modelling
- Borrower can create funding requests (after deal modelling)

### 3. Funding Request Approval

**Who Approves:** Facility Agent

**What Gets Approved:** Borrower's request to draw funds

**Why It Exists:**
- Ensures request complies with facility rules
- Verifies borrowing capacity
- Validates documentation

**What Happens After:**
- Status changes to APPROVED
- Funding notice auto-generated (Pending Token Generated)
- FA can approve and e-sign for lenders

### 4. Funding Notice Processing

**Who Acts:** Facility Agent, then Lenders

**Process:**
1. FA clicks Approve on funding notice
2. FA e-signs for each lender (E-sign 0/n → n/n)
3. Each lender can see the notice once their e-sign is complete
4. Lenders review, transfer funds, Confirm and Settle

**Why It Exists:**
- Ensures proper authorization before lender visibility
- Creates formal signed documents for each lender
- Allows lenders to confirm fund transfers

### 5. Pool Mandate Acceptance

**Who Approves:** Market Maker (Accept button)

**What Gets Approved:** Pools submitted for deal structuring

**Why It Exists:**
- Ensures market maker commits to structuring
- Verifies pool meets requirements
- Creates formal deal commitment

**What Happens After:**
- Status changes to Deal
- Pool is finalized
- Market maker proceeds with structuring

## Why Approvals Matter

**Quality Control** - Every approval ensures review before proceeding

**Risk Management** - Reviewers assess risk before commitment

**Compliance** - Approvals verify regulatory requirements are met

**Accountability** - All decisions are documented with who/when

**Protection** - Both submitters and reviewers are protected

## Approval vs Change Request vs Rejection

| Action | Outcome |
|--------|---------|
| **Approve** | Item proceeds to next stage |
| **Request Changes** | Item returns to submitter for modification |
| **Reject** | Item is finalized as rejected, cannot proceed |
