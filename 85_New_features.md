---
title: New Features
description: Learn about new features and capabilities added to Intain Markets
---

# New Features

## Overview

This document tracks features and capabilities currently implemented in Intain Markets.

## Implemented Features

### Credit Facility Module

**Automatic Master Commitment Creation:**

* When term sheets are approved, master commitments are automatically created
* Master commitment created with Draft status
* Pre-populated with term sheet data
* Facility agent configures facility structure and submits for lender approval

**Per-Lender E-Signature Tracking:**

* Facility agents sign funding notices for each lender individually
* E-sign progress shows as (0/n) → (n/n)
* Each lender's signature status tracked separately
* Each lender can see funding notices once their e-sign is complete

**Individual Lender Approval Tracking:**

* Each lender's approval status tracked separately
* Facility becomes ACTIVE when at least one lender approves
* Each lender's approval tracked with timestamps

**Token Generation:**

* Tokens automatically created for funding notices
* Unique blockchain contract address stored
* Token distribution calculated from lender participation percentages
* Tokens created on Avalanche C-Chain

### E-Signature Integration

**Adobe Sign Integration:**

* Term sheets signed via Adobe Sign before submission
* Master commitments signed via Adobe Sign for lender approval
* Funding notices signed via Adobe Sign per lender
* Signed documents stored securely

**Signature Tracking:**

* Term sheet status changes to BorrowerSigned after signing
* Master commitment lender signatures tracked individually
* Funding notice signatures tracked per lender (E-sign 0/n → n/n)

### Status Tracking

**Comprehensive Status History:**

* All status changes tracked with who, when, and reason
* Action history shows all actions taken
* Complete audit trails maintained

**Status Workflows:**

* Term Sheets: Draft → BorrowerSigned → FAReview → Accepted
* Master Commitments: Draft → PendingLenderApproval → ACTIVE
* Funding Requests: DRAFT → FAReview → APPROVED
* Funding Notices: Pending Token Generated → FA Approved → E-signed for lenders

### Pool Module

**Loan Mapping from Loan Registry:**

* Select loans and click Map to Pool
* Loans can only be mapped to one pool at a time

**NFT Minting:**

* Batch verification required before minting
* Certificates section for minting and viewing NFTs

**Pool Sharing:**

* Share with market makers, investors, rating agencies
* Control feedback and download permissions per share

### Loans Module

**Loan Tape Standardization (LTS):**

* Upload loan files via Imports section
* Basic and Intelligent AI mapping options
* Save mappings for future use

**Batch Verification:**

* Self Certify option for issuers
* Submit to verification agent option
* Status: Pending → Reviewed → Certified

### Asset Sale Module (February–September 2026)

**Whole Loan Sale Workflow:**

* Complete deal creation, underwriter review, investor commitment, and settlement
* NFT-based ownership transfer during settlement
* Post-sale repayment lifecycle with loan tape upload, bank wire initiation, investor receipt confirmation, and NFT burn for deal closure

**Repayment Flow:**

* Post-sale repayment process for asset sales
* Loan tape upload and bank wire initiation
* Investor receipt confirmation and NFT burn for deal closure

**Receivables Analytics Shell:**

* Comprehensive analytics embedded within asset sale deals
* Asset Analysis: Overview, Strats, Performance, Receivables
* Risk Surveillance: Overview, Concentration, Data Checks, Exceptions, Performance Triggers
* Reports section for deal-level reporting

**Receivables RNFT Burn (March 2026):**

* Investor-initiated async burn of receivables NFTs on repaid asset sale deals

### Credit Facility Deal Creation RemoteV2 (September 2026)

**11-Tab Wizard for Facility Agents:**

* General, Facilities, Fees, Expenses, Manual Inputs, Accounts, Triggers, Borrowing Base, Calculations, Waterfall, Review
* Streamlined deal setup flow for facility agents

### Microsoft Entra SSO (February 2026)

**Single Sign-On:**

* SSO via Microsoft Entra (formerly Azure AD)
* OAuth callback and role selection flow
* Seamless integration with existing authentication

### Admin View-As / Impersonation (February 2026)

**Read-Only Impersonation:**

* Admins can view the platform as another user for support purposes
* Read-only mode prevents unintended changes

### Audit Module (March 2026)

**Centralized Activity Logging:**

* Cross-module activity logging with export capabilities
* Centralized audit trail accessible via the Activity Audit sidebar item

### E-Signature v2 (February 2026)

**Refactored E-Signature System:**

* Supports both Adobe Sign and ZohoSign
* Shared helpers and mock signing for test environments
* DocuSign support removed

### Modelling Workbench (January–February 2026)

**Scenario Comparison Tool:**

* Configure and compare cashflow models for pools
* Available to market makers and investors

### Historical Tape Upload (February 2026)

**Historical Data Ingestion:**

* New screen for uploading historical loan tape data

### Issuer V2 Shell (January 2026)

**Updated Issuer Screens:**

* V2 dashboard, pool details, batches, and profile screens for issuers

### Pool Analysis IDA Button (September 2026)

**IDA-Powered Analytics:**

* Analytics entry point on pool preview details for market makers and investors

### v2 API Consolidation (January–September 2026)

**API Migration:**

* Pools, loans, batches, organizations, users, dataroom, and securitization migrated to versioned /api/v2 endpoints
* Zod validation and cursor-based pagination
* Standardized error handling

**Batches v2 (March 2026):**

* New batch management API with enhanced verification workflows

**Loan Registry v2 (2026):**

* Updated asset registry with IDA (AI-assisted field mapping)
* Reference ingestion ID support

### ABDP Verification Agent Integration (2026)

**Automated Batch Certification:**

* Batch loan tapes are streamed from Snowflake directly to the ABDP (Verification Agent) platform for certification
* ABDP exchanges JWT tokens via Entra SSO OBO (On-Behalf-Of) flow for secure machine-to-machine auth
* Certification results are posted back to the platform and recorded on the batch
* VA certification evidence (contract files + loan tape) is uploaded automatically
* Issuers submit batches via the Batch Verification screen; the ABDP processes asynchronously
* Notification emails sent to both issuer and verification agent on submission and completion

### Participation Agreements Module (2026)

**New Product Line:**

* Participation Agreements added as a fourth transaction type alongside Asset Sale, Credit Facilities, and Securitization
* Visible in the sidebar navigation and dashboard overview tiles for all roles
* Enables structured participation agreement workflows between issuers, market makers, and investors
* Integrated with the unified dashboard showing deal counts and status alongside other product lines

### Delegation Workflows (2026)

**Typed Delegation Requests:**

* Principal-to-delegatee typed delegation requests via v2 API

### Rate Limiting (2026)

**Security Hardening:**

* Redis-backed rate limiting on all API routes

### Wallet Onboarding (2026)

**Per-Organization Wallet Setup:**

* Per-organization wallet onboarding with sanctions screening

### Notification Drawer v2 (March 2026)

**Real-Time Notifications:**

* App-wide real-time notifications with server-sent events (SSE)

### Server-side Column Filters (March–September 2026)

**Enhanced Table Filtering:**

* Server-side filtering across batches, NFTs, pools, and admin lists

## Current Development

**Payment Integration:**

* Kinexys integration for fund transfers
* Circle integration for fund transfers
* Payment methods selectable during Confirm and Settle

**Multi-Blockchain Support:**

* Solana integration for token transfers
* Users can choose Avalanche or Solana

## How to Stay Informed

Check release notes, documentation updates, and platform notifications for new features and enhancements.
