---
title: Why Can't I Act
description: Troubleshooting guide for when actions are unavailable in Intain Markets
---

# Why Can't I Act

## Overview

This troubleshooting guide helps you understand why you can't take certain actions and how to resolve common issues.

## Common Issues and Solutions

### Pools

**Q: Why can't I edit my pool?**

| Possible Cause | Solution |
|----------------|----------|
| Pool is in Deal status | Pools cannot be edited after deal finalization |
| You're not the issuer | Only the issuer who created the pool can edit |

**Q: Why can't I share my pool?**

| Possible Cause | Solution |
|----------------|----------|
| Pool not in Created/Preview status | Can only share in Created or Preview status |
| No organizations selected during setup | Edit pool and add organizations first |

**Q: Why can't I click Start Deal?**

| Possible Cause | Solution |
|----------------|----------|
| NFT minting not complete | All loans in pool must have NFTs minted |
| Check Certificates section | Verify batch verification is complete and NFTs minted |

### Loans

**Q: Why can't I map a loan to a pool?**

| Possible Cause | Solution |
|----------------|----------|
| Loan already mapped | A loan can only be in one pool. Unmap first. |
| No pools created | Create a pool first via Set-up Pool |

**Q: Why can't I mint NFTs?**

| Possible Cause | Solution |
|----------------|----------|
| Batch not verified | Complete batch verification first (status: Reviewed) |
| Go to Certificates section | NFT minting is done from Certificates, not Batch Verification |

**Q: Why is Mint NFT button disabled?**

| Possible Cause | Solution |
|----------------|----------|
| Batch status is Pending | Complete verification (Self Certify or via verification agent) |
| Already minted | Check if NFTs are already minted (View NFT button enabled) |

### Term Sheets

**Q: Why can't I submit my term sheet?**

| Possible Cause | Solution |
|----------------|----------|
| Not signed yet | Click Create Draft → complete Adobe Sign |
| Required fields missing | Fill all required fields |
| Documents not uploaded | Upload required documents |

**Q: Why can't I edit my term sheet?**

| Possible Cause | Solution |
|----------------|----------|
| Status is FAReview | Wait for FA decision |
| Status is Accepted | Cannot edit approved term sheets |
| Status is Rejected | Create a new term sheet |

### Master Commitments

**Q: Why can't I create a funding request?**

| Possible Cause | Solution |
|----------------|----------|
| MC not Active | At least one lender must approve |
| Deal modelling not complete | FA must complete Set Up Deal first |
| Check Facility Setup Status | Must show "Completed" |

**Q: Why can't I see the master commitment?**

| Possible Cause | Solution |
|----------------|----------|
| Term sheet not approved | Wait for FA to approve term sheet |
| Check Credit Facility section | MC appears under the term sheet |

### Funding Requests

**Q: Why can't I approve a funding request?**

| Possible Cause | Solution |
|----------------|----------|
| Not in FAReview status | Borrower must submit first |
| Not logged in as FA | Switch to Facility Agent role |

### Funding Notices

**Q: Why can't I see the funding notice as a lender?**

| Possible Cause | Solution |
|----------------|----------|
| FA hasn't completed your e-sign | FA must e-sign for you first |
| Check with FA | Your e-sign must be completed |

**Q: Why can't I Confirm and Settle?**

| Possible Cause | Solution |
|----------------|----------|
| Haven't reviewed the notice | Click Review Funding Notice first |
| Haven't selected payment method | Select payment method during review |

### General

**Q: Why can't I see certain items?**

| Possible Cause | Solution |
|----------------|----------|
| Not shared with you | Item must be shared with your organization |
| Wrong role selected | Log out and log in with correct role |

**Q: Why are all my buttons disabled?**

| Possible Cause | Solution |
|----------------|----------|
| Session expired | Log out and log back in |
| Item in wrong status | Check status badge on the item |
| Waiting for another party | Check who needs to act next |

## How to Diagnose Issues

1. **Check Status** - Look at the item's status badge
2. **Hover Over Button** - Tooltips explain why buttons are disabled
3. **Verify Role** - Ensure you're logged in with correct role
4. **Check Prerequisites** - Review if all required steps are complete
5. **Contact Support** - If issue persists, contact support with details
