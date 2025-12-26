# Removed Loans & Calculations

## Overview

When loans are removed from pools, they're excluded from pool calculations but remain visible for tracking purposes. Understanding how removed loans affect calculations helps you manage pool metrics accurately.

## Removed Loans Concept

### What Does "Removed" Mean?

**Removed loans are:**
- Excluded from pool balance calculations
- Not counted in loan counts
- Excluded from weighted averages
- Still visible in pool (marked as removed)
- Can be reinstated later

**Removed loans are NOT:**
- Deleted from the system
- Completely hidden
- Permanently gone
- Lost from records

### Visibility vs. Exclusion

**Visibility:**
- Removed loans are still visible in pool's loan list
- You can see which loans were removed
- You can view removed loan details
- You can filter to show/hide removed loans

**Exclusion:**
- Removed loans don't count in calculations
- Pool metrics exclude removed loans
- Aggregate statistics don't include them
- Pool balance doesn't include them

---

## Impact on Pool Calculations

### Total Balance

**How it works:**
- Pool balance calculated from MongoDB `previewstdloantape` collection
- Function: `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
- Query: Loans with `poolid: poolId` (removed loans still have `poolid` set)
- Filter: Excludes loans with `loanPoolStatus: "Removed"` (or filters them out)
- Calculation:
  - `originalbalance`: `Sum("Original Principal Balance")` for active loans only
  - `currentbalance`: `Sum("Current Principal Balance")` for active loans only
- Removed loans' balances are NOT included
- Balance decreases when loans are removed
- Balance increases when loans are reinstated

**Database Query:**
```javascript
// MongoDB aggregation
{
  $match: { poolid: poolId },
  $addFields: {
    numericOriginalPrincipalBalance: { $convert: { input: "$Original Principal Balance", to: "double", onError: 0, onNull: 0 } },
    numericCurrentPrincipalBalance: { $convert: { input: "$Current Principal Balance", to: "double", onError: 0, onNull: 0 } }
  },
  $group: {
    _id: "$poolid",
    totalLoans: { $sum: 1 },  // Count (excludes removed if filtered)
    totalPrincipalBalance: { $sum: "$numericOriginalPrincipalBalance" },  // Sum original (excludes removed)
    totalCurrentBalance: { $sum: "$numericCurrentPrincipalBalance" }  // Sum current (excludes removed)
  }
}
```

**Example:**
- Pool has 100 loans, total balance $10,000,000
- Remove 5 loans with total balance $500,000 (set `loanPoolStatus: "Removed"`)
- System recalculates: `CalculateNoofLoansAndBalanceRefactored(poolId, issuerDb)`
- New pool balance: $9,500,000 (stored in `pool_detail.currentbalance`)
- Loan count: 95 loans (stored in `pool_detail.numberofloans`)
- Removed loans deleted from PostgreSQL `poolloantape` table

### Loan Count

**How it works:**
- Loan count = Number of active loans in pool
- Removed loans are NOT counted
- Count decreases when loans removed
- Count increases when loans reinstated

**Example:**
- Pool has 100 loans
- Remove 3 loans
- New loan count: 97 loans
- Removed loans not included in count

### Weighted Average Coupon (WAC)

**How it works:**
- WAC calculated from PostgreSQL `poolloantape` table (not MongoDB)
- Function: `getBdbTiles(poolId, assetClass)`
- Query: Loans with `"Pool ID" = poolId` and latest `loandataupdatedtill` date
- Removed loans excluded: Loans with `loanPoolStatus: "Removed"` are deleted from PostgreSQL, so automatically excluded
- Weight = Each loan's "Current Principal Balance"
- Only active loans included (removed loans not in PostgreSQL)

**Calculation (PostgreSQL):**
```sql
SELECT
  CASE
    WHEN NULLIF(Sum("Current Principal Balance" * "Current Interest Rate")::numeric, 0) / Sum("Current Principal Balance") * 100 IS NULL 
    THEN 'NA'
    ELSE TO_CHAR(ROUND((Sum("Current Principal Balance" * "Current Interest Rate") / Sum("Current Principal Balance") * 100)::numeric, 2), 'FM999999990.00')
  END AS wac
FROM public.poolloantape
WHERE "Pool ID" = $1
AND "loandataupdatedtill" = (SELECT MAX("loandataupdatedtill") FROM poolloantape WHERE "Pool ID" = $1)
```
- Formula: `Sum(Balance × Interest Rate) / Sum(Balance) × 100`
- Only includes loans in PostgreSQL (removed loans deleted, so excluded automatically)
- Returns "NA" if no loans or all balances zero

**Example:**
- Pool WAC: 5.5% (calculated from PostgreSQL)
- Remove high-rate loans (7%) via `/updateLoanStatus?status=Removed`
- System deletes removed loans from PostgreSQL `poolloantape` table
- Next WAC query: Calculates from remaining loans only
- WAC decreases (weighted average of remaining loans)
- Reinstating those loans: Need to push back to PostgreSQL, then WAC includes them again

### Average FICO Score

**How it works:**
- Average FICO = Weighted average of FICO scores
- Weight = Each loan's balance
- Only active loans included
- Removed loans excluded

**Calculation:**
```
Average FICO = Sum(Balance × FICO) / Sum(Balance)
(Only for active loans, removed loans excluded)
```

**Example:**
- Pool average FICO: 720
- Remove low-FICO loans (650)
- Average FICO increases
- Reinstating those loans decreases average

### Average Loan-to-Value (LTV)

**How it works:**
- Average LTV = Weighted average of LTV ratios
- Weight = Each loan's balance
- Only active loans included
- Removed loans excluded

**Calculation:**
```
Average LTV = Sum(Balance × LTV) / Sum(Balance)
(Only for active loans, removed loans excluded)
```

**Example:**
- Pool average LTV: 75%
- Remove high-LTV loans (90%)
- Average LTV decreases
- Reinstating those loans increases average

### Average DTI/DSCR

**How it works:**
- Average DTI/DSCR = Weighted average
- Weight = Each loan's balance
- Only active loans included
- Removed loans excluded

**Calculation:**
```
Average DTI/DSCR = Sum(Balance × DTI/DSCR) / Sum(Balance)
(Only for active loans, removed loans excluded)
```

**Example:**
- Pool average DTI: 35%
- Remove high-DTI loans (45%)
- Average DTI decreases
- Reinstating those loans increases average

---

## Calculation Updates

### Automatic Updates

#### When loans are removed
- MongoDB Pool Metrics: Update immediately via `CalculateNoofLoansAndBalanceRefactored()`
  - `numberofloans`, `originalbalance`, `currentbalance` recalculate
  - Updates `pool_detail` collection automatically
  - Changes reflect immediately in MongoDB
  
- PostgreSQL Analytics Metrics: Update on next query
  - Removed loans deleted from `poolloantape` table immediately
  - WAC, FICO, LTV, DTI/DSCR calculated from remaining loans
  - Next query to `getBdbTiles()` returns updated metrics
  
- No manual calculation needed for removal
- Changes reflect in real-time for MongoDB metrics
- PostgreSQL metrics update on next query

#### When loans are reinstated
- MongoDB Pool Metrics: May need manual recalculation
  - Set `loanPoolStatus: "Reinstated"` updates loan status
  - May need to call `CalculateNoofLoansAndBalanceRefactored()` manually
  - Or system may recalculate automatically (check implementation)
  
- PostgreSQL Analytics Metrics: Requires manual sync
  - Reinstated loan needs to be pushed back to PostgreSQL
  - Call `postgresDataPush({ loanIds: [loanid], poolid: poolId, module: "pool", issuerOrgDbName })`
  - Loan included in `poolloantape` table again
  - Next query to `getBdbTiles()` includes reinstated loan
  
- Manual steps may be required for reinstatement
- Verify system behavior for your use case

### What Updates

**Immediately updates:**
- Total balance
- Loan count
- All weighted averages (WAC, FICO, LTV, DTI/DSCR)
- Aggregate statistics
- Pool metrics dashboard

**Doesn't update:**
- Historical records (past calculations preserved)
- Audit trail (shows what happened when)
- Status history (tracks changes)

---

## Viewing Removed Loans

### In Loan List

**How to see removed loans:**
- Loan list shows all loans (active and removed)
- Removed loans marked with "Removed" status
- Can filter to show only removed loans
- Can filter to hide removed loans
- Can filter to show only active loans

### Status Indicators

**Visual indicators:**
- Removed loans have "Removed" badge
- Different color or styling
- Clear status label
- Easy to identify

### Loan Details

**What you can see:**
- All loan information
- Why it was removed (if documented)
- When it was removed
- Who removed it
- Can view but not edit (usually)

---

## Managing Removed Loans

### Reviewing Removed Loans

**Why review:**
- Check if removal was correct
- Identify loans that could be reinstated
- Understand pool composition
- Track removal reasons

**How to review:**
1. Filter to show removed loans
2. Review each removed loan
3. Check removal reasons
4. Decide on reinstatement

### Reinstating Removed Loans

**When to reinstate:**
- Loan issues resolved
- Data corrections made
- Mistaken removal
- Pool criteria changed

**Impact of reinstatement:**
- Loan included in calculations again
- All metrics update
- Pool balance increases
- Loan count increases

### Permanent Removal

**When appropriate:**
- Loan definitely doesn't belong
- Loan has permanent issues
- Pool finalized and changes not allowed
- No intention to reinstate

**What happens:**
- Loan stays removed
- Excluded from calculations
- Visible for audit purposes
- Can't be reinstated (if pool finalized)

---

## Best Practices

### Before Removing

1. **Understand impact**: Know how removal affects metrics
2. **Review carefully**: Ensure loan should be removed
3. **Document reason**: Note why removing
4. **Check alternatives**: Could issues be fixed instead?

### When Removing

1. **Remove selectively**: Only remove loans that don't belong
2. **Monitor metrics**: Watch how calculations change
3. **Verify updates**: Confirm metrics updated correctly
4. **Document decisions**: Record removal reasons

### After Removing

1. **Review metrics**: Check updated calculations
2. **Verify accuracy**: Ensure calculations correct
3. **Track removals**: Keep record of removed loans
4. **Consider reinstatement**: Review if loans can be put back

### Managing Calculations

1. **Understand formulas**: Know how metrics calculated
2. **Monitor changes**: Watch metrics when loans removed/reinstated
3. **Verify accuracy**: Check calculations make sense
4. **Document changes**: Record metric changes and reasons

---

## Common Scenarios

### Scenario 1: Remove High-Risk Loans

1. Identify high-risk loans (low FICO, high LTV)
2. Remove from pool
3. Pool average FICO increases
4. Pool average LTV decreases
5. Pool metrics improve
6. Pool more attractive to investors

### Scenario 2: Remove Incorrect Data

1. Identify loans with data errors
2. Remove temporarily
3. Correct loan data
4. Reinstate corrected loans
5. Pool metrics update with correct data

### Scenario 3: Criteria-Based Removal

1. Pool criteria updated
2. Some loans no longer qualify
3. Remove non-qualifying loans
4. Pool metrics update
5. Pool meets new criteria

### Scenario 4: Temporary Removal

1. Loan needs review
2. Remove temporarily
3. Review and resolve
4. Reinstate if appropriate
5. Or keep removed if not

---

## Troubleshooting

### "Removed loan still in calculations"
- Verify loan status is actually "Removed"
- Refresh page to see updated metrics
- Check if filters hiding removed loans
- Contact support if issue persists

### "Metrics didn't update after removal"
- Wait a moment for calculation
- Refresh page
- Verify removal was successful
- Check loan status changed
- Contact support if needed

### "Can't see removed loans"
- Check filter settings
- Look for "Show Removed" option
- Verify loan was actually removed
- Check pool view settings

### "Calculations seem wrong"
- Verify which loans are active vs removed
- Check loan balances are correct
- Review calculation formulas
- Contact support if calculations incorrect

---

## Key Takeaways

1. Removed = Excluded: Removed loans excluded from calculations
2. Visible but not counted: Can see removed loans but they don't count
3. Metrics update automatically: Calculations reflect active loans only
4. Reversible: Can reinstate removed loans
5. Impact varies: Removal affects different metrics differently

Understanding removed loans and calculations helps you manage pool metrics accurately and make informed decisions about loan inclusion and exclusion.
