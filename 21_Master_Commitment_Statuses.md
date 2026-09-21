---
title: Master Commitment Statuses
description: Understand the different statuses master commitments go through
---

# Master Commitment Statuses

## Overview

Master commitments progress through three main statuses from creation to activation. Understanding these statuses helps you know what actions are available and what needs to happen next.

## Lifecycle Overview

```
Term Sheet Approved → Auto-Create → Draft → FA Configures → PendingLenderApproval → Any Lender Approves → Active
```

## Status Meanings

### Draft

**Meaning**: The master commitment has been automatically created from an approved term sheet, and the facility agent is configuring it.

**When This Occurs**:
- Immediately after a term sheet is approved
- Automatically created by the system

**What Facility Agents Can Do**:
- Open the Create Facility popup
- Configure all sections (Basic, Parties & Accounts, etc.)
- Add lenders and set commitment amounts
- Create sub-facilities (if multiple branch)
- Edit all fields
- Data auto-saves as they enter

**What Happens Next**:
- Click **Create Facility** to submit for lender approval
- Status changes to PendingLenderApproval

**Dashboard View**:
- Appears under the approved term sheet as a dropdown
- Action: **Create Facility**

### PendingLenderApproval

**Meaning**: The facility agent has completed configuration and submitted the master commitment for lender approval.

**When This Occurs**:
- After facility agent clicks Create Facility
- The facility is now shared with selected lenders

**What Lenders Can Do**:
- See the facility in their Opportunities section
- Click Review & Approve to review facility details
- Review all configuration and terms
- Click Approve & E-Sign to approve

**What Facility Agents Can Do**:
- View the facility (no editing)
- Wait for lender approval

**What Happens Next**:
- Any lender approves → Status changes to Active
- If rejected, status may need to be reconfigured

**Dashboard View (Lenders)**:
- Appears in Opportunities section
- Action: **Review & Approve**

### Active

**Meaning**: At least one lender has approved the master commitment, and the facility is operational.

**When This Occurs**:
- After any one lender completes Approve & E-Sign

**What Facility Agents Can Do**:
- Complete deal modelling (Set Up Deal)
- Review funding requests when submitted
- Process funding notices

**What Borrowers Can Do**:
- Map NFT-minted loans to the facility (after deal modelling)
- Create funding requests (after deal modelling)

**What Lenders Can Do**:
- View the facility in their Credit Facility section
- Review funding notices when available
- Confirm fund transfers

**Dashboard View (FA)**:
- Appears in Active Facilities tab
- Action: **Set Up Deal** (then **Review Funding Request** after funding requests are submitted)

**Dashboard View (Lenders)**:
- Appears in Credit Facility section
- Action: **View Facility**, **Review Funding Notice** (when available)

## Additional Status: Facility Setup Status

After a master commitment becomes Active, there's an additional status that tracks deal modelling:

### Facility Setup Status: In Progress

**Meaning**: The master commitment is active, but deal modelling is not yet complete.

**What This Means**:
- Facility agent needs to complete deal modelling
- Borrower cannot yet create funding requests

### Facility Setup Status: Completed

**Meaning**: Deal modelling is complete.

**What This Means**:
- Borrower can now map loans and create funding requests
- Funding workflow can proceed

## Status Summary

| Status | Who Acts | Available Actions |
|--------|----------|-------------------|
| Draft | Facility Agent | Configure facility, add lenders, Create Facility |
| PendingLenderApproval | Lender | Review & Approve, E-Sign |
| Active | FA, Borrower, Lender | Deal modelling, funding requests, fund transfers |

| Facility Setup Status | Meaning | Borrower Can Raise Funding Request |
|----------------------|---------|-------------------------------------|
| In Progress | Deal modelling not complete | No |
| Completed | Deal modelling complete | Yes |
