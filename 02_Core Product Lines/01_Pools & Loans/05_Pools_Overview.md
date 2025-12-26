# Pools Overview

## What is a Pool?

A pool is a collection of loans grouped together for the purpose of securitization, whole loan sales, or other structured finance transactions. Think of it as a container that holds multiple loans, making it easier to manage, analyze, and present them to potential investors or lenders.

## Key Concepts

### Pool vs. Deal

#### Pool (Preview)
- A pool in "preview" status is a collection of loans being prepared
- It's shared with potential market makers and investors for review
- It's not yet finalized or committed
- You can add, remove, or modify loans during this stage

#### Deal
- A deal is a finalized pool that has been approved and structured
- It represents a committed transaction
- Loans are locked in and cannot be easily changed
- It's ready for execution and funding

### Why Create a Pool?

Pools help you:
- Organize loans: Group related loans together
- Present to investors: Show a cohesive package of assets
- Calculate metrics: See aggregate statistics (total balance, average interest rate, etc.)
- Manage workflow: Track the entire process from creation to deal completion
- Share efficiently: Share one pool instead of many individual loans

## Pool Components

### Basic Information

When you create a pool, you provide:
- Pool Name: A unique identifier for your pool (alphanumeric, minimum 2 characters). This is used along with issuer organization name, asset class, and date to generate a unique Pool ID automatically.
- Asset Class: The type of loans (e.g., Auto Loans, Commercial Mortgage, Personal Loans). This determines which standard fields are available and affects metric calculations (e.g., Commercial Mortgage uses DSCR, others use DTI).
- Transaction Type: The type of transaction (Whole Loan, Securitization, Credit Facility, Participation Agreement) - alphanumeric field
- Description: Additional details about the pool (optional text field)
- Closing Deal: Whether this is a closing deal or not ("Yes" or "No")

### Pool ID Generation

The system automatically generates a unique Pool ID when you create a pool. The format is:
- Format: `[First 2 chars of Pool Name][First char of Issuer Org Name][First char of Asset Class][Last 2 digits of Year][3-digit sequence number]`
- Example: If pool name is "AutoPool", issuer org is "ABC Bank", asset class is "Auto Loans", and year is 2024, the Pool ID might be "AUA24A001"
- Uniqueness: The system ensures Pool ID and Pool Name are unique - if either already exists, creation will fail with an error message

### Associated Organizations

You can assign various parties to your pool:
- Market Makers: Organizations that will structure and market the pool
- Investors: Organizations that may invest in the pool
- Servicers: Organizations that will service the loans
- Paying Agents: Organizations that handle payments
- Rating Agencies: Organizations that will rate the pool
- Verification Agents: Organizations that verify loan data

### Loans in the Pool

- Number of Loans: Total count of loans mapped to the pool
- Original Balance: Total original principal amount
- Current Balance: Current outstanding principal amount
- Loan Details: Individual loan information and metrics

## Pool Metrics

The platform automatically calculates key metrics for your pool. These calculations happen in real-time and update whenever loans are added, removed, or updated.

### Aggregate Statistics

#### Total Principal Balance
- Current Balance: Sum of all active loans' "Current Principal Balance" (excludes removed loans)
- Original Balance: Sum of all active loans' "Original Principal Balance" (excludes removed loans)
- Updates automatically when loans are mapped, removed, or reinstated

#### Weighted Average Coupon (WAC)
- Formula: `Sum(Current Principal Balance × Current Interest Rate) / Sum(Current Principal Balance) × 100`
- Only includes active loans (removed loans excluded)
- Returns "NA" if no loans or all balances are zero
- Calculated from PostgreSQL `poolloantape` table using the latest `loandataupdatedtill` date

#### Average FICO Score
- Formula: `Sum(Current Principal Balance × Borrower FICO) / Sum(Current Principal Balance)`
- Weighted by loan balance (larger loans have more influence)
- Rounded to 2 decimal places, then floored to integer
- Returns "NA" if no loans or all balances are zero

#### Average Loan-to-Value (LTV)
- Formula: `Sum(Current Principal Balance × Current Loan-To-Value) / Sum(Current Principal Balance) × 100`
- Weighted average percentage
- Returns "NA" if no loans or all balances are zero

#### Average DTI/DSCR
- For Commercial Mortgage: Uses "Current Debt Service Coverage Ratio" (DSCR)
- For Other Asset Classes: Uses "Debt To Income Ratio" (DTI)
- Formula: `Sum(Current Principal Balance × DTI/DSCR) / Sum(Current Principal Balance) × 100`
- Returns "NA" if no loans or all balances are zero

### Loan Counts
- Total Loans: Number of active loans in the pool (loans with `poolid` matching the pool ID)
- Active Loans: Loans with positive "Current Principal Balance" (> 0)
- Status Breakdown: Counts by `workflow_status` (STANDARDISED, SUBMITTED, VERIFIED)
- NFT Completion: Percentage of loans with "Deployed Address" populated (NFT minted)

### How Metrics Update

#### Automatic Updates
- When you map loans to a pool → Metrics recalculate immediately
- When you remove loans from a pool → Metrics recalculate excluding removed loans
- When you reinstate removed loans → Metrics recalculate including reinstated loans
- When loan data is updated → Metrics recalculate on next view (uses latest `loandataupdatedtill` date)

#### Data Source
- Pool-level counts and balances come from MongoDB `previewstdloantape` collection
- Detailed metrics (WAC, FICO, LTV, DTI/DSCR) come from PostgreSQL `poolloantape` table
- Metrics use the most recent loan data (`loandataupdatedtill` = maximum date for that pool)

## Pool Lifecycle Overview

1. **Created**: Pool is created with basic information
2. **Preview**: Pool is shared with market makers and investors
3. **Mandate Pending**: Waiting for market maker acceptance
4. **Deal**: Pool is finalized and structured

(For detailed status information, see "Pool Lifecycle & Statuses")

## What You Can Do with a Pool

### As an Issuer

#### Pool Creation
- Create pools: Start new pools by providing pool name, asset class, transaction type, description, and closing deal flag
- Automatic Pool ID: System generates unique Pool ID automatically (format: [PoolPrefix][IssuerOrgInitial][AssetInitial][Year][Sequence])
- Initial State: Pool starts with status "Created", 0 loans, 0 balance, empty shareOptions and poolShareOptions

#### Loan Management
- Map loans: Select loans (by filters or individually) and map them to pools
- Validation: System checks loans aren't already mapped to another pool before mapping
- Automatic Updates: When loans are mapped, pool's `numberofloans`, `originalbalance`, and `currentbalance` update automatically
- PostgreSQL Sync: Mapped loans are pushed to PostgreSQL `poolloantape` table for analytics

#### Pool Updates
- Update details: Modify pool description, organization assignments (market makers, investors, servicers, etc.)
- Share Options: Configure which organizations can view, provide feedback, or download pool data
- Status Restrictions: Can only edit when pool is in "Created" or "Preview" status

#### Sharing
- Share previews: Share pools with market makers, investors, rating agencies, etc.
- Configure permissions: Set `allowFeedBack` and `allowDownload` for each shared organization
- Track views: See which organizations have viewed your pool

#### Viewing and Analytics
- View metrics: See real-time aggregate statistics calculated from active loans
- Download reports: Export pool data and standardized loan tapes
- Track status: Monitor pool status (Created → Preview → Mandate Pending → Deal)
- View feedback: See comments and change requests from shared parties

### As a Market Maker

- Review pools: See pools shared with you
- Accept mandates: Accept pool mandates to structure deals
- Analyze metrics: Review pool statistics and loan characteristics
- Request changes: Provide feedback on pools

### As an Investor

- View previews: See pools shared with you
- Analyze opportunities: Review pool metrics and loan details
- Evaluate risk: Assess pool characteristics before investing

## Pool Sharing

### Sharing Options

When you share a pool, you can:
- Choose recipients: Select which organizations to share with
- Set permissions: Control what recipients can see and do
- Track views: See who has viewed your pool
- Receive feedback: Get comments and change requests

### Preview Sharing

- Pools in "Preview" status can be shared with multiple parties
- Recipients can view but not modify (unless you grant permissions)
- Sharing doesn't change the pool status
- You can share with market makers, investors, rating agencies, etc.

## Pool Status and Visibility

### Status Determines Visibility

- Created: Only visible to issuer
- Preview: Visible to issuer and shared parties
- Mandate Pending: Visible to issuer and assigned market maker
- Deal: Visible to all relevant parties

### Status Determines Actions

- Created/Preview: You can edit, add loans, share
- Mandate Pending: Limited editing, waiting for market maker
- Deal: Read-only, finalized

## Best Practices

1. **Name clearly**: Use descriptive pool names
2. **Complete information**: Fill in all relevant details
3. **Map loans early**: Add loans as soon as possible to see metrics
4. **Review metrics**: Check aggregate statistics before sharing
5. **Share strategically**: Share with relevant parties at the right time
6. **Respond to feedback**: Address change requests promptly
7. **Track progress**: Monitor status changes and notifications

## Common Questions

#### Can I add loans after sharing?
- Yes, you can add loans to pools in Preview status
- Recipients will see updated metrics

#### Can I remove loans from a pool?
- Yes, before the pool becomes a Deal
- Removing loans updates all metrics automatically

#### What if I make a mistake?
- You can edit pool information while in Created/Preview status
- If shared, recipients will see updates

#### How do I know if my pool is ready to share?
- Check that all required information is filled
- Review the metrics to ensure they're accurate
- Verify loans are properly mapped

Pools are the foundation of structured finance transactions on Intain Markets. Understanding how they work helps you effectively present your loan portfolios to potential investors and complete successful transactions.
