# All Loan States Explained

## Overview

This comprehensive guide explains all possible loan statuses and states across different status fields. Loans have multiple status fields that track different aspects of their lifecycle.

## Loan Status Fields

**Database Collection:** `previewstdloantape` (MongoDB) - organization-specific database

Loans have five main status fields:
1. **Status** (Mapping status) - Field name: `Status` (string)
2. **workflow_status** (Workflow stage) - Field name: `workflow_status` (string)
3. **verificationSource** (Verification method) - Field name: `verificationSource` (string)
4. **nftLoanStatus** (NFT minting status) - Field name: `nftLoanStatus` (string)
5. **loanPoolStatus** (Status within pool) - Field name: `loanPoolStatus` (string)

---

## Status Field: Mapping Status

### Unmapped

**What it means:**
- Loan is not assigned to any pool: `Status: 'Unmapped'` in `previewstdloantape` collection
- Loan exists in system but not in a pool: loan document exists in organization's database
- Available for mapping: can be mapped to pool via `POST /maploanstopool`
- Database field: `Status: 'Unmapped'` (exact string value)
- Database field: `loanPoolStatus: ''` (empty string, normal state)

**When it's set:**
- When loan is first uploaded
- When loan is unmapped from a pool
- Initial state for new loans

**What you can do:**
- Map loan to a pool
- Edit loan information (if allowed)
- Delete loan (if not verified)
- View loan details

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

---

### Pool Name (Dynamic Status)

**What it means:**
- Loan is assigned to a specific pool
- Status field shows the pool name
- Indicates which pool the loan belongs to

**When it's set:**
- When loan is mapped to a pool
- Status field is replaced with pool name

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

**Next status:**
- SUBMITTED (when included in batch)

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

**Next status:**
- VERIFIED (after verification)

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

**This is final:**
- Verification is complete
- Loan can proceed to next stages

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

**Next status:**
- Minted (when NFT created)

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

---

## loanPoolStatus Field: Status Within Pool

### "" (Empty - Normal)

**What it means:**
- Loan is active in pool: `loanPoolStatus: ''` (empty string) in `previewstdloantape` collection
- Standard status: normal active state, included in all pool calculations
- Included in pool calculations: loan counts toward `numberofloans`, `originalbalance`, `currentbalance` in `pool_detail` collection, and included in PostgreSQL analytics queries (`getBdbTiles`) for WAC, FICO, LTV, DTI/DSCR calculations
- Database field: `loanPoolStatus: ''` (empty string, not null)
- Updated via: `GET /updateLoanStatus` endpoint when loan status changes

**When it's set:**
- Default status in pool
- When loan is mapped
- Normal active state

---

### Reconsider

**What it means:**
- Loan needs reconsideration
- May have issues identified
- Under review

**When it's set:**
- When issues are identified
- When review is needed
- Manual status change

**Next status:**
- "" (Normal) if resolved
- Removed if removed

---

### Removed

**What it means:**
- Loan removed from pool: `loanPoolStatus: 'Removed'` in `previewstdloantape` collection
- Not included in pool calculations: excluded from `numberofloans`, `originalbalance`, `currentbalance` in `pool_detail` collection (updated via `CalculateNoofLoansAndBalanceRefactored` function), and excluded from PostgreSQL `poolloantape` table analytics (via `deleteLoansFromPoolInPostgres` function)
- Still visible but excluded: loan document remains in database but excluded from calculations
- Database field: `loanPoolStatus: 'Removed'` (exact string value)
- Updated via: `GET /updateLoanStatus` endpoint with `loanPoolStatus: 'Removed'`
- Impact: Pool metrics immediately updated in MongoDB, PostgreSQL analytics updated on next query (loans deleted from `poolloantape` table)

**When it's set:**
- When loan is removed from pool
- Manual removal action
- Exclusion from pool

**Next status:**
- Reinstated (if put back)
- Or remains Removed

---

### Reinstated

**What it means:**
- Loan was removed but put back
- Now included in pool again
- Active status restored

**When it's set:**
- When removed loan is reinstated
- Manual reinstatement action
- Return to active status

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

1. Track all statuses: Monitor all status fields
2. Understand transitions: Know what causes status changes
3. Verify before proceeding: Ensure verification complete
4. Manage pool status: Handle reconsideration and removal appropriately
5. Monitor workflow: Track loan through entire lifecycle

---

## Key Takeaways

1. Five status fields: Track different aspects of loan lifecycle
2. Status combinations: Multiple statuses work together
3. Status transitions: Clear progression through workflow
4. Status history: All changes recorded
5. Complete tracking: Full lifecycle visibility

Understanding all loan states helps you effectively manage loans and track their progress through the platform workflow.
