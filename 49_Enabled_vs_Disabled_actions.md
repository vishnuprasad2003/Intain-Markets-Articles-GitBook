---
title: Enabled vs Disabled Actions
description: Understand why actions are enabled or disabled and what you can do about it
---

# Enabled vs Disabled Actions

## Overview

Understanding why actions are enabled or disabled helps you know what you can do and why certain actions aren't available. This guide explains the logic behind enabled and disabled buttons and actions, helping you understand workflow requirements and what needs to happen to enable actions.

## Applicable Users

- All platform users who see enabled or disabled action buttons

## Rules Explained

### Why Actions Are Enabled

Actions are enabled when all of the following conditions are met:

1. **You Have Permission**
   - Your role allows the action
   - You have access to the item
   - You're assigned to the item
   - Permissions are granted for this action

2. **Status Allows It**
   - Item is in correct status for this action
   - Workflow permits this action at this stage
   - Status progression allows it
   - Not blocked by current status

3. **Prerequisites Met**
   - Required information is present
   - Previous steps completed
   - Dependencies satisfied
   - All requirements met

### Why Actions Are Disabled

Actions are disabled when any of the following conditions apply:

1. **Wrong Status**
   - Item isn't in right status for this action
   - Workflow doesn't permit action at this stage
   - Status blocks the action
   - Wrong stage in workflow

2. **Missing Information**
   - Required fields not filled
   - Documents not uploaded
   - Information incomplete
   - Prerequisites missing

3. **Waiting for Others**
   - Another party needs to act first
   - Previous step not completed
   - Dependency not satisfied
   - Waiting for action from another role

4. **Already Completed**
   - Action was already taken
   - Cannot repeat action
   - Already in final state
   - Process complete for this action

5. **No Permission**
   - Your role doesn't allow this action
   - You don't have access to this item
   - Not assigned to item
   - Permissions not granted

## Impact on Users

### When Actions Are Enabled

- **You can proceed** - Enabled buttons mean you can take the action now.

- **Workflow can progress** - Taking enabled actions moves the workflow forward.

- **Requirements are met** - All conditions for the action are satisfied.

- **You have permission** - Your role allows this action.

### When Actions Are Disabled

- **You need to wait** - Disabled buttons mean you cannot take the action yet.

- **Requirements not met** - Some condition prevents the action.

- **Workflow is blocked** - Something needs to happen before you can proceed.

- **Check tooltips or messages** - Disabled buttons usually show reasons why they're disabled.

### How to Enable Actions

1. **Check Status** - Ensure item is in correct status for the action.

2. **Complete Prerequisites** - Fill required fields, upload documents, complete previous steps.

3. **Wait for Others** - If waiting for another party, wait for them to complete their action.

4. **Verify Permissions** - Ensure your role allows this action and you have access.

5. **Review Requirements** - Check what's needed and ensure everything is complete.

## Important Notes

- **Enabled buttons mean you can use them** - If a button is enabled, you can click it and the action will proceed.

- **Disabled buttons usually show reasons** - Hover over disabled buttons or check tooltips to see why they're disabled.

- **Status controls what actions are available** - The current status is the primary factor determining action availability.

- **Prerequisites must be met** - Required information, documents, or previous steps must be complete.

- **Permissions determine access** - Your role and permissions control what actions you can take.

- **Workflow order matters** - Actions must happen in the correct order according to workflow rules.

- **Complete requirements** - All requirements must be met before actions are enabled.

- **Check messages** - The platform often shows messages explaining why actions are disabled.

- **Status changes enable actions** - When status changes, new actions may become available.

- **Individual tracking** - Each user's permissions and access are tracked individually.

Understanding enabled vs disabled actions helps you know what you can do, why certain actions aren't available, what needs to happen to enable actions, and how to work effectively within workflow requirements.
