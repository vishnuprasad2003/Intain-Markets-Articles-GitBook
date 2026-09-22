---
title: Status or Logic Changes
description: Platform changes to status workflows, business logic, and process flows — including the WLS status rename, v2 API migration, e-signature provider changes, audit centralization, and authentication updates
---

# Status or Logic Changes

## Overview

This document records changes to status workflows, business logic, and process flows that have been implemented in Intain Markets. If you are returning to the platform after a period of inactivity, or if something behaves differently than you remember, this document explains what changed and why.

## What Changed

### Asset Sale (Whole Loan Sale) Status Rename

**What Changed:**
The platform renamed two deal statuses in the asset sale (Whole Loan Sale) module to better reflect the deal lifecycle:

| Previous Status | New Status | What It Represents |
|---|---|---|
| **Closed** | **Active** | The sale has settled and the investor holds the assets — the deal is live and ongoing |
| **Repaid** | **Closed** | Repayment has cleared the balance — the deal is retired and complete |

**Why It Changed:**
The previous naming was counterintuitive. A deal that had just settled was called "Closed," which implied it was finished — when in fact it was just beginning its active life. Meanwhile, a deal that was truly finished was called "Repaid," which described the mechanism rather than the state. The new naming follows a natural lifecycle: a deal settles, becomes **Active**, and eventually, after repayment completes, becomes **Closed**.

**What Was Affected:**
- The `wls_deal.status` field on every deal document
- Every entry in `wls_deal.statusHistory[]` that contained the old values
- The mirrored `wls_commitments.status` field (only `Repaid` → `Closed`; commitment-level `Closed` was unambiguous)
- The on-chain DealOnboarding status string and `closedDeal` flag, which were rewritten to match the new naming

**How the Migration Worked:**
The rename required careful handling because both old and new naming share the word "Closed." A `Closed` status recorded before a deal reached `Active` (the new sale-milestone name) was the legacy sale milestone and was renamed to `Active`. A `Closed` status recorded after a deal was already `Active` was already the new terminal status and was left unchanged. Each migrated deal was stamped with a `statusRenameMigratedAt` marker so repeat runs could not misinterpret their values. On-chain status strings were rewritten to match, and the `closedDeal` flag was recalculated under the new rule (set for `Closed` and `Cancelled` deals, not for `Active` deals).

**Full Asset Sale Lifecycle (Current):**
Draft → Pending Review → Approved → Published → Commit → Invest → Settlement In Progress → Settled → **Active** → Repayment In Progress → **Closed**

Terminal statuses: Cancelled, Defaulted

### v2 API Migration

**What Changed:**
Core platform modules have been migrated from legacy `/api/v1` endpoints to standardized `/api/v2` endpoints. The migrated modules include:

- Pools, loans, and batches
- Organizations and users
- Data room
- Securitization
- Feedback
- Dashboard and analytics
- Audit

**What This Means for Users:**
The API migration is largely invisible to end users — the platform UI has been updated to use the new endpoints. However, any external integrations or API consumers that were built against the older endpoints should be updated.

**What Changed Technically:**
- Standardized request validation using Zod schemas (consistent error messages when required fields are missing or invalid)
- Cursor-based pagination replacing offset-based pagination (more reliable for large datasets)
- Consistent error handling and response envelope structure across all modules
- The current API version prefix is `/api/v2`; legacy `/api/v1` endpoints are being phased out

### E-Signature Provider Migration

**What Changed:**
The platform has migrated from DocuSign to **Adobe Sign** and **ZohoSign** as the supported e-signature providers. DocuSign is no longer supported.

**What This Means for Users:**
- When you sign a term sheet, master commitment, funding notice, or investor agreement, the signing experience uses Adobe Sign or ZohoSign
- Both providers integrate through the platform's shared e-signature architecture, so the workflow is the same regardless of which provider your organization uses
- The signing popup, signature tracking, and completion notifications work the same way they did before

**What Was Affected:**
- All e-signature envelope creation, signing, and status tracking
- Term sheet signing (borrower and facility agent)
- Master commitment approval signing (lender)
- Funding notice e-signatures (facility agent signs for each lender)
- Batch self-certification signing (issuer)
- Investor agreement signing (asset sale workflow)

### Authentication Changes — Microsoft Entra SSO

**What Changed:**
Microsoft Entra (formerly Azure AD) single sign-on has been added as a primary authentication method alongside direct login.

**What This Means for Users:**
- If your organization uses Microsoft Entra, you can sign in using your existing organizational credentials
- The platform validates your Microsoft Entra access token and maps your identity to your Intain Markets role
- SSO refresh token handling maintains your session without repeated sign-ins
- On-Behalf-Of token exchange enables downstream service access using your SSO credentials

**Login Methods Now Supported:**
- Direct email/password login
- Microsoft Entra SSO login

### Audit Trail Centralization

**What Changed:**
All modules now write to a single, centralized audit module through `audit.helper.record()`. Previously, some modules had inconsistent or incomplete audit logging. The centralized audit module provides:

- A single `audit_events` collection with a fixed schema (version 3)
- Mandatory fields: event type, category, action, resource (type and ID), and a human-readable summary
- Seven event categories: Authentication, Authorization, Data Mutation, Data Access, Chain, Integration, System
- Over 25 resource types covering every module
- Indefinite retention (the previous 24-month TTL has been removed — audit records are now kept permanently)

**What This Means for Users:**
- The Activity Audit sidebar item provides a unified view of all platform activity
- You can filter, sort, and export the audit log
- Every action across every module is now consistently recorded

### Credit Facility Workflow Separation

**What Changed:**
Credit facilities now have a dedicated workflow that is fully separated from the securitization and pool workflows:

**Workflow:** Term Sheet → Master Commitment → Funding Request → Funding Notice

Key automation in this workflow:
- Master commitments are **auto-created** when a term sheet is approved (status: Accepted), pre-populated with term sheet data
- Funding notices are **auto-generated** when a funding request is approved, starting with status Pending Token Generated
- Per-lender e-signature tracking ensures the facility agent signs for each lender individually

### Pool Preview Loan Status Visibility

**What Changed:**
Removed and reinstated loans are now visible in the UI with their current status:
- **Removed** loans maintain "Removed" status and remain visible
- **Reinstated** loans show "Reinstated" status and remain visible
- Complete loan status history is maintained and displayed

Previously, removed loans could disappear from some views. Now, all loan statuses are visible regardless of the loan's current state.

### Status Value Standardization

**What Changed:**
Several status values were standardized for consistency:
- Term sheet "Approved" → **"Accepted"** (to distinguish from other approval actions in the platform)
- Master commitment "Active" → **"ACTIVE"** (consistent casing)
- Funding request statuses use uppercase consistently: **DRAFT**, **APPROVED**, **REJECTED**, **CHANGES_REQUESTED**

### Multi-Factor Authentication for Sensitive Operations

**What Changed:**
Multi-factor authentication (MFA) via one-time password has been added as a required step for sensitive operations:

| Action | Required Role | MFA Action |
|---|---|---|
| NFT Minting | Issuer | `NFT_MINT` |
| NFT Transfer (Asset Sale) | Issuer | `NFT_TRANSFER` |
| FT Approval (Token Approval) | Issuer | `FT_APPROVE` |
| FT Transfer | Paying Agent | `FT_TRANSFER` |

Users must verify their identity via OTP before these operations can proceed. Emergency access requests are available for users who cannot complete MFA through the normal flow.

## Impact on Existing Users

### What You Need to Know

- **Asset sale statuses** — If you previously tracked deals by their "Closed" or "Repaid" status, note that these now mean "Active" and "Closed" respectively. The complete lifecycle is: Draft → Pending Review → Published → Commit → Invest → Settlement In Progress → Settled → Active → Repayment In Progress → Closed.

- **E-signature experience** — Signing popups now use Adobe Sign or ZohoSign. The workflow is the same, but the signing interface may look different from what you remember with DocuSign.

- **Audit history** — The centralized audit module now captures all activity. You can access it via Activity Audit in the sidebar for a unified view of platform activity.

- **Authentication** — If your organization has been configured for Microsoft Entra SSO, you can sign in with your organizational credentials. Direct login remains available.

- **MFA prompts** — If you perform NFT minting, token approval, or fund transfers, you will now be prompted for a one-time password before the action can proceed.

- **API consumers** — If you consume platform APIs directly, update your integrations to use `/api/v2` endpoints. The v1 endpoints are being phased out.
