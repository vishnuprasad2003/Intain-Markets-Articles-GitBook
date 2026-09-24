---
title: Who Can Do What
description: >-
  Comprehensive role-permission matrix showing what each role can see and do
  across all platform modules — pools, loans, credit facilities, asset sales,
  data rooms, and administration
---

# Who Can Do What

## Overview

This reference guide provides a comprehensive view of what each role can do in Intain Markets. The platform enforces these permissions at the API level — not just in the UI — so they cannot be bypassed. Your role is assigned when your account is created and determines both what you can see and what actions are available to you.

Two factors control whether you can perform an action: your **role** (are you the right type of user?) and the **status** of the item (is it in the right state for this action?). Both must be satisfied.

## Roles Covered

The platform defines the following roles:

| Role                              | Primary Function                                                                               |
| --------------------------------- | ---------------------------------------------------------------------------------------------- |
| **Issuer / Borrower**             | Creates and manages pools, loans, and term sheets. Originates transactions.                    |
| **Market Maker / Facility Agent** | Reviews pools, structures deals, approves term sheets and funding requests. Intermediary role. |
| **Investor / Lender**             | Reviews opportunities, approves commitments, provides funding. Capital provider role.          |
| **Underwriter**                   | Reviews and approves asset sale deals before they reach investors. Gatekeeper role.            |
| **Servicer**                      | Uploads loan tapes for assigned deals. Operational support role.                               |
| **Rating Agency**                 | Reviews shared pools and provides feedback. Advisory role.                                     |
| **Paying Agent**                  | Executes fund transfers for securitization. Settlement role.                                   |
| **Admin**                         | Manages organizations, users, KYC, and platform-wide operations. Administrative role.          |

## What Each Role Can Do

### Issuer / Borrower

**Pools Module:**

| Action                              | When Available                                 |
| ----------------------------------- | ---------------------------------------------- |
| Create Pool                         | Always (via Set-up Pool button)                |
| Edit Pool                           | Pool status: Created                           |
| Share Pool                          | Pool status: Created or Preview                |
| Submit to Market Maker (Start Deal) | After NFT minting complete                     |
| Accept / Reject Loan Removal        | When market maker or investor requests removal |
| Provide Feedback                    | On own pools only                              |

**Loans Module:**

| Action                                  | When Available                                   |
| --------------------------------------- | ------------------------------------------------ |
| Upload Loan File                        | Always (via Imports section)                     |
| Trigger LTS (Loan Tape Standardization) | After upload                                     |
| Save Mapping                            | After LTS mapping                                |
| Map Loans to Pool                       | From Loan Registry; loan not already mapped      |
| Add Loans to Batch                      | From Loan Registry; loan not already in batch    |
| Self Certify Batch                      | Batch status: Pending (MFA required: `NFT_MINT`) |
| Mint NFT                                | Batch status: Reviewed                           |
| View NFT                                | After minting                                    |

**Credit Facility Module (as Borrower):**

| Action                                    | When Available                                                         |
| ----------------------------------------- | ---------------------------------------------------------------------- |
| Create Term Sheet                         | Always (via Term Sheet Setup)                                          |
| Sign Term Sheet                           | Term sheet status: Draft                                               |
| Submit Term Sheet to FA                   | Term sheet status: BorrowerSigned                                      |
| Edit Term Sheet (after changes requested) | Term sheet status: CHANGES\_REQUESTED                                  |
| Map Loans to Facility                     | MC status: ACTIVE and deal modelling completed                         |
| Create Funding Request                    | MC status: ACTIVE and deal modelling completed                         |
| Edit Funding Request                      | Funding request status: DRAFT or CHANGES\_REQUESTED                    |
| Submit Funding Request                    | Funding request status: DRAFT (with all required fields and documents) |

**Asset Sale Module (as Issuer):**

| Action                      | When Available                                                     |
| --------------------------- | ------------------------------------------------------------------ |
| Create Deal                 | Always (via Asset Sale module)                                     |
| Assign Loans to Deal        | Deal status: Draft                                                 |
| Publish Deal                | After loan assignment complete                                     |
| Initiate Repayment          | Deal status: Active (post-settlement)                              |
| Transfer NFTs               | Deal status: Settlement In Progress (MFA required: `NFT_TRANSFER`) |
| Approve Token Transfer (FT) | When token approval is needed (MFA required: `FT_APPROVE`)         |

**Data Room:**

| Action         | When Available                           |
| -------------- | ---------------------------------------- |
| Upload Files   | For pools/deals where you are the issuer |
| Delete Files   | For pools/deals where you are the issuer |
| Rename Files   | For pools/deals where you are the issuer |
| Download Files | For your own pools/deals                 |
| Create Folders | For pools/deals where you are the issuer |

### Market Maker / Facility Agent

**Pools Module:**

| Action               | When Available               |
| -------------------- | ---------------------------- |
| Review Pool          | When shared with you         |
| Accept Mandate       | Pool status: Mandate Pending |
| Reject Mandate       | Pool status: Mandate Pending |
| Provide Feedback     | After accepting mandate      |
| Request Loan Removal | After accepting mandate      |
| Share to Investor    | Pool status: Deal            |

**Credit Facility Module (as Facility Agent):**

| Action                                        | When Available                                      |
| --------------------------------------------- | --------------------------------------------------- |
| Review Term Sheet                             | Term sheet status: FAReview                         |
| Approve Term Sheet                            | Term sheet status: FAReview                         |
| Reject Term Sheet                             | Term sheet status: FAReview                         |
| Request Changes on Term Sheet                 | Term sheet status: FAReview                         |
| Configure Master Commitment (Create Facility) | MC status: Draft                                    |
| Add Lenders to Facility                       | MC status: Draft                                    |
| Create Sub-Facility                           | MC status: Draft, contract type: multiple           |
| Submit MC for Lender Approval                 | MC status: Draft (after configuration complete)     |
| Set Up Deal (Deal Modelling)                  | MC status: ACTIVE                                   |
| Review Funding Request                        | Funding request status: FAReview                    |
| Approve Funding Request                       | Funding request status: FAReview                    |
| Reject Funding Request                        | Funding request status: FAReview                    |
| Request Changes on Funding Request            | Funding request status: FAReview                    |
| Approve Funding Notice                        | After funding request approved and notice generated |
| E-sign for Each Lender                        | After funding notice approved                       |

### Investor / Lender

**Pools Module:**

| Action               | When Available                          |
| -------------------- | --------------------------------------- |
| Review Pool          | When shared with you (Pools section)    |
| Provide Feedback     | If feedback permission enabled on share |
| Download Data        | If download permission enabled on share |
| Request Loan Removal | After pool shared with you              |

**Credit Facility Module (as Lender):**

| Action                             | When Available                                           |
| ---------------------------------- | -------------------------------------------------------- |
| Review Master Commitment           | MC status: PendingLenderApproval (Opportunities section) |
| Approve & E-Sign Master Commitment | MC status: PendingLenderApproval                         |
| Review Funding Notice              | After FA completes e-sign for your lender entry          |
| Select Payment Method              | During funding notice review                             |
| Confirm and Settle                 | After transferring funds                                 |

**Asset Sale Module (as Investor):**

| Action                  | When Available                                  |
| ----------------------- | ----------------------------------------------- |
| View Available Deals    | When deals are published and approved           |
| Commit to Deal          | Deal status: Approved / Commit                  |
| Sign Investor Agreement | After commitment                                |
| Confirm Settlement      | After agreement signed and settlement initiated |
| Confirm Repayment       | When repayment initiated                        |
| Burn NFTs               | After repayment confirmed                       |

### Underwriter

**Asset Sale Module:**

| Action                     | When Available                                  |
| -------------------------- | ----------------------------------------------- |
| Review Deal                | When deal is published (status: Pending Review) |
| Approve Deal               | After review                                    |
| Reject Deal                | After review                                    |
| Manage Investor Allocation | After deal approval                             |

### Servicer

| Action                   | When Available                      |
| ------------------------ | ----------------------------------- |
| View Assigned Deals      | Always (only deals assigned to you) |
| Upload Monthly Loan Tape | For assigned deals                  |
| View Deal Details        | For assigned deals                  |

### Rating Agency

| Action            | When Available                 |
| ----------------- | ------------------------------ |
| View Shared Pools | When pools are shared with you |
| Provide Feedback  | If feedback permission enabled |
| Download Data     | If download permission enabled |

Rating agencies cannot request loan removal, create pools, or approve anything.

### Paying Agent

| Action                  | When Available                                                 |
| ----------------------- | -------------------------------------------------------------- |
| Execute FT Transfer     | When fund distribution is needed (MFA required: `FT_TRANSFER`) |
| View Settlement Details | For assigned securitization deals                              |

### Admin

| Action                            | When Available                                 |
| --------------------------------- | ---------------------------------------------- |
| Manage Organizations              | Always                                         |
| Approve / Reject KYC              | When KYC submissions are pending               |
| Process LTS Delegation            | When delegated by issuer                       |
| Process Deal Modelling Delegation | When delegated by facility agent               |
| View Platform-Wide Analytics      | Always                                         |
| View-As (Impersonate) User        | Always (read-only mode only)                   |
| Run Status Migrations             | When administrative data fixes are needed      |
| Access Audit Module               | Always (sees all organizations' events)        |
| Manage User Accounts              | Always (activate, deactivate, update profiles) |

## Important Access Notes

**Role determines visibility and actions** — You only see items that are shared with you, assigned to you, or where you have a defined role. An investor cannot see a pool that has not been shared with them. A lender cannot see a funding notice until the facility agent has completed the e-signature for their specific entry.

**Status determines action availability** — Actions are enabled and disabled based on the current status of the item. A term sheet in Draft status can be edited; a term sheet in FAReview cannot be edited by the borrower. These rules are enforced at the backend, not just in the UI.

**Both role AND status must be satisfied** — Having the right role is necessary but not sufficient. You also need the item to be in the right status. A facility agent with the role to approve term sheets cannot approve one that is still in Draft status — it must be in FAReview.

**MFA is required for blockchain operations** — NFT minting, NFT transfer, FT approval, and FT transfer all require multi-factor authentication. Even if you have the correct role and the item is in the correct status, you must verify your identity with a one-time password before these operations can proceed.

**Platform enforces permissions automatically** — You cannot bypass role restrictions. The platform checks your role and the item's status on every request. If an action is not available to you, the API returns an error regardless of how the request is made.

**Sharing controls visibility** — For pools, the issuer controls who can see the pool through sharing settings. Sharing permissions separately control feedback access and download access. Recipients only see pools that have been shared with them.

**Per-lender visibility on funding notices** — A lender can only see a funding notice after the facility agent has completed the e-signature for that specific lender. Until the FA signs for you, the funding notice does not appear in your view, even though it may already be visible to other lenders whose signatures are complete.
