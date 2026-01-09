---
title: Roles in Credit Facilities
description: Understand the different roles and their responsibilities in credit facility transactions
---

# Roles in Credit Facilities

## Overview

Credit facility transactions involve multiple parties with distinct roles and responsibilities. Understanding these roles helps you navigate the workflow and know what actions each party can take. Note that in the Credit Facility module, roles have different names compared to other modules.

## Role Name Mapping

In the Credit Facility module, the standard platform roles are referred to by different names:

| Standard Role | Credit Facility Name |
|---------------|---------------------|
| Issuer | **Borrower** |
| Market Maker | **Facility Agent** |
| Investor | **Lender** |

## Role Responsibilities

### Borrower (Issuer)

The borrower initiates and manages credit facility requests. They are the party seeking funds through the credit facility.

**What Borrowers Do:**
- Create term sheets proposing new credit facilities
- Sign term sheets via Adobe Sign
- Submit term sheets to facility agents for review
- Respond to change requests and resubmit updated term sheets
- View approved master commitments
- Map NFT-minted loans to active facilities
- Create funding requests to draw down funds
- Approve token transfers for funding notices
- Track facility utilization and available capacity

**Dashboard View:**
- Access Credit Facility section from left expandable menu
- See term sheets created by them
- See master commitments under approved term sheets
- Actions: Submit Term Sheet, Edit Term Sheet (when changes requested), View Term Sheet, Map Loans, Funding Request

### Facility Agent (Market Maker)

The facility agent reviews, structures, and manages credit facilities. They act as the intermediary between borrowers and lenders.

**What Facility Agents Do:**
- Review term sheets submitted by borrowers
- Approve, reject, or request changes on term sheets
- Configure master commitments (add lenders, set up facility rules)
- Create sub-facilities for multiple-lender arrangements
- Submit master commitments for lender approval
- Set up deal modelling after master commitment is active
- Review funding requests from borrowers
- Approve, reject, or request changes on funding requests
- E-sign funding notices for each lender
- Monitor facility operations and compliance

**Dashboard View:**
- Access Credit Facility section from left expandable menu
- See **Set-up** tab with term sheets and master commitments awaiting setup
- See **Active Facilities** tab with active master commitments
- Actions: Review Term Sheet, Create Facility, Set Up Deal, Review Funding Request, E-sign

### Lender (Investor)

Lenders provide funding for credit facilities. They review and approve facilities, and transfer funds for approved drawdowns.

**What Lenders Do:**
- Review master commitments (or sub-master commitments) shared with them
- Approve and e-sign master commitments via Adobe Sign
- View approved facilities in their Credit Facility section
- Review funding notices for approved drawdowns
- Select payment methods and transfer funds
- Confirm and settle fund transfers
- Track their participation and commitments

**Dashboard View:**
- Access Opportunities section to see pending master commitments for approval
- Access Credit Facility section to see approved facilities and funding notices
- Actions: Review & Approve (for master commitments), Review Funding Notice, Confirm and Settle

### Servicer

Servicers manage ongoing loan administration for active facilities.

**What Servicers Do:**
- Upload monthly loan tapes for facility loans
- Monitor loan performance
- Provide servicing reports

**Dashboard View:**
- Access Servicer dashboard showing deals
- View deal details
- Upload recurring loan data

## Role-Based Access

### What Each Role Can See

| Item | Borrower | Facility Agent | Lender | Servicer |
|------|----------|----------------|--------|----------|
| Term Sheets | Own created | Submitted for review | - | - |
| Master Commitments | Approved ones | All in progress | Assigned to them | - |
| Funding Requests | Own created | Submitted for review | - | - |
| Funding Notices | Own (after token approval) | All | Assigned to them (after token approval) | - |
| Deal Details | - | - | - | Assigned deals |

### What Each Role Can Do

| Action | Borrower | Facility Agent | Lender | Servicer |
|--------|----------|----------------|--------|----------|
| Create Term Sheet | ✓ | - | - | - |
| Review Term Sheet | - | ✓ | - | - |
| Configure Master Commitment | - | ✓ | - | - |
| Approve Master Commitment | - | - | ✓ | - |
| Set Up Deal Modelling | - | ✓ | - | - |
| Map Loans to Facility | ✓ | - | - | - |
| Create Funding Request | ✓ | - | - | - |
| Review Funding Request | - | ✓ | - | - |
| E-sign Funding Notice | - | ✓ | - | - |
| Approve Token Transfer | ✓ | - | - | - |
| Confirm Fund Transfer | - | - | ✓ | - |
| Upload Monthly Loan Tapes | - | - | - | ✓ |

## Workflow Summary by Role

### Borrower Workflow

1. Create term sheet and enter details
2. Sign via Adobe Sign
3. Submit to facility agent
4. If changes requested, edit and resubmit
5. After approval, wait for facility agent to configure and lender to approve
6. After facility is active and deal modelling complete, map loans and create funding requests
7. After funding notice is ready, approve token transfer
8. Receive funds after lender confirms transfer

### Facility Agent Workflow

1. Review submitted term sheets
2. Approve, reject, or request changes
3. For approved term sheets, configure master commitment (add lenders, rules)
4. Submit to lenders for approval
5. After lender approval, set up deal modelling
6. Review funding requests from borrowers
7. Approve, reject, or request changes on funding requests
8. E-sign funding notices for each lender

### Lender Workflow

1. Review master commitments in Opportunities section
2. Approve and e-sign via Adobe Sign
3. View approved facilities in Credit Facility section
4. Review funding notices when available
5. Transfer funds and confirm settlement
