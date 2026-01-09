---
title: Term Sheet Change Requests
description: Learn how to respond to change requests on term sheets
---

# Term Sheet Change Requests

## Overview

When a facility agent reviews a term sheet, they may request changes before approving it. This guide explains how borrowers respond to change requests by editing, re-signing, and resubmitting their term sheets.

## Who Can Use This

- **Borrowers**: Edit and resubmit term sheets when changes are requested

## When This Is Used

Use this process when:
- Your term sheet status shows **CHANGES_REQUESTED**
- The facility agent has requested modifications to your term sheet
- You need to update and resubmit your term sheet

## Step-by-Step Process

### Step 1: Review the Change Request

1. **Check Dashboard**
   - Navigate to Credit Facility section
   - Find your term sheet with status **CHANGES_REQUESTED**
   - The Action column shows **Edit Term Sheet**

2. **Understand What Needs to Change**
   - Review the change request details provided by the facility agent
   - Note what specific changes are requested
   - Understand the reasoning if provided

![Review Changes Requested - Issuer](imagesByMdFilesFolder/17/ReviewChangesRequestedIssuer.png)

### Step 2: Edit the Term Sheet

1. **Click Edit Term Sheet**
   - Click the **Edit Term Sheet** action
   - The term sheet opens for editing

2. **Make Requested Changes**
   - Update the fields as requested by the facility agent
   - Modify financial terms if needed (amount, rate, etc.)
   - Upload new or revised documents if required
   - Address all requested changes

### Step 3: Update and Re-sign

1. **Click Update**
   - After making all changes, click **Update**
   - An Adobe Sign popup window opens automatically

2. **Complete E-Signature**
   - Review the updated term sheet document
   - Complete the electronic signature process
   - Status changes to **BorrowerSigned**

### Step 4: Resubmit to Facility Agent

1. **Submit Term Sheet Popup Appears**
   - After signing, the **Submit to FA** popup appears
   - Review the submission details

2. **Click Submit**
   - Click **Submit** to resubmit the updated term sheet
   - Status changes from **BorrowerSigned** to **FAReview**
   - Facility agent receives notification

![Submit Term Sheet to FA](imagesByMdFilesFolder/17/SubmitTermSheetToFA.png)

### Step 5: Await Review

1. **Monitor Status**
   - The facility agent reviews your updated term sheet
   - Possible outcomes:
     - **Approved**: Status changes to Accepted, master commitment created
     - **Rejected**: Status changes to Rejected (create new term sheet)
     - **Changes Requested Again**: Repeat the process

## Change Request Flow

```
CHANGES_REQUESTED → Edit Term Sheet → Update → Sign (Adobe Sign) → Submit → FAReview
```

The facility agent may:
- Approve → Accepted → Master commitment created
- Reject → Rejected (final)
- Request more changes → CHANGES_REQUESTED (repeat process)

## Rules & Validations

- **Only CHANGES_REQUESTED Can Edit**: You can only edit term sheets when they're in CHANGES_REQUESTED status.

- **Re-signing Required**: Every time you update a term sheet, you must sign it again via Adobe Sign.

- **Submit After Signing**: You must submit the term sheet after signing for the facility agent to review.

- **Multiple Rounds Possible**: The facility agent may request changes multiple times before approving.

- **Address All Changes**: Make sure to address all requested changes before resubmitting.

## What Happens Next

**After Resubmitting:**
- Facility agent reviews your updated term sheet
- You receive notification of the decision

**If Approved:**
- Status changes to Accepted
- Master commitment is automatically created
- Facility configuration proceeds

**If Rejected:**
- Status changes to Rejected (final state)
- You need to create a new term sheet

**If More Changes Requested:**
- Status changes back to CHANGES_REQUESTED
- Repeat the edit, sign, and submit process
