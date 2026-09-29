---
title: Securitization Deal Lifecycle & Statuses
description: Deal statuses, lifecycle progression, tranche approval statuses, and commit/invest phases in Securitization on Intain Markets.
---

# Securitization Deal Lifecycle & Statuses

A securitization deal moves through four statuses. The deal is automatically created when the Underwriter accepts the pool mandate — it is never created manually by a button click.

---

## Deal Lifecycle

```
Created → Awaiting Approval → Open → Closed
```

| Status | What It Means | Who Acts |
|--------|--------------|----------|
| **Created** | Pool mandate accepted; Underwriter is setting up the deal — modeling tranches, assigning investors — via the Tools tab. | Underwriter sets up tranches and publishes to Issuer when ready. |
| **Awaiting Approval** | Underwriter has published the deal to the Issuer for review. No further edits by the Underwriter until the Issuer acts. | Issuer reviews the tranche structure, terms, and investor assignments. Issuer publishes to investors when satisfied. |
| **Open** | Issuer has published the deal to investors. The deal is live. Underwriter manages Commit and Invest phases. | Investors view, commit, and invest. Paying Agent delivers FTs. |
| **Closed** | Deal is closed. No new investment activity. | Read-only for all roles. |

![Deal details page — shows current status and deal fields](images/89-securitization-deal-lifecycle/deal-status-view.png)
*Deal details page — current status, deal name, and key fields*

---

## Tranche Approval Statuses

Each tranche tracks its own approval status independently from the deal:

| Status | Meaning |
|--------|---------|
| **Pending** | Tranche created; Issuer has not yet approved the FT contract. |
| **Approved** | Issuer has approved the FT contract. Investors can commit; Paying Agent can deliver FTs. |
| **Rejected** | FT contract approval was rejected. Tranche cannot receive commitments. |

Tranches must be **Approved** before investors can commit to them.

---

## Commit Phase vs Invest Phase

The Underwriter controls two sub-phases within an **Open** deal:

### Commit Phase

- Underwriter opens the Commit phase after the deal is published to investors.
- Investors commit amounts to tranches — **no funds transfer** in this phase.
- Available Commitments on each tranche decreases as investors commit.
- Investors can only commit once per tranche.

### Invest Phase

- Underwriter switches from Commit to Invest when ready to collect funds.
- **Payment mode is set at this point** (offchain or onchain — cannot be changed after).
- Investors click a **single Invest button** to invest in all their committed tranches at once.
- **Offchain:** Investor pays via bank wire → Paying Agent sees the pending payment → approves it → FTs are delivered.
- **Onchain:** Investor transfers USDC via MetaMask → FT transfer happens automatically on-chain.

> The deal cannot revert from Invest phase to Commit phase. The payment mode is fixed once set.

---

## Payment Mode

| Mode | How Payment Works | When FTs Are Delivered |
|------|------------------|----------------------|
| **Offchain** | Investor makes a bank wire transfer | After Paying Agent approves the payment |
| **Onchain** | Investor transfers USDC via MetaMask to the escrow contract | Automatically after on-chain confirmation |

The payment mode applies to all investors in the deal — it cannot be set per investor.

---

## Deal Lifecycle Flow

```
Pool (mandate accepted)
    ↓ auto-converted
Created → Underwriter sets up deal in Tools tab
    ↓ Underwriter publishes
Awaiting Approval → Issuer reviews deal
    ↓ Issuer publishes to investors
Open
  → Underwriter opens Commit phase → Investors commit
  → Underwriter switches to Invest phase → Investors invest (single button)
  → Paying Agent confirms payments → FTs delivered
    ↓
Closed
```

---

## Related Articles

→ See [Deal Creation & Tranche Setup](90_Deal_Creation_and_Tranche_Setup.md) for how the Underwriter builds the deal in the Tools tab.  
→ See [Investor Commitment Phase](91_Investor_Commitment_Phase.md) for investor actions in the Commit phase.  
→ See [Investment & Settlement](92_Investment_and_Settlement.md) for the Invest phase and payment flows.
