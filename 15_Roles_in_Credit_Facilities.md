# Roles in Credit Facilities

## Overview

Credit facilities involve three main parties, each with distinct responsibilities and permissions. Understanding these roles helps you know what you can do and what's expected of you.

## Borrower (Issuer)

### Who They Are

Borrowers are organizations that need credit facilities. They initiate the process and request funds as needed.

### Key Responsibilities

**Term Sheet Phase:**
- Create term sheets with facility terms
- Upload required documents
- Sign term sheet via DocuSign
- Submit term sheet for facility agent review
- Respond to change requests
- Preview term sheet after signing

**Master Commitment Phase:**
- View auto-created master commitment
- Provide information if requested by facility agent
- Monitor master commitment status

**Funding Request Phase:**
- Create funding requests against active facilities
- Specify requested amounts
- Provide supporting documentation
- Submit requests for review
- Respond to change requests
- Track request status

**Funding Notice Phase:**
- Approve token transfers
- Enable lender visibility
- Monitor funding notice progress
- Track drawdown status

### What They Can See

- Their own term sheets (all statuses)
- Master commitments linked to their term sheets
- Their funding requests
- Funding notices requiring their approval
- Facility status and details
- Status history and audit trails

### What They Cannot Do

- Cannot approve their own term sheets
- Cannot create master commitments (auto-created)
- Cannot approve their own funding requests
- Cannot sign funding notices (facility agent signs)
- Cannot approve funding notices as lenders

---

## Facility Agent (Market Maker)

### Who They Are

Facility agents structure and manage credit facilities. They act as intermediaries between borrowers and lenders.

### Key Responsibilities

**Term Sheet Phase:**
- Review term sheets submitted by borrowers
- Analyze facility terms and borrower creditworthiness
- Request changes if needed
- Approve or reject term sheets
- Provide feedback to borrowers

**Master Commitment Phase:**
- Configure master commitment (auto-created from approved term sheet)
- Set up facility rules and parameters
- Define borrowing base calculations
- Configure collateral eligibility rules
- Add and configure lender groups
- Complete facility setup
- Submit for lender approval

**Funding Request Phase:**
- Review funding requests for compliance
- Verify borrowing base availability
- Check collateral eligibility
- Approve or reject requests
- Request changes if needed
- Provide feedback to borrowers

**Funding Notice Phase:**
- Generate tokens (via updateTokenDistribution)
- Sign funding notices for each lender individually
- Complete e-signature process per lender
- Manage token distribution
- Track individual lender status

### What They Can See

- Term sheets submitted for their review
- Master commitments they're managing
- Funding requests requiring review
- Funding notices they need to sign
- Facility status and details
- All facility activity

### What They Cannot Do

- Cannot create term sheets (borrowers create them)
- Cannot approve master commitments as lenders
- Cannot create funding requests (borrowers create them)
- Cannot approve funding notices economically (lenders do this)

---

## Lender

### Who They Are

Lenders provide the capital for credit facilities. They participate in facilities and approve individual drawdowns.

### Key Responsibilities

**Master Commitment Phase:**
- Review master commitments pending approval
- Evaluate facility terms and structure
- Sign master commitment via DocuSign
- Approve facility (any lender approval activates it)
- Monitor facility status

**Funding Notice Phase:**
- Review funding notices (after borrower token approval)
- Evaluate each drawdown request
- Approve or reject individual drawdowns
- Confirm fund transfers after participating
- Track their participation

### What They Can See

- Master commitments pending their approval
- Funding notices (after borrower approval)
- Their participation in facilities
- Fund transfer confirmations
- Facility details and status
- Their lender-specific information

### What They Cannot Do

- Cannot create term sheets
- Cannot create master commitments
- Cannot create funding requests
- Cannot sign funding notices (facility agent signs)
- Cannot approve token transfers (borrower does this)

---

## Role Interactions

### Borrower ↔ Facility Agent

**Term Sheet:**
- Borrower creates → Facility agent reviews
- Facility agent requests changes → Borrower updates
- Facility agent approves → Master commitment auto-created

**Funding Request:**
- Borrower creates → Facility agent reviews
- Facility agent requests changes → Borrower updates
- Facility agent approves → Funding notice auto-generated

### Facility Agent ↔ Lender

**Master Commitment:**
- Facility agent configures → Lender reviews
- Lender approves → Facility becomes ACTIVE

**Funding Notice:**
- Facility agent signs → Lender reviews
- Lender approves/rejects → Drawdown proceeds or stops

### Borrower ↔ Lender

**Indirect interaction:**
- Borrower creates funding request
- Facility agent approves
- Funding notice generated
- Borrower approves tokens
- Lender sees and approves/rejects

---

## Permission Summary

| Action | Borrower | Facility Agent | Lender |
|--------|----------|----------------|--------|
| Create Term Sheet | Yes | No | No |
| Review Term Sheet | No | Yes | No |
| Approve Term Sheet | No | Yes | No |
| Create Master Commitment | No | Yes (auto-created) | No |
| Configure Master Commitment | No | Yes | No |
| Approve Master Commitment | No | No | Yes |
| Create Funding Request | Yes | No | No |
| Review Funding Request | No | Yes | No |
| Approve Funding Request | No | Yes | No |
| Generate Tokens | No | Yes | No |
| Sign Funding Notice | No | Yes | No |
| Approve Token Transfer | Yes | No | No |
| Approve Funding Notice | No | No | Yes |
| Confirm Fund Transfer | No | No | Yes |

---

## Role-Based Views

### Borrower Dashboard

**Shows:**
- Term sheets requiring action
- Funding requests needing attention
- Funding notices requiring token approval
- Facility status updates
- Pending change requests

### Facility Agent Dashboard

**Shows:**
- Term sheets for review
- Master commitments to configure
- Funding requests for review
- Funding notices to sign
- Facility activity summary

### Lender Dashboard

**Shows:**
- Master commitments pending approval
- Funding notices for review
- Participation opportunities
- Fund transfer confirmations needed
- Facility status updates

---

## Best Practices

### For Borrowers

1. **Complete term sheets thoroughly**: Provide all required information
2. **Respond promptly**: Address change requests quickly
3. **Create clear funding requests**: Specify amounts and purposes
4. **Approve tokens timely**: Enable lender visibility
5. **Track facility status**: Monitor your credit facility

### For Facility Agents

1. **Review thoroughly**: Ensure compliance before approval
2. **Configure completely**: Set up all master commitment rules
3. **Respond promptly**: Keep workflow moving
4. **Sign timely**: Complete funding notice signatures
5. **Monitor activity**: Track all facility activity

### For Lenders

1. **Review carefully**: Understand facility terms
2. **Evaluate requests**: Assess each drawdown
3. **Approve/reject promptly**: Keep process moving
4. **Confirm transfers**: Complete the funding process
5. **Track participation**: Monitor your involvement

---

## Common Questions

**Can I have multiple roles?**
- Yes, but you select one role when logging in
- Switch roles by logging out and back in
- Each role has its own view and permissions

**What if I'm both borrower and lender?**
- You'll have separate views for each role
- Switch roles to see different perspectives
- Can participate in facilities from both sides

**Why can't I see certain items?**
- Check your role - you may not have permission
- Some items are only visible at certain statuses
- Verify you're assigned to the facility

**Why are some actions disabled?**
- Check the status - some statuses restrict actions
- Verify you have permission for that action
- Ensure prerequisites are met

Understanding roles in credit facilities helps you know what you can do, what's expected of you, and how to effectively participate in the credit facility workflow.
