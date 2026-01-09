---
title: Funding Notice Processing Overview
description: Overview of how funding notices are processed from creation to lender visibility
---

# Funding Notice Processing Overview

## Overview

This guide provides an overview of how funding notices are processed, from the moment a funding request is approved until lenders can see and act on the funding notice. The process involves the facility agent approving and e-signing for each lender.

## Funding Notice Flow

When a funding request is approved, the following process occurs:

### 1. Funding Notice Auto-Generated

**What Happens:**
- Funding notice is automatically created
- Status: **Pending Token Generated**
- Contains all details from the funding request

**Who Acts:** System (automatic)

### 2. Facility Agent Approves

**What Happens:**
- Facility agent reviews the funding notice
- Clicks **Approve**
- Prepares notice for e-signature process

**Who Acts:** Facility Agent

### 3. Facility Agent E-Signs for Each Lender

**What Happens:**
- Action shows **E-sign (0/n)** where n = number of lenders
- Facility agent clicks E-sign
- Adobe Sign popup opens
- Signs for one lender at a time
- Count updates: (1/n), (2/n), ... (n/n)

**Who Acts:** Facility Agent

**Progress Tracking:**
| E-Sign Status | Meaning |
|---------------|---------|
| E-sign (0/3) | No lenders signed yet |
| E-sign (1/3) | Signed for 1 lender |
| E-sign (2/3) | Signed for 2 lenders |
| E-sign (3/3) | All lenders signed |

### 4. Funding Notice Visible to Lenders

**What Happens:**
- As each lender's e-sign is completed
- That lender can see the funding notice in their Credit Facility section
- Each lender gains visibility once their e-sign is done

**Who Acts:** Lenders can act once their e-sign is complete

### 5. Lenders Review and Transfer

**What Happens:**
- Lenders click **Review Funding Notice**
- Review drawdown details and allocation
- Select payment method
- Transfer funds
- Click **Confirm and Settle**

**Who Acts:** Lenders

### 6. Process Complete

**What Happens:**
- Tokens transferred to borrower
- Borrower receives funds
- Drawdown complete

## Summary Flow

```
Funding Request APPROVED
       ↓
Funding Notice Auto-Generated (Pending Token Generated)
       ↓
FA clicks Approve
       ↓
FA E-signs for each lender (0/n → n/n)
       ↓
Each lender's e-sign complete → Funding Notice VISIBLE TO THAT LENDER
       ↓
Lenders review → Transfer funds → Confirm and Settle
       ↓
Tokens transferred to Borrower
```

## Key Points

**Auto-Generation** - Funding notices are automatically created when funding requests are approved.

**FA Approval Required** - The facility agent must approve the funding notice.

**Per-Lender E-Sign** - The facility agent signs for each lender individually via Adobe Sign.

**Visibility After E-Sign** - Each lender sees the funding notice once the facility agent has completed their individual e-sign.

**Individual Lender Process** - Each lender reviews, transfers, and confirms independently.
