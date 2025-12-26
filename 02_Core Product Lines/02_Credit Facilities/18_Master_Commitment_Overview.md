# Master Commitment Overview

## What is a Master Commitment?

A master commitment is the finalized credit facility agreement that defines the complete facility structure. It's automatically created when a term sheet is approved and contains all the rules, parameters, and lender information needed to operate the facility.

## Key Concepts

### Auto-Creation

Master commitments are automatically created:
- Trigger: Term sheet status changes to `'Accepted'` (via `POST /cf/acceptTermSheet/:termSheetId`)
- Function: System automatically calls `autoCreateMasterCommitment(termSheet, masterCommitmentId)` function
- Database: Creates document in `cf_master_commitments` collection (MongoDB)
- No manual creation allowed: Cannot be created via API - only auto-generated
- Created immediately: Happens synchronously during term sheet approval process
- ID Generation: `masterCommitmentId` generated using format `MC-MMDDYYYY-XXXX` where MMDDYYYY is current date (month/day/year) and XXXX is random alphanumeric suffix (e.g., `MC-12012024-abc1`)

### Pre-Populated Data

**From term sheet:**
- Facility amount
- Interest rates and margins
- Maturity date
- Advance rates
- Pricing index
- Other commercial terms

**These fields are read-only:**
- Cannot be changed in master commitment
- Reflects approved term sheet terms
- Provides foundation for facility

### Facility Agent Configuration

**Facility agent completes (editable fields, initially empty):**
- `facilityName`: Name of the facility (string)
- `collateralRules`: Array of collateral eligibility rules (initially empty array `[]`)
- `lenderGroups`: Array of lender groups with commitment amounts and voting percentages (initially empty array `[]`)
- `servicerOrgId`: Array of servicer organization IDs (initially empty array `[]`)
- `borrowingBase`: Borrowing base calculation configuration
- `availableCapacity`: Available borrowing capacity
- `facilitySetupModelStatus`: Tracks setup completion (`'In Progress'` initially, changes to `'Completed'` when all required fields filled)
- `requiredFieldsCompleted`: Boolean flag indicating if all required fields are complete (initially `false`)
- `contractType`: Type of contract (`'single'` or `'multiple'` for sub-commitments)

**Auto-Save Functionality:**
- Facility agent can auto-save individual fields (via `POST /cf/master-commitments/:masterCommitmentId/auto-save-field`)
- Field name and value provided in request body
- System validates field type and updates database
- Supports arrays (`lenderGroups`, `collateralRules`), numbers (`totalCommitmentAmount`), strings (`facilityName`), and dates
- Can save multiple times while in `'DRAFT'` status

---

## Master Commitment Components

### Facility Rules

**Borrowing Base Rules:**
- How borrowing base is calculated
- Collateral eligibility criteria
- Advance rates for different collateral types
- Concentration limits
- Other borrowing constraints

### Lender Configuration

**Lender Groups:**
- List of participating lenders
- Each lender's commitment amount
- Voting percentages
- Lender-specific terms
- Approval requirements

### Collateral Rules

**Eligibility Criteria:**
- What collateral qualifies
- How collateral is valued
- Collateral concentration limits
- Collateral monitoring requirements

### Facility Parameters

**Operational Settings:**
- Draw frequency
- Payment terms
- Reporting requirements
- Covenant templates
- Other facility parameters

---

## Master Commitment Status Flow

### Complete Workflow

```
Auto-Created (Draft) → PendingLenderApproval → ACTIVE
```

### Status 1: Draft

**What it means:**
- Master commitment auto-created from approved term sheet
- Facility agent can configure it
- Not yet submitted for lender approval
- Can be edited freely

**What facility agent can do:**
- Configure all facility rules
- Set up lender groups
- Define borrowing base calculations
- Set collateral eligibility rules
- Save multiple times
- Edit anytime

**What happens:**
- Pre-populated with term sheet data (read-only)
- Empty fields for facility agent to complete
- Ready for configuration

### Status 2: PendingLenderApproval

**What it means:**
- Facility agent has completed configuration
- Submitted for lender approval
- Waiting for lender decision
- Any selected lender can approve

**How it's achieved:**
- Facility agent completes all required fields
- Clicks "Create" or "Submit" button
- Status changes to "PendingLenderApproval"
- Lenders receive notifications

**What happens:**
- Lenders can review master commitment
- Any selected lender can approve
- One approval activates the facility
- E-signature envelope generated after approval

### Status 3: ACTIVE

**What it means:**
- Facility is active and operational
- Borrowers can create funding requests
- Facility is ready for drawdowns
- Lenders have approved

**How it's achieved:**
- Any selected lender approves via DocuSign
- Status changes to "ACTIVE"
- Facility becomes operational
- E-signature envelope generated (for documentation)

**What happens:**
- Borrowers can create funding requests
- Facility agent can manage facility
- Lenders can participate in funding
- Facility is fully operational

---

## Key Features

### Automatic Creation

**When term sheet approved:**
- System automatically creates master commitment
- Links to term sheet via termSheetId
- Pre-populates with term sheet data
- Sets initial status to "Draft"
- Assigns facility agent as creator

### Pre-Populated Fields

**From term sheet (read-only):**
- Requested commitment amount
- Advance rate
- Margin
- Pricing index
- Fixed rate (if applicable)
- Maturity date
- Draw frequency
- Covenant template

**Empty for facility agent:**
- Facility rules
- Lender groups
- Borrowing base configuration
- Collateral eligibility rules
- Other facility parameters

### Lender Approval

Simple approval mechanism:
- Any selected lender can approve: Lender must be in the `lenderGroups` array of the master commitment
- One approval activates facility: When any lender in `lenderGroups` approves via DocuSign (via `GET /docusign/signing-complete?envelopeRequest=masterCommitmentSign&masterCommitmentId=...`), status changes from `'PendingLenderApproval'` to `'ACTIVE'`
- No complex voting thresholds: Simple approval - any one lender approval activates the commitment
- E-signature for documentation: After approval, e-signature envelope generated for documentation purposes (no actual signing required at this point - already signed via DocuSign)
- Individual tracking: Each lender's approval status tracked separately in `lenderGroups` array via `lenderStatus` field: `'pending_approval'` → `'approved'` → `'esignature_completed'`

### Individual Lender Tracking

**Each lender tracked separately:**
- Lender status (pending_approval, approved, esignature_completed)
- Approval timestamp
- Commitment amount
- Voting percentage
- Individual approval status

---

## Facility Setup

### Configuration Process

**Facility agent steps:**
1. Review pre-populated term sheet data
2. Configure facility rules
3. Set up borrowing base calculations
4. Define collateral eligibility
5. Add and configure lender groups
6. Complete all required fields
7. Submit for lender approval

### Required Configuration

**Must complete:**
- Facility rules and parameters
- Lender groups (at least one lender)
- Borrowing base setup
- Collateral rules
- All mandatory fields

### Validation

**Before submission:**
- All required fields must be filled
- Lender groups must be configured
- Facility rules must be complete
- Validation rules must pass

---

## Relationship to Term Sheet

### Linkage

**Master commitment linked to term sheet:**
- Via termSheetId field
- References original term sheet
- Pre-populated with term sheet data
- Cannot exist without approved term sheet

### Data Flow

**Term Sheet → Master Commitment:**
- Approved term sheet triggers creation
- Term sheet data pre-populates master commitment
- Master commitment extends term sheet with rules
- Master commitment enables funding

### Independence

**Once created:**
- Master commitment is independent entity
- Can be managed separately
- Has its own status and workflow
- Term sheet changes don't affect it (after creation)

---

## Common Workflow

### Complete Setup

1. **Term sheet approved** → Master commitment auto-created (Draft)
2. **Facility agent configures** → Sets up rules and lenders (still Draft)
3. **Facility agent submits** → Status changes to PendingLenderApproval
4. **Lender approves** → Status changes to ACTIVE
5. **Facility operational** → Borrowers can create funding requests

### Editing During Draft

**Facility agent can:**
- Edit master commitment multiple times
- Save as draft repeatedly
- Make changes anytime
- Configure completely before submitting

**Once submitted:**
- Cannot edit (status is PendingLenderApproval)
- Must wait for lender approval
- Or facility agent can withdraw (if system allows)

---

## Best Practices

### For Facility Agents

1. **Configure completely**: Set up all rules before submitting
2. **Review term sheet data**: Verify pre-populated information
3. **Set up lenders properly**: Configure lender groups correctly
4. **Test calculations**: Verify borrowing base setup
5. **Submit when ready**: Don't rush submission

### For Lenders

1. **Review carefully**: Understand facility terms and rules
2. **Evaluate structure**: Assess facility setup
3. **Approve promptly**: Keep workflow moving
4. **Track participation**: Monitor your involvement

### For Borrowers

1. **Monitor progress**: Track master commitment status
2. **Understand rules**: Know facility parameters
3. **Prepare for funding**: Ready to create funding requests when ACTIVE
4. **Stay informed**: Watch for status updates

---

## Key Takeaways

1. **Auto-created**: Automatically created from approved term sheet
2. **Pre-populated**: Contains term sheet data (read-only)
3. **Configurable**: Facility agent sets up rules and lenders
4. **Lender approval**: Any lender approval activates facility
5. **Enables funding**: ACTIVE status allows funding requests

Understanding master commitments helps you know how facilities are structured and what happens after your term sheet is approved.
