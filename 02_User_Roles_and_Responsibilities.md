---
title: User Roles and Responsibilities
description: Understand different user roles and what each role can do in the platform
---

# User Roles and Responsibilities

## Overview

Intain Markets uses distinct user roles, each with specific responsibilities and access permissions. Your role determines what actions you can take, what information you can see, and what you're responsible for. The platform automatically filters information and actions based on your role.

![Role Selection showing all 7 roles](images/02-user-roles-and-responsibilities/role-selection.png)

## What Each Role Can Do

### Issuer

Issuers create and manage assets, pools, and submit items for review.

**What Issuers Do:**
- Create and manage pools
- Onboard and standardize loans via imports and the loan registry
- Map loans to pools and verify via batch verification
- Mint asset NFTs for verified loans
- Share pools with other parties for review
- Respond to feedback from market makers and investors
- Accept or reject loan removal requests
- Create and submit term sheets for credit facilities
- Create asset sale deals, assign loans, configure sale terms, and publish for review
- Initiate repayment on active asset sale deals (upload loan tape, send wire, submit confirmation)
- Upload historical loan tapes

### Market Maker

Market Makers help structure deals and facilitate transactions.

**What Market Makers Do:**
- Review pools shared by issuers (accept/reject mandates)
- Provide feedback at pool and loan level
- Request loan removal from pools
- Review and approve term sheets for credit facilities
- Configure facilities, add participants, and set up deal modelling
- Complete deal setup and calculations (borrowing base, waterfalls, triggers)
- Approve notices and e-sign documents
- Review and approve asset sale deals submitted by issuers
- Manage investor commitment allocation in asset sales
- Access the modelling workbench for scenario comparison

### Investor

Investors provide funding for transactions.

**What Investors Do:**
- Review pools shared by issuers or market makers
- Provide feedback at pool and loan level
- Request loan removal from pools
- Download data and reports
- Review and approve credit facility master commitments
- Review and approve funding notices
- E-sign commitments and agreements
- Select payment method and confirm fund transfers
- Commit to asset sale deals and sign investor agreements
- Confirm repayment receipt on asset sale deals
- Burn receivables NFTs to close asset sale positions
- Access portfolio analytics, risk surveillance, and ESMA reporting

### Servicer

Servicers manage ongoing administration.

**What Servicers Do:**
- Upload monthly loan tapes for assigned deals (5-step upload flow: upload → preview → map fields → preview mapped → summarize)
- View deal details and performance
- Manage ongoing servicing activities
- Support both credit facility and asset sale deal types

### Paying Agent

Paying Agents handle payment distributions.

**What Paying Agents Do:**
- View assigned pools and facilities
- Manage payment distributions
- Ensure funds are properly allocated

### Rating Agency

Rating Agencies analyze and review items.

**What Rating Agencies Do:**
- View items shared with them (read-only)
- Provide feedback if permissions allow
- Download data if permissions allow
- Cannot request loan removal

### Admin

Admins have system-level access for platform administration.

**What Admins Do:**
- Create and manage organizations
- Approve KYC for users
- Process delegation requests
- Handle tasks on behalf of other users when delegated
- Use the "View As" (impersonation) feature for read-only support of other users
- Manage user accounts and organization settings

## Important Access Notes

**Role Selection** — Select the correct role during login. You can only use one role per session. If you have multiple roles, you may be prompted to select one after authentication.

**Role-Based Views** — You only see items relevant to your role or shared with your organization. The dashboard, sidebar navigation, and available actions all adapt to your role.

**Action Availability** — Action buttons are enabled or disabled based on your role and the item's current status. Disabled actions indicate that your role cannot perform that action at the current stage.

**Automatic Enforcement** — The platform enforces role-based rules automatically. You cannot perform actions outside your role's permissions.

**Microsoft SSO** — The platform supports Microsoft Entra single sign-on. If your organization uses Entra SSO, you can log in using your Microsoft credentials without a separate platform password.
