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
   - **Pool Name**: Provide a unique name to identify the pool
   - **Asset Class**: Select the type of loans (e.g., auto loans, personal loans, mortgages, etc.)
   - **Transaction Type**: Choose the transaction type (e.g., securitization, whole loan sale, etc.)
   - **Description**: Add a description if needed to provide context
   - **Closing Deal**: Indicate if this is a closing deal (Yes or No)

3. **Assign Organizations**
   - **Market Makers**: Select market maker organizations who will structure the deal
   - **Investors**: Choose investor organizations who will review investment opportunities
   - **Servicers**: Assign servicer organizations if needed for ongoing loan administration
   - **Paying Agents**: Add paying agent organizations if needed for payment distributions
   - **Rating Agencies**: Select rating agency organizations if needed for analysis
   - **Verification Agents**: Add verification agent organizations if needed

4. **Review Information**
   - Review all entered information for accuracy
   - Verify organization assignments are correct
   - Ensure pool name is unique
   - Check that all required fields are filled

5. **Create Pool**
   - Click "Create" button or similar
   - Pool is created with a unique identifier
   - Pool status is set to "Created"
   - Initial metrics are set to zero (no loans mapped yet)
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
   - Pool metrics calculate automatically from mapped loans
   - **Number of Loans**: Total count of mapped loans
   - **Original Balance**: Sum of original principal balances from all mapped loans
   - **Current Balance**: Sum of current principal balances from all mapped loans
   - **Weighted Average Coupon (WAC)**: Average interest rate weighted by current principal balance
   - **Weighted Average FICO**: Average borrower credit score weighted by current principal balance
   - **Weighted Average LTV**: Average loan-to-value ratio weighted by current principal balance
   - **DSCR/DTI**: Debt service coverage ratio (for commercial mortgages) or debt-to-income ratio (other asset classes), weighted by current principal balance
   - **Loan Count**: Count of active loans
   - **Beginning Loan Balance**: Sum of beginning loan balances
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
   - Based on the selected recipient type, the system displays organizations that were added to this pool during creation or editing
   - Choose which organizations to share with from the available options
   - Can share with multiple organizations simultaneously

![Pool Share - Select Recipient Organization](imagesByMdFilesFolder/30/Pool_Share_Select_recipient_org.png)

3. **Set Sharing Permissions**
   - Configure permissions for selected organizations:
     - **Allow Feedback**: Recipients can provide comments and feedback (defaults to enabled)
     - **Allow Download**: Recipients can download pool data (defaults to enabled)
     - **Acceptance Status**: Status for market maker mandates (defaults to pending)
   - Permissions are set automatically with defaults, can be edited later

![Pools Sharing Settings](imagesByMdFilesFolder/30/Pools_Sharing_Settings.png)

4. **Complete Sharing**
   - Click "Share" or "Save" button
   - Sharing permissions are saved
   - Recipients receive notifications
   - Pool becomes visible to shared parties
   - Pool status may change to "Preview" if it was in "Created" status

![Pool Sharing - Issuer](imagesByMdFilesFolder/30/PoolSharing_Issuer.png)

5. **Manage Shared Organizations**
   - Navigate to pool details page
   - Below the main table, find the **Sharing** tab
   - View all shared organizations and their access settings
   - As the issuer, you can edit accessibility settings for each shared organization
   - Modify feedback and download permissions as needed
   - Changes are saved automatically

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
