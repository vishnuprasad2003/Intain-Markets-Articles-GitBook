---
title: Securitization Overview
description: Overview of the Securitization module on Intain Markets — how pools become structured deals, how tranches work, and what each role does.
---

# Securitization Overview

Securitization on Intain Markets converts a pool of loans into a structured deal with multiple investment tranches. Each tranche receives its own Fungible Token (FT) on the Avalanche blockchain, representing fractional ownership of that tranche's principal balance.

Securitization is one of four product lines alongside **Credit Facilities**, **Asset Sale**, and **Participation Agreements**.

---

## End-to-End Workflow

1. **Asset Onboarding** — Issuer creates a Securitization pool and uploads loans via the Asset Registry
2. **Preview** — Underwriter and Investors can preview the pool before mandate acceptance
3. **Mandate Acceptance** — Issuer submits pool to Underwriter; Underwriter accepts → pool is **automatically converted to a Deal**
4. **Deal Setup (Tools tab)** — Underwriter opens the deal → uses the **Tools tab** to model tranches, set deal terms, and assign investors
5. **Publish to Issuer** — Underwriter publishes the deal; Issuer reviews tranche structure and terms
6. **Publish to Investors** — Issuer approves and publishes the deal; deal goes **Open** and investors can view it
7. **Investor Commitment** — Underwriter opens the Commit phase; Investors commit amounts to individual tranches (no funds move)
8. **Invest Phase** — Underwriter switches to Invest phase; Investors click a **single Invest button** to invest in all their committed tranches at once and make payment
9. **Payment Settlement** — Onchain: USDC + FT transfer happen automatically. Offchain: Investor pays via bank transfer → Paying Agent approves the payment → FTs are delivered
10. **Token Approval** — Issuer approves the FT contract per tranche (MFA + on-chain wallet signing)
11. **FT Delivery** — Paying Agent delivers FT tokens to investors (MFA required)
12. **Ongoing Reporting** — Servicer uploads monthly loan tapes; Investors view monthly portfolio and loan performance reports

![Securitization module — deals list for Issuer](images/88-securitization-overview/securitization-section.png)
*Securitization deals list — Issuer view showing deal IDs, statuses, and tranche counts*

---

## Key Concepts

| Concept | Description |
|---------|-------------|
| **Tranche** | A class of investment in the deal (e.g., Senior, Mezzanine). Each tranche has its own principal balance, interest rate, and FT token. |
| **Fungible Token (FT)** | An ERC-20 token on Avalanche — one per tranche. Holding FTs represents ownership of that tranche's principal. Symbol: 2 letters Issuer + 2 chars Deal + 2 letters Tranche (e.g., `PI98SE`). |
| **Commit Phase** | Investors declare how much they want in each tranche. No funds transfer yet. |
| **Invest Phase** | Investors confirm investment with a single button and transfer funds (bank wire or USDC). |
| **Payment Mode** | Offchain (bank wire) or Onchain (USDC via MetaMask). Selected by Underwriter when switching to Invest phase — applies to all investors in the deal. |
| **Tools Tab** | The Underwriter's workspace within a deal for modeling tranches, assigning investors, and managing deal terms. |

---

## Roles in Securitization

| Role | Key Actions |
|------|------------|
| **Issuer** | Creates pool → onboards loans → reviews deal → approves FT contract (MFA + on-chain) |
| **Underwriter** | Accepts mandate → sets up deal via Tools tab → assigns investors → publishes to Issuer → opens Commit/Invest phases |
| **Investor** | Previews pool → views deal → commits to tranches → invests (single button) → receives FT tokens |
| **Paying Agent** | Approves offchain payments → delivers FT tokens (MFA required) → manages accounts and ledger |
| **Servicer** | Uploads monthly loan tapes post-close |
| **Rating Agency** | Read-only access to pool and deal information |

---

## Payment Modes

| Mode | How It Works |
|------|-------------|
| **Offchain** | Investor transfers via bank wire → Paying Agent sees the pending payment → Paying Agent approves → FTs are delivered |
| **Onchain** | Investor connects MetaMask → transfers USDC to the deal's smart contract → FT transfer happens automatically on-chain |

---

## Related Articles

→ See [Deal Lifecycle & Statuses](89_Securitization_Deal_Lifecycle_and_Statuses.md) for deal status definitions and phase transitions.  
→ See [Deal Creation & Tranche Setup](90_Deal_Creation_and_Tranche_Setup.md) for how the deal is built after mandate acceptance.  
→ See [Securitization Roles & Permissions](95_Securitization_Statuses_and_Roles.md) for a full permissions reference.
