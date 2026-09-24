---
title: Asset Sale FAQs
description: Frequently asked questions about asset sales, repayment, and related workflows
---

# Asset Sale FAQs

## Overview

This document answers the most common questions about the Asset Sale module, including deal creation, investor participation, settlement, repayment, and troubleshooting. If you have a question about how asset sales work on Intain Markets, you will likely find the answer here.

## Frequently Asked Questions

### General

**Q: What is an asset sale?**

A: An asset sale is a transaction where an issuer sells a portfolio of loans or receivables to investors. On Intain Markets, this is managed through the Asset Sale module (also referred to internally as Whole Loan Sale). The complete workflow covers deal creation, underwriter review, investor commitment, settlement with NFT ownership transfer, and post-sale repayment.

***

**Q: How is an asset sale different from securitization?**

A: In an asset sale, the actual loan assets are transferred directly from the issuer to investors. In securitization, loans are pooled into a special purpose vehicle and sliced into tranches with different risk profiles. Asset sales are simpler structurally — investors purchase the loans themselves rather than tranched securities backed by the loans.

***

**Q: What roles are involved in an asset sale?**

A: Four primary roles participate in asset sales:

* **Issuer**: Creates deals, assigns loans, initiates repayment
* **Underwriter (Market Maker)**: Reviews deals, manages investor allocation
* **Investor**: Commits capital, signs agreements, confirms settlement and repayment
* **Servicer**: Uploads and manages loan tapes throughout the deal lifecycle

***

### Deal Creation and Review

**Q: Can I edit a deal after it has been published?**

A: No. Once a deal is published (submitted for underwriter review), deal fundamentals cannot be edited. If changes are needed after publication, the underwriter would reject the deal, and you would need to create a new deal or revise the rejected one.

***

**Q: What happens if the underwriter rejects my deal?**

A: If the underwriter rejects your deal, you are notified with feedback. You can create a new deal addressing the feedback, with the same or a modified loan portfolio. The rejected deal is retained for audit purposes.

***

**Q: Can I assign loans from multiple pools to a single deal?**

A: Yes. You can assign loans individually or by pool. When assigning by pool, all loans in the selected pool are mapped to the deal. You can also assign individual loans from different pools to create a custom deal portfolio.

***

### Commitment and Allocation

**Q: Can I change my commitment amount after submitting?**

A: You can update your commitment amount before the underwriter finalizes allocation. Once allocation is finalized, commitment amounts are locked and cannot be changed.

***

**Q: What happens if a deal is over-subscribed?**

A: If total investor commitments exceed the deal size, the underwriter manages the allocation to determine how much each investor receives. The underwriter may use pro-rata allocation, priority-based allocation, or custom adjustments to fit within the deal capacity.

***

### Settlement

**Q: How are funds transferred during settlement?**

A: Funds are transferred via bank wire (off-chain transaction). The platform provides settlement details and reference information, but the actual wire transfer happens through your banking channels. Both the investor and issuer confirm the transfer on the platform.

***

**Q: What are receivables NFTs?**

A: After settlement, the platform mints NFTs (Non-Fungible Tokens) on the blockchain that represent investor ownership of the loan receivables. These NFTs serve as immutable proof of ownership and are transferred to investor wallets during settlement.

***

### Repayment

**Q: How is the repayment amount calculated?**

A: The repayment amount is auto-calculated from the latest loan tape uploaded by the issuer. The loan tape reflects actual borrower payments on the underlying loans. The issuer cannot manually override the calculated amount — it is derived from the loan-level data.

***

**Q: What is the difference between full and partial repayment?**

A: A full repayment means the entire outstanding balance of the deal is being repaid, resulting in deal closure. A partial repayment means only a portion of the balance is being repaid, and the deal remains active for future repayment cycles. The type is auto-determined from the loan tape data.

***

**Q: What payment methods are supported for repayment?**

A: Currently, only bank wire (off-chain transaction) is supported for repayment. The issuer transfers funds via bank wire and uploads a wire confirmation document as part of the repayment initiation.

***

**Q: What happens after I confirm repayment receipt?**

A: After confirming receipt, the NFT burn step becomes available. You navigate to Asset Analysis → Receivables, click Burn next to your receivables NFT, and confirm the burn. Once the NFT is burned, the deal status moves to Closed.

***

### NFT Burn

**Q: Can I undo an NFT burn?**

A: No. Burning an NFT is irreversible. The tokenized position is permanently destroyed on the blockchain. Make sure you have confirmed receipt of the repayment before burning.

***

**Q: What happens to the deal after all NFTs are burned?**

A: When all investor NFTs are burned and repayment is confirmed, the deal status changes to Closed. The deal shows as Fully Repaid with 100% repaid. The complete audit trail (settlement → repayment → burn) is permanently preserved.

***

### Troubleshooting

**Q: Why can't I see the Initiate Repayment button?**

A: The Initiate Repayment option is only available on deals in **Active** status. If the deal is in a different status (e.g., Settlement In Progress, Settled, or already in Repayment In Progress), the button will not appear. Also ensure you have the Issuer role for the deal.

***

**Q: Why can't I burn my NFT?**

A: The NFT burn option becomes available only after you have confirmed repayment receipt. Navigate to Investment Operations → Confirm Repayment Receipt first, then return to Asset Analysis → Receivables to burn.

***

**Q: I uploaded a loan tape but the repayment amount looks wrong. What should I do?**

A: The repayment amount is calculated from the loan tape data. If it looks incorrect, check your loan tape file for accuracy. You can re-upload a corrected loan tape and re-map the fields. Contact Intain support if you need assistance preparing the loan tape.

***

**Q: Why is my deal status showing Defaulted?**

A: The Defaulted status indicates that the underlying loan portfolio has encountered a default condition. This is typically set when loan performance metrics fall below the deal's threshold requirements. Contact your counterparties and review the deal's performance analytics for details.
