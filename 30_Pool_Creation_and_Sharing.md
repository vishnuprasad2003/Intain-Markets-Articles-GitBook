---
title: Pool Creation and Sharing
description: Learn how to create pools and share them with other organizations
---

# Pool Creation and Sharing

## Overview

This guide covers the complete process of creating pools and sharing them with other organizations. As an issuer, you'll learn how to create pools, add loans, configure sharing options, and share pools with market makers, investors, and other parties.

## Who Can Use This

- Issuers who create and manage pools for securitization or whole loan sales

## When This Is Used

Use pool creation and sharing when:
- You want to create a new pool to group loans together
- You need to present loans to potential investors or market makers
- You want to organize loans for a structured finance transaction
- You need to share pools with other parties for review or structuring
- You want to collaborate with market makers, investors, or rating agencies

## Step-by-Step Process

### Creating a Pool

1. **Access Pool Creation**
   - Navigate to the Pools section
   - Click "Create New Pool" or similar button
   - Pool creation form opens

2. **Enter Basic Information**
   - **poolName**: Provide a unique name to identify the pool (string, must be unique - validated against existing poolName)
   - **assetClass**: Select the type of loans (string, e.g., "auto loans", "personal loans", "mortgages", etc.)
   - **transactionType**: Choose the transaction type (string, e.g., "securitization", "whole loan sale", etc.)
   - **description**: Add a description if needed to provide context (string, optional)
   - **Isclosingdeal**: Indicate if this is a closing deal (string, "Yes" or "No")

3. **Assign Organizations**
   - **marketMakerOrgId**: Select market maker organization IDs (array of strings) who will structure the deal
   - **investorOrgId**: Choose investor organization IDs (array of strings) who will review investment opportunities
   - **servicerOrgId**: Assign servicer organization IDs (array of strings) if needed for ongoing loan administration
   - **payingAgentOrgId**: Add paying agent organization IDs (array of strings) if needed for payment distributions
   - **ratingAgencyOrgId**: Select rating agency organization IDs (array of strings) if needed for analysis
   - **verificationAgentOrgId**: Add verification agent organization IDs (array of strings) if needed
   - Organizations are stored as arrays of organization IDs

4. **Review Information**
   - Review all entered information for accuracy
   - Verify organization assignments are correct
   - Ensure pool name is unique
   - Check that all required fields are filled

5. **Create Pool**
   - Click "Create" button or similar
   - System calls API: POST /pools/createPool
   - System generates unique poolId using format based on poolName, issuerOrgName, assetClass, date, and count
   - Pool is created with status: "Created"
   - Initial metrics set: numberofloans: 0, originalbalance: 0, currentbalance: 0
   - shareOptions initialized as empty object {}
   - poolShareOptions initialized as empty object {}
   - Pool is visible only to you initially
   - Pool is ready for loan mapping

![Pool Creation - Issuer](imagesByMdFilesFolder/30/PoolCreation_Issuer.png)

### Adding Loans to Pool

1. **Navigate to Pool Details**
   - Open the pool you created
   - Go to the Loans section or Loan Mapping area
   - View available loans for mapping

2. **Select Loans to Map**
   - Browse or search for loans to include
   - Select individual loans or use bulk selection
   - Can select multiple loans at once
   - Verify loans are not already mapped to another pool

3. **Map Loans to Pool**
   - Confirm loan selection
   - Click "Map to Pool" or similar button
   - Loans are assigned to the pool
   - Loan status changes to "Mapped"

![Loan Map to Pool - Issuer](imagesByMdFilesFolder/30/LoanMapToPoolIssuer.png)

4. **Review Pool Metrics**
   - Pool metrics calculate automatically from mapped loans via CalculateNoofLoansAndBalanceRefactored function
   - Metrics stored in pool_detail collection:
     - **numberofloans**: Total count of mapped loans (calculated from previewstdloantape collection where poolid matches)
     - **originalbalance**: Sum of "Original Principal Balance" from all mapped loans (converted to numeric, summed)
     - **currentbalance**: Sum of "Current Principal Balance" from all mapped loans (converted to numeric, summed)
   - Additional metrics from PostgreSQL (via getBdbTiles function):
     - **current_principal_balance**: Sum of current principal balances
     - **wac**: Weighted Average Coupon (Current Interest Rate weighted by Current Principal Balance)
     - **fico**: Weighted Average FICO (Borrower FICO weighted by Current Principal Balance)
     - **ltv**: Weighted Average LTV (Current Loan-To-Value weighted by Current Principal Balance)
     - **dscr/dti**: Debt service coverage ratio (if assetClass is "Commercial Mortgage") or Debt-to-income ratio (other asset classes), weighted by Current Principal Balance
     - **loan_cnt**: Count of loans with Current Principal Balance > 0
     - **beginning_loan_balance**: Sum of "Beginning Loan Balance"
   - Metrics update automatically when loans are added or removed

![Pool Details - Issuer](imagesByMdFilesFolder/30/Pool_Details_Issuer.png)

5. **Add or Remove Loans**
   - Continue adding loans as needed
   - Remove loans if necessary (they'll be excluded from calculations)
   - Metrics update automatically with each change
   - Review metrics after each change

### Sharing the Pool

1. **Access Sharing Settings**
   - Navigate to pool details page
   - Click the **Share** button at the top right
   - A pop-up window appears for sharing configuration

![Pool Share - Issuer](imagesByMdFilesFolder/30/Pool_Share_Issuer.png)

2. **Select Recipient Organizations**
   - In the pop-up, select the recipient organization type
   - Based on the selected recipient type, the system displays organizations that were added to this pool during creation or editing (from marketMakerOrgId, investorOrgId, etc. arrays)
   - Choose which organizations to share with from the available options
   - Can share with multiple organizations simultaneously
   - System calls API: POST /configureShareOptions

![Pool Share - Select Recipient Organization](imagesByMdFilesFolder/30/Pool_Share_Select_recipient_org.png)

3. **Set Sharing Permissions**
   - System configures shareOptions object for selected organizations
   - Each organization in shareOptions has:
     - **allowFeedBack**: Boolean (defaults to true) - Recipients can provide comments and feedback
     - **allowDownload**: Boolean (defaults to true) - Recipients can download pool data
     - **acceptanceStatus**: String (defaults to 'pending') - Status for market maker mandates
   - Permissions are set automatically with defaults, can be edited later

![Pools Sharing Settings](imagesByMdFilesFolder/30/Pools_Sharing_Settings.png)

4. **Complete Sharing**
   - Click "Share" or "Save" button
   - System updates shareOptions object in pool_detail collection
   - Recipients receive notifications
   - Pool becomes visible to shared parties
   - Pool status may change to "Preview" if it was in "Created" status

![Pool Sharing - Issuer](imagesByMdFilesFolder/30/PoolSharing_Issuer.png)

5. **Manage Shared Organizations**
   - Navigate to pool details page
   - Below the main table, find the **Sharing** tab
   - View all shared organizations and their access settings in shareOptions object
   - As the issuer, you can edit accessibility settings for each shared organization
   - Modify allowFeedBack and allowDownload permissions as needed
   - System updates shareOptions object with modified permissions

## Rules & Validations

- Pool names must be unique - you cannot create two pools with the same name.

- Loans can only belong to one pool at a time - you must unmap a loan from one pool before mapping it to another.

- You can share pools with multiple organizations simultaneously - sharing doesn't need to be done one at a time.

- Sharing permissions control what recipients can do - set appropriate permissions based on what you want recipients to be able to do.

- Pool metrics calculate automatically from mapped loans - you don't need to calculate them manually, and they update when loans are added or removed.

- You can edit pools while they're in Created or Preview status - once a pool becomes a Deal, editing is restricted.

- Removed loans are excluded from pool calculations - if you remove loans, metrics update automatically.

- Pool status affects sharing capabilities - some statuses may restrict sharing or require certain statuses before sharing.

- Sharing is recorded in audit trail - all sharing actions are tracked with who shared what with whom and when.

- Recipients must have appropriate roles - market makers can accept mandates, investors can review opportunities, etc.

## What Happens Next

After creating and sharing a pool:
- Recipients can view and analyze the pool in their views
- Market makers can review and accept mandates to structure deals
- Investors can review opportunities and express interest
- Rating agencies can analyze pool characteristics for rating purposes
- You receive feedback and can respond accordingly
- Pool may progress through statuses based on recipient actions
- Pool moves toward final deal completion

After sharing with market makers:
- Market makers can accept mandates to structure the deal
- Pool may move to "Mandate Pending" status
- Market maker structures the deal
- Pool progresses toward "Deal" status

Understanding pool creation and sharing helps you effectively present your loan portfolios, collaborate with other parties, and move pools through the structured finance workflow.
