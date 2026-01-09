---
title: Token Generation and E-Sign
description: Understanding token generation and the e-signature process in credit facilities
---

# Token Generation and E-Sign

## Overview

This guide explains the token generation process and how e-signatures are used in the credit facility module. Token generation occurs when funding notices are created, and e-signatures are required at multiple points in the workflow.

## Token Generation

### When Tokens Are Generated

Tokens are generated at the funding notice stage:

1. **Funding Request Approved** - FA approves the borrower's funding request
2. **Funding Notice Auto-Created** - System generates the funding notice with status **Pending Token Generated**
3. **Token Preparation** - The system prepares tokens for the drawdown

### Token Generation Status

| Status | Meaning |
|--------|---------|
| **Pending Token Generated** | Funding notice created, tokens being prepared |
| **Token Generated** | Tokens ready, awaiting FA approval and e-sign |

## E-Signature Workflow

E-signatures are required at several points in the credit facility workflow:

### 1. Term Sheet E-Sign (Borrower)

**Who Signs:** Borrower
**When:** After creating the term sheet, before submitting to FA

**Process:**
1. Borrower creates term sheet
2. Clicks to sign via Adobe Sign
3. Completes e-signature
4. Status changes to **BorrowerSigned**
5. Can now submit to FA

### 2. Master Commitment E-Sign (Lender)

**Who Signs:** Lender
**When:** When approving the master commitment

**Process:**
1. Lender reviews the master commitment
2. Clicks **Review & Approve**
3. Adobe Sign popup opens
4. Completes e-signature
5. Master commitment becomes **Active**

### 3. Funding Notice E-Sign (Facility Agent)

**Who Signs:** Facility Agent (for each lender)
**When:** After approving the funding notice

**Process:**
1. FA approves the funding notice
2. Action shows **E-sign (0/n)**
3. FA clicks E-sign
4. Adobe Sign popup opens
5. Signs for one lender at a time
6. Count updates: (1/n), (2/n), ... (n/n)
7. Each lender can see the notice once their e-sign is complete

![FA - Token Generation and E-Sign](imagesByMdFilesFolder/40/FA_FundingNotice_Save_TokenGeneration.png)

### E-Sign Progress Tracking

| E-Sign Status | Meaning |
|---------------|---------|
| E-sign (0/3) | No lenders signed yet |
| E-sign (1/3) | Signed for 1 lender |
| E-sign (2/3) | Signed for 2 lenders |
| E-sign (3/3) | All lenders signed |

## Complete Flow

```
1. Borrower creates Term Sheet → E-Sign (Adobe Sign) → Submit
2. FA approves → Master Commitment created
3. FA configures → Lender reviews → E-Sign (Adobe Sign) → Active
4. Borrower creates Funding Request → Submit → FA approves
5. Funding Notice generated (Token Generation)
6. FA approves → E-Sign for each lender (Adobe Sign)
7. Lenders see notice → Transfer funds → Confirm and Settle
8. Tokens transferred to Borrower
```

## Key Points

**Token Generation** - Occurs automatically when funding notices are created from approved funding requests.

**Multiple E-Sign Points** - E-signatures are required from borrowers, lenders, and facility agents at different stages.

**Adobe Sign Integration** - All e-signatures are processed through Adobe Sign for legal validity.

**Per-Lender E-Sign** - Facility agent signs separately for each lender on funding notices.

**Audit Trail** - All signatures and token generation events are recorded for compliance.
