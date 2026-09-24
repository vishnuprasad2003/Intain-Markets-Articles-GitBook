---
title: Asset Sale FAQs
description: Common questions about Asset Sale deals, settlement, repayment, and NFT burn
---

# Asset Sale FAQs

## Overview

Short answers to common Asset Sale questions. For full steps, use the linked articles.

## Frequently Asked Questions

### General

**Q: What is an Asset Sale?**

A: The issuer sells a loan or receivables portfolio to investors. The UI label is Asset Sale; internally it is also called Whole Loan Sale. The path is create → review → commit → settle → repay → close. See [Asset Sale Overview](32_Asset_Sale_Overview.md).

**Q: How is this different from securitization?**

A: Asset Sale transfers the loans themselves. Securitization pools loans and issues tranches. Investors here buy the assets, not a sliced security.

**Q: Who is involved?**

A: **Issuer** creates the deal and records repayment. **Underwriter (Market Maker)** reviews and allocates. **Investor** commits, signs, settles, and burns the NFT. **Servicer** keeps loan tapes current.

### Deal creation and review

**Q: Can I edit after publish?**

A: Not the package. The underwriter must reject the deal back to **Draft**. Then you edit and publish again.

**Q: What if the underwriter rejects the deal?**

A: You get feedback. Revise in Draft and resubmit. The rejected history is kept for audit.

**Q: Can one deal use loans from more than one pool?**

A: Yes. Assign loans one by one or map multiple pools.

### Commitment and allocation

**Q: Can I change my commitment?**

A: Yes, until the underwriter finalizes allocation. After that, amounts are locked.

**Q: What if the deal is over-subscribed?**

A: The underwriter reduces allocations so they fit capacity.

### Settlement

**Q: How do funds move?**

A: **Bank (Wire/ACH)** — wire, upload confirmation, both sides confirm, issuer transfers NFTs after MFA. **Stablecoin** — MetaMask deposits USDC into escrow; delivery is automatic. **Kinexys** is planned. See [Settlement](36_Settlement_and_NFT_Transfer.md).

**Q: What is a receivables NFT?**

A: An on-chain token minted at settlement that proves you own the receivables. After repayment you burn it to close.

### Repayment

**Q: How is the amount set?**

A: From the latest loan tape. On receivables deals you cannot type over the tape total.

**Q: Full vs partial vs default?**

A: Full can close the deal after burn. Partial keeps the deal live for the next installment. Default, once confirmed, is permanent.

**Q: Which rails work for repayment?**

A: Bank wire only. Stablecoin and Kinexys are not enabled for repayment yet.

**Q: What happens after I accept?**

A: On a full repayment, **Burn** appears under Asset Analysis → Receivables. After burn, the deal can close.

### NFT burn and troubleshooting

**Q: Can I undo a burn?**

A: No. Confirm the wire first.

**Q: Why is Initiate Repayment missing?**

A: The deal must be **Active**, and you must be the issuer. It is hidden during settlement or if repayment is already in progress.

**Q: Why can’t I burn?**

A: Accept repayment first. NFT status must be **Retirement pending**.

**Q: The repayment amount looks wrong.**

A: Fix the loan tape and re-map. On receivables deals the amount comes only from the tape.

**Q: Why is the deal Defaulted?**

A: The issuer declared default and you confirmed it. No further repayment can be recorded.
