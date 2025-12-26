---
title: Pool Creation and Sharing
description: Learn how to create pools and share them with other organizations
---

# Pool Creation and Sharing

## Overview

This guide covers the complete process of creating pools and sharing them with other organizations. As an issuer, you'll learn how to create pools, add loans, configure sharing options, and share pools with market makers, investors, and other parties to facilitate structured finance transactions.

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
   - **Pool Name**: Provide a unique name to identify the pool (must be unique)
   - **Asset Class**: Select the type of loans (auto loans, personal loans, mortgages, etc.)
   - **Transaction Type**: Choose the transaction type (securitization, whole loan sale, etc.)
   - **Description**: Add a description if needed to provide context
   - **Closing Deal Indicator**: Indicate if this is a closing deal

3. **Assign Organizations**
   - **Market Makers**: Select market makers who will structure the deal
   - **Investors**: Choose investors who will review investment opportunities
   - **Servicers**: Assign servicers if needed for ongoing loan administration
   - **Paying Agents**: Add paying agents if needed for payment distributions
   - **Rating Agencies**: Select rating agencies if needed for analysis
   - **Other Parties**: Add any other parties as required

4. **Review Information**
   - Review all entered information for accuracy
   - Verify organization assignments are correct
   - Ensure pool name is unique
   - Check that all required fields are filled

5. **Create Pool**
   - Click "Create" button or similar
   - Pool is created with "Created" status
   - Pool is visible only to you initially
   - Pool is ready for loan mapping

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

4. **Review Pool Metrics**
   - Pool metrics calculate automatically
   - **Total Balance**: Sum of all mapped loan balances
   - **Loan Count**: Number of loans in the pool
   - **Weighted Average Coupon**: Interest rate weighted by loan balance
   - **Weighted Average FICO**: Credit score weighted by loan balance
   - **Other Metrics**: Geographic distribution, average loan size, etc.
   - Verify metrics are accurate and meet your requirements

5. **Add or Remove Loans**
   - Continue adding loans as needed
   - Remove loans if necessary (they'll be excluded from calculations)
   - Metrics update automatically with each change
   - Review metrics after each change

### Sharing the Pool

1. **Access Sharing Settings**
   - Navigate to pool details
   - Find the Sharing or Organization Assignment section
   - Click to configure sharing

2. **Select Organizations to Share With**
   - Choose which organizations to share with
   - Select from market makers, investors, rating agencies, etc.
   - Can share with multiple organizations simultaneously
   - Review organization list

3. **Set Sharing Permissions**
   - **View Only**: Recipients can view but not provide feedback
   - **Allow Feedback**: Recipients can provide comments and feedback
   - **Allow Change Requests**: Recipients can request changes
   - **Allow Downloads**: Recipients can download pool data
   - Configure appropriate permissions for each organization type

4. **Review Sharing Configuration**
   - Review selected organizations
   - Verify permissions are set correctly
   - Ensure sharing is configured as intended

5. **Complete Sharing**
   - Click "Share" or "Save" button
   - Confirm sharing action
   - Recipients receive notifications
   - Pool becomes visible to shared parties
   - Pool status may change to "Preview"

6. **Verify Sharing**
   - Confirm recipients can see the pool
   - Check that sharing permissions are working
   - Verify notifications were sent
   - Ensure pool is visible to shared parties

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

Understanding pool creation and sharing helps you effectively present your loan portfolios, collaborate with other parties, and move pools through the structured finance workflow to successful deal completion.
