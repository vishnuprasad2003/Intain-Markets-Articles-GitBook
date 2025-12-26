# Facility Setup Status

## Overview

The facility setup status tracks whether a master commitment has been fully configured and is ready for lender approval. This status helps facility agents know what still needs to be completed before submitting the facility for lender approval.

## What is Facility Setup Status?

### Purpose

The facility setup status indicates:
- Whether all required facility configuration is complete
- What still needs to be set up
- Whether the facility is ready for submission
- Progress of facility configuration

### Status Values

**In Progress:**
- Facility setup is not yet complete
- Some required fields or configurations are missing
- Facility agent is still working on configuration
- Not ready for lender approval

**Completed:**
- All required facility setup is complete
- All fields filled and validated
- Facility rules configured
- Lender groups set up
- Ready for submission to lender approval

---

## Understanding Setup Status

### What Gets Tracked

**Configuration Completeness:**
- Facility rules and parameters
- Borrowing base calculations
- Collateral eligibility rules
- Lender groups configuration
- Required field completion

### Status Indicators

**In Progress:**
- Visual indicator shows setup incomplete
- Lists what still needs to be done
- Guides facility agent on next steps
- Prevents premature submission

**Completed:**
- Visual indicator shows setup complete
- All requirements met
- Ready to submit for lender approval
- Can proceed to next phase

---

## Setup Requirements

### Required Configuration

**Facility Rules:**
- Borrowing base calculation method
- Collateral eligibility criteria
- Advance rates
- Concentration limits
- Other facility parameters

**Lender Groups:**
- At least one lender group configured
- Lender commitment amounts
- Voting percentages
- Lender-specific terms

**Borrowing Base:**
- Calculation method defined
- Collateral types specified
- Eligibility rules set
- Monitoring requirements

**Collateral Rules:**
- Eligibility criteria defined
- Valuation methods specified
- Concentration limits set
- Monitoring requirements

### Validation

**Before Completion:**
- All required fields must be filled
- Validation rules must pass
- Configuration must be consistent
- No errors or warnings

---

## Status and Workflow

### During Setup (In Progress)

**What facility agent can do:**
- Continue configuring facility
- Fill in missing fields
- Set up lender groups
- Configure borrowing base
- Define collateral rules
- Save progress multiple times

**What facility agent cannot do:**
- Cannot submit for lender approval (setup incomplete)
- Cannot finalize facility (not ready)

### After Setup (Completed)

**What facility agent can do:**
- Submit for lender approval
- Review complete configuration
- Verify all settings
- Proceed to next phase

**What happens:**
- Status shows "Completed"
- Facility ready for submission
- Can change status to PendingLenderApproval
- Lenders can review and approve

---

## Checking Setup Status

### Where to See It

**Master Commitment Page:**
- Setup status displayed prominently
- Shows "In Progress" or "Completed"
- Lists incomplete items (if In Progress)
- Indicates readiness for submission

**Status Indicators:**
- Color-coded badges
- Progress indicators
- Completion checkmarks
- Warning messages

### Understanding Status

**In Progress:**
- Review what's incomplete
- Complete missing items
- Check validation messages
- Continue configuration

**Completed:**
- Verify all settings correct
- Review configuration
- Submit when ready
- Proceed to lender approval

---

## Common Scenarios

### Scenario 1: Complete Setup

1. Master commitment created → Setup status: "In Progress"
2. Facility agent configures rules → Still "In Progress"
3. Sets up lender groups → Still "In Progress"
4. Completes all requirements → Setup status: "Completed"
5. Submits for lender approval → Status: PendingLenderApproval

### Scenario 2: Partial Setup

1. Master commitment created → Setup status: "In Progress"
2. Facility agent starts configuration → Still "In Progress"
3. Some fields incomplete → Still "In Progress"
4. Completes all fields → Setup status: "Completed"
5. Ready to submit

### Scenario 3: Validation Issues

1. Facility agent fills fields → Setup status: "In Progress"
2. Validation errors found → Still "In Progress"
3. Fixes validation issues → Still "In Progress"
4. All validations pass → Setup status: "Completed"

---

## Best Practices

### For Facility Agents

1. **Complete systematically**: Work through setup step by step
2. **Check requirements**: Know what's required for completion
3. **Validate early**: Check validation as you go
4. **Review thoroughly**: Verify all settings before submitting
5. **Use status guide**: Let status guide your next steps

### Completing Setup

1. **Fill all required fields**: Don't leave anything blank
2. **Configure completely**: Set up all rules and parameters
3. **Validate configuration**: Ensure all validations pass
4. **Review before submit**: Double-check everything
5. **Submit when ready**: Don't rush submission

---

## Troubleshooting

### "Setup status stuck on In Progress"
- Check what fields are incomplete
- Review validation messages
- Ensure all required fields filled
- Verify lender groups configured
- Check for errors or warnings

### "Can't submit for approval"
- Verify setup status is "Completed"
- Check all required fields filled
- Ensure validation passes
- Review error messages
- Complete missing items

### "Status not updating to Completed"
- Verify all requirements met
- Check validation rules
- Ensure no errors present
- Refresh page
- Contact support if persists

---

## Key Takeaways

1. **Tracks configuration**: Shows facility setup progress
2. **Two states**: In Progress or Completed
3. **Guides workflow**: Indicates what needs to be done
4. **Prevents premature submission**: Blocks submission until complete
5. **Enables next phase**: Completed status allows lender approval

Understanding facility setup status helps facility agents track their progress and know when the facility is ready for lender approval.
