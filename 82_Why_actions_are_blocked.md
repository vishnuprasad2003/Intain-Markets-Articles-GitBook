---
title: Why Actions Are Blocked
description: Common reasons actions are unavailable and how to resolve them
---

# Why Actions Are Blocked

→ See also [Why Can't I Act](83_Why_cant_I_act.md) · [Enabled vs Disabled Actions](69_Enabled_vs_Disabled_actions.md)

An action stays blocked until **your role**, the **item's status**, and any **earlier steps** all line up.

## Common Causes

| Cause | Example | Fix |
|---|---|---|
| Wrong status | Can't submit a term sheet in Draft until signed | Finish the earlier step |
| Missing step | Can't mint NFTs until batch is Reviewed | Complete batch verification first |
| Someone else must act | Term sheet is In Review; waiting for facility agent | Wait for notification |
| Wrong role | Only facility agent can approve a term sheet | Sign in with the correct role |
| Already done | Item is already approved | Move to the next step |

## By Item Type

### Pools
| Blocked | Reason | Fix |
|---|---|---|
| Edit | Status is Deal | Editing stops after deal is accepted |
| Start Deal | NFTs not minted | Finish NFT minting in Certificates |
| Share | No organisations selected | Edit pool to add organisations |

### Loans
| Blocked | Reason | Fix |
|---|---|---|
| Map to Pool | Already in a pool | Unmap from current pool first |
| Mint NFT | Batch not Reviewed | Finish Self Certify or verification agent review |
| Add to Batch | Already in a batch | Remove from current batch first |

### Term Sheets
| Blocked | Reason | Fix |
|---|---|---|
| Submit to FA | Not signed | Click Create Draft → sign via Adobe Sign |
| Edit | Status is In Review or Accepted | Wait for facility agent, or create new |

### Master Commitments
| Blocked | Reason | Fix |
|---|---|---|
| Create Funding Request | Not Active, or deal modelling not Completed | Lender must approve; facility agent must finish Set Up Deal |
| Edit configuration | Status is Active or Pending | Only editable in Draft |

### Funding Notices
| Blocked | Reason | Fix |
|---|---|---|
| Lender can't see notice | Facility agent hasn't signed for them | FA must complete e-sign for that lender |
| Confirm and Settle | Review not done | Click Review Funding Notice first |

### Asset Sale
| Blocked | Reason | Fix |
|---|---|---|
| Publish deal | No loans assigned or sale terms missing | Assign loans and complete sale terms |
| Start repayment | Deal not Active, or loan tape not uploaded | Upload loan tape and save mapping |
| Burn NFT | Repayment not confirmed | Confirm Repayment Receipt first |

## How to Diagnose

1. Read the item's current status
2. Hover the button — the tooltip shows the reason
3. Confirm your role matches the required one
4. Check that all earlier steps are complete
5. If unresolved, contact support with the item reference and status
