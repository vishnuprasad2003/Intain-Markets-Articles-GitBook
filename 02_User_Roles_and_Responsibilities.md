---
title: User Roles and Responsibilities
description: Understand different user roles and what each role can do in the platform
---

# User Roles and Responsibilities

## Overview

Intain Markets uses distinct user roles, each with specific responsibilities and access permissions. Your role determines what actions you can take, what information you can see, and what you're responsible for. The platform automatically filters information and actions based on your role, showing only what's relevant to your responsibilities.

## Roles Covered

The platform supports several distinct roles, each designed for specific responsibilities in structured finance transactions:

- **Issuer (Borrower)** - Organizations that own loans and create pools or credit facility requests. They initiate transactions and manage loan portfolios.

- **Market Maker (Facility Agent)** - Organizations that structure deals and facilitate transactions. They review opportunities, structure deals, and facilitate transactions between issuers and investors.

- **Investor (Lender)** - Organizations that provide funding and make investment decisions. They review opportunities, evaluate investments, and provide capital for transactions.

- **Servicer** - Organizations that manage ongoing loan administration. They handle loan servicing, payment tracking, and ongoing administration after deals are completed.

- **Paying Agent** - Organizations that handle payment distributions. They manage payment distributions and ensure funds are properly allocated to all parties.

- **Rating Agency** - Organizations that analyze pools for rating purposes. They review pool data, analyze characteristics, and provide ratings for structured finance transactions.

- **Admin** - System administrators with platform-level access. They manage users, configure system settings, and handle platform-level administrative tasks.

## What Each Role Can Do

### Issuer (Borrower)

Issuers create and manage pools, submit credit facility requests, and manage loan portfolios. They are the initiators of transactions and have primary responsibility for creating and managing pools and credit facility requests.

**Primary Capabilities:**
- Create pools and assign loans to them
- Share pools with market makers, investors, and other parties
- Submit term sheets for credit facilities
- Create funding requests against active facilities
- Manage loan data and pool information
- Respond to feedback and make changes
- View their pools and track status changes
- Approve token transfers for funding notices

**Limitations:**
- Cannot approve their own submissions—they must wait for other parties to review and approve
- Cannot create master commitments—these are automatically created when term sheets are approved
- Cannot approve funding requests—these require facility agent approval

**Responsibilities:**
- Ensure pool data is accurate and complete
- Respond to feedback and change requests promptly
- Maintain loan data quality
- Track pool and facility status
- Coordinate with market makers and facility agents

### Market Maker (Facility Agent)

Market Makers help structure deals and facilitate transactions. They play a crucial role in reviewing opportunities, structuring deals, and facilitating transactions between issuers and investors.

**Primary Capabilities:**
- Review pools shared with them
- Accept or reject mandates to structure deals
- Provide feedback and request changes on pools
- Review and approve term sheets
- Configure master commitments after they're auto-created
- Review and approve funding requests
- Sign funding notices for lenders
- Structure deals and move pools toward completion
- View pools and facilities they're involved with

**Limitations:**
- Cannot create pools or term sheets themselves—they review and structure items created by issuers
- Cannot approve master commitments—these require lender approval
- Cannot approve their own reviews—approval decisions are tracked separately

**Responsibilities:**
- Review opportunities thoroughly
- Provide constructive feedback
- Structure deals effectively
- Ensure compliance with requirements
- Facilitate transactions efficiently

### Investor (Lender)

Investors provide funding for transactions. They review opportunities, evaluate investments, and make funding decisions based on their investment criteria and risk tolerance.

**Primary Capabilities:**
- Review pools and investment opportunities shared with them
- Review and approve credit facilities and master commitments
- Approve or reject funding requests and funding notices
- Review master commitments and facility setups
- Confirm fund transfers
- View their investments and track status
- Express interest in opportunities
- Analyze pool characteristics and loan details

**Limitations:**
- Cannot create pools or term sheets—they review and approve items created by issuers
- Cannot approve term sheets—these require facility agent approval
- Cannot approve funding requests—these require facility agent approval first

**Responsibilities:**
- Evaluate opportunities thoroughly
- Make informed investment decisions
- Review facility structures carefully
- Track investments and commitments
- Confirm fund transfers promptly

### Servicer

Servicers manage ongoing loan administration after deals are completed. They handle loan servicing, payment tracking, and ongoing administration to ensure loans are properly managed.

**Primary Capabilities:**
- View pools and loans assigned to them
- Manage loan servicing activities
- Track payments and loan performance
- Update loan statuses and information
- Handle ongoing administration tasks

**Limitations:**
- Cannot create or approve pools—they manage loans after deals are completed
- Cannot approve transactions—they focus on post-deal administration
- Cannot modify deal structures—they work within established deal parameters

**Responsibilities:**
- Maintain accurate loan records
- Track payments and performance
- Update loan statuses promptly
- Ensure proper loan administration
- Report on loan performance

### Paying Agent

Paying Agents handle payment distributions. They manage payment distributions and ensure funds are properly allocated to all parties according to deal terms.

**Primary Capabilities:**
- View pools and facilities assigned to them
- Manage payment distributions
- Ensure funds are properly allocated
- Handle payment-related tasks

**Limitations:**
- Cannot create or approve pools—they handle payment distributions
- Cannot approve transactions—they focus on payment processing
- Cannot modify deal structures—they work within established deal parameters

**Responsibilities:**
- Ensure accurate payment distributions
- Allocate funds correctly
- Process payments promptly
- Maintain payment records
- Report on payment activities

### Rating Agency

Rating Agencies analyze pools for rating purposes. They review pool data, analyze characteristics, and provide ratings for structured finance transactions.

**Primary Capabilities:**
- View pools shared with them
- Access pool and loan data for analysis
- Review pool characteristics and metrics
- Perform rating analysis
- Download data (if permissions allow)

**Limitations:**
- Have read-only access—cannot make changes or approvals
- Cannot create or modify pools—they analyze existing pools
- Cannot approve transactions—they provide analysis only

**Responsibilities:**
- Analyze pools thoroughly
- Provide accurate ratings
- Maintain analysis standards
- Ensure rating quality
- Report on rating analysis

### Admin

Admins have system-level access for platform administration. They manage users, configure system settings, and handle platform-level administrative tasks.

**Primary Capabilities:**
- Manage users and organizations
- Configure system settings
- Access administrative functions
- Handle platform-level tasks

**Limitations:**
- Typically don't participate in regular business transactions
- Cannot approve business transactions—they manage platform administration
- Cannot create business items—they support platform operation

**Responsibilities:**
- Maintain platform security
- Configure system settings
- Manage users and organizations
- Support platform operation
- Ensure platform availability

## Important Access Notes

**Role Selection** - Select the correct role during login. If you have multiple roles, you can log in with different roles at different times, but only one role per session.

**Role-Based Views** - You only see items where you have a role or where items are shared with you. The platform automatically filters information based on your role.

**Action Availability** - Action buttons are enabled or disabled based on your role and the item's status. Disabled buttons show why the action isn't available.

**Multiple Roles** - Some users may have multiple roles, but you can only use one role per session. Switch roles by logging out and logging back in.

**Role-Based Permissions** - Role-based permissions ensure proper workflow—issuers cannot approve their own submissions, and each role has appropriate responsibilities.

**Automatic Enforcement** - The platform enforces role-based rules automatically, so you can only take actions appropriate for your role.

**Collaboration Between Roles** - Issuers create, market makers structure, investors fund, and servicers manage ongoing administration.

**Role Attribution** - All actions are recorded with role information, ensuring accountability and proper attribution.
