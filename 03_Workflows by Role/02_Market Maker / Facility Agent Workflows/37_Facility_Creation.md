# Facility Creation

## Overview

Facility creation is the process where facility agents configure master commitments after they're automatically created from approved term sheets. This guide covers how to set up facility rules, configure lender groups, and complete facility setup.

## Understanding Master Commitment Creation

### Automatic Creation

**What happens automatically:**
- When term sheet is approved (status: Accepted)
- System calls `autoCreateMasterCommitment()` function
- Master commitment created with Draft status
- Pre-populated with term sheet data (read-only)
- Ready for facility agent configuration

### Pre-Populated Data

**From term sheet (read-only):**
- Facility amount
- Interest rates and margins
- Maturity date
- Advance rates
- Pricing index
- Other commercial terms

**Empty for completion:**
- Facility rules and parameters
- Lender groups
- Borrowing base configuration
- Collateral eligibility rules

---

## Configuring Facility Rules

### Step 1: Set Up Borrowing Base

**What to configure:**
- Borrowing base calculation method
- Collateral types and eligibility
- Advance rates for different collateral
- Concentration limits
- Other borrowing constraints

**How to configure:**
1. Navigate to master commitment
2. Go to Borrowing Base section
3. Set calculation method
4. Define collateral eligibility
5. Set advance rates and limits

### Step 2: Define Collateral Rules

**What to define:**
- Collateral eligibility criteria
- Collateral valuation methods
- Collateral concentration limits
- Collateral monitoring requirements

**How to define:**
1. Go to Collateral Rules section
2. Set eligibility criteria
3. Define valuation methods
4. Set concentration limits
5. Configure monitoring

### Step 3: Configure Facility Parameters

**What to configure:**
- Draw frequency
- Payment terms
- Reporting requirements
- Covenant templates
- Other operational settings

**How to configure:**
1. Go to Facility Parameters section
2. Set operational parameters
3. Configure reporting
4. Set up covenants
5. Complete configuration

---

## Setting Up Lender Groups

### Step 1: Add Lenders

**How to add:**
1. Navigate to Lender Groups section
2. Click "Add Lender" or "Add Lender Group"
3. Select lender organization
4. Enter lender details
5. Add lender to group

### Step 2: Configure Lender Details

**For each lender:**
- Commitment amount
- Voting percentage
- Lender-specific terms
- Other lender parameters

**How to configure:**
1. Select lender from group
2. Enter commitment amount
3. Set voting percentage
4. Configure lender terms
5. Save lender configuration

### Step 3: Complete Lender Setup

**Requirements:**
- At least one lender group configured
- All lender details complete
- Commitment amounts specified
- Voting percentages set
- Ready for submission

---

## Completing Facility Setup

### Step 1: Review Configuration

**Before submitting:**
- Review all facility rules
- Verify lender groups complete
- Check borrowing base setup
- Ensure all required fields filled
- Validate configuration

### Step 2: Validate Setup

**System checks:**
- All required fields filled
- Validation rules pass
- Configuration consistent
- No errors or warnings
- Setup status: Completed

### Step 3: Submit for Lender Approval

**Process:**
1. Review complete configuration
2. Verify setup status is "Completed"
3. Click "Create" or "Submit" button
4. Confirm submission
5. Status changes to PendingLenderApproval

**What happens:**
- Status changes to PendingLenderApproval
- Lenders receive notifications
- Lenders can review master commitment
- Any lender can approve
- Facility becomes ACTIVE when approved

---

## Best Practices

### For Facility Agents

**Configuration:**
1. Complete systematically: Work through setup step by step
2. Review term sheet data: Verify pre-populated information
3. Set up lenders properly: Configure lender groups correctly
4. Test calculations: Verify borrowing base setup
5. Submit when ready: Don't rush submission

**Setup process:**
1. Fill all fields: Complete all required information
2. Configure completely: Set up all rules and parameters
3. Validate early: Check validation as you go
4. Review thoroughly: Verify all settings before submitting
5. Use status guide: Let status guide your next steps

---

## Common Scenarios

### Scenario 1: Complete Setup

1. Master commitment created → Draft
2. Configure facility rules → Still Draft
3. Set up lender groups → Still Draft
4. Complete all configuration → Setup: Completed
5. Submit for approval → PendingLenderApproval
6. Lender approves → ACTIVE

### Scenario 2: Iterative Configuration

1. Master commitment created → Draft
2. Start configuration → Still Draft
3. Save multiple times → Still Draft
4. Complete configuration → Setup: Completed
5. Submit → PendingLenderApproval

### Scenario 3: Multiple Lenders

1. Configure facility rules → Draft
2. Add Lender A → Still Draft
3. Add Lender B → Still Draft
4. Add Lender C → Still Draft
5. Complete setup → Submit
6. Any lender can approve → ACTIVE

---

## Troubleshooting

### "Can't configure facility"
- Check master commitment status is Draft
- Verify you're the facility agent
- Ensure term sheet was approved
- Check you have permission

### "Setup status not completing"
- Check what fields are incomplete
- Review validation messages
- Ensure all requirements met
- Verify lender groups configured

### "Can't submit for approval"
- Verify setup status is Completed
- Check all required fields filled
- Ensure validation passes
- Review error messages

---

## Key Takeaways

1. Auto-created: Master commitment created automatically
2. Pre-populated: Contains term sheet data (read-only)
3. Configurable: Facility agent sets up rules and lenders
4. Complete setup: All requirements must be met
5. Lender approval: Any lender approval activates facility

Understanding facility creation helps facility agents effectively configure master commitments and set up credit facilities for operation.
