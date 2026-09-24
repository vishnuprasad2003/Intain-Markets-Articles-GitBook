---
title: Loans Overview
description: What loans are and how they move through upload, standardization, pool mapping, verification, and NFT minting
---

# Loans Overview

A loan is one credit agreement. After uploading a loan tape, loans are saved to your organisation and managed in the Loan Registry. Standard (mapped) columns show Intain field names; unmatched columns show original headers in italic.

## Loan Journey

```
Upload (Imports) → LTS field mapping → Loan Registry (Unmapped) → Map to Pool → Add to Batch → Verify → Mint NFT
```

## Key Sections

| Section | What you do |
|---|---|
| **Imports** | Upload loan tape (Excel/CSV); choose As Of Date and Asset Class |
| **Loan Tape Standardization (LTS)** | Match column headers to Intain standard fields; AI suggests matches; delegate to Admin if needed |
| **Loan Registry** | View all loans; Map to Pool; Add to Batch |
| **Batch Verification** | Self Certify (via Adobe Sign) or submit to Verification Agent |
| **Certificates** | Mint NFTs when batch is Reviewed; View NFTs |

## How It Works

**1. Upload** — **Imports** → select As Of Date and Asset Class → choose file → **Submit** → Job ID created → **Trigger LTS**

**2. Standardize (LTS)** — **Trigger LTS** → Map Fields popup → AI pre-fills matches → review/adjust dropdowns → **Save Mapping** → action changes to **View Mapped**

**3. Loan Registry** — **View Mapped → Open in Registry** (or navigate directly). Select loans → **Map to Pool** or **Add to Batch**. Pool metrics auto-update on mapping.

**4. Batch Verification** — **Batch Verification** sidebar → click Batch ID → Loans tab → **Self Certify** (sign via Adobe Sign) or submit to Verification Agent. After verification → batch status **Reviewed**.

**5. Mint NFTs** — **Certificates** → batch in **Reviewed** state → **Mint NFT** → select loans → **Mint Selected** → runs in background → batch status → **Verified**

## Key Rules

- One pool per loan — unmap to reassign
- Only **NFT-minted loans** are eligible for credit facility (master commitment) mapping
- Batch must be **Reviewed** before Mint NFT is enabled
- As Of Date in Loan Tape section shows data for different reporting periods (useful for monthly uploads)

![Loans Onboarding - Uploading - Issuer](.gitbook/assets/Loans_Onboarding_Uploading_Issuer.png)
![Asset Registry - Issuer View](.gitbook/assets/issuer-loan-registry.png)
![Batch Verification](.gitbook/assets/BatchVerification.png)
![NFT Minting](.gitbook/assets/NftMinting.png)

→ See [Loan Management](42_Loan_Management.md) for detailed step-by-step instructions.
→ See [All Loan States Explained](66_All_loan_states_explained.md) for status reference.
