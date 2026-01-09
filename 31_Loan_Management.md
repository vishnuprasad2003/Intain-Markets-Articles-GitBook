---
title: Loan Management
description: Learn how to onboard loans, standardize them, map to pools, verify, and mint NFTs
---

# Loan Management

## Overview

Loan management covers the complete loan workflow from uploading loan tape files through verification and NFT minting. As an issuer, you onboard loans through the Imports section, standardize them using Loan Tape Standardization (LTS), manage them in the Loan Registry, map them to pools, add them to batches for verification, and mint them as NFTs.

## Who Can Use This

- **Issuers/Borrowers**: Upload loan data, perform standardization, manage loans in registry, map to pools, verify batches, and mint NFTs.

## When This Is Used

Use loan management when:
- You need to upload new loan tape data into the platform
- You need to standardize loan tape columns to Intain standard fields
- You want to view and manage your loans in the Loan Registry
- You need to map loans to pools
- You want to add loans to batches for verification
- You need to verify loans through self-certification or verification agent
- You want to mint loans as NFTs for credit facility transactions

## Step-by-Step Process

### Part 1: Uploading and Standardizing Loans

#### Step 1: Access the Imports Section

1. **Navigate to Imports**
   - Log in to the platform with your Issuer credentials
   - From the left expandable menu (which expands when you hover over it), click on **Imports**
   - The Imports screen displays with upload options at the top and a table of previously uploaded files below

![Access Imports](imagesByMdFilesFolder/31/AccessImports.png)

#### Step 2: Upload Your Loan Tape File

1. **Select Upload Parameters**
   - Select the **As Of Date** for this loan tape (the reporting date for the loan data)
   - Select the **Asset Class** (Auto Loans, Personal Loans, Mortgages, Commercial Mortgages, etc.)
   - Click **Choose File** to browse for your loan tape file (Excel or CSV format)

2. **Submit the File**
   - Review your selections
   - Click **Submit** to upload the file
   - The system creates a **Job ID** for tracking this upload
   - The file appears in the table below with the action **Trigger LTS**

![Select and Upload File](imagesByMdFilesFolder/31/SelectAndUploadFile.png)

#### Step 3: Trigger Loan Tape Standardization (LTS)

1. **Start Standardization**
   - In the table, find your uploaded file
   - Click the **Trigger LTS** button in the Actions column
   - The **Map Fields** popup opens, showing your loan tape column headers alongside Intain standard fields

![Loans Onboarding - Uploading - Issuer](imagesByMdFilesFolder/31/Loans_Onboarding_Uploading_Issuer.png)

2. **Choose Mapping Method**
   - At the top of the popup, you have options:
     - **Delegation Button**: Click to delegate this task to Admin. A popup appears where you enter start date, end date, and required documents. After submitting, Admin will complete the mapping on your behalf.
     - **Re-run Button**: Click to choose between:
       - **Basic**: Standard AI mapping will match your columns to Intain fields
       - **Intelligent**: Enhanced AI mapping for better accuracy

3. **Review and Edit Mappings**
   - The popup shows each of your loan tape headers with a dropdown to select the matching Intain standard field
   - AI mapping pre-populates suggested matches
   - Review each mapping and edit using the dropdowns if needed
   - Ensure critical fields (Loan ID, Balance, Interest Rate, etc.) are correctly mapped

4. **Save the Mapping**
   - Once satisfied with the mappings, click **Save Mapping**
   - The loans are saved to your organization's database
   - The popup closes
   - In the Imports table, the action changes from **Trigger LTS** to **View Mapped**

![Review Standardized Loans](imagesByMdFilesFolder/31/ReviewStandardizedLoans.png)

#### Step 4: View Mapped Loans and Access Loan Registry

1. **View the Mapped Loans**
   - Click **View Mapped** in the Actions column
   - A screen shows all the loans that were standardized from that file
   - At the bottom, click **Open in Registry** to navigate to the Loan Registry

2. **Access the Loan Registry**
   - You can also navigate directly to the **Loan Registry** from the left expandable menu
   - The Loan Registry shows all your onboarded loans
   - **Mapped columns** (Intain standard fields) appear first
   - **Unmapped columns** (original headers that didn't match) appear after, with headers in italic

![Access Loan Registry](imagesByMdFilesFolder/31/accessLoanRegistry.png)

### Part 2: Managing Loans in the Registry

#### Viewing Loan Data

1. **Understanding the Display**
   - Loans are listed with their data across all columns
   - Mapped columns show standard Intain field names
   - Unmapped columns show original headers in italic format
   - Use horizontal scrolling to view all columns
   - The **Status** column shows:
     - **Unmapped**: Loan is not assigned to any pool
     - **Mapped**: Loan is assigned to a pool

2. **Using the Buttons**
   - **Add Loan**: Navigates to the Imports section to upload more loan files
   - **Map to Pool**: Enabled when you've selected loans that aren't already mapped to a pool
   - **Add to Batch**: Enabled when you've selected loans that aren't already in a batch

#### Mapping Loans to Pools

1. **Select Loans**
   - Use checkboxes to select individual loans, or use the select-all checkbox
   - Selected loans should be in "Unmapped" status (not already in a pool)

2. **Click Map to Pool**
   - Click the **Map to Pool** button
   - A popup appears with a dropdown showing all your pools

3. **Choose the Target Pool**
   - Select the pool you want to map the loans to
   - The dropdown shows pools you've created

![Choose Pool to Map](imagesByMdFilesFolder/31/ChoosePoolToMap.png)

4. **Confirm and Complete Mapping**
   - Review your selection
   - Click **Submit** to complete the mapping
   - The loans are now mapped to the selected pool
   - Pool metrics update automatically
   - In the Loan Registry, the Status column now shows the pool name for these loans

![Confirm Mapping](imagesByMdFilesFolder/31/ConfirmMapping.png)

### Part 3: Batch Verification

#### Adding Loans to a Batch

1. **Select Loans for Batch**
   - In the Loan Registry, select loans using checkboxes
   - Selected loans should not already be in a batch
   - Click **Add to Batch**
   - The loans are grouped into a batch

#### Accessing Batch Verification

1. **Navigate to Batch Verification**
   - From the left expandable menu, click on **Batch Verification**
   - The screen shows all your batches with their details
   - **Batch Verification Status**: Starts as **Pending**
   - **Verification Status**: Starts as **No**

2. **Open Batch Details**
   - Click on a **Batch ID** to open the batch details page
   - Two tabs are available: **Loans** and **Documents**

#### Self Certification

1. **Access the Loans Tab**
   - In batch details, the Loans tab shows all loans in this batch
   - The **Self Certify** button is available

2. **Initiate Self Certification**
   - Click **Self Certify**
   - A popup appears asking for:
     - Name
     - Signer Name
     - Email
     - Place

3. **Complete E-Signature**
   - Fill in the required fields
   - Click **E-Sign**
   - An Adobe Sign popup window opens automatically
   - The popup shows the loan certification details listing all loans in the batch
   - Complete the signature process in Adobe Sign

4. **Certification Complete**
   - After signing, the verification progresses
   - Verification Status changes to **Self Certify (Data Only)**
   - Batch Verification Status changes to **Reviewed**

#### Verification Agent Process

1. **Upload Documents (Optional)**
   - Go to the **Documents** tab in batch details
   - Select document type and verification template
   - Select the file from your file share (files must be pre-uploaded to the file share)
   - These documents will be used by the verification agent

2. **Submit to Verification Agent**
   - Submit the batch for verification agent review
   - The verification agent receives this in their dashboard
   - They verify loan details against the uploaded documents
   - After verification, they certify the batch

3. **Verification Outcomes**
   - **Certified**: Verified by third-party verification agent
   - **Self Certified**: Issuer logged in as verification agent and verified
   - **Self Certify (Data Only)**: Issuer used Self Certify button directly

### Part 4: NFT Minting

#### Accessing Certificates Section

1. **Navigate to Certificates**
   - From the left expandable menu, click on **Certificates**
   - The screen shows the same batch details with verification status
   - **Actions column** shows:
     - **View NFT**: View already minted NFTs
     - **Mint NFT**: Mint loans as NFTs

2. **Button Availability**
   - When Batch Verification Status is **Pending**: Both buttons are disabled
   - When Batch Verification Status is **Reviewed**: Both buttons are enabled
   - When Batch Verification Status is **Verified**: Only View NFT is enabled

#### Minting NFTs

1. **Start Minting**
   - Ensure Batch Verification Status is **Reviewed**
   - Click **Mint NFT**
   - A screen shows all loans in the batch with checkboxes

2. **Select Loans to Mint**
   - Use the select-all checkbox at the top left to select all loans, or
   - Select individual loans using their checkboxes

3. **Execute Minting**
   - Click **Mint Selected** at the top right
   - Minting runs as a background process
   - Progress can be monitored

4. **Minting Complete**
   - After all selected loans are minted:
     - Batch Verification Status changes to **Verified**
     - Loans now have NFT representations on the blockchain
     - Click **View NFT** to see the minted NFTs
     - These loans are now eligible for credit facility mapping

## Rules & Validations

- **File Format**: Loan tape files must be in Excel (.xlsx) or CSV format with column headers in the first row.

- **Required Fields**: Critical fields like Loan ID must be mapped for successful standardization.

- **One Pool Per Loan**: Loans can only be mapped to one pool at a time. Unmap from current pool before mapping to another.

- **Batch Requirements**: Loans must not already be in a batch to be added to a new batch.

- **Verification Before Minting**: Batch Verification Status must be Reviewed before NFT minting is enabled.

- **Credit Facility Eligibility**: Only NFT-minted loans can be mapped to master commitments for credit facilities.

- **Automatic Updates**: Pool metrics update automatically when loans are mapped or removed.

- **Data Persistence**: All loan data is stored in your organization's database after standardization.

## What Happens Next

**After Uploading and Standardizing:**
- Loans appear in your Loan Registry
- Loans are available for mapping to pools
- Loans can be added to batches for verification

**After Mapping to Pool:**
- Pool metrics include the mapped loans
- Loans appear in the pool's Loans tab
- You can share the pool with market makers, investors, and rating agencies

**After Batch Verification:**
- NFT minting becomes available
- Loans are validated and ready for tokenization

**After NFT Minting:**
- Loans have blockchain representation
- Loans are eligible for credit facility mapping
- Loans can be used in master commitment transactions
