---
title: Why Actions Are Blocked
description: Understand common reasons actions are blocked and how to resolve them
---

# Why Actions Are Blocked

## Overview

An action stays blocked until the status, your role, and any earlier steps all line up. Use this page to see the usual cause and what to do next.

## Frequently Asked Questions

### Why is this action blocked?

**Wrong status**

* You cannot submit a term sheet in Draft until it is signed.
* You cannot edit a term sheet in Under Review.
* You cannot create a funding request until the master commitment is ACTIVE.

Check the status and finish the step that moves it forward.

**A required step is missing**

* The term sheet is not signed in Adobe Sign.
* NFTs cannot be minted until batch verification is complete.
* A funding request stays off until deal modelling is complete.

Finish that step first.

**Someone else must act**

* The term sheet is in Under Review.
* The master commitment is in Pending Lender Approval.
* You do not see a funding notice because the facility agent has not signed for you.

Wait for that person. You will be notified when it is your turn.

**Wrong role**

* Only a facility agent can approve a term sheet.
* Only a lender can approve a master commitment.
* Only the issuer who created a pool can edit it.

Sign in with the role that owns the action.

**Already done**

* The term sheet was already submitted.
* The NFTs were already minted.
* The item was already approved.

Go to the next step.

### Pools

| Blocked action | Usual reason              | What to do                            |
| -------------- | ------------------------- | ------------------------------------- |
| Edit pool      | Status is Deal            | Editing stops after the deal is final |
| Start Deal     | NFTs are not minted       | Finish NFT minting                    |
| Share pool     | No organizations selected | Edit the pool and add organizations   |

### Loans

| Blocked action | Usual reason          | What to do                      |
| -------------- | --------------------- | ------------------------------- |
| Map to Pool    | Already in a pool     | Unmap it from that pool first   |
| Mint NFT       | Batch is not verified | Finish batch verification       |
| Add to Batch   | Already in a batch    | Remove it from that batch first |

### Term sheets

| Blocked action | Usual reason           | What to do                            |
| -------------- | ---------------------- | ------------------------------------- |
| Submit to FA   | Not signed             | Create Draft and finish the e-sign    |
| Edit           | Status is Under Review | Wait for the facility agent           |
| Edit           | Status is Accepted     | Approved term sheets cannot be edited |

### Master commitments

| Blocked action         | Usual reason               | What to do                                         |
| ---------------------- | -------------------------- | -------------------------------------------------- |
| Create Funding Request | Not ACTIVE                 | Wait for a lender to approve                       |
| Create Funding Request | Deal modelling is not done | The facility agent must finish Set Up Deal         |
| Edit configuration     | Status is ACTIVE           | An active facility cannot be reconfigured this way |

### Funding requests

| Blocked action | Usual reason           | What to do                         |
| -------------- | ---------------------- | ---------------------------------- |
| Approve        | Status is DRAFT        | The borrower must submit first     |
| Edit           | Status is Under Review | Wait for the facility agent        |
| Edit           | Status is APPROVED     | Approved requests cannot be edited |

### Funding notices

| Blocked action       | Usual reason            | What to do                           |
| -------------------- | ----------------------- | ------------------------------------ |
| Lender cannot see it | Your e-sign is not done | The facility agent must sign for you |
| Confirm and Settle   | Review is not done      | Open Review Funding Notice first     |

### How do I tell what is wrong?

1. Read the status on the item.
2. Hover the button. The tooltip explains why it is off.
3. Confirm your role.
4. Check that earlier steps are finished.
5. Open notifications for anything still pending.

| If you cannot…                   | Check…                                                       |
| -------------------------------- | ------------------------------------------------------------ |
| Submit a term sheet              | Is it signed?                                                |
| Create a funding request         | Is the master commitment ACTIVE? Is deal modelling complete? |
| Mint an NFT                      | Is the batch Reviewed?                                       |
| See a funding notice as a lender | Has the facility agent signed for you?                       |
| Edit an item                     | Is the status Draft or Changes Requested?                    |
| Approve an item                  | Are you in the approving role?                               |
| Publish an asset sale deal       | Are loans assigned and sale terms set?                       |
| Start repayment                  | Is the deal Active? Is the loan tape uploaded and mapped?    |
| Burn an NFT                      | Have you confirmed repayment receipt?                        |

### Asset sale

**Why can’t I publish my asset sale deal?**

The deal must be in Draft, with at least one loan assigned and the required sale terms filled in.

**Why can’t I start repayment?**

The deal must be Active. Upload the latest loan tape and save the field mapping. Only an Issuer can start repayment.

**Why can’t I burn my NFT?**

Confirm repayment receipt first. Open Investment Operations, then Confirm Repayment Receipt. Return to Asset Analysis, then Receivables, to burn.

---

→ See [Enabled vs Disabled Actions](69_Enabled_vs_Disabled_actions.md) · [Why Approvals Exist](71_Why_approvals_exist.md)
