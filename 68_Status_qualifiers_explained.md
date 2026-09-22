---
title: Status Qualifiers Explained
description: Understand status qualifiers that provide additional context about item states
---

# Status Qualifiers Explained

## Overview

Statuses in Intain Markets often include qualifiers that provide additional context. This guide explains what each qualifier means.

## Common Status Qualifiers

### "Pending" Qualifier

**Meaning:** Waiting for someone to take action

**Examples:**
| Status | Meaning |
|--------|---------|
| Mandate Pending | Pool waiting for market maker to accept/reject |
| PendingLenderApproval | MC waiting for lender to approve |
| Pending Token Generated | Funding notice waiting for FA to process |

**What to Do:** Wait for the other party to act, or if you're that party, take action

### "Review" Qualifier

**Meaning:** Being reviewed by someone

**Examples:**
| Status | Who Reviews |
|--------|-------------|
| FAReview (Term Sheet) | Facility Agent |
| FAReview (Funding Request) | Facility Agent |
| Under Review (Pool) | Market Maker or Investor |

**What to Do:** If you're the reviewer, make a decision. If you're the submitter, wait.

### "Requested" Qualifier

**Meaning:** Changes needed before proceeding

**Examples:**
| Status | What's Needed |
|--------|---------------|
| CHANGES_REQUESTED (Term Sheet) | Borrower must edit and resubmit |
| CHANGES_REQUESTED (Funding Request) | Borrower must edit and resubmit |

**What to Do:** Make the requested changes and resubmit

### "Active" Qualifier

**Meaning:** Item is operational and ready for use

**Examples:**
| Status | What It Means |
|--------|---------------|
| ACTIVE (Master Commitment) | Facility is operational, borrower can create funding requests |

**What to Do:** Proceed with operations (funding requests, etc.)

### "Approved" Qualifier

**Meaning:** Item has been approved

**Examples:**
| Status | What Happens Next |
|--------|-------------------|
| APPROVED (Funding Request) | Funding notice auto-generated |
| Accepted (Term Sheet) | Master commitment auto-created |

**What to Do:** Proceed to next stage

### "Rejected" Qualifier

**Meaning:** Item has been declined (final)

**Examples:**
| Status | What to Do |
|--------|------------|
| Rejected (Term Sheet) | Create new term sheet |
| REJECTED (Funding Request) | Create new funding request |

**What to Do:** Create a new item addressing the rejection reasons

### "Signed" Qualifier

**Meaning:** E-signature completed

**Examples:**
| Status | What It Means |
|--------|---------------|
| BorrowerSigned (Term Sheet) | Borrower has signed, can now submit to FA |

**What to Do:** Proceed to submission

### "Mapped/Unmapped" Qualifier (Loans)

**Meaning:** Loan pool assignment status

| Status | Meaning |
|--------|---------|
| Mapped | Loan is assigned to a pool |
| Unmapped | Loan exists but not assigned to any pool |

**What to Do:** Map loans from Loan Registry using Map to Pool button

### Verification Status Qualifiers (Batches)

| Status | Meaning |
|--------|---------|
| Pending | Not yet verified |
| Reviewed | Verification complete |
| Certified | Verified by third-party agent |
| Self Certified | Verified by issuer (via verification agent login) |
| Self Certify (Data Only) | Self-certified by issuer directly |

## How Qualifiers Help

**Clarify Position:** Know exactly where an item is in its workflow

**Indicate Next Steps:** Understand what needs to happen next

**Explain Actions:** Understand why certain buttons are enabled/disabled

**Track Progress:** Monitor progression through workflows

## Quick Reference

| Qualifier | You're Waiting? | Action Required By |
|-----------|-----------------|-------------------|
| Pending | Yes | Other party |
| Review | Maybe | Reviewer decides |
| Requested | No | You (make changes) |
| Active | No | Ready for operations |
| Approved | No | Proceed to next step |
| Rejected | No | Create new item |
| Signed | No | Proceed to submit |

## Asset Sale Status Qualifiers

Asset Sale deals use a distinct set of status qualifiers that track the transaction lifecycle from deal creation through settlement and repayment.

### Asset Sale Deal Statuses

| Status | Meaning |
|--------|---------|
| **Draft** | Deal created, issuer is configuring details and assigning loans |
| **Pending Review** | Issuer has submitted the deal for underwriter review |
| **Published** | Underwriter approved; deal is visible to investors for commitment |
| **Cancelled** | Deal was cancelled before progressing further |
| **Commit** | Investors are submitting commitments to the deal |
| **Invest** | Commitments finalized; investors are allocated and ready to fund |
| **Settlement In Progress** | Funds and NFTs are being exchanged between parties |
| **Settled** | All settlement steps completed successfully |
| **Active** | Deal is active and operational post-settlement |
| **Repayment In Progress** | Issuer has initiated repayment to investors |
| **Closed** | Repayment completed and deal is closed |
| **Defaulted** | Deal has defaulted on repayment obligations |

### How Deal Status Drives Actions

The Asset Sale deal status determines which call-to-action (CTA) buttons are available at each stage. For example:

- **"Publish"** is only available when the deal is in **Draft**
- **"Approve/Reject"** is only available when the deal is in **Pending Review**
- **"Submit Commitment"** is only available when the deal is **Published**
- **"Initiate Repayment"** is only available when the deal is **Active**

This ensures that actions are performed in the correct sequence and by the correct role.

### Settlement Substates

During **Settlement In Progress**, the platform tracks per-investor settlement progress through substates:

| Substate | Meaning |
|----------|---------|
| Payment Sent | Investor has sent payment to the issuer |
| Payment Confirmed | Issuer has confirmed receipt of payment |
| NFT Transferred | Loan NFTs have been transferred to the investor |

Each investor's settlement progresses independently, allowing the platform to track partial settlement across multiple investors.
