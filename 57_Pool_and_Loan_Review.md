---
title: Pool and Loan Review
description: Learn how market makers and investors review pools and loans shared with them
---

# Pool and Loan Review

## Overview

Pool and loan review is the process where market makers and investors evaluate pools shared with them. When issuers share pools with you, you review the pool's composition, metrics, loan characteristics, and details. This guide explains how to review pools and what sections are available for analysis.

## Who Can Use This

- **Market Makers/Facility Agents**: Receive pool shares from issuers, evaluate them, provide feedback, request loan removals, and can share pools further with investors.

- **Investors/Lenders**: Receive pool shares from issuers or market makers, evaluate them, provide feedback, and request loan removals. Investors cannot share pools further.

Both roles have the same pool view and review capabilities. The key difference is that market makers can share pools with investors, while investors cannot share pools with anyone.

## When This Is Used

Use pool and loan review when:
- You receive a pool share notification from an issuer (or from a market maker, if you're an investor)
- A pool appears in your Pools dashboard (shared with your organization)
- You need to evaluate the pool before providing feedback
- You want to analyze pool characteristics and loan details

## Review Process

### Accessing Shared Pools

1. **Navigate to Pools Dashboard**
   - Log in to the platform with your Market Maker or Investor credentials
   - Navigate to the **Pools** section from the left expandable menu (the menu expands when you hover over it)
   - Your Pools dashboard shows pools that have been shared with your organization
   - The status column shows **Mandate Pending** (for Share flow) or **Ready for Deal** (for Start Deal flow)

2. **Open Pool Details**
   - Click on the **Pool ID** to open the pool details page
   - Review comprehensive information about the pool and its loans

### Reviewing Pool Information

1. **Review Summary Metrics**
   - Summary tiles at the top show pool metrics calculated from mapped loans
   - Metrics update automatically when loans are added or removed from the pool

2. **Review Pool Details**
   - Check pool name, asset class, transaction type, and description
   - Understand the context and structure
   - Review organization assignments to see who else is involved (issuer, servicer, etc.)

3. **Analyze Summary Charts**
   - In the Summary section, review charts showing pool composition
   - Examine distributions by loan characteristics

### Analyzing Loan Characteristics

1. **Review Loans Tab**
   - Navigate to the **Loans** tab to see individual mapped loans
   - Review key loan fields for each loan in the pool
   - Click on a **Loan ID** to view detailed analytics for that specific loan
   - **Actions column** shows available actions:
     - **Cross icon**: Request removal of a loan you believe should be excluded
     - **Chat box icon**: Provide loan-level feedback or comments

2. **Review Loan Tape Section**
   - Navigate to the **Loan Tape** section for detailed loan-level data
   - Mapped columns appear first; unmapped columns appear in italic
   - Use the **As Of Date** dropdown to view data from different reporting periods (useful for understanding loan data over time when monthly loan tapes are uploaded)
   - Click the **Download** button to export loan data in XLSX or CSV format (if download is permitted)

3. **Review Stratifications**
   - Navigate to the **Strats** section for stratification analytics
   - Examine distributions by various loan characteristics

4. **Review Performance**
   - Navigate to the **Performance** section for performance analytics

### Reviewing Documentation

1. **Check Supporting Documents**
   - Review any documents the issuer has attached to the pool
   - Look for relevant materials and supporting information

## Evaluation Criteria

When reviewing pools, use the available sections:

- **Pool Metrics**: Review the summary tiles to understand pool composition
- **Loan Details**: Examine individual loans in the Loans tab and Loan Tape section
- **Stratifications**: Use the Strats section to understand loan distributions
- **Performance**: Review the Performance section for analytics
- **Documents**: Check any attached documents for additional information

## Making Decisions

### Accept or Reject (Mandate/Deal)

From the Pools dashboard, you can:

1. **Accept**
   - Click **Accept** in the Actions column
   - A confirmation popup appears
   - Click **Accept** to confirm
   - For Mandate Pending: Your status changes to Under Review, feedback becomes available
   - For Ready for Deal: The pool becomes a Deal

2. **Reject**
   - Click **Reject** in the Actions column
   - A confirmation popup appears
   - Click **Reject** to confirm
   - The issuer is notified of your rejection

### Provide Feedback

After accepting a mandate (for market makers), you can provide feedback:

1. **Pool-Level Feedback**
   - Navigate to the **Feedback** section
   - Add feedback about the pool overall
   - Ask questions about pool characteristics, structure, or documentation

2. **Loan-Level Feedback**
   - Navigate to the **Loans** tab
   - Click the **chat box icon** next to a specific loan
   - Provide feedback about that particular loan

### Request Loan Removal

If you believe a loan should be excluded from the pool:

1. **Navigate to the Loans Tab**
   - Locate the loan you want to request removal for
   - Click the **cross icon** in the Actions column

2. **Submit Removal Request**
   - Your removal request is sent to the issuer
   - The issuer reviews your request and decides:
     - **Accept (tick)**: Loan becomes Removed and excluded from calculations
     - **Reject (cross)**: Loan remains in the pool

### Share with Investors (Market Makers Only)

If you're a market maker, you can share the pool with investors:

1. **Click the Share Button**
   - At the top of the pool details page, click **Share**
   - A popup appears to configure sharing

2. **Select Investors**
   - Choose investor organizations to share with
   - Configure permissions (feedback, download)
   - Confirm the share

### Download for Analysis (if permitted)

If the issuer has enabled download for your organization:

1. **Navigate to the Loan Tape Section**
   - Click the **Download** button
   - Select format (XLSX or CSV)
   - Download loan data for offline analysis

## Rules & Validations

- **View-Only Pool Access**: You can view and analyze pool information but cannot edit the pool itself.

- **Feedback After Acceptance (Market Makers)**: Market makers cannot provide feedback until they accept the mandate. After accepting, feedback functionality becomes available.

- **Feedback Permissions**: Your ability to provide feedback depends on permissions set by the issuer. If feedback is disabled for your organization, you cannot add feedback.

- **Download Permissions**: Your ability to download loan tape data depends on permissions set by the issuer.

- **Sharing Capability**: Market makers can share pools with investors. Investors cannot share pools with anyone.

- **Loan Removal Requests**: You can request loan removals; the issuer decides whether to accept.

- **Multiple Pools**: You can review multiple pools simultaneously.

- **Feedback Is Recorded**: All feedback is stored with timestamps for audit purposes.

## What Happens Next

**After Accepting (Market Maker - Mandate):**
- Your status changes to Under Review
- Feedback functionality becomes available
- You can provide pool-level and loan-level feedback
- You can request loan removals
- You can share the pool with investors

**After Accepting (Ready for Deal):**
- The pool becomes a Deal
- Structural editing is restricted
- Deal structuring and downstream activities proceed

**After Providing Feedback:**
- The issuer receives your feedback and may respond
- Pool composition may be adjusted based on your input

**After Loan Removal Request:**
- The issuer reviews and decides on your request
- If accepted, the loan is removed and metrics update
- If rejected, the loan remains

**After Sharing with Investors (Market Makers):**
- Investors see the pool in their Pools dashboard
- Investors can review and provide feedback
