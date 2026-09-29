---
title: Investment & Settlement
description: How investors transfer funds and complete their investment in the Invest phase of a Securitization deal, covering both offchain (bank wire) and onchain (stablecoin) payment modes.
---

# Investment & Settlement

The Invest phase is when investors transfer actual funds and confirm their investment in a securitization tranche. The Underwriter switches the deal from Commit to Invest phase and selects the payment mode — this choice applies to all investors in the deal.

---

## Switching to Invest Phase

**Who:** Underwriter  
**When:** After collecting sufficient investor commitments in the Commit phase

1. Navigate to the deal details page
2. Click **Switch to Invest Phase**
3. Select the **Payment Mode**:
   - **Offchain** — investors wire funds via traditional bank transfer
   - **Onchain** — investors transfer USDC stablecoin via MetaMask wallet
4. Confirm the switch

> ⚠️ **Important:** The payment mode cannot be changed after switching to Invest phase. All investors in the deal use the same payment method.

---

## Investor Actions in Invest Phase

### Offchain (Bank Wire) Flow

Investors who committed during the Commit phase now transfer funds via bank wire:

1. Obtain the wire transfer details from the deal page
2. Initiate the bank wire from your financial institution
3. Return to Intain Markets → navigate to the deal → click **Invest**
4. In the Invest modal:
   - Enter the **Wire Reference Number**
   - Upload your **Payment Confirmation Document**
5. Click **Confirm & Invest**

The Paying Agent reviews the wire reference and confirmation document before the investment is marked complete. After confirmation, the Paying Agent delivers FT tokens.

### Onchain (Stablecoin) Flow

Investors use a MetaMask wallet to transfer USDC directly to the deal's escrow contract:

1. Open the deal in Invest phase → click **Invest**
2. Connect your MetaMask wallet when prompted
3. Review the USDC amount to transfer (equals your committed amount)
4. Confirm the USDC transaction in MetaMask
5. The on-chain transaction is recorded automatically
6. Click **Invest** to confirm your investment on Intain Markets

The blockchain transaction is verified before marking the investment complete.

![Investor deal view — showing invest options](images/92-investment-and-settlement/investor-deals-view.png)
*Investor view of a securitization deal in Invest phase*

---

## Settlement Record

A settlement record is created for each investor-tranche combination when the investor clicks **Invest**. This record tracks:

- The tranche invested in
- The amount invested
- The payment mode used
- The date of confirmation
- The status (Pending → Completed)

After investment is confirmed, the **Invested Amount** on the tranche is updated. The tranche's Invested Amount reflects the total from all investors who have completed their investment.

---

## After Investment: FT Delivery

Once investment is confirmed, FT tokens are not automatically delivered — they require the following:

1. **Issuer approves the FT contract** for each tranche (MFA required + wallet signing)
2. **Paying Agent delivers FTs** to each investor (MFA required)

Each investor receives FT tokens proportional to their invested amount.

→ See [Token Approval & FT Delivery](93_Token_Approval_and_FT_Delivery.md) for the full FT delivery workflow.

---

## Rules & Validations

- Investors can only invest up to their committed amount — no investing more than what was committed
- Wire reference and confirmation document are required for offchain investments
- MetaMask wallet must hold sufficient USDC balance for onchain investments
- The deal must be in Invest phase — investing is blocked in Commit phase or any other status
- Investors who did not commit in the Commit phase cannot invest

---

## Related Articles

→ See [Investor Commitment Phase](91_Investor_Commitment_Phase.md) for the prior Commit phase.  
→ See [Token Approval & FT Delivery](93_Token_Approval_and_FT_Delivery.md) for what happens after investment.  
→ See [Deal Lifecycle & Statuses](89_Securitization_Deal_Lifecycle_and_Statuses.md) for payment mode details.
