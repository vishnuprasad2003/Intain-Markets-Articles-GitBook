# Loan Lifecycle & Statuses

## Overview

Loans progress through various statuses as they move through the platform workflow. Understanding these statuses helps you track where each loan is in the process and know what actions are available.

## Loan Status Fields

Loans have multiple status fields that track different aspects:

1. **Status** (Mapping status)
2. **workflow_status** (Workflow stage)
3. **verificationSource** (Verification method)
4. **nftLoanStatus** (NFT minting status)
5. **loanPoolStatus** (Status within pool)

---

## Status Field: Mapping Status

### Unmapped

**What it means:**
- Loan is not assigned to any pool
- Loan exists in system but not in a pool
- Available for mapping

**When it's set:**
- When loan is first uploaded
- When loan is unmapped from a pool
- Initial state for new loans

**What you can do:**
- Map loan to a pool
- Edit loan information (if allowed)
- Delete loan (if not verified)
- View loan details

**Next steps:**
- Map to a pool to include in transactions

---

### Mapped

**What it means:**
- Loan is assigned to a pool
- Loan belongs to a specific pool
- Included in pool calculations

**When it's set:**
- When loan is mapped to a pool
- Automatically when mapping occurs

**What you can do:**
- View loan in pool
- Remove from pool (if status allows)
- Update loan information (if allowed)
- View pool metrics including this loan

**Next steps:**
- Loan progresses with pool workflow

---

### Pool Name (Dynamic Status)

**What it means:**
- Loan is assigned to a specific pool
- Status field shows the pool name
- Indicates which pool the loan belongs to

**When it's set:**
- When loan is mapped to a pool
- Status field is replaced with pool name

**What you can do:**
- See which pool loan belongs to
- Manage loan within pool context
- Track loan with pool

---

## workflow_status Field: Workflow Stage

### STANDARDISED

**What it means:**
- Loan has been processed and standardized
- Data quality validated
- Ready for further processing

**When it's set:**
- After loan upload and standardization
- When loan data is processed
- Initial workflow status

**What happens:**
- Loan data is cleaned and standardized
- Validation checks performed
- Ready for mapping

**Next steps:**
- Map to pool
- Submit for verification

---

### SUBMITTED

**What it means:**
- Loan is included in a batch
- Submitted for verification
- Waiting for verification process

**When it's set:**
- When batch is created with this loan
- Loan is submitted for verification
- Part of verification workflow

**What happens:**
- Loan is grouped with other loans
- Batch created for verification
- Verification process begins

**Next steps:**
- Verification agent reviews
- Or self-certification process
- Loan becomes verified

---

### VERIFIED

**What it means:**
- Loan has been verified
- Verification process completed
- Loan is validated

**When it's set:**
- After verification agent approval
- After self-certification completion
- After e-signature certification

**What happens:**
- Verification source recorded
- Loan can proceed to next stages
- Audit trail created

**Next steps:**
- Can be included in deals
- Can be minted as NFT (if applicable)
- Ready for transaction completion

---

## verificationSource Field: Verification Method

### No

**What it means:**
- No verification has been performed
- Loan not yet verified
- Initial state

**When it's set:**
- When loan is first created
- Before verification process
- Default state

**Next steps:**
- Submit for verification
- Complete verification process

---

### Self Certified

**What it means:**
- Loan verified by issuer
- Issuer self-certified the data
- Issuer takes responsibility

**When it's set:**
- When issuer self-certifies batch
- Issuer confirms data accuracy
- Self-certification workflow

**What it means for you:**
- You've certified the loan data
- You're responsible for accuracy
- Loan is verified

---

### Certified

**What it means:**
- Loan verified by Verification Agent (VA)
- Independent verification completed
- VA confirmed data accuracy

**When it's set:**
- When VA verifies the batch
- VA completes verification
- Independent verification workflow

**What it means for you:**
- Third party verified the data
- Independent validation
- Higher confidence level

---

### Self Certified (Data Only)

**What it means:**
- Self-certified via e-signature
- DocuSign or ZohoSign completion
- E-signature based certification

**When it's set:**
- When e-signature process completes
- After DocuSign/ZohoSign signing
- E-signature certification workflow

**What it means for you:**
- Certified through e-signature
- Digital certification
- Audit trail includes signature

---

## nftLoanStatus Field: NFT Minting Status

### Not Minted

**What it means:**
- NFT has not been created yet
- Loan is eligible for NFT minting
- Will be minted when appropriate

**When it's set:**
- Initial state for all loans
- Before NFT creation
- Default status

**What happens:**
- Loan is tracked for minting eligibility
- Can be selected for minting
- Ready for tokenization

**Next steps:**
- NFT minting process
- Token creation
- Blockchain recording

---

### Minted (Other Values)

**What it means:**
- NFT has been created
- Loan is tokenized
- On blockchain

**When it's set:**
- After NFT minting process
- When token is created
- Blockchain recording complete

**What happens:**
- Loan is represented as NFT
- Blockchain record created
- Tokenized asset

---

## loanPoolStatus Field: Status Within Pool

The `loanPoolStatus` field tracks a loan's status within a specific pool. This is separate from the `Status` field (which tracks mapping) and `workflow_status` (which tracks verification workflow).

### "" (Empty String - Normal)

**What it means:**
- Loan is active in pool
- Standard status
- Included in pool calculations
- Default state when loan is first mapped to pool

**When it's set:**
- Default status when loan is mapped to pool (via `/maploanstopool`)
- Initial state: `loanPoolStatus: ""` (empty string)
- Normal active state

**Database Field:**
- `loanPoolStatus: ""` (empty string, not null)

**What you can do:**
- Loan included in all pool calculations
- Loan counted in `numberofloans`
- Loan balance included in `originalbalance` and `currentbalance`
- Loan included in weighted averages (WAC, FICO, LTV, DTI/DSCR)
- Normal pool operations
- Standard workflow

**Calculation Impact:**
- Loan is included in all PostgreSQL `poolloantape` queries
- Loan balance contributes to pool metrics
- Loan appears in normal loan lists (not filtered out)

---

### Reconsider

**What it means:**
- Loan needs reconsideration
- Market maker or investor flagged the loan for review
- Issuer should review and decide

**When it's set:**
- Endpoint: `GET /updateLoanStatus?poolId=...&loanid=...&status=Reconsider`
- When market maker or investor requests reconsideration
- Manual status change by issuer (responding to feedback)

**Database Update:**
- Updates loan: `{ "Loan ID": loanid, "poolid": poolId }`
- Sets: `loanPoolStatus: "Reconsider"`
- Other fields remain unchanged

**What happens:**
- Loan flagged for attention
- Loan may be excluded from some calculations (depends on filter)
- Review process begins
- Issuer can see loan needs attention

**Next steps:**
- Review loan details
- Address identified issues
- Change status:
  - Back to normal: Set `loanPoolStatus: ""` (empty string)
  - Remove: Set `loanPoolStatus: "Removed"`
  - Reinstated: Set `loanPoolStatus: "Reinstated"` (if was removed)

---

### Removed

**What it means:**
- Loan removed from pool calculations
- Not included in pool metrics
- Still visible in pool but excluded from calculations
- Loan stays in pool (not unmapped)

**When it's set:**
- Endpoint: `GET /updateLoanStatus?poolId=...&loanid=...&status=Removed`
- When issuer accepts reconsideration suggestion
- When issuer manually removes loan from pool

**Database Update:**
- Updates loan: `{ "Loan ID": loanid, "poolid": poolId }`
- Sets: `loanPoolStatus: "Removed"`
- Other fields remain unchanged (loan still has `poolid` set)

**What happens:**
- **Pool Metrics Recalculate:**
  - Calls `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
  - Recalculates `numberofloans`, `originalbalance`, `currentbalance` excluding removed loan
  - Updates `pool_detail` collection
  
- **PostgreSQL Cleanup:**
  - Calls `deleteLoansFromPoolInPostgres(poolId, [loanid])`
  - Deletes loan from PostgreSQL `poolloantape` table
  - Loan no longer included in analytics queries
  
- **Loan Visibility:**
  - Loan still visible in MongoDB `previewstdloantape` collection
  - Loan still has `poolid` field set (not unmapped)
  - Can be filtered by `loanPoolStatus: "Removed"`

**Next steps:**
- Can be reinstated: Set `loanPoolStatus: ""` (empty string) or `"Reinstated"`
- Or left removed: Loan stays excluded from calculations
- Or unmapped: Set `Status: "Unmapped"` and `poolid: ""` (different action)

---

### Reinstated

**What it means:**
- Loan was removed but put back into pool calculations
- Now included in pool again
- Active status restored

**When it's set:**
- Endpoint: `GET /updateLoanStatus?poolId=...&loanid=...&status=Reinstated`
- When issuer rejects reconsideration suggestion
- When issuer manually reinstates removed loan

**Database Update:**
- Updates loan: `{ "Loan ID": loanid, "poolid": poolId }`
- Sets: `loanPoolStatus: "Reinstated"`
- Other fields remain unchanged

**What happens:**
- Loan included in calculations again
- Pool metrics should recalculate (may need manual trigger)
- Loan should be pushed back to PostgreSQL (may need manual action)
- Active status restored

**Note:**
- Reinstatement sets `loanPoolStatus: "Reinstated"` (not empty string)
- Some systems may treat "Reinstated" as active, others may require setting to "" (empty)
- Check system behavior for your use case

---

### Unmapped (Status Change, Not loanPoolStatus)

**What it means:**
- Loan is completely removed from pool
- Loan is no longer associated with the pool
- Different from "Removed" (which keeps loan in pool but excludes from calculations)

**When it's set:**
- Endpoint: `GET /updateLoanStatus?poolId=...&loanid=...&status=Unmapped`
- When issuer unmaps loan from pool

**Database Update:**
- Updates loan: `{ "Loan ID": loanid, "poolid": poolId }`
- Sets:
  - `poolid: ""` (clears pool association)
  - `Status: "Unmapped"` (changes mapping status)
  - `loanPoolStatus: ""` (clears pool status)

**What happens:**
- **Pool Metrics Recalculate:**
  - Calls `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
  - Recalculates pool metrics excluding unmapped loan
  
- **PostgreSQL Cleanup:**
  - Calls `deleteLoansFromPoolInPostgres(poolId, [loanid])`
  - Deletes loan from PostgreSQL `poolloantape` table
  
- **Loan Status:**
  - Loan becomes available for mapping to other pools
  - Loan `Status` changes to "Unmapped"
  - Loan can be mapped to different pool

#### Difference from "Removed"
- Unmapped: Loan completely removed from pool, can be mapped elsewhere
- Removed: Loan stays in pool (`poolid` still set), excluded from calculations, can be reinstated

---

## Complete Loan Lifecycle Flow

### Typical Flow

```
1. Upload → Status: "Unmapped", workflow_status: "STANDARDISED", verificationSource: "No", nftLoanStatus: "Not Minted"
   ↓
2. Map to Pool → Status: "Mapped" or <Pool Name>
   ↓
3. Create Batch → workflow_status: "SUBMITTED"
   ↓
4. Verify → workflow_status: "VERIFIED", verificationSource: "Self Certified" | "Certified" | "Self Certified (Data Only)"
   ↓
5. Mint NFT (if applicable) → nftLoanStatus: <Minted>
   ↓
6. Deal Completion → Loan in finalized deal
```

### Status Transitions

**Mapping:**
- Unmapped → Mapped (when mapped to pool)
- Mapped → Unmapped (when removed from pool)

**Workflow:**
- STANDARDISED → SUBMITTED (when included in batch)
- SUBMITTED → VERIFIED (after verification)

**Verification:**
- No → Self Certified/Certified/Self Certified (Data Only) (after verification)

**NFT:**
- Not Minted → Minted (after NFT creation)

**Pool Status:**
- "" → Reconsider (when flagged)
- "" → Removed (when removed)
- Removed → Reinstated (when put back)

---

## Understanding Status Combinations

### Common Combinations

**New Loan:**
- Status: "Unmapped"
- workflow_status: "STANDARDISED"
- verificationSource: "No"
- nftLoanStatus: "Not Minted"
- loanPoolStatus: ""

**Active Pool Loan:**
- Status: <Pool Name>
- workflow_status: "VERIFIED"
- verificationSource: "Self Certified" or "Certified"
- nftLoanStatus: "Not Minted" or "Minted"
- loanPoolStatus: "" (normal)

**Removed Loan:**
- Status: <Pool Name> or "Unmapped"
- workflow_status: "VERIFIED"
- verificationSource: <any>
- nftLoanStatus: <any>
- loanPoolStatus: "Removed"

---

## Best Practices

1. **Track statuses**: Monitor all status fields
2. **Understand transitions**: Know what causes status changes
3. **Verify before proceeding**: Ensure verification complete
4. **Manage pool status**: Handle reconsideration and removal appropriately
5. **Monitor workflow**: Track loan through entire lifecycle

Understanding loan lifecycle and statuses helps you effectively manage loans and track their progress through the platform workflow.
