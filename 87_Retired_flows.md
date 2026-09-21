---
title: Retired Flows
description: Learn about workflows and features that have been retired in Intain Markets
---

# Retired Flows

## Overview

This document tracks workflows and features that have been retired or changed in Intain Markets.

## Loans Module Changes

### Batch Verification Process

**Previous (Retired):**
- Only Verification Agent could certify batches
- Issuer had to submit batch and wait for VA to verify
- No self-certification option

**Current:**
- Issuer can **Self Certify** batches directly
- Issuer can also submit to Verification Agent if needed
- Multiple verification paths available

### NFT Minting Location

**Previous:**
- NFT minting is done by Verification Agent

**Current:**
- NFT minting in **Certificates** section
- View NFT and Mint NFT buttons in Certificates
- Batch Verification for verification only

## Pool Module Changes

### Pool Sharing for Preview

**Previous (Retired):**
- Only Issuer could share pools with market makers and investors
- Market Maker could not share to investors

**Current:**
- Issuer shares pools with market makers and investors
- Market Maker can also share accepted pools to investors

### Loan Status Display

**Previous (Retired):**
- Removed loans not visible in UI
- Reinstated loans not tracked
- Limited loan status history

**Current:**
- Removed loans show "Removed" status, remain visible
- Reinstated loans show "Reinstated" status
- Complete loan status history maintained

## API and Integration Retirements

### Legacy v1 Pool/Loan Endpoints

**Deprecated:**
- Pre-v2 pool and loan API endpoints are deprecated in favor of /api/v2/pools and /api/v2/loans
- The legacy routes remain mounted but will be removed in a future release

### DocuSign Integration

**Removed:**
- DocuSign e-signature support has been removed
- Use Adobe Sign or ZohoSign for electronic signatures

### Legacy Notification System

**Deprecated:**
- The v1 notification endpoints are deprecated in favor of the v2 notification module with SSE (server-sent events) support

### IPFS File Storage

**Migrating:**
- Legacy IPFS file access is being migrated to Azure Blob storage
- IPFS endpoints remain available during the migration period but should not be used for new files

### Legacy Data Room

**Deprecated:**
- The v1 data room is being replaced by the v2 data room module with folder-based organization, SFTP import, and access grants

## Deprecated Features

Features may be marked as deprecated before retirement. Check release notes for deprecation announcements.

## How to Stay Current

- **Release Notes** - Review for changes
- **Documentation** - Reflects current workflows
- **Support** - Contact for clarification on current processes
