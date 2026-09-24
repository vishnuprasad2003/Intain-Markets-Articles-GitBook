---
title: Enabled vs Disabled Actions
description: Understand why actions are enabled or disabled in Intain Markets
---

# Enabled vs Disabled Actions

## Overview

A button is on or off based on your role, the item’s status, and whether earlier steps are finished.

## Roles Covered

Actions below are grouped by the person who can take them: Issuer, Market Maker, Investor, Borrower, Facility Agent, Lender, and Underwriter. If you are in a different role, the button stays off.

## What Each Role Can Do

### Pool actions

**Created — Issuer**

* On: Edit pool details, add or remove loans, share the pool
* Off: Start Deal, until NFT minting is complete

**Preview — Issuer**

* On: Edit, respond to feedback, share with more organizations, Start Deal if NFTs are minted, accept or reject loan removal requests

**Preview — Market Maker**

* On: View, Accept, Reject
* Off: Edit (issuer only), feedback until you accept the mandate

**Under Review — Market Maker**

* On: Feedback, request loan removal, share to investors
* Off: Edit

**Under Review — Investor**

* On: View. Feedback and download only if those permissions were turned on for your share
* Off: Edit

**Deal — Issuer**

* On: View
* Off: Edit and Share. The deal is committed

### Loan actions

**Loan Registry — Issuer**

* On: Map to Pool if the loan is not already in a pool. Add to Batch if the loan is not already in a batch
* Off: Map to Pool if it is already in another pool. Add to Batch if it is already in a batch

**Batch Verification**

* Pending: Self Certify is on. Mint NFT is off
* Reviewed: View details is on. Mint NFT is on in Certificates

**Certificates**

* Pending: View NFT and Mint NFT are off
* Reviewed: View NFT and Mint NFT are on
* Verified: View NFT is on. Mint NFT is off because minting is already done

### Term sheet actions

**Draft — Borrower**

* On: Edit, upload documents, Create Draft (starts e-sign)
* Off: Submit to FA until you have signed

**Signed by the borrower — Borrower**

* On: Submit to FA, view
* Off: Edit, unless the facility agent requests changes

**Under Review — Borrower**

* On: View
* Off: Edit, while you wait for the facility agent

**Under Review — Facility Agent**

* On: Approve, Reject, Request Changes
* Off: Edit

**Changes Requested — Borrower**

* On: Edit, update, resubmit, and sign again

**Accepted — Borrower**

* On: View
* Off: Edit. The master commitment has been created

### Master commitment actions

**Draft — Facility Agent**

* On: Edit the configuration, add lenders, create sub-facilities if the facility is multiple branch, Create Facility

**Pending Lender Approval — Facility Agent**

* On: View
* Off: Edit

**Pending Lender Approval — Lender**

* On: Review & Approve, including e-sign
* Off: Edit

**Active — Facility Agent**

* On: Set Up Deal, review funding requests
* Off: Edit the facility structure

**Active — Borrower**

* On: Map loans and create a funding request after deal modelling is complete
* Off: Create a funding request while deal modelling is still in progress

### Funding request actions

**DRAFT — Borrower**

* On: Edit, Submit to FA
* Off: Approve. That is the facility agent’s action

**Under Review — Borrower**

* On: View
* Off: Edit

**Under Review — Facility Agent**

* On: Approve, Reject, Request Changes

### Funding notice actions

**Pending Token Generated — Facility Agent**

* On: Approve
* Off: E-sign until you approve

**After the facility agent approves**

* On: E-sign, from 0/n through n/n

**After your e-sign is complete — Lender**

* On: Review Funding Notice, select a payment method, Confirm and Settle

### Asset sale actions

**Create Deal — Issuer:** on when you are signed in as Issuer. Off for Underwriter and Investor.

**Publish Deal — Issuer:** on in Draft when at least one loan is assigned. Off in any other status, or when no loans are assigned.

**Approve or Reject — Underwriter:** on in Pending Review. Off in every other status, and off if you are not an Underwriter.

**Submit Commitment — Investor:** on when the deal is Published. Off otherwise, and off if you are not an Investor.

**Finalize Allocation — Underwriter:** on after at least one commitment is in. Off before that.

**Initiate Repayment — Issuer:** on when the deal is Active and a loan tape has been uploaded. Off otherwise.

**Confirm Repayment Receipt — Investor:** on during Repayment In Progress. Off otherwise.

**Burn NFT — Investor:** on after you confirm repayment receipt. Off before that.

## Important Access Notes

| Reason                   | Example                                                                        |
| ------------------------ | ------------------------------------------------------------------------------ |
| Wrong status             | A term sheet in Draft cannot be submitted until it is signed                   |
| Missing step             | A funding request stays off until deal modelling is complete                   |
| Waiting for someone else | A lender does not see a funding notice until the facility agent signs for them |
| Wrong role               | Only the facility agent can approve a term sheet                               |
| Already done             | You cannot approve an item that is already approved                            |

To turn an action on:

1. Check the status.
2. Finish required fields, documents, and signatures.
3. Confirm you are in the correct role.
4. Wait if another party must act first.
5. Hover the button and read the tooltip.
