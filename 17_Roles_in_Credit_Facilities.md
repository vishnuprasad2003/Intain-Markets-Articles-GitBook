---
title: Roles in Credit Facilities
description: >-
  Borrower, Facility Agent, Lender, Servicer, and Paying Agent responsibilities in a credit facility
---

# Roles in Credit Facilities

In credit facilities, platform roles use different names:

| Platform Role | Credit Facility Name |
|---|---|
| Issuer | **Borrower** |
| Underwriter / Facility Agent | **Facility Agent** |
| Investor | **Lender** |

## What Each Role Does

### Borrower (Issuer)

- Create, sign, and submit the term sheet
- Edit and resubmit when changes are requested
- Map NFT-minted loans to the active facility
- Create, submit, and edit funding requests
- Approve token transfers when a notice is ready to settle

**Dashboard:** **Credit Facility** — shows term sheets, master commitments, and funding requests.

### Facility Agent

- Review term sheets → Approve (creates master commitment), Reject, or Request Changes
- Configure master commitment: add lenders, set shares, create sub-facilities if needed, submit for lender approval
- Complete deal modelling after at least one lender approves
- Review funding requests → Approve (creates funding notice), Reject, or Request Changes
- Approve each funding notice and e-sign once per lender

**Dashboard:** **Credit Facility** — **Set-up** tab for pending items; **Active Facilities** tab for live facilities.

### Lender (Investor)

- Review master commitment (or sub-facility) in **Opportunities** → **Approve & E-Sign**
- One lender's approval activates the facility
- Review funding notice after facility agent signs for them
- Choose payment method, transfer funds, **Confirm and Settle**

**Dashboard:** **Opportunities** for pending approvals; **Credit Facility** for active facilities and notices.

### Servicer

- Upload monthly loan tapes for assigned active deals
- View loan data and deal details

### Paying Agent

- Named on the master commitment by the facility agent; no separate Credit Facility workflow actions

## Permission Summary

| Action | Borrower | Facility Agent | Lender |
|---|---|---|---|
| Create / sign / submit term sheet | ✓ | — | — |
| Approve / reject / request changes on term sheet | — | ✓ | — |
| Configure facility and add lenders | — | ✓ | — |
| Approve & e-sign master commitment | — | — | ✓ |
| Deal modelling | — | ✓ | — |
| Map loans | ✓ | — | — |
| Create / submit funding request | ✓ | — | — |
| Approve / reject funding request | — | ✓ | — |
| E-sign funding notice | — | ✓ | — |
| Review notice, transfer funds, settle | — | — | ✓ |

## Key Notes

- **Status controls buttons** — borrower cannot edit a term sheet while it is **In review**
- **Change requests vs rejection** — changes keep the item open; rejection requires a new item
- **One lender activates the facility** — other lenders can approve later; each is tracked independently
- **Signatures** — borrower signs term sheet; lenders sign commitment; facility agent signs each lender's notice

→ See [Term Sheet Workflow](18_Term_Sheet_Workflow.md) for step-by-step borrower instructions.
→ See [Facility Approval](58_Facility_Approval.md) for lender approval steps.
