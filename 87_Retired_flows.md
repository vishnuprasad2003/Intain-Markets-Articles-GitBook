---
title: Retired Flows
description: Complete record of workflows, features, integrations, and API versions that have been retired or deprecated in Intain Markets
---

# Retired Flows

## Overview

This document is the authoritative record of workflows, features, and integrations that have been retired, deprecated, or significantly changed in Intain Markets. Reviewing this page helps existing users understand why a familiar feature may have moved, changed behavior, or disappeared entirely, and what replaces it. New users can skip items marked "Removed" but should note "Deprecated" items that still function but will be removed in a future release.

## What Changed

### 1. DocuSign E-Signature Integration — Removed

**Previous Behavior:**
DocuSign was the original e-signature provider used for term sheets, master commitments, funding notices, and batch self-certification. Envelopes were created via the DocuSign API, and signed documents were stored with `docusignEnvelopeId` and `docusignEnvelopeStatus` fields.

**Current Behavior:**
DocuSign has been fully replaced by **Adobe Sign** and **ZohoSign** as the supported e-signature providers. The platform's unified e-signature helper (`esignature.helper.js`) now supports two provider descriptors:
- `ESIGN_PROVIDERS.ADOBESIGN` — production provider, stores envelopes in the `adobesign_requests` collection
- `ESIGN_PROVIDERS.ZOHOSIGN` — alternative provider, stores envelopes in the `zohosign_requests` collection

**What Users Should Know:**
- All new e-signature workflows use Adobe Sign or ZohoSign
- Legacy DocuSign field names (`docusignEnvelopeId`, `docusignEnvelopeStatus`) still appear in some database records for historical term sheets and master commitments created before the migration
- The `docusign_envelopes` collection remains in the database for historical reference but is no longer written to
- Webhook routes for DocuSign (`/docusign`) are still registered in rate-limit configuration for backward compatibility but are not actively used

### 2. Legacy v1 Pool and Loan API Endpoints — Deprecated

**Previous Behavior:**
Pool and loan operations were served through unversioned or v1 API routes (e.g., `/pools/list`, `/loans/list`).

**Current Behavior:**
All pool, loan, batch, feedback, and dashboard modules have been refactored to live under a versioned API prefix. The current standard is `/api/v2`:

| Module | Legacy Path | Current Path |
|--------|-------------|--------------|
| Pools | `/pools/*` | `/api/v2/pools/*` |
| Loans | `/loans/*` | `/api/v2/loans/*` |
| Batches | `/batches/*` | `/api/v2/batches/*` |
| Feedback | `/feedback/*` | `/api/v2/feedback/*` |
| Dashboard | `/dashboard/*` | `/api/v2/dashboard/*` |
| Securitization | various | `/api/v2/securitization/*` |
| Receivables (RNFT) | various | `/api/v1/receivables/rnft/*` |
| Data Room | various | `/api/v2/datarooms/*` |

**What Users Should Know:**
- The legacy routes remain mounted for backward compatibility but will be removed in a future release
- The next breaking change will move routes to `/api/v3`; `/api/v2` will be retired at that point
- Frontend migration can happen URL by URL — no flag day required
- Organizations and some administrative routes still use `/api/v1/organizations/*` paths

### 3. IPFS File Storage — Migrated to Azure Blob Storage

**Previous Behavior:**
All off-chain documents (collateral profiles, financial statements, KYC documents, signed PDFs, loan data files) were stored on IPFS. References were stored as IPFS Content Identifiers (CIDs) — plain strings like `QmXyz...`.

**Current Behavior:**
Azure Blob Storage is now the primary off-chain object store. New documents are stored as structured Blob pointers containing the container name, blob path, and Azure version ID. The `blobStorageHelper` module handles all document operations.

**Backward Compatibility:**
- The system automatically detects whether a stored reference is a Blob pointer (object) or a legacy IPFS CID (string) using the `isBlobPointer` utility
- Legacy IPFS CIDs are still readable through the configured IPFS gateway (`config.ipfsGetURL`)
- Historical documents do not need to be migrated — reads are transparently routed to the correct storage backend
- SAS URL generation (for temporary read-only download links) is only supported for Blob-stored documents, not legacy IPFS CIDs

**What Users Should Know:**
- No user action required — the migration is transparent
- New file uploads always go to Azure Blob Storage
- Historical files stored on IPFS remain accessible
- IPFS endpoints should not be used for new file integrations

### 4. Legacy v1 Notification System — Deprecated

**Previous Behavior:**
Notifications were delivered through basic REST polling endpoints.

**Current Behavior:**
The v2 notification module uses **Server-Sent Events (SSE)** for real-time push notifications. The `notification.sse` module provides:
- `broadcast(orgId, content)` — send a real-time notification to a specific organization
- `broadcastToMany(orgIds, content)` — send to multiple organizations simultaneously
- Multi-channel delivery combining SSE (real-time) with email (asynchronous) via `notificationHandler.sendMultiChannel()`

Notifications are sent for key workflow events including funding request approvals, term sheet status changes, batch verification completions, e-signature completions, and settlement events.

### 5. Legacy Data Room — Replaced by v2 Data Room Module

**Previous Behavior:**
The v1 data room provided basic document storage and retrieval per pool or deal.

**Current Behavior:**
The v2 data room module (`api/dataroom/`) provides a significantly richer feature set:
- **Folder-based organization** — hierarchical folder tree within each data room
- **SFTP landing-zone import** — automated file ingestion with zip expansion
- **Organization-level access grants** — three access levels for granular permission control
- **Per-document feedback counts** — integrated with the feedback module
- **Multi-select zip download** — download multiple documents as a single archive
- **Short-lived download URLs** — time-limited SAS URLs for secure document access
- **Audit trail** — complete history of uploads, downloads, and access changes

**What Users Should Know:**
- The v2 data room is fully operational and is the only supported data room
- SFTP import allows automated document delivery from external systems
- Access grants control which organizations can view documents at the room, folder, or document level

### 6. Batch Verification Process — Changed

**Previous Behavior:**
Only the Verification Agent could certify loan batches. The Issuer had to submit each batch and wait for the Verification Agent to review and verify it. There was no option for self-certification.

**Current Behavior:**
The Issuer now has two verification paths:
- **Self Certify** — The Issuer can certify batches directly via the e-signature workflow (`batchSelfCertify`). Loans in self-certified batches are stamped with `verificationSource: 'Self Certified (Data Only)'`
- **Submit to Verification Agent** — The traditional path where a third-party Verification Agent reviews and certifies the batch

The self-certification flow uses the same e-signature infrastructure (Adobe Sign / ZohoSign) and records the certificate in the same format, ensuring audit trail consistency.

### 7. NFT Minting Location — Changed

**Previous Behavior:**
NFT minting was performed by the Verification Agent as part of the batch verification workflow.

**Current Behavior:**
NFT minting has moved to the **Certificates** section in the UI. Issuers can:
- View NFT details using the **View NFT** button
- Mint NFTs using the **Mint NFT** button
- Batch Verification is now used for verification purposes only, not minting

### 8. Pool Sharing Permissions — Expanded

**Previous Behavior:**
Only the Issuer could share pools with Market Makers and Investors. Market Makers could not forward pools to investors.

**Current Behavior:**
- The Issuer can share pools with both Market Makers and Investors
- Market Makers can also share accepted pools to Investors, enabling a pass-through distribution model

### 9. Loan Status Display — Enhanced

**Previous Behavior:**
Removed loans were not visible in the UI. Reinstated loans were not tracked. Loan status history was limited.

**Current Behavior:**
- Removed loans show a **Removed** status and remain visible in the pool's loan list
- Reinstated loans show a **Reinstated** status with a complete trail
- Full loan status history is maintained, including all transitions and the actor who performed each change

### 10. Legacy E-Signature Route — Deprecated

A v1 e-signature route pattern (referred to as `legacyRoute` in the codebase) is still available. This route calls the provider controller directly and returns the provider's own response envelope (`{ statuscode, isSuccess, message, data }`) instead of the platform's standard success response. This route is kept only for backward compatibility and will be removed when all consumers have migrated to the v2 e-signature endpoints.

## Impact on Existing Users

**No Immediate Action Required for Most Changes** — The platform maintains backward compatibility for deprecated features. Legacy IPFS documents remain readable, legacy API routes still function, and historical DocuSign records are preserved.

**Action Required for Integrations** — If you have external systems calling legacy API endpoints (unversioned pool/loan routes), plan to migrate to the `/api/v2` prefixed routes before the next major version release.

**E-Signature Provider Change** — If your organization previously configured DocuSign, you must now use Adobe Sign or ZohoSign. Contact support if your organization's e-signature provider has not been updated.

**Self-Certification Option** — Issuers who previously depended on the Verification Agent for all batch certifications can now choose self-certification for faster processing when third-party verification is not required.
