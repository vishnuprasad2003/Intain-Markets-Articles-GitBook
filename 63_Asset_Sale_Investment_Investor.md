---
title: Asset Sale Investment
description: How an investor reviews, commits, signs, and settles an Asset Sale deal
---

# Asset Sale Investment

## Overview

This is the investor path from a published deal through settlement: review the package, submit a commitment, sign the agreement, send funds, and receive the receivables NFT. You do not create the deal, assign loans, or allocate other investors. Those actions belong to the issuer and underwriter. Your path is review → commit → sign → settle → hold the NFT. Skip a step and the next button stays disabled until that earlier required gate is fully finished. Repayment and burn are a later stage — see the link at the end.

## Who Can Use This

- **Investors**

You only see deals from **Published** onward, and only if Buyer Visibility includes you (**All** or **Selected**). If a colleague can see a deal and you cannot, you are likely outside the Selected list — ask the issuer or underwriter, do not assume a platform error.

## When This Is Used

Use this when a deal is **Published**, **Commit**, **Invest**, or in settlement and you are the buyer.

## Step-by-Step Process

### Review

Open **Asset Sale**, select the deal, and review the summary, loan list, sale terms (price, dates, recourse), and documents. Check servicing setup and whether the sale is Marketed or Bilateral. Use **Asset Analysis** if you need stratifications or risk checks before you commit.

![Investor Asset Sale View](images/63-asset-sale-investment-investor/investor-asset-sale.png)

### Commit

Enter your amount and click **Submit**. You can change it until the underwriter finalizes allocation. If the deal is over-subscribed, your final amount may be lower than you submitted. You are notified when the deal moves to **Invest**.

### Sign

Open the investor agreement from deal details. Sign in Adobe Sign inside the platform (no separate Adobe account), or wait if the issuer is uploading a signed PDF. Status must become **Signed**. Signing is blocked unless the deal is **Invest**.

### Settle

1. When the deal is **Settlement In Progress**, open Confirm and Settle and use the selected rail.
2. **Bank (Wire/ACH)** — send the wire for your allocated amount, upload the confirmation, click **Confirm Payment**. The issuer then confirms receipt and starts NFT transfer (MFA on their side).
3. **Stablecoin** — connect the MetaMask account that matches your verified settlement address, approve USDC, and deposit into escrow. Delivery is automatic if the wallet and network are correct.
4. After NFTs arrive, the deal is **Active**. Your position is on-chain.

## Rules & Validations

- Only **Published** / **Commit** deals accept new commitments.
- One commitment per deal; locked after allocation.
- Bank wire needs both your confirmation and the issuer’s receipt confirmation.
- Stablecoin needs a verified wallet and enough USDC plus gas.
- After NFT transfer, settlement is not reversed from the UI.
- Your MetaMask account must match the verified settlement address. A different account will be rejected.

### If a step is missing

No **Submit** on commitment usually means the deal is not Published/Commit or the commit window ended. No signing action means the deal is not **Invest** or you are not the selected investor. No settle action means the agreement is still **Not Signed**.

## What Happens Next

The issuer may upload loan tapes on the Active deal. When they record repayment, use [Repayment Receipt & NFT Burn](64_Repayment_Receipt_and_NFT_Burn_Investor.md). Keep wire confirmations until the deal is **Active**. If NFT transfer is delayed on a bank settlement, the issuer still needs to complete MFA and start the transfer — you cannot mint the token yourself.

Settlement rails: [Settlement & NFT Transfer](36_Settlement_and_NFT_Transfer.md).
