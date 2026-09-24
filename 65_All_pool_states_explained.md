---
title: All Pool States Explained
description: Understand all possible pool statuses and what each means
---

# All Pool States Explained

## Overview

This reference lists pool statuses and the loan statuses you see inside a pool. The label can differ by role. The status tells you which actions are available and whether the pool can still be edited.

## Lifecycle Overview

**Preview flow (Share)**

```
Created → Preview → recipient sees Mandate Pending → after accept, Under Review → Deal
```

**Start Deal flow**

```
Created or Preview → Deal → recipient sees Ready for Deal → after accept, Deal confirmed
```

Issuers see Created, Preview, or Deal. Recipients see Mandate Pending, Under Review, or Ready for Deal, depending on the share and whether they have accepted.

Editing becomes more limited as the pool moves toward Deal.

## Status Meanings

### Issuer view

**Created**

Only the issuer who created the pool can see it.

* Full editing: details, organizations, loans, and loan tapes
* Actions: Edit Pool Details, Edit Loan Tape, Share, and map loans from the Loan Registry
* Next: Share, or Start Deal after the pool is ready

**Preview**

The issuer used **Share**. Recipients can review the pool. The issuer can still edit.

* Recipients see Mandate Pending, or Under Review after they accept
* Issuer actions: edit, share with more organizations, manage permissions, and Start Deal when ready
* Next: respond to feedback, then Start Deal

**Deal**

The pool is committed. Structural editing is off.

* Recipients who have not accepted Start Deal still see Ready for Deal. After they accept, they see Deal
* Actions: view the pool and continue deal structuring
* Next: structuring, investor allocation, documents, and closing

### Recipient view

**Mandate Pending**

You received a preview share and have not accepted or rejected.

* Actions: view, Accept, Reject
* Market makers cannot give feedback until they accept

**Under Review**

You accepted the preview share.

* Actions: pool feedback, loan feedback, loan removal requests, and share with investors
* The issuer can still edit

**Ready for Deal**

The issuer clicked **Start Deal**. Loans are finalized, typically with an NFT on each loan.

* Actions: view, Accept, Reject
* Accept confirms the deal

### Loan statuses inside a pool

**Mapped** — The loan is in the pool and counts in metrics. It appears on the Loans tab and in the Loan Tape. Someone can request its removal.

**Pending** — The loan is mapped, and the market maker has not accepted the preview mandate. Acceptance moves it to Accepted.

**Accepted** — The market maker accepted the mandate. The loan is confirmed in the pool.

**Under Reconsider / Reconsider** — Removal was requested. Market makers and investors see Under Reconsider. The issuer sees Reconsider, with a tick to accept removal and a cross to reject it. The loan still counts until the issuer decides.

**Removed** — The issuer accepted the removal. The loan is out of the metrics, stays visible, and can be reinstated.

## What Each Status Indicates

**Created** — The pool is private. Finish the name, asset class, transaction type, organizations, and loan mapping before you share.

**Preview** — Other organizations are reviewing it. You can still edit. Use feedback before you commit.

**Mandate Pending** — Decide whether to accept. Accept moves a market maker to Under Review and turns feedback on. Reject declines the share. The issuer can share again.

**Under Review** — You can comment, request removals, and share with investors. The issuer may change the pool from your feedback.

**Ready for Deal** — Start Deal has been clicked and the usual prerequisites are met. Accept commits the deal. Reject declines it.

**Deal** — The structure is locked. The accepting market maker continues structuring and later steps.

**Removed** — The loan is out of the calculations. It remains visible and can be reinstated.

## Status Transitions Summary

| From Status             | Action            | To Status           | Who                      |
| ----------------------- | ----------------- | ------------------- | ------------------------ |
| (none)                  | Create Pool       | Created             | Issuer                   |
| Created                 | Share (Preview)   | Preview             | Issuer                   |
| Created or Preview      | Start Deal        | Deal                | Issuer                   |
| Mandate Pending         | Accept            | Under Review        | Market Maker             |
| Mandate Pending         | Reject            | Can be shared again | Market Maker             |
| Ready for Deal          | Accept            | Deal (confirmed)    | Market Maker             |
| Ready for Deal          | Reject            | Can be shared again | Market Maker             |
| Mapped (loan)           | Removal requested | Under Reconsider    | Market Maker or Investor |
| Under Reconsider (loan) | Issuer accepts    | Removed             | Issuer                   |
| Under Reconsider (loan) | Issuer rejects    | Mapped or Accepted  | Issuer                   |

## Editing Rights by Status

| Pool Status                      | Issuer can edit         | Recipient actions                              |
| -------------------------------- | ----------------------- | ---------------------------------------------- |
| Created                          | Yes, fully              | Pool is not visible                            |
| Preview                          | Yes, fully              | View, Accept or Reject, feedback after accept  |
| Under Review (market maker view) | Yes, fully              | Feedback, removal requests, share to investors |
| Deal                             | No, structure is locked | View and deal structuring                      |

Pool status is separate from Asset Sale deal status. A pool can stay Created, Preview, or Deal while its Asset Sale deal moves through Draft, Published, Active, Closed, and the other deal statuses. See [Asset Sale Statuses](70_Asset_Sale_Statuses.md).
