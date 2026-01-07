---
title: Signature Visibility
description: Understand who can see signatures and when they're visible in Intain Markets
---

# Signature Visibility

## Overview

Electronic signatures are used for term sheets, master commitments, and funding notices. This guide explains who can see signatures, when they're visible, and how signature status is tracked.

## Term Sheet Signatures

**Borrower Signature** - When borrower signs:
- Borrower sees signature immediately after signing
- Facility agent sees signature when term sheet is in FAReview status
- Status changes to "BorrowerSigned" after completion
- Visible in term sheet's document section

**Who Can See:** Borrowers and facility agents

**When Visible:** Immediately after signing, remains visible throughout workflow

## Master Commitment Signatures

**Lender Signatures** - When lenders sign:
- Each lender sees their own signature after signing
- Facility agent sees all lender signatures
- Borrower sees lender signatures after facility becomes ACTIVE
- Individual lender signature status tracked in lenderGroups array (lenderStatus field)

**Who Can See:** Lenders see their own, facility agents see all, borrowers see after activation

**When Visible:** After e-signature completion, remains visible throughout facility lifecycle

## Funding Notice Signatures

**Facility Agent Signature** - When facility agent signs:
- Facility agent sees signature after signing
- Borrower sees signature after signing
- Lenders see signature when funding notice is visible to them
- Signature tracked per lender in tokenDistribution array

**Per-Lender Signing** - Facility agent signs separately for each lender:
- Each lender's signature status tracked individually
- esignatureStatus field shows 'pending' or 'ESIGN_COMPLETED'
- Each lender sees their specific signed document

**Who Can See:** Facility agents, borrowers, and lenders based on role and funding notice status

**When Visible:** After completion, remains visible throughout funding notice lifecycle

## Signature Status Tracking

**Term Sheet** - Status changes to "BorrowerSigned" after DocuSign completion. Signed PDF stored in IPFS.

**Master Commitment** - lenderStatus in lenderGroups array shows 'pending_approval', 'approved', or 'esignature_completed'. Facility becomes ACTIVE when at least one lender approves. Signed PDF stored in IPFS.

**Funding Notice** - esignatureStatus in tokenDistribution array shows 'pending' or 'ESIGN_COMPLETED' for each lender. eSignaturePendingCount tracks remaining lenders. eSignatureStatus shows aggregate status.

## Accessing Signed Documents

**Term Sheets** - Navigate to term sheet details → Documents section → View signed PDF

**Master Commitments** - Navigate to master commitment details → Documents section → View signed PDF with all lender signatures

**Funding Notices** - Navigate to funding notice details → Documents section → View signed PDF for your lender allocation

## Important Notes

**Role-Based Visibility** - Signature visibility depends on role and workflow stage.

**Status Controls Visibility** - Some signatures visible only when items reach certain statuses (e.g., lender signatures visible to borrowers after facility becomes ACTIVE).

**Audit Trail** - All signatures recorded with who signed, when, and signature details.

**Permanent Records** - Signed documents stored in IPFS. Signatures cannot be removed or modified once completed.

**Signature Requirements** - Term sheets must be signed before submission. Master commitments must be signed before activation. Funding notices must be signed before lender review.
