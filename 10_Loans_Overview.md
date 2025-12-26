# Loans Overview

## What are Loans?

**Loans** are individual credit agreements that represent money lent to borrowers. In Intain Markets, loans are the building blocks of pools - you group multiple loans together to create pools for securitization, whole loan sales, or credit facilities.

## Key Concepts

### Loan Data

Each loan contains information about:
- **Borrower details**: Who received the loan
- **Loan terms**: Amount, interest rate, maturity date
- **Collateral**: What secures the loan (if applicable)
- **Performance**: Current status, payments, balance
- **Risk metrics**: FICO score, LTV ratio, DTI/DSCR

### Loans in Pools

- Loans are **mapped** to pools (assigned to a specific pool)
- A loan can belong to one pool at a time
- Loans can be **unmapped** (not assigned to any pool)
- Pool metrics are calculated from the loans in that pool

### Loan Lifecycle

Loans go through various stages:
- **Uploaded**: Loan data is imported into the system
- **Standardized**: Data is processed and standardized
- **Mapped**: Assigned to a pool
- **Submitted**: Included in a batch for verification
- **Verified**: Verified by verification agent or self-certified
- **Minted**: NFT created (if applicable)

---

## Loan Information

### Basic Loan Details

**Identification**
- Loan ID: Unique identifier
- Borrower name
- Loan number

**Financial Terms**
- Original loan amount
- Current principal balance
- Interest rate
- Maturity date
- Payment terms

**Collateral** (if applicable)
- Property type
- Property value
- Collateral description

### Risk Metrics

**Credit Information**
- Borrower FICO score
- Credit history
- Debt-to-income ratio (DTI) or Debt service coverage ratio (DSCR)

**Loan Characteristics**
- Loan-to-value ratio (LTV)
- Loan purpose
- Property type (for mortgages)

**Performance Data**
- Payment history
- Current status
- Delinquency information
- Default status

---

## Loan Statuses

### Mapping Status

**Unmapped**
- Loan is not assigned to any pool
- Can be mapped to a pool
- Can be deleted (if not verified)

**Mapped**
- Loan is assigned to a pool
- Shows which pool it belongs to
- Pool name appears as status

### Workflow Status

**STANDARDISED**
- Loan has been processed and standardized
- Ready for mapping to pools
- Data quality validated

**SUBMITTED**
- Loan is included in a batch
- Submitted for verification
- Waiting for verification process

**VERIFIED**
- Loan has been verified
- Verification source recorded (Self Certified, Certified, or Self Certified (Data Only))
- Ready for further processing

### NFT Status

**Not Minted**
- NFT has not been created yet
- Loan is eligible for NFT minting
- Will be minted when appropriate

**Minted**
- NFT has been created
- Loan is tokenized
- On blockchain

### Pool Status (within pool)

**Normal**
- Loan is active in pool
- Included in pool calculations
- Standard status

**Reconsider**
- Loan needs reconsideration
- May have issues identified
- Under review

**Removed**
- Loan removed from pool
- Not included in pool calculations
- Still visible but excluded

**Reinstated**
- Loan was removed but put back
- Now included in pool again
- Active status restored

---

## Loan Management

### Uploading Loans

**Methods:**
- Upload Excel/CSV files via file upload endpoint
- Import loan tape with field mapping
- System processes and standardizes automatically

**Upload Process:**

**Step 1: Auto-Mapping (Field Mapping)**
- Endpoint: `POST /automapping`
- Request body:
  ```javascript
  {
    asset_class: "<Asset Class>",        // Required: e.g., "Auto Loans", "Commercial Mortgage"
    loantapefields: ["Field1", "Field2", ...],  // Required: Array of field names from uploaded file
    AsOfDate: "<YYYY-MM-DD>",            // Required: As of date for loan data
    filename: "<filename>",               // Required: Name of uploaded file
    approach: "<approach>"                // Required: Mapping approach
  }
  ```
- System process:
  1. Fetches `MasterFields` from MongoDB for the asset class
  2. Filters out Z- fields (internal fields starting with "Z-" or "Z_")
  3. Creates standard fields list (`stdfields`)
  4. Calls AI mapping service: `POST ${config.aiUrl}loantape/map_fields`
  5. AI service returns field mappings with confidence scores
  6. System enriches mappings with:
     - Field types from `MasterFields`
     - Categories from `MasterFields`
     - Summary tags (for principal/interest collections)
     - ESMA compliance flags (ND1-ND4, ND5 allowed)
  7. Returns mapped fields ready for review

**Step 2: Save Mapping and Process Tape**
- Endpoint: `POST /previewsavemapping`
- System process:
  1. Validates mapping data
  2. Processes Excel file with field mappings
  3. Standardizes each loan record:
     - Maps Excel columns to standard fields
     - Calculates "Number Of Days In Arrears" if missing (from Last Payment Date)
     - Calculates "Loan Status" if missing (buckets days in arrears)
     - Sets standard metadata fields:
       - `Asset Class`: From request
       - `Created Date`: Current UTC timestamp
       - `As Of Date`: Converted to UTC date
       - `Loan Data`: "Yes"
       - `workflow_status`: "STANDARDISED"
       - `Status`: "Unmapped" (or "Mapped" if `functiontodo !== "upload"`)
       - `issuerOrgId`, `issuerId`, `jobId`: From request
       - `batchid`: "" (empty initially)
       - `Verificationtemplate`: "" (empty initially)
       - `Contract Data`: "No"
       - `nftLoanStatus`: "Not Minted"
       - `Deployed Address`: "" (empty initially)
       - `verificationSource`: "No"
       - `poolid`: "" (empty if unmapped) or poolId if mapping directly
       - `loanPoolStatus`: "" (empty initially)
    4. Collects unmapped columns into `unmappedcolumns` object
    5. Identifies PII fields from `MasterFields` for encryption
    6. Encrypts PII fields using AES encryption
  7. Inserts loans in batches to MongoDB `previewstdloantape` collection (avoids document size limits)
  8. Updates `fileUploads` collection: `status: "Mapped"` for the `jobId`

**Step 3: Review Standardized Loans**
- View loans via: `GET /getallloans` or filtered endpoints
- Loans have `workflow_status: "STANDARDISED"`
- Loans have `Status: "Unmapped"` (ready for mapping)
- Review field mappings and data quality

**Step 4: Map to Pools**
- Map loans to pools via: `POST /maploanstopool`
- See "Mapping Loans to Pools" section below

### Mapping Loans to Pools

**How to map:**
- Endpoint: `POST /maploanstopool`
- Request body:
  ```javascript
  {
    selectAll: true/false,              // Select all matching loans or specific ones
    selectedLoans: ["Loan1", "Loan2"],  // Array of loan IDs (if selectAll is false)
    filters: [{ "Loan ID": "Loan1" }], // MongoDB filter objects (if selectAll is true)
    poolId: "<poolId>",                 // Required: Target pool ID
    issuerOrgId: "<issuerOrgId>"        // Required: Issuer organization ID
  }
  ```

**Mapping Process:**
1. **Select Loans:**
   - If `selectAll: true`: System builds filter query from `filters` array, finds all matching loans
   - If `selectAll: false`: Uses `selectedLoans` array directly
   
2. **Validation:**
   - System checks loans aren't already mapped to another pool
   - Query: `{ "Loan ID": { $in: loanIds }, poolid: { $exists: true, $nin: [null, "", " "] } }`
   - If any loans already mapped, throws error: "Selected loans already mapped to a different pool"
   
3. **Update Loans:**
   - Updates loans in issuer's MongoDB `previewstdloantape` collection:
     ```javascript
     {
       poolid: poolId,
       Status: "Mapped",
       loanPoolStatus: "Pending"
     }
     ```
   
4. **PostgreSQL Sync:**
   - Pushes loan data to PostgreSQL `poolloantape` table
   - Metadata: `{ loanIds, poolid, module: "pool", issuerOrgDbName }`
   - Loans available for analytics and metric calculations
   
5. **Update Pool Metrics:**
   - Calls `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
   - Recalculates:
     - `numberofloans`: Count of loans with `poolid: poolId`
     - `originalbalance`: Sum of "Original Principal Balance"
     - `currentbalance`: Sum of "Current Principal Balance"
   - Updates `pool_detail` collection

**What happens:**
- Loan `Status` field changes to "Mapped" (or shows pool name in UI)
- Loan `poolid` field set to target pool ID
- Loan `loanPoolStatus` set to "Pending"
- Loan appears in pool's loan list (via `/getpreviewstdloantapeusinglatestdate?poolId=...`)
- Pool metrics recalculate automatically (`numberofloans`, `originalbalance`, `currentbalance`)
- Loan data pushed to PostgreSQL for analytics
- Loan is included in pool calculations (WAC, FICO, LTV, DTI/DSCR)

### Managing Loans in Pools

**View Loans:**
- **Get loans by pool**: `GET /getpreviewstdloantapeusinglatestdate?poolId=...&asOfDate=...&status=...&orgId=...&page=...&pageSize=...`
  - Returns paginated loan list
  - Filters by `poolid`, `loanPoolStatus`, and UI filters
  - Includes unread feedback counts for loans
  - Uses latest `loandataupdatedtill` date from PostgreSQL
  
- **Dynamic filters**: `POST /LoantapeDynamicFilters`
  - Complex MongoDB filters in request body
  - Supports pagination with `lastSeenId`, `page`, `pageSize`
  - Returns filtered and paginated results
  
- **Download loan tape**: `POST /downloadpreviewstdloantape`
  - Exports standardized loan tape as Excel
  - Includes all mapped fields
  - Rounded values for display

**Loan Actions:**

**Update Loan Status:**
- Endpoint: `GET /updateLoanStatus?poolId=...&loanid=...&status=...`
- Status values:
  - **"Unmapped"**: Removes loan from pool
    - Sets `poolid: ""`, `Status: "Unmapped"`, `loanPoolStatus: ""`
    - Recalculates pool metrics
    - Deletes loan from PostgreSQL `poolloantape` table
  - **"Reconsider"**: Marks loan for reconsideration
    - Sets `loanPoolStatus: "Reconsider"`
    - Loan flagged for review
  - **"Reinstated"**: Reinstates removed loan
    - Sets `loanPoolStatus: "Reinstated"`
    - Loan included in pool again
  - **"Removed"**: Removes loan from pool calculations
    - Sets `loanPoolStatus: "Removed"`
    - Recalculates pool metrics (excludes removed loan)
    - Deletes loan from PostgreSQL `poolloantape` table

**Delete Loans:**
- Endpoint: `POST /previewdeleteloans`
- Request body:
  ```javascript
  {
    issuerOrgId: "<issuerOrgId>",  // Required
    loanIds: ["Loan1", "Loan2"],    // Optional: Specific loan IDs
    selectAll: true/false           // Optional: Delete all eligible loans
  }
  ```
- **Deletion Rules:**
  - Only deletes loans with `Status: "Unmapped"` (not mapped to any pool)
  - Only deletes loans with `batchid` empty/null (not in any batch)
  - Cannot delete mapped loans (must unmap first)
  - Cannot delete loans in batches (must remove from batch first)
- **Process:**
  1. Builds query: `{ Status: "Unmapped", $or: [{ batchid: { $in: [null, "", " "] } }, { batchid: { $exists: false } }] }`
  2. If `selectAll: true`: Finds all matching loans
  3. If `selectAll: false`: Uses `loanIds` array
  4. Deletes matching loans from `previewstdloantape` collection
  5. Returns count of deleted loans

---

## Loan Calculations

### Individual Loan Metrics

Each loan has its own:
- Principal balance
- Interest rate
- Payment amount
- Outstanding balance
- Risk metrics

### Pool-Level Aggregates

When loans are in a pool, the system calculates:
- **Total balance**: Sum of all loan balances
- **Weighted Average Coupon (WAC)**: Average interest rate weighted by balance
- **Average FICO**: Average borrower credit score
- **Average LTV**: Average loan-to-value ratio
- **Average DTI/DSCR**: Average debt metrics
- **Loan count**: Number of loans

### Impact of Loan Changes

**When you add loans:**
- Pool balance increases
- Metrics recalculate
- Loan count increases

**When you remove loans:**
- Pool balance decreases
- Metrics recalculate
- Loan count decreases
- Removed loans excluded from calculations

---

## Loan Verification

### Verification Process

**Purpose:**
- Validate loan data accuracy
- Ensure compliance
- Confirm loan eligibility
- Create audit trail

**Methods:**
- **Self Certified**: Issuer certifies the data
- **Certified**: Verification agent verifies
- **Self Certified (Data Only)**: E-signature based certification

### Verification Status

**Before verification:**
- verificationSource: "No"
- Loan not yet verified
- Cannot proceed to certain stages

**After verification:**
- verificationSource: "Self Certified", "Certified", or "Self Certified (Data Only)"
- Loan is verified
- Can proceed to next stages

---

## Best Practices

### Loan Data Quality

1. **Complete information**: Ensure all required fields filled
2. **Accurate data**: Verify loan details are correct
3. **Consistent format**: Follow standardization requirements
4. **Regular updates**: Keep loan data current

### Loan Mapping

1. **Map early**: Map loans to pools as soon as possible
2. **Review metrics**: Check pool metrics after mapping
3. **Verify completeness**: Ensure all intended loans mapped
4. **Monitor status**: Track loan statuses

### Loan Management

1. **Regular review**: Check loans periodically
2. **Address issues**: Handle reconsideration requests
3. **Update status**: Keep loan statuses current
4. **Track changes**: Monitor loan modifications

---

## Common Questions

**Can a loan be in multiple pools?**
- No, a loan belongs to one pool at a time
- Must be unmapped from one pool before mapping to another

**What happens when I remove a loan from a pool?**
- Loan status changes to "Removed"
- Loan excluded from pool calculations
- Pool metrics recalculate
- Loan can be reinstated later

**Can I edit loan information?**
- Depends on loan status and permissions
- Some statuses allow editing
- Verified loans may have restrictions

**How do I know if loan data is accurate?**
- Review standardized data
- Check validation messages
- Verify against source documents
- Use verification process

Understanding loans helps you effectively manage your loan portfolios and create successful pools for structured finance transactions.
