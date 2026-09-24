---
title: Status Qualifiers Explained
description: Understand status qualifiers that provide additional context about item states
---

# Status + Qualifiers Explained

## Overview

A status tells you where an item sits in its workflow. Many statuses also carry a qualifier — a word such as Pending, In review, or Changes Requested — that tells you who needs to act next. This guide explains those words and what you should do when you see them. The same word can appear on a term sheet, a funding request, a pool, or a deal. The meaning stays the same even when the item type changes.

## Common Status Qualifiers

### "Pending" Qualifier

**Meaning:** Someone still has to act. The item is waiting.

**Examples:**

| Status                  | Meaning                                                                        |
| ----------------------- | ------------------------------------------------------------------------------ |
| Mandate Pending         | A pool is waiting for the market maker to accept or decline the mandate        |
| Pending                 | A facility is waiting for a lender to approve it                               |
| Pending Token Generated | A funding notice is waiting for the facility agent to finish processing tokens |

**What to Do:** If you are the person named in the status, take the action. If you are waiting on someone else, the item stays as it is until they do.

### "Review" Qualifier

**Meaning:** A reviewer has the item and has not decided yet. On screen this often appears as **In review**.

**Examples:**

| Status                           | Who Reviews              |
| -------------------------------- | ------------------------ |
| In review (term sheet)           | Facility agent           |
| In review (funding request)      | Facility agent           |
| Under Review (pool)              | Market maker or investor |
| Pending Review (Asset Sale deal) | Underwriter              |

**What to Do:** If you are the reviewer, approve, reject, or request changes. If you submitted the item, wait for that decision. You usually cannot edit it while it is in review.

### "Requested" Qualifier

**Meaning:** The reviewer needs changes before they can continue. On screen this appears as **Changes Requested**.

**Examples:**

| Status                              | What's Needed                                          |
| ----------------------------------- | ------------------------------------------------------ |
| Changes Requested (term sheet)      | The borrower edits the term sheet and submits it again |
| Changes Requested (funding request) | The borrower edits the request and submits it again    |

**What to Do:** Read the comments, make the changes, and resubmit the same item. For a term sheet, you also sign again before you submit. This is not a rejection. The same item stays open.

### "Active" Qualifier

**Meaning:** The item is in force and can be used.

**Examples:**

| Status                   | What It Means                                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Active (facility)        | Lenders have approved. The borrower can map loans and create funding requests after deal modelling is complete |
| Active (Asset Sale deal) | Settlement is finished. The issuer can start repayment when it is due                                          |

**What to Do:** Continue the work that this status unlocks. Do not treat Active as “finished.” It means the next operating step is available.

### "Approved" Qualifier

**Meaning:** A reviewer has accepted the item, and the next record is created from that decision.

**Examples:**

| Status                      | What Happens Next                         |
| --------------------------- | ----------------------------------------- |
| Approved (funding request)  | A funding notice is created automatically |
| Accepted (term sheet)       | The facility is created automatically     |
| Published (Asset Sale deal) | Investors can see the deal and commit     |

Term sheets use **Accepted** for this outcome. Funding requests use **Approved**. Both mean the reviewer said yes and the workflow moves forward.

**What to Do:** Open the next item the platform created, or wait for the next party if the next step is theirs.

### "Rejected" Qualifier

**Meaning:** The reviewer declined this item. The decision is final for this item.

**Examples:**

| Status                     | What to Do                   |
| -------------------------- | ---------------------------- |
| Rejected (term sheet)      | Create a new term sheet      |
| Rejected (funding request) | Create a new funding request |

**What to Do:** Read the reason, then start a new item that addresses it. You can still open the rejected item, but you cannot edit it or send it back.

### "Signed" Qualifier

**Meaning:** The required electronic signature is done.

**Examples:**

| Status              | What It Means                                                               |
| ------------------- | --------------------------------------------------------------------------- |
| Signed (term sheet) | The borrower has signed and can submit the term sheet to the facility agent |

**What to Do:** Submit the item if you are the person who just signed. If someone else must sign next, wait until their signature is recorded. A funding notice shows signature progress as a count, such as 1 of 3, until every required signature is complete.

### "Mapped/Unmapped" Qualifier (Loans)

**Meaning:** Whether a loan has been assigned to a pool.

| Status   | Meaning                                         |
| -------- | ----------------------------------------------- |
| Mapped   | The loan is assigned to a pool                  |
| Unmapped | The loan exists and is not assigned to any pool |

**What to Do:** From the Loan Registry, use **Map to Pool** for loans that should be included. A loan cannot be mapped twice.

### Verification Status Qualifiers (Batches)

| Status                   | Meaning                                                             |
| ------------------------ | ------------------------------------------------------------------- |
| Pending                  | Not yet verified                                                    |
| Reviewed                 | Verification is complete                                            |
| Certified                | A verification agent certified the batch                            |
| Self Certified           | The issuer certified the batch through a verification agent sign-in |
| Self Certify (Data Only) | The issuer self-certified the batch directly                        |

**What to Do:** Leave Pending batches until verification finishes. Reviewed, Certified, and self-certified batches can move on to the next step, such as minting, when your role allows it.

## How Qualifiers Help

**They show position.** You can tell whether an item is still being prepared, waiting on a reviewer, or already decided.

**They show the next step.** Pending means wait or act, depending on whether you are the party named. Changes Requested means you edit and resubmit. Rejected means you start over.

**They explain the buttons.** A button is available only when the status allows that action. If **Submit** is missing, the item is probably not signed yet. If **Edit** is missing, the item is in review, approved, or rejected.

**They show progress.** Watching the qualifier change is how you follow a term sheet, a pool, or a deal without opening every screen.

## Quick Reference

| Qualifier            | You're Waiting? | Action Required By                |
| -------------------- | --------------- | --------------------------------- |
| Pending              | Yes             | The other party                   |
| In review            | Maybe           | The reviewer                      |
| Changes Requested    | No              | You (make the changes)            |
| Active               | No              | Ready for the next operating step |
| Approved or Accepted | No              | Continue to the next stage        |
| Rejected             | No              | Create a new item                 |
| Signed               | No              | Submit, if you are the signer     |

## Asset Sale Status Qualifiers

Asset Sale deals use their own statuses. They track the deal from creation through settlement and repayment. These names appear on the deal itself.

### Asset Sale Deal Statuses

| Status                     | Meaning                                                        |
| -------------------------- | -------------------------------------------------------------- |
| **Draft**                  | The issuer is still setting up the deal and assigning loans    |
| **Pending Review**         | The issuer has sent the deal to the underwriter                |
| **Published**              | The underwriter approved it. Investors can commit              |
| **Cancelled**              | The deal was cancelled before it went further                  |
| **Commit**                 | Investors are submitting commitments                           |
| **Invest**                 | Commitments are set. Investors are allocated and ready to fund |
| **Settlement In Progress** | Funds and loan NFTs are being exchanged                        |
| **Settled**                | Settlement steps are complete                                  |
| **Active**                 | The deal is operating after settlement                         |
| **Repayment In Progress**  | The issuer has started repayment to investors                  |
| **Closed**                 | Repayment is complete and the deal is closed                   |
| **Defaulted**              | The deal has defaulted on repayment                            |

### How Deal Status Drives Actions

The deal status controls which buttons you see:

* **Publish** is available when the deal is **Draft**
* **Approve** and **Reject** are available when the deal is **Pending Review**
* **Submit Commitment** is available when the deal is **Published**
* **Initiate Repayment** is available when the deal is **Active**

The sequence keeps each action with the right role. An issuer cannot approve their own deal, and an investor cannot commit before the deal is published.

### Settlement Substates

While a deal is **Settlement In Progress**, each investor is tracked separately:

| Substate          | Meaning                                     |
| ----------------- | ------------------------------------------- |
| Payment Sent      | The investor has sent payment to the issuer |
| Payment Confirmed | The issuer has confirmed that payment       |
| NFT Transferred   | The loan NFTs have moved to the investor    |

One investor can be at Payment Confirmed while another is still at Payment Sent. The deal stays in Settlement In Progress until the required investors finish.
