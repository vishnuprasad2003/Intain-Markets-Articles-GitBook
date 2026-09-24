---
title: Pool Creation and Sharing
description: Create a pool, map loans, and share with underwriters / facility agents, investors, or rating agencies
---

# Pool Creation & Sharing

## Creating a Pool

1. **Pools → Set-up Pool** (top right)
2. Fill in: **Pool Name** (must be unique), **Asset Class**, **Transaction Type**, **Description** (optional), **Closing Deal** flag
3. Assign organisations: Underwriters / Facility Agents, Investors, Servicers, Paying Agents, Rating Agencies, Verification Agents
4. Click **Create** → pool status is **Created**; metrics start at zero until loans are mapped

![Pool Creation - Issuer](<.gitbook/assets/PoolCreation_Issuer (1).png>)

## Mapping Loans from Asset Registry

1. **Asset Registry → select loans** (checkbox) → click **Map to Pool**
2. Choose the target pool from the dropdown → confirm
3. Loans move to **Mapped** status; pool metrics update automatically

> Each loan belongs to one pool at a time. Unmap first to reassign.

![Loan Map to Pool - Issuer](<.gitbook/assets/LoanMapToPoolIssuer (2).png>)

## Viewing Pool Details

In pool details (click Pool ID):
- **Summary** — charts and analytics
- **Loans tab** — mapped loans; chat icon = loan feedback; tick/cross = respond to removal requests
- **Loan Tape** — full field data; select **As Of Date** to view different periods; download XLSX/CSV
- **Feedback** — pool-level comments from recipients (issuers can view but not add pool-level feedback)
- **Sharing tab** — organisations shared with and their permissions

![Pool Details - Issuer](<.gitbook/assets/Pool_Details_Issuer (1).png>)

## Editing Pool Details

While **Created** or **Preview**: click **Edit → Edit Pool Details** to change name, asset class, transaction type, or organisation assignments. Use **Edit → Edit Loan Tape** for recurring monthly uploads.

## Sharing (Preview Flow)

Use **Share** to send the pool for mandate review while retaining editing rights.

1. **Share** button → select **Recipient** type → select organisations → set permissions
2. **Allow Feedback** (default on) — recipients can comment on pool and loans
3. **Allow Download** (default on) — recipients can download loan tape
4. Add documents (optional) → click **Share**
5. Pool moves to **Preview**; recipients see **Mandate Pending** with Accept/Reject buttons

After acceptance: recipient view shows **Under Review**; feedback becomes available. After rejection: pool stays in **Preview**; revise and re-share.

![Pool Sharing - Issuer](<.gitbook/assets/PoolSharing_Issuer (1).png>)

## Starting a Deal (Start Deal Flow)

Use **Start Deal** when pool composition is final and all pool loans have been NFT-minted.

1. Click **Start Deal** → select recipients → send invitation
2. Recipients see **Ready for Deal** with Accept/Reject
3. **Accept** → pool status changes to **Deal**; structural editing is locked
4. **Reject** → pool stays in **Ready for Deal**; revise and resend

## Managing Sharing Permissions

**Pool details → Sharing tab** — toggle **Allow Feedback** or **Allow Download** per organisation. Changes take effect immediately.

## Key Rules

| Rule | Detail |
|---|---|
| Pool name | Must be unique |
| Loan mapping | One pool per loan; unmap first to move |
| Metrics | Auto-calculate when loans are added/removed |
| Preview permissions | Feedback and download are on by default; set per organisation |
| Start Deal prerequisite | All pool loans must be NFT-minted |
| Editing window | Created, Preview, Under Review — editing allowed; Deal — locked |
| Feedback before acceptance | Underwriters / Facility Agents cannot leave feedback until mandate accepted |

→ See [Pool Feedback Workflow](09_Pool_Feedback_Workflow.md) for detailed feedback steps.
→ See [Loan Management](42_Loan_Management.md) for NFT minting prerequisites.
