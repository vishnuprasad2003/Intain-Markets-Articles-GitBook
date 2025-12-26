# User Roles & Responsibilities

## Overview

Intain Markets operates with distinct user roles, each with specific responsibilities and access permissions. Understanding your role helps you know what actions you can take and what you're responsible for in the platform.

## Role Types

### Issuer (Borrower)

#### Who They Are

Issuers are organizations that need funding. They create loan pools, submit credit facility requests, and manage their loan portfolios.

#### Key Responsibilities

- Create and manage loan pools
- Upload and standardize loan data
- Map loans to pools
- Submit term sheets for credit facilities
- Create funding requests against active master commitments
- Approve token transfers for funding notices
- Respond to change requests from facility agents
- Manage loan statuses (reject, reinstate, remove)

#### What They Can See

- Their own pools and loans
- Pools shared with them for preview
- Their credit facility term sheets and funding requests
- Funding notices requiring their approval
- Status updates and notifications

#### What They Cannot Do

- Approve their own term sheets or funding requests
- Create master commitments (this is done by facility agents)
- Approve funding notices (this is done by lenders)

---

### Market Maker / Facility Agent

#### Who They Are

Market Makers and Facility Agents are intermediaries who structure deals, review submissions, and facilitate transactions between issuers and investors/lenders.

#### Key Responsibilities

- Review and approve/reject pool mandates
- Review term sheets and request changes or approve them
- Create and configure master commitments after term sheet approval
- Set up facility rules, lender groups, and borrowing base calculations
- Review funding requests for compliance
- Generate tokens and sign funding notices for each lender
- Manage deal setup and calculations

#### What They Can See

- Pools shared with them for mandate review
- Term sheets submitted for their review
- Master commitments they've created or are managing
- Funding requests requiring their review
- Funding notices they need to sign

#### What They Cannot Do

- Create term sheets (this is done by issuers)
- Approve funding notices as lenders (they sign on behalf of facility, but lenders approve economically)

---

### Investor / Lender

#### Who They Are

Investors and Lenders provide capital. They review opportunities, approve facilities, and participate in funding.

#### Key Responsibilities

- Review pool previews shared with them
- Approve master commitments (any lender approval activates the facility)
- Review funding notices
- Approve or reject individual funding drawdowns
- Confirm fund transfers after participating

#### What They Can See

- Pool previews shared with them
- Master commitments pending their approval
- Funding notices visible after borrower token approval
- Their participation history and status

#### What They Cannot Do

- Create pools or term sheets
- Approve their own funding requests
- Modify master commitments (they can only approve or reject)

---

### Servicer

#### Who They Are

Servicers manage ongoing loan administration, collections, and payments.

#### Key Responsibilities

- Manage loan servicing activities
- Update loan statuses and payment information
- Handle borrower communications
- Process payments and distributions

#### What They Can See

- Loans assigned to them for servicing
- Payment and collection information
- Loan status updates

### Paying Agent

#### Who They Are

Paying Agents handle payment distributions to investors and lenders.

#### Key Responsibilities

- Process payment distributions
- Manage fund transfers
- Handle payment reconciliations
- Distribute payments according to agreements

#### What They Can See

- Payment schedules and distributions
- Fund transfer confirmations
- Payment history

---

## Role Permissions Summary

| Action | Issuer | Facility Agent | Lender | Servicer | Paying Agent |
|--------|--------|----------------|--------|----------|--------------|
| Create Pool | Yes | No | No | No | No |
| Create Term Sheet | Yes | No | No | No | No |
| Review Term Sheet | No | Yes | No | No | No |
| Create Master Commitment | No | Yes | No | No | No |
| Approve Master Commitment | No | No | Yes | No | No |
| Create Funding Request | Yes | No | No | No | No |
| Review Funding Request | No | Yes | No | No | No |
| Approve Funding Notice | No | No | Yes | No | No |
| Sign Funding Notice | No | Yes | No | No | No |

## Understanding Role-Based Views

The platform automatically shows you:

- Only relevant items: You see pools, loans, or facilities where you have a role
- Appropriate actions: Buttons and options match your permissions
- Status context: You understand what actions are available based on current status

## Multiple Roles

Some users may have multiple roles. For example, an organization might be both an Issuer and a Lender. When logging in, you select your role, and the platform adjusts accordingly. You can switch roles by logging out and logging back in with a different role.

## Collaboration Between Roles

The platform facilitates collaboration:

- Issuers create and submit items
- Facility Agents review and structure
- Lenders approve and fund
- Servicers manage ongoing operations

Each role has clear responsibilities, and the workflow ensures proper approvals happen in the right order.

## Getting Help

If you're unsure about what you can do, look at the available buttons and actions in your interface. If you're unsure about what you're responsible for, check this guide or contact support. If something is disabled, the platform usually shows a reason in a tooltip or message.

If you can see an action, you have permission to use it. If it's disabled, there's a reason, usually waiting for another party or missing required information.
