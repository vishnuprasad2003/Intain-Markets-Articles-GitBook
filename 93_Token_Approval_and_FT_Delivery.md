---
title: Token Approval & FT Delivery
description: How Issuers approve Fungible Token (FT) contracts and how Paying Agents deliver FTs to investors in a Securitization deal on Intain Markets.
---

# Token Approval & FT Delivery

Each securitization tranche has its own ERC-20 Fungible Token (FT) deployed on the Avalanche blockchain at tranche creation. Before FTs can be delivered to investors, two steps must complete: the **Issuer approves the FT contract**, then the **Paying Agent delivers the tokens**.

---

## What is the Fungible Token (FT)?

- An ERC-20 token on the Avalanche L1 subnet
- One FT contract per tranche in the deal
- Token symbol: 2 letters (Issuer abbrev.) + 2 chars (Deal abbrev.) + 2 letters (Tranche abbrev.), e.g., `PI98SE`
- Token name: `{Issuer Organization} Securitization Token`
- FTs represent ownership of the tranche's principal — holding FTs entitles the investor to principal and interest payments

---

## Step 1: Issuer FT Contract Approval

Before the Paying Agent can deliver FTs to investors, the Issuer must authorize the FT contract.

**Who:** Issuer  
**When:** After at least one investor has completed investment in a tranche  
**Required:** MFA (one-time password) + on-chain wallet signing

### Process

1. Navigate to **Securitization** → open the deal → find the tranche
2. Click **Approve Token** on the tranche
3. Enter your **MFA code** when prompted
4. Your connected wallet will request a signature for `approve(adminAddress, totalSupply)` on the FT contract
5. Confirm the transaction in your wallet
6. The FT contract status updates to Approved

> ⚠️ **Important:** This is an **on-chain transaction** — it requires your issuer wallet to have sufficient AVAX for gas fees. The approval grants the Intain Markets admin contract the ability to transfer FTs on behalf of the deal.

This step must be completed **once per tranche**. If a deal has 3 tranches, the Issuer must approve each tranche's FT contract separately.

---

## Step 2: Paying Agent FT Delivery

After the Issuer has approved the FT contract, the Paying Agent delivers tokens to investors.

**Who:** Paying Agent  
**When:** After Issuer approves the FT contract — and, for offchain deals, after the Paying Agent has already approved the investor's payment  
**Required:** MFA (one-time password)

> **Offchain deals:** FTs are delivered **after** the Paying Agent approves the investor's bank wire payment. Approval of the payment and delivery of FTs are two separate steps.  
> **Onchain deals:** FTs transfer automatically with the USDC payment. The Paying Agent delivery step is not required.

### Process

1. Navigate to **Securitization** → open the deal → select the tranche
2. Click **Deliver FTs**
3. Choose delivery scope:
   - **Deliver to all investors** — delivers FTs to every investor who has invested in this tranche
   - **Deliver to one investor** — select a specific investor by organization
4. Enter your **MFA code** when prompted
5. Confirm delivery

The platform transfers FT tokens proportional to each investor's invested amount. Investors can see their FT balance after delivery.

---

## What Investors See After FT Delivery

Once FTs are delivered to their wallet:
- The investor can view their FT token balance in the deal details
- FTs appear in the investor's connected blockchain wallet (MetaMask or compatible)
- The token balance reflects the principal amount invested in the tranche

---

## FT Delivery Status

| Status | Meaning |
|--------|---------|
| **Pending** | FT contract deployed but Issuer has not yet approved |
| **Approved** | Issuer approved the FT contract; Paying Agent can deliver |
| **Delivered** | FTs have been successfully transferred to investors |

---

## Rules & Validations

- FT approval requires a valid MFA code — invalid codes are rejected
- FT delivery requires a valid MFA code from the Paying Agent
- The Issuer wallet must have AVAX for gas fees on the approval transaction
- FTs can only be delivered after the Issuer approval is confirmed on-chain
- Delivery to a specific investor requires the investor's organization to have completed investment

---

## Related Articles

→ See [Investment & Settlement](92_Investment_and_Settlement.md) for the investor investment flow before FT delivery.  
→ See [Accounts & Transactions](94_Accounts_and_Transactions.md) for how Paying Agents track fund flows.  
→ See [Securitization Roles & Permissions](95_Securitization_Statuses_and_Roles.md) for MFA requirements by role.
