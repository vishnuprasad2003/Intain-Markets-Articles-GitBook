---
title: Signature Visibility
description: Understand who can see signatures and when they're visible in Intain Markets
---

# Signature Visibility

## Overview

Electronic signatures via Adobe Sign are used for term sheets, master commitments, and funding notices. This guide explains who can see signatures and when.

## Term Sheet Signatures

### When Borrower Signs

**Who Signs:** Borrower (via Create Draft button)

**Process:**
1. Borrower clicks **Create Draft**
2. Adobe Sign popup opens
3. Borrower completes signature
4. Status changes to **BorrowerSigned**

**Visibility:**
| Party | Can See? | When |
|-------|----------|------|
| Borrower | Yes | Immediately after signing |
| Facility Agent | Yes | When term sheet is in FAReview |

**Where to View:** Term sheet details → Documents section

## Master Commitment Signatures

### When Lender Signs

**Who Signs:** Lender (via Approve & E-Sign button)

**Process:**
1. Lender clicks **Approve & E-Sign** in Opportunities section
2. Adobe Sign popup opens
3. Lender completes signature
4. Status changes to **ACTIVE** (one lender approval activates)

**Visibility:**
| Party | Can See? | When |
|-------|----------|------|
| Lender | Yes | Their own signature, immediately |
| Facility Agent | Yes | All lender signatures |
| Borrower | Yes | After facility becomes ACTIVE |

**Where to View:** Master commitment details → Documents section

## Funding Notice Signatures

### When Facility Agent Signs

**Who Signs:** Facility Agent (for each lender)

**Process:**
1. Funding request approved → Funding notice generated
2. FA clicks **Approve** on funding notice
3. FA clicks **E-sign (0/n)** - starts e-signature
4. Adobe Sign popup opens for each lender
5. FA signs for that lender
6. Count updates (1/n, 2/n, ... n/n)
7. Each lender's e-sign complete → Visible to that lender

**E-Sign Progress:**
| Status | Meaning |
|--------|---------|
| E-sign (0/3) | No lenders signed yet |
| E-sign (1/3) | FA signed for 1 lender |
| E-sign (2/3) | FA signed for 2 lenders |
| E-sign (3/3) | All lenders signed |

**Visibility:**
| Party | Can See? | When |
|-------|----------|------|
| Facility Agent | Yes | Immediately after signing |
| Lender | Yes | After FA completes e-sign for that lender |
| Borrower | Yes | After FA completes e-signs |

**Where to View:** Credit Facility section → Funding notice details

## Signature Status Fields

### Term Sheet
- Status: **BorrowerSigned** after signing

### Master Commitment
- lenderStatus: 'pending_approval' → 'approved' → 'esignature_completed'
- Facility becomes ACTIVE when at least one lender approves

### Funding Notice
- E-sign count: (0/n) → (n/n)
- Individual lender e-signature tracked
- Each lender can see the funding notice once their e-sign is complete

## Important Notes

**Role-Based Visibility** - What you see depends on your role

**Status-Based Visibility** - Some signatures only visible after certain statuses

**Permanent Records** - Signed documents stored securely, cannot be modified

**Audit Trail** - All signatures recorded with who, when, and details
