---
title: Role-Based Pool Views
description: Understand how different users see pools based on their role
---

# Role-Based Pool Views

## Overview

Different users see pools differently based on their role in the platform. The role you select during login determines what pools you can see, what information is displayed, and what actions are available. Issuers see pools they create and manage; market makers see pools shared with them for review and structuring; investors see pools shared with them; rating agencies see pools shared for analysis. Each role has a tailored view that shows only relevant information and appropriate actions.

## How to Navigate the Platform

**Accessing the Pools Section** - From the left expandable menu (which expands when you hover over it), click on **Pools** to navigate to the Pools dashboard. The dashboard displays all pools relevant to your role with their current statuses and available actions.

**Viewing Pool Details** - In the Pools dashboard, click on a **Pool ID** to navigate to the pool details page. The details page shows comprehensive information: summary tiles with metrics, tabbed sections for loans, loan tape, stratifications, performance, feedback, and sharing (depending on your role and the pool's sharing configuration).

**Understanding Your View** - The pools you see depend on:
- **Your role**: Issuers see pools they created; market makers, investors, and rating agencies see pools shared with them
- **Pool status**: Pools in Created status are visible only to the issuer; other statuses are visible to shared parties
- **Sharing configuration**: You can only see pools that have been shared with your organization (except issuers who see their own pools regardless)

**Role Selection at Login** - When you log in, you select your role. If you have multiple roles in the platform, you can log in with different roles to see different views. For example, logging in as Issuer shows pools you created; logging in as Market Maker shows pools shared with you.

## What You Will See

### Issuer / Borrower View

As an issuer, you have full control over pools you create. Your Pools dashboard shows all pools you've created, regardless of their current status.

**Pools Dashboard**
- All pools you've created with their Pool IDs, names, statuses, and metrics
- **Set-up Pool** button at top right to create new pools
- Status indicators showing where each pool is in the workflow
- Action options for each pool

![Pools Screen - Issuer](imagesByMdFilesFolder/07/Pools_Screen_Issuer.png)

**Pool Details Page** (accessible by clicking on a Pool ID)
- **Summary tiles** at top showing pool metrics
- **Summary section** with charts showing pool composition and distributions
- **Loans tab** showing all mapped loans with action icons:
  - **Chat box icon**: Opens loan-level feedback/comments dialog
  - **Tick icon**: Appears when a market maker requests loan removal—click to accept (loan becomes Removed)
  - **Cross icon**: Appears when a market maker requests loan removal—click to reject the removal request
- **Loan Tape section** showing detailed loan data (mapped columns first, unmapped columns in italic)
  - **As Of Date dropdown** to select loan data for different reporting periods
  - **Download button** to export loan data in XLSX or CSV format
- **Strats section** with stratification analytics
- **Performance section** with performance analytics
- **Feedback section** showing pool-level feedback from shared parties (you can view but not add pool-level feedback)
- **Sharing tab** showing all shared organizations and their permissions (feedback, download)—you can edit these settings

**Top Action Buttons**
- **Edit button** with two options:
  - **Edit Pool Details**: Opens the same form as Set-up Pool to modify pool information and organization assignments
  - **Edit Loan Tape**: Upload recurring loan tape data for subsequent reporting periods with As Of Date selection
- **Share button**: Opens sharing configuration to share with organizations (market makers, investors, rating agencies, etc.)
- **Start Deal button**: Enabled after prerequisites (typically all pool loans NFT-minted); initiates Deal flow

### Market Maker / Facility Agent View

As a market maker, you see pools that issuers have shared with you. Your Pools dashboard shows these shared pools with their statuses and available actions.

**Pools Dashboard**
- Pools shared with your organization, displayed with status and actions
- Status shows **Mandate Pending** for Preview shares awaiting your decision, **Ready for Deal** for Start Deal shares
- Actions include **Review**, **Accept**, **Reject** depending on status

![Pool Screen - Market Maker](imagesByMdFilesFolder/07/Pool_Screen_MarketMaker.png)

**Pool Details Page** (after clicking on Pool ID, typically after accepting)
- Same view as issuer for information sections: Summary, Loans, Loan Tape, Strats, Performance, Feedback
- **Sharing tab is not visible** (only issuers manage sharing configuration)
- **Edit button and Start Deal button are not visible** (these are issuer actions)
- **Share button** is available—you can share the pool with investors only
- **Loans tab actions**:
  - **Cross icon**: Click to request removal of a loan from the pool (sends request to issuer)
  - **Chat box icon**: Opens loan-level feedback dialog for comments
- You can provide pool-level feedback in the Feedback section (after accepting the mandate)

**Acceptance Pop-up** (when you click Accept from the dashboard)
- Confirmation dialog for accepting the mandate/deal
- Accept and Cancel buttons
- After accepting a Preview share, your view shows **Under Review** status

### Investor / Lender View

As an investor, you see pools shared with you. Your view is similar to the market maker view but without the ability to share further.

**Pools Dashboard**
- Pools shared with your organization
- Status and action options for each pool

![Pools Screen - Investor](imagesByMdFilesFolder/07/Pools_Screen_Investor.png)

**Pool Details Page**
- Same information sections as market maker: Summary, Loans, Loan Tape, Strats, Performance, Feedback
- **Share button is not visible** (investors cannot share pools further)
- **Loans tab actions**:
  - **Cross icon**: Click to request removal of a loan from the pool (sends request to issuer)
  - **Chat box icon**: Opens loan-level feedback dialog for comments
- You can provide pool-level and loan-level feedback

### Rating Agency View

As a rating agency, you see pools shared with you for rating analysis. Your view is read-only for most actions—you can analyze and provide comments but cannot reject loans or share pools.

**Pools Dashboard**
- Pools shared with your organization for rating analysis
- Status indicators for each pool

![Pools Screen - Rating Agency](imagesByMdFilesFolder/07/Pools_Screen_RatingAgency.png)

**Pool Details Page**
- Same information sections: Summary, Loans, Loan Tape, Strats, Performance, Feedback
- **No Share button** (rating agencies cannot share pools)
- **Loans tab actions**:
  - **Chat box icon**: Opens loan-level feedback dialog for comments
  - **No cross icon** (rating agencies cannot request loan removals)
- You can provide comments in pool-level and loan-level feedback sections

## Helpful Tips

**Check Your Role** - If you're not seeing expected pools, verify you logged in with the correct role. Different roles see different sets of pools.

**Issuer Pools Are Private Until Shared** - Pools in Created status are visible only to the issuer who created them. Other parties can only see pools after they've been shared.

**Market Maker Actions After Acceptance** - Before accepting a mandate, market makers cannot provide feedback. After accepting, feedback functionality becomes available and the status shows Under Review.

**Loan-Level vs Pool-Level Feedback** - Use the chat box icon in the Loans tab for loan-specific feedback. Use the Feedback section for pool-level comments. As an issuer, you can view pool-level feedback but respond through loan-level comments.

**Loan Rejection Flow** - When a market maker or investor clicks the cross icon to request loan removal, the issuer sees tick and cross icons on that loan. Tick accepts the removal (loan becomes Removed); cross rejects the removal request.

**As Of Date Selection** - In the Loan Tape section, use the As Of Date dropdown to view loan data for different reporting periods. This is useful when monthly loan tapes are uploaded for recurring calculations.

**Download Permissions** - Your ability to download loan tape data depends on the permissions set by the issuer in the Sharing tab. If download is disabled for your organization, the download option may not be available.

**Status Affects Actions** - The actions available to you depend on both your role and the pool's current status. Disabled actions typically have tooltips explaining why they're unavailable.

**Dashboard Navigation** - Use the left expandable menu to navigate between sections. The menu expands when you hover over it, showing section names for easy navigation.
