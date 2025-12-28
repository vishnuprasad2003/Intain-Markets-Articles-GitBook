---
title: Facility Setup Status
description: Understand how facility setup status tracks configuration completion
---

# Facility Setup Status

## Overview

The facility setup status tracks whether a master commitment has been fully configured and is ready for lender approval. This status helps facility agents know what still needs to be completed before submitting the facility, ensuring all required fields and configurations are in place. It's separate from the master commitment workflow status and focuses specifically on configuration completeness, guiding facility agents through the setup process.

## Lifecycle Overview

Facility setup status starts as **In Progress** when the master commitment is first created and facility agents begin configuration. It remains In Progress while facility agents work on setting up facility rules, borrowing base calculations, lender groups, and other required configurations. Once all required fields are filled and validations pass, the status changes to **Completed**, indicating the facility is ready for submission to lenders.

The setup status is designed to guide facility agents through the configuration process, showing what's incomplete and preventing submission until everything is ready. This ensures that facilities are fully configured before they're submitted for lender approval, maintaining quality and completeness. Understanding this status helps facility agents track their progress and know when setup is complete.

## Status Meanings

**In Progress** - The facility agent is still configuring the master commitment. Some required fields or configurations are incomplete, and the facility is not ready for submission. Setup status shows In Progress when configuration work is ongoing.

**Completed** - All required fields and configurations are complete, validation passes, and the master commitment is ready for lender approval. Setup status shows Completed when all requirements are met and the facility can be submitted.

## What Each Status Indicates

**In Progress Status** indicates that configuration work is still ongoing. Required fields may be empty, facility rules may need setup, borrowing base calculations may need configuration, or lender groups may need to be added. Facility agents can continue working, save progress multiple times, and complete configurations. This status tells you that setup is not yet complete and submission is not yet possible. You need to complete all required configurations before the status changes to Completed.

**Completed Status** indicates that all required configurations are finished and validations have passed. All required fields are filled, facility rules are configured, borrowing base calculations are set up, lender groups are added, and the facility is ready for lender approval. Facility agents can submit for lender approval, and the master commitment can progress to Pending Lender Approval status. This status tells you that setup is complete and the facility is ready for the next stage. You can proceed with submission knowing that all requirements are met.

Understanding facility setup status helps facility agents track their configuration progress, know what still needs to be completed, verify when setup is ready for submission, ensure all required fields and configurations are in place before submitting for lender approval, and work efficiently through the facility configuration process.
