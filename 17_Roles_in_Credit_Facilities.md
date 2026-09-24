---
title: Roles in Credit Facilities
description: Guide to Borrower, Facility Agent, Lender, Servicer, and Paying Agent responsibilities in a credit facility
---

# Roles in Credit Facilities

## Overview

A credit facility uses names that differ from other parts of the platform. The Issuer is the **Borrower**. The Market Maker is the **Facility Agent**. The Investor is the **Lender**. Each role sees different screens and can act only at certain stages.

## Roles Covered

| Platform Role | Credit Facility Name | Primary Function |
|---------------|----------------------|------------------|
| Issuer | **Borrower** | Seeks funds |
| Market Maker | **Facility Agent** | Reviews and manages the facility |
| Investor | **Lender** | Approves terms and provides funds |
| Servicer | **Servicer** | Administers the loans |
| Paying Agent | **Paying Agent** | Named for payment administration |

## What Each Role Can Do

### Borrower (Issuer)

The borrower starts the facility and later requests draws.

- **Term sheet** — Create the term sheet, enter amounts, rates, tenors, and conditions, and sign with Adobe Sign.
- **Submit** — Send the signed term sheet to the facility agent. If changes are requested, edit and resubmit.
- **After approval** — View the master commitment and map loans that already have an NFT.
- **Funding** — Create a funding request with the draw amount, purpose, and documents. Edit and resubmit if changes are requested.
- **Token approval** — Approve token transfers when a funding notice is ready to settle.
- **Monitoring** — Track use, remaining capacity, and past draws.

**Dashboard:** Open **Credit Facility**. You see your term sheets and, under approved term sheets, master commitments. Actions include Submit Term Sheet, Edit Term Sheet (when changes are requested), View Term Sheet, Map Loans, and Create Funding Request.

### Facility Agent (Market Maker)

The facility agent sits between the borrower and the lenders.

- **Term sheet review** — **Approve** (a master commitment is created), **Reject** (final), or **Request Changes** (the borrower can edit and resubmit).
- **Master commitment** — Add lenders, set participation, create sub-facilities if needed, and send the commitment to lenders.
- **Deal modelling** — After at least one lender approves, complete deal setup.
- **Funding request review** — **Approve** (a funding notice is created for each lender), **Reject**, or **Request Changes**.
- **Funding notices** — E-sign each lender’s notice with Adobe Sign.
- **Oversight** — Monitor use and compliance.

**Dashboard:** Open **Credit Facility**. **Set-up** lists term sheets and commitments still being configured. **Active Facilities** lists live commitments. Actions include Review Term Sheet, Create Facility, Set Up Deal, Review Funding Request, and E-sign Funding Notice.

### Lender (Investor)

Lenders provide the capital.

- **Master commitment** — In **Opportunities**, review the commitment or sub-facility shared with you, then approve and e-sign with Adobe Sign. One lender’s approval is enough to make the commitment **ACTIVE**.
- **Participation** — View the facility, your committed amount, and remaining capacity in **Credit Facility**.
- **Funding notice** — Review the draw allocated to you after the facility agent approves the borrower’s request.
- **Fund transfer** — Choose the payment method, send the funds, and click **Confirm and Settle**.
- **Monitoring** — Track your commitments and funding history.

**Dashboard:** **Opportunities** shows commitments waiting for approval. **Credit Facility** shows approved facilities and funding notices. Actions include Review & Approve, Review Funding Notice, and Confirm and Settle.

### Servicer

The servicer handles loan administration after the facility is live and loans are mapped.

- Upload monthly loan tapes
- Monitor loan performance
- Provide servicing reports
- Open deal details for facilities they service

**Dashboard:** The Servicer dashboard lists active deals. From a deal you can view loan data and upload a recurring loan tape.

### Paying Agent

The facility agent names the Paying Agent organization while configuring the master commitment. The Paying Agent does not have a separate Credit Facility dashboard or funding actions. The name is kept on the facility for legal and payment administration records.

## Important Access Notes

| Action | Borrower | Facility Agent | Lender | Servicer | Paying Agent |
|--------|----------|----------------|--------|----------|--------------|
| Create Term Sheet | ✓ | — | — | — | — |
| Sign Term Sheet (Adobe Sign) | ✓ | — | — | — | — |
| Submit Term Sheet | ✓ | — | — | — | — |
| Review Term Sheet | — | ✓ | — | — | — |
| Approve, Reject, or Request Changes on Term Sheet | — | ✓ | — | — | — |
| Configure Master Commitment | — | ✓ | — | — | — |
| Add Lenders | — | ✓ | — | — | — |
| Submit Master Commitment for Lender Approval | — | ✓ | — | — | — |
| Approve and E-Sign Master Commitment | — | — | ✓ | — | — |
| Set Up Deal Modelling | — | ✓ | — | — | — |
| Map Loans | ✓ | — | — | — | — |
| Create Funding Request | ✓ | — | — | — | — |
| Review Funding Request | — | ✓ | — | — | — |
| Approve, Reject, or Request Changes on Funding Request | — | ✓ | — | — | — |
| E-Sign Funding Notice | — | ✓ | — | — | — |
| Review Funding Notice | — | — | ✓ | — | — |
| Confirm Fund Transfer | — | — | ✓ | — | — |
| Upload Monthly Loan Tapes | — | — | — | ✓ | — |
| Named on the Master Commitment | — | — | — | — | ✓ |

**You see your own actions.** A borrower does not see the facility agent’s review buttons. A lender does not see term sheet creation.

**Status controls the buttons.** A borrower can edit a term sheet in **Draft** or **Changes Requested**, not while the facility agent is reviewing it.

**One lender activates the facility.** The first lender approval moves the master commitment to **ACTIVE**. The facility agent can then set up the deal, and the borrower can map loans after that setup is finished.

**Change requests continue the same item.** Rejection does not. After a rejection, start a new term sheet or funding request.

**Signatures** — The borrower signs the term sheet, the lender signs the master commitment, and the facility agent signs each funding notice. These use Adobe Sign.

**Borrower** — Create the term sheet, sign, submit, revise if asked, wait for approval, map loans, create funding requests, approve tokens, and receive funds.

**Facility Agent** — Review term sheets, configure the master commitment, send it to lenders, set up the deal, review funding requests, and e-sign funding notices.

**Lender** — Review the commitment in Opportunities, approve and e-sign, review funding notices, transfer funds, and confirm settlement.

**Servicer** — Open active deals, upload monthly loan tapes, and monitor performance.

**Paying Agent** — Named on the master commitment by the facility agent. There is no separate Credit Facility workflow for this role.
