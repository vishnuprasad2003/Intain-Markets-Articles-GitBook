---
title: Asset Sale FAQs
description: Common questions about Asset Sale deals, settlement, repayment, and NFT burn
---

# Asset Sale FAQs

Short answers to common Asset Sale questions. For full steps, use the linked articles.

## General

**Q1. What is an Asset Sale?**
The issuer sells a loan or receivables portfolio to investors. The UI label is Asset Sale; internally it is also called Whole Loan Sale. The path is create → review → commit → settle → repay → close.
→ See [Asset Sale Overview](32_Asset_Sale_Overview.md)

**Q2. How is this different from securitization?**
Asset Sale transfers the loans themselves. Securitization pools loans and issues tranches. Investors here buy the assets, not a sliced security.
→ See [Asset Sale Overview](32_Asset_Sale_Overview.md)

**Q3. Who is involved?**
**Issuer** creates the deal and records repayment. **Underwriter** reviews and allocates. **Investor** commits, signs, settles, and burns the NFT. **Servicer** keeps loan tapes current.
→ See [User Roles & Responsibilities](02_User_Roles_and_Responsibilities.md)

## Deal creation and review

**Q4. Can I edit after publish?**
Not the package. The underwriter must reject the deal back to **Draft**. Then you edit and publish again.
→ See [Deal Creation & Publishing](34_Deal_Creation_and_Publishing.md)

**Q5. What if the underwriter rejects the deal?**
You get feedback. Revise in Draft and resubmit. The rejected history is kept for audit.
→ See [What Happens After Rejection](72_What_happens_after_rejection.md)

**Q6. Can one deal use loans from more than one pool?**
Yes. Assign loans one by one or map multiple pools. Use **Assets** or **Pools** tab in the deal wizard.
→ See [Deal Creation & Publishing](34_Deal_Creation_and_Publishing.md)

## Commitment and allocation

**Q7. Can I change my commitment?**
Yes, until the underwriter finalizes allocation. After that, amounts are locked.
→ See [Investor Commitment & Allocation](35_Investor_Commitment_and_Allocation.md)

**Q8. What if the deal is over-subscribed?**
The underwriter reduces allocations so they fit capacity. You will be notified of your locked amount after **Finalize Allocation**.
→ See [Asset Sale Review & Allocation](56_Asset_Sale_Review_and_Allocation.md)

## Settlement

**Q9. How do funds move?**
**Bank (Wire/ACH)** — wire, upload confirmation, both sides confirm, issuer transfers NFTs after MFA. **Stablecoin** — MetaMask deposits USDC into escrow; delivery is automatic. **Kinexys** is planned.
→ See [Settlement & NFT Transfer](36_Settlement_and_NFT_Transfer.md)

**Q10. What is a receivables NFT?**
An on-chain token minted at settlement that proves you own the receivables. After repayment you burn it to close the position.
→ See [NFT Burn](38_Receivables_and_NFT_Burn.md)

## Repayment

**Q11. How is the repayment amount set?**
From the latest loan tape. On receivables deals you cannot type over the tape total — the amount is calculated automatically.
→ See [Repayment Flow](37_Repayment_Flow.md)

**Q12. What is the difference between full, partial, and default?**
Full can close the deal after burn. Partial keeps the deal live for the next installment. Default, once confirmed by the investor, is permanent and cannot be reversed.
→ See [Repayment Flow](37_Repayment_Flow.md)

**Q13. Which rails work for repayment?**
Bank wire only. Stablecoin and Kinexys are not enabled for repayment yet.
→ See [Repayment Flow](37_Repayment_Flow.md)

**Q14. What happens after the investor accepts repayment?**
On a full repayment, **Burn** appears under Asset Analysis → Receivables. After burn, the deal can close.
→ See [NFT Burn](38_Receivables_and_NFT_Burn.md)

## NFT burn and troubleshooting

**Q15. Can I undo a burn?**
No. NFT burn is irreversible. Confirm the wire and repayment details before burning.
→ See [NFT Burn](38_Receivables_and_NFT_Burn.md)

**Q16. Why is Initiate Repayment missing?**
The deal must be **Active**, and you must be the issuer. It is hidden during settlement or if repayment is already in progress.
→ See [Repayment Flow](37_Repayment_Flow.md)

**Q17. Why can't I burn the NFT?**
Accept repayment first. NFT status must be **Retirement pending** before the Burn button appears.
→ See [NFT Burn](38_Receivables_and_NFT_Burn.md)

**Q18. The repayment amount looks wrong.**
Fix the loan tape and re-map. On receivables deals the amount comes only from the tape — you cannot override it manually.
→ See [Repayment Flow](37_Repayment_Flow.md)

**Q19. Why is the deal Defaulted?**
The issuer declared default and the investor confirmed it. No further repayment can be recorded. The status is permanent.
→ See [Repayment Flow](37_Repayment_Flow.md)
