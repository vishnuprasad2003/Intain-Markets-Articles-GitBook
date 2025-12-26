# Loan Rejection & Reinstatement

## Overview

Sometimes loans need to be removed from pools temporarily or permanently. The platform provides mechanisms to reject loans (remove them) and reinstate them (put them back) when appropriate.

## Loan Rejection

### What is Loan Rejection?

**Rejection** means removing a loan from a pool. The loan is:
- Excluded from pool calculations
- Not counted in pool metrics
- Still visible but marked as removed
- Can be reinstated later if needed

### When to Reject Loans

**Common scenarios:**
- Loan doesn't meet pool criteria
- Data quality issues identified
- Loan needs correction before inclusion
- Pool requirements changed
- Loan performance issues
- Compliance concerns

### How to Reject a Loan

**Process:**
1. Navigate to pool's loan list (via `/getpreviewstdloantapeusinglatestdate?poolId=...`)
2. Select loan(s) to remove
3. Update loan status via endpoint: `GET /updateLoanStatus?poolId=<poolId>&loanid=<loanId>&status=Removed`
4. System processes removal automatically

**Endpoint Details:**
- **Endpoint**: `GET /updateLoanStatus`
- **Query Parameters**:
  - `poolId`: Pool ID (required)
  - `loanid`: Loan ID to remove (required)
  - `status`: "Removed" (required)

**What happens:**
1. **Loan Status Update:**
   - System updates loan in issuer's MongoDB `previewstdloantape` collection
   - Query: `{ "Loan ID": loanid, "poolid": poolId }`
   - Update: `{ $set: { loanPoolStatus: "Removed" } }`
   - Loan's `loanPoolStatus` changes to "Removed"
   - Other fields remain unchanged (loan still has `poolid` set)

2. **Pool Metrics Recalculation:**
   - System calls `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
   - Aggregates loans with `poolid: poolId` and `loanPoolStatus: { $ne: "Removed" }` (or filters out removed)
   - Recalculates:
     - `numberofloans`: Count of active loans (excludes removed)
     - `originalbalance`: Sum of "Original Principal Balance" (excludes removed)
     - `currentbalance`: Sum of "Current Principal Balance" (excludes removed)
   - Updates `pool_detail` collection with new metrics

3. **PostgreSQL Cleanup:**
   - System calls `deleteLoansFromPoolInPostgres(poolId, [loanid])`
   - Deletes loan from PostgreSQL `poolloantape` table
   - Loan no longer included in analytics queries
   - PostgreSQL metrics (WAC, FICO, LTV, DTI/DSCR) recalculate automatically on next query

4. **Loan Visibility:**
   - Loan still visible in MongoDB `previewstdloantape` collection
   - Loan still has `poolid` field set (not unmapped)
   - Loan can be filtered by `loanPoolStatus: "Removed"`
   - Loan appears in pool's loan list but marked as removed

**Response:**
- Returns: `{ statuscode: 200, isSuccess: true, message: "Loan Status Updated successfully" }`

---

## Impact of Rejection

### On Pool Metrics

**What changes:**
- **Total Balance**: Decreases by removed loan's balance
- **Loan Count**: Decreases by number of removed loans
- **Weighted Averages**: Recalculate without removed loans
  - WAC (Weighted Average Coupon)
  - Average FICO
  - Average LTV
  - Average DTI/DSCR
- **Aggregate Statistics**: All metrics update

**What stays the same:**
- Pool basic information
- Other loans in pool
- Pool status (usually)
- Pool sharing settings

### On Loan Status

**Loan's status:**
- `loanPoolStatus`: Changes to "Removed"
- `Status`: May remain as pool name or change
- `workflow_status`: Usually unchanged
- `verificationSource`: Usually unchanged
- `nftLoanStatus`: Usually unchanged

**Loan visibility:**
- Still visible in pool's loan list
- Marked as "Removed"
- Can be filtered to show/hide removed loans
- Can be reinstated

---

## Loan Reinstatement

### What is Reinstatement?

**Reinstatement** means putting a removed loan back into the pool. The loan:
- Is included in pool calculations again
- Counted in pool metrics
- Returns to active status
- Fully participates in pool

### When to Reinstate Loans

**Common scenarios:**
- Loan issues were resolved
- Data corrections made
- Pool criteria updated
- Mistaken removal corrected
- Loan now meets requirements

### How to Reinstate a Loan

**Process:**
1. Navigate to pool's loan list (via `/getpreviewstdloantapeusinglatestdate?poolId=...&status=Removed`)
2. Filter to show removed loans (set `status=Removed` query parameter)
3. Select loan(s) to reinstate
4. Update loan status via endpoint: `GET /updateLoanStatus?poolId=<poolId>&loanid=<loanId>&status=Reinstated`
5. System processes reinstatement

**Endpoint Details:**
- **Endpoint**: `GET /updateLoanStatus`
- **Query Parameters**:
  - `poolId`: Pool ID (required)
  - `loanid`: Loan ID to reinstate (required)
  - `status`: "Reinstated" (required)

**What happens:**
1. **Loan Status Update:**
   - System updates loan in issuer's MongoDB `previewstdloantape` collection
   - Query: `{ "Loan ID": loanid, "poolid": poolId }`
   - Update: `{ $set: { loanPoolStatus: "Reinstated" } }`
   - Loan's `loanPoolStatus` changes to "Reinstated"
   - Other fields remain unchanged

2. **Pool Metrics Recalculation:**
   - **Note**: Reinstatement may require manual pool metrics recalculation
   - System may need to call `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)` manually
   - Recalculates:
     - `numberofloans`: Count including reinstated loan
     - `originalbalance`: Sum including reinstated loan's balance
     - `currentbalance`: Sum including reinstated loan's balance
   - Updates `pool_detail` collection

3. **PostgreSQL Sync:**
   - **Note**: Reinstated loan may need to be pushed back to PostgreSQL
   - May need to call `postgresDataPush({ loanIds: [loanid], poolid: poolId, module: "pool", issuerOrgDbName })`
   - Loan included in PostgreSQL `poolloantape` table again
   - PostgreSQL metrics (WAC, FICO, LTV, DTI/DSCR) include reinstated loan on next query

4. **Loan Visibility:**
   - Loan appears in normal loan lists (not filtered out)
   - Loan included in all pool operations
   - Loan fully active in pool

**Response:**
- Returns: `{ statuscode: 200, isSuccess: true, message: "Loan Status Updated successfully" }`

**Important Notes:**
- Reinstatement sets `loanPoolStatus: "Reinstated"` (not empty string)
- Some systems may treat "Reinstated" as equivalent to "" (empty) for calculations
- Verify system behavior - you may need to manually set to "" (empty string) for full inclusion
- PostgreSQL sync may need manual trigger after reinstatement

---

## Impact of Reinstatement

### On Pool Metrics

**What changes:**
- **Total Balance**: Increases by reinstated loan's balance
- **Loan Count**: Increases by number of reinstated loans
- **Weighted Averages**: Recalculate including reinstated loans
  - WAC (Weighted Average Coupon)
  - Average FICO
  - Average LTV
  - Average DTI/DSCR
- **Aggregate Statistics**: All metrics update

**What stays the same:**
- Pool basic information
- Other loans in pool
- Pool status (usually)
- Pool sharing settings

### On Loan Status

**Loan's status:**
- `loanPoolStatus`: Changes back to "" (normal)
- `Status`: Usually remains as pool name
- `workflow_status`: Usually unchanged
- `verificationSource`: Usually unchanged
- `nftLoanStatus`: Usually unchanged

**Loan visibility:**
- Appears in normal loan list
- No longer marked as removed
- Included in all pool operations
- Fully active

---

## Reconsideration Status

### What is Reconsideration?

**Reconsideration** is an intermediate status where:
- Loan is flagged for review
- May be excluded from some calculations
- Indicates loan needs attention
- Can lead to removal or resolution

### When Loans are Marked for Reconsideration

**Common scenarios:**
- Issues identified during review
- Data quality concerns
- Compliance questions
- Performance concerns
- Validation errors

### Reconsideration Process

**Marking for reconsideration:**
1. Identify loan needing review
2. Mark as "Reconsider"
3. Loan status changes
4. Review process begins

**After reconsideration:**
- **Resolve**: Fix issues, return to normal
- **Remove**: Reject loan from pool
- **Keep**: Leave as is if acceptable

---

## Best Practices

### Before Rejecting

1. **Review carefully**: Ensure loan should be removed
2. **Check impact**: Understand how removal affects metrics
3. **Document reason**: Note why loan is being removed
4. **Consider alternatives**: Could issues be fixed instead?

### When Rejecting

1. **Be selective**: Only remove loans that truly don't belong
2. **Batch if needed**: Remove multiple loans at once if appropriate
3. **Verify metrics**: Check that metrics updated correctly
4. **Notify if needed**: Inform relevant parties if required

### When Reinstating

1. **Verify readiness**: Ensure loan is ready to be included
2. **Check impact**: Understand how reinstatement affects metrics
3. **Review changes**: Confirm any corrections made
4. **Update status**: Ensure loan status is appropriate

### Managing Removed Loans

1. **Track removals**: Keep record of why loans were removed
2. **Review periodically**: Check if removed loans can be reinstated
3. **Clean up**: Remove permanently if not needed
4. **Document decisions**: Record removal and reinstatement reasons

---

## Common Scenarios

### Scenario 1: Data Quality Issue

1. Loan has incorrect data
2. Mark for reconsideration
3. Review and identify issue
4. Remove loan from pool
5. Correct loan data
6. Reinstate loan with corrected data

### Scenario 2: Criteria Change

1. Pool criteria updated
2. Some loans no longer qualify
3. Remove non-qualifying loans
4. Pool metrics update
5. Pool continues with qualifying loans

### Scenario 3: Mistaken Removal

1. Loan removed by mistake
2. Identify error
3. Reinstate loan immediately
4. Pool metrics restore
5. Continue normal operations

### Scenario 4: Temporary Removal

1. Loan needs correction
2. Remove temporarily
3. Make corrections
4. Reinstate when ready
5. Pool includes corrected loan

---

## Troubleshooting

### "Can't remove loan"
- Check pool status (some statuses restrict removal)
- Verify you have permission
- Ensure loan is in pool
- Check if loan is locked

### "Metrics didn't update"
- Refresh page
- Check if removal was successful
- Verify loan status changed
- Contact support if issue persists

### "Can't reinstate loan"
- Check pool status (some statuses restrict changes)
- Verify loan was actually removed
- Ensure you have permission
- Check if pool allows reinstatement

### "Removed loan still showing in calculations"
- Verify loan status is "Removed"
- Check if filters are applied
- Refresh page
- Contact support if issue persists

---

## Key Takeaways

1. **Rejection removes loans**: Excludes from pool calculations
2. **Reinstatement restores loans**: Includes back in pool
3. **Metrics update automatically**: Calculations reflect changes
4. **Status tracks state**: `loanPoolStatus` shows current state
5. **Reversible process**: Can remove and reinstate as needed

Understanding loan rejection and reinstatement helps you effectively manage loans in your pools and maintain pool quality and compliance.
