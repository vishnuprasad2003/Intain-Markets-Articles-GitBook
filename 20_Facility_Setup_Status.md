---
title: Facility Setup Status
description: Understand how facility setup status tracks configuration completion
---

# Facility Setup Status

## Overview

The facility setup status tracks whether a master commitment has been fully configured and is ready for lender approval. This status helps facility agents know what still needs to be completed before submitting the facility, ensuring all required fields and configurations are in place.

## Reference Details

### In Progress Status

**What It Means**: The facility agent is still configuring the master commitment. Some required fields or configurations are incomplete, and the facility is not ready for submission.

**What You Can Do**:
- Continue configuring facility rules and parameters
- Set up borrowing base calculations
- Define collateral eligibility rules
- Add and configure lender groups
- Fill in required fields
- Save your progress multiple times

**What You Cannot Do**:
- Submit for lender approval (setup is incomplete)
- Mark setup as complete (validation will fail)

**What Shows as Incomplete**:
- Required fields that are empty
- Facility rules that need configuration
- Borrowing base calculations that need setup
- Lender groups that need to be added
- Other required configurations

**How to Check**: View the setup status indicator on the master commitment page. It shows "In Progress" and may list what's incomplete.

**Typical Duration**: This status lasts until you complete all required configurations and fields.

**What Happens Next**: Complete all required fields and configurations. When everything is complete, setup status changes to "Completed."

### Completed Status

**What It Means**: All required fields and configurations are complete, validation passes, and the master commitment is ready for lender approval.

**What You Can Do**:
- Submit the master commitment for lender approval
- Review all configurations one final time
- Verify everything is correct
- Proceed with lender approval process

**What You Cannot Do**:
- Cannot submit if setup is incomplete (validation prevents this)

**What Shows as Complete**:
- All required fields are filled
- Facility rules are configured
- Borrowing base calculations are set up
- Lender groups are added and configured
- All validations pass

**How to Check**: View the setup status indicator. It shows "Completed" and indicates you can proceed with submission.

**Typical Duration**: This status lasts until you submit for lender approval. Once submitted, the master commitment moves to "Pending Lender Approval" status.

**What Happens Next**: Submit the master commitment for lender approval. Status changes to "Pending Lender Approval," and lenders can review and approve.

## Important Notes

- **Setup Status Guides Configuration**: The setup status indicator shows what's incomplete and what needs to be done, helping you track your progress.

- **Validation Prevents Submission**: You cannot submit for lender approval until setup status shows "Completed" and all validations pass.

- **All Required Fields Must Be Filled**: Every required field must be completed before setup can be marked as complete.

- **Configuration Must Be Valid**: Not only must fields be filled, but configurations must be valid (for example, borrowing base calculations must be properly set up).

- **Status Updates Automatically**: Setup status updates automatically as you complete fields and configurations. You don't need to manually update it.

- **Multiple Saves Allowed**: You can save your progress multiple times while configuring. Setup status remains "In Progress" until everything is complete.

- **Final Review Recommended**: Before submitting, review all configurations to ensure everything is correct, as changes may be difficult after submission.

- **Setup Status Is Different from Master Commitment Status**: Setup status tracks configuration completion, while master commitment status tracks workflow progression (Draft, Pending Lender Approval, Active).

- **Incomplete Setup Blocks Submission**: The system prevents submission until setup is complete, ensuring all required information is provided.

- **Status History**: Setup status changes are recorded, so you can see when configuration was completed.

Understanding facility setup status helps facility agents track their configuration progress, know what still needs to be completed, verify when setup is ready for submission, and ensure all required fields and configurations are in place before submitting for lender approval.
