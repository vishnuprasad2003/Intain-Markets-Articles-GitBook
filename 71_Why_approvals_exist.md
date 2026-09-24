---
title: Why Approvals Exist
description: Understand why Intain Markets requires approvals at every critical step and how each approval protects the parties
---

# Why Approvals Exist

## Overview

Deals, term sheets, funding requests, and similar items do not move forward until someone else approves them. The person who prepares an item is not the person who approves it. This page explains that rule and the approval points you will see.

## How the Platform Is Designed

### The Maker-Checker Pattern

- The **maker** prepares the item: a term sheet, a funding request, a pool mandate, or a deal.
- The **checker** is someone else, usually in another organization. They approve, reject, or request changes.

The platform keeps those roles apart. A borrower cannot approve their own term sheet. An issuer cannot approve their own asset sale deal. If you do not have the approving role, the approval action is not available to you.

### Why a step does not move on its own

Each step is a financial or legal commitment:

- Approving a term sheet means the facility agent accepts the borrower and the terms.
- Approving a master commitment means a lender is committing capital.
- Approving a funding request means the draw fits the facility rules.
- Accepting a pool mandate means the market maker will structure the deal.

An approval gives the affected party a chance to stop incomplete documents or terms that should not proceed.

## What This Enables for Users

| Approval | Who approves | Who is protected |
|---|---|---|
| Term sheet | Facility Agent | Lenders, because the terms are reviewed before a commitment is created |
| Master commitment | Lender | The lender, before capital is committed |
| Funding request | Facility Agent | Lenders, because the draw is checked against facility rules |
| Funding notice e-signature | Facility Agent, for each lender | The lender, before funds are sent |
| Pool mandate | Market Maker | The market maker, before they commit to structure the pool |
| Asset sale deal | Underwriter | Investors, before the deal is shown to them |
| Token approval | Issuer | All parties. A one-time code is required before tokens are distributed |
| KYC approval | Admin | The platform, before access is granted |

Every decision records who acted, when, and any comment they entered.

At most approval points there are three choices:

| Action | Meaning | What happens |
|---|---|---|
| **Approve** | The reviewer accepts the item | It moves to the next stage. Some later records are created for you, such as a master commitment after a term sheet is approved |
| **Request Changes** | The item can be fixed | It returns to the submitter, who can edit and send it again |
| **Reject** | The item should not continue | It stays rejected. The submitter can create a new item |

Some steps have only two choices. A pool mandate is accept or reject. A lender either approves and e-signs a master commitment, or does not.

## Key Principles to Understand

Approvals are there so a party can review risk before they are bound. The reviewer sees the details needed for that decision in one place.

The platform applies the split itself. You cannot approve an item you are not allowed to approve, even if you can see it.

An approval also starts the next step:

- An approved term sheet creates a master commitment in **Draft**, filled from the term sheet.
- An approved funding request creates a funding notice in **Pending Token Generated**.
- An approved asset sale deal becomes visible to investors for commitment.
- The first lender to approve a master commitment makes the facility **Active**, so deal modelling and later funding can start.

Some actions also ask for a one-time password. Issuers confirm NFT minting, NFT transfer, and token approval this way. A paying agent confirms a fund transfer this way. If you cannot complete that check, an emergency access request is available.

Several approvals also require Adobe Sign or ZohoSign. A lender’s approval of a master commitment is a signed commitment, not only a button click.
