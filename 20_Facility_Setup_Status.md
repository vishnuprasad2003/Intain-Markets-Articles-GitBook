---
title: Facility Setup Status
description: Understand how facility setup status tracks configuration completion
---

# Facility Setup Status

## Overview

The facility setup status (facilitySetupModelStatus) tracks whether operational parameters and facility management settings have been completed for an ACTIVE master commitment. This status is separate from the master commitment workflow status and focuses on post-activation operational configuration. Facility setup model can only be completed after the master commitment becomes ACTIVE.

## Lifecycle Overview

Facility setup status starts as **In Progress** (or undefined) when the master commitment is first created. It remains In Progress while facility agents configure the master commitment (lender groups, collateral rules, borrowing base calculations). After the master commitment becomes ACTIVE (lender approval), facility agents can complete the facility setup model by calling API endpoint: PUT /cf/master-commitments/:masterCommitmentId/facility-setup-model/complete. System validates master commitment status is ACTIVE. System validates facilitySetupModelStatus is not already Completed. System updates facilitySetupModelStatus to **Completed**, updates updatedAt and updatedBy, adds entry to actionHistory. Once completed, the status changes to **Completed**, indicating operational parameters are configured.

The setup status guides facility agents through post-activation operational configuration, ensuring facility management settings are complete for active facilities.

## Status Meanings

**In Progress** (or undefined) - The facility agent is still configuring operational parameters for the ACTIVE master commitment. Facility setup model configuration is ongoing, and operational settings may be incomplete. Setup status shows In Progress when operational configuration work is ongoing.

**Completed** - All operational parameters and facility management settings are complete for the ACTIVE master commitment. Facility setup model has been marked as completed via API endpoint. Setup status shows Completed when all operational requirements are met and the facility is fully configured for operations.

## What Each Status Indicates

**In Progress Status** indicates that operational configuration work is still ongoing for the ACTIVE master commitment. Operational parameters may need setup, servicer assignments may need configuration, or facility management settings may be incomplete. Facility agents can continue working on operational configuration. System validates master commitment must be ACTIVE before allowing completion.

**Completed Status** indicates that all operational parameters and facility management settings are finished. Facility setup model has been marked as completed via API endpoint (PUT /cf/master-commitments/:masterCommitmentId/facility-setup-model/complete). System updates facilitySetupModelStatus to Completed, records actionHistory entry, and the facility is fully configured for operational use. This can only be done once per facility and only for ACTIVE master commitments.
