---
title: Funding Requests
description: How borrowers create and submit funding requests to draw from an active credit facility
---

# Funding Requests

## Prerequisites

Before creating a funding request:
- Master commitment status = **Active** (at least one lender has approved)
- Facility Setup Status = **Completed** (facility agent finished deal modelling)
- Loans with NFTs mapped to the facility (if required)

## Creating a Funding Request

1. **Credit Facility → active master commitment → Funding Request**
2. Fill in:
   - **Draw Amount** — must fit remaining borrowing capacity
   - **Funding Date**
   - **Purpose of Funds**
   - **Draw Currency**
   - **Collateral Addendum** (upload required document)
3. **Review** → saves as **Draft**
4. **Submit** → status → **In review (facility agent)**; facility agent notified

![Funding Request Creation - Issuer](<.gitbook/assets/FundingRequest_Creation_Issuer (2).png>)

## Mapping Loans (If Required)

**Map Loans** → **Add Loans to Facility** → select NFT-minted loans → **Next** → **Map**.

Only loans with an NFT can be selected. A loan cannot be in two facilities at once.

## Funding Request Statuses

| Status | Meaning | Actions |
|---|---|---|
| **Draft** | Saved; not submitted | Edit, Submit |
| **In review (facility agent)** | Waiting for decision | View only |
| **Approved** | Approved; funding notice created | View; approve token transfer when asked |
| **Rejected** | Final | View only; create a new request |
| **Changes Requested** | Facility agent needs changes | Edit, resubmit |

## Responding to Changes Requested

1. Open the request → edit as directed by the facility agent's comments
2. **Submit** → status returns to **In review (facility agent)**

## Key Rules

- Draw amount must fit available borrowing capacity
- One request at a time — wait for the current one to be processed before creating another
- Rejected requests are final — create a new request to try again
- Submit after clicking Review — Draft is not visible to the facility agent

→ See [Funding Request Outcomes](25_Funding_Request_Outcomes.md) for what happens after each decision.
→ See [Token Approval](45_Token_Approval.md) for steps after approval.
