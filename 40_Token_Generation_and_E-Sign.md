---
title: Funding Notice Processing (FA)
description: Learn how facility agents process funding notices with approval and e-signatures
---

# Funding Notice Processing (Facility Agent)

## Overview

After a funding request is approved, a funding notice is automatically generated. The facility agent then processes the funding notice by approving it and e-signing for each lender individually. As each e-sign is completed, that lender can see the funding notice.

## Who Can Use This

- **Facility Agents** who process funding notices

## When This Is Used

Use this process when:
- You have approved a funding request
- A funding notice has been generated (Pending Token Generated)
- You need to make the funding notice visible to lenders

## Step-by-Step Process

### Step 1: Access the Funding Notice

1. **Navigate to Credit Facility**
   - Log in with your Facility Agent credentials
   - From the left expandable menu, click on **Credit Facility**
   - Go to the **Active Facilities** tab

2. **Find the Funding Notice**
   - Locate the funding notice under the relevant master commitment
   - Status shows **Pending Token Generated**

### Step 2: Approve the Funding Notice

1. **Click Approve**
   - Click **Approve** on the funding notice
   - This prepares the notice for e-signatures

### Step 3: E-Sign for Each Lender

1. **View E-Sign Status**
   - After approval, the action shows **E-sign (0/n)** where n = number of lenders
   - Example: E-sign (0/3) means 3 lenders, none signed yet

2. **Sign for First Lender**
   - Click E-sign
   - Adobe Sign popup opens
   - Complete the electronic signature for this lender
   - Count updates to (1/n)

![FA - Funding Notice Save - Token Generation](imagesByMdFilesFolder/40/FA_FundingNotice_Save_TokenGeneration.png)

3. **Sign for Remaining Lenders**
   - Click E-sign again
   - Sign for the next lender
   - Repeat for each lender
   - Count progresses: (1/n) → (2/n) → (n/n)
   - Each lender can see the funding notice once their e-sign is completed

4. **E-Signs Complete**
   - When count shows (n/n), all lenders have been signed for
   - Each lender has visibility to the funding notice

### E-Sign Progress Tracking

| E-Sign Status | Meaning |
|---------------|---------|
| E-sign (0/3) | No lenders signed yet (3 total) |
| E-sign (1/3) | Signed for 1 lender |
| E-sign (2/3) | Signed for 2 lenders |
| E-sign (3/3) | All lenders signed |

### Lender Visibility

1. **Individual Lender Access**
   - Each lender sees the funding notice once the FA has e-signed for them
   - Lenders see it in their **Credit Facility** section
   - Action shows **Review Funding Notice** for lenders

2. **Lender Process**
   - Lenders review the funding notice
   - Lenders select payment method
   - Lenders transfer funds
   - Lenders click **Confirm and Settle**

3. **Completion**
   - Tokens are transferred
   - Borrower receives the funds

## Rules & Validations

- **Approve Before E-Sign**: You must approve the funding notice before e-signing.

- **Sign Per Lender**: You sign for each lender individually via Adobe Sign.

- **Individual Visibility**: Each lender sees the funding notice once their e-sign is complete.

- **Individual Tracking**: Each lender's e-signature status is tracked separately.

## What Happens Next

**After E-Signs:**
- Each lender can see their funding notice once signed for
- Lenders review and transfer funds
- Lenders click Confirm and Settle
- Tokens transferred to borrower
- Drawdown complete
