---
title: Token IDs and Timestamps
description: Comprehensive reference for understanding token identifiers, contract addresses, blockchain timestamps, and transaction hashes in Intain Markets
---

# Token IDs and Timestamps

## Overview

When Intain Markets records tokens — for a credit facility funding notice, or as a loan NFT — it also stores permanent references on the blockchain. You use those references to see which token belongs to which loan or notice, and to confirm that a step really happened. You do not need the technical layout of the token. You need to know where the reference appears on screen and what it proves.

Two kinds of tokens show up in the product. A **funding notice** uses tokens that represent the draw and how it is split across lenders. A **loan** uses an NFT, which is a unique token for that loan. Both are recorded on the blockchain.

## Reference Details

### Contract Addresses

A contract address is the blockchain location of the token record for one notice or one set of loans. On screen, treat it as the token’s home address: it identifies which tokens belong together.

**Funding notice**

When a funding request is approved and the notice moves from **Pending Token Generated** to tokens generated, the platform creates a token record for that notice only. That address is not reused for another notice. It is the reference for the tokens on that draw. The token’s name and short symbol are built from the facility name and the notice, so you can recognize them if you look them up outside the platform.

**Loan NFTs**

Each loan NFT belongs to the token record for its pool or deal and has its own **token ID** inside that record. Together, the address and the token ID point to one loan. A different loan in the same pool has a different token ID.

**Facility**

When a facility is finalized, the platform also records it on the blockchain. The facility stores that address and the transaction reference for the step that registered it. That pair shows the facility was registered, and which transaction did it.

These addresses do not change after they are created. If you need to confirm a token, start from the address shown on the notice, the certificate, or the facility, then use the transaction reference for the specific step.

### Transaction reference

A transaction reference identifies one blockchain step. Every on-chain action in Intain Markets produces one. You can use it to look the step up independently of what the screen says.

| What happened | Where you see the reference | What it proves |
|---------------|----------------------------|----------------|
| Tokens created for a funding notice | The funding notice | The notice’s tokens were created |
| Tokens recorded to a lender | That lender’s row on the notice | That lender’s tokens were delivered |
| A loan NFT created | The loan certificate | The collateral NFT was created |
| Facility registered | The facility | The facility was registered on the blockchain |
| A token approval | The approval record | A party was allowed to move the tokens |
| Settlement or delivery | The settlement record | Escrow or delivery was completed |

The reference is a long code beginning with `0x`. On transaction details it is often a link. Open it to see the step on a blockchain explorer, including who sent it, who received it, and the time the network recorded.

### Block timestamps

A block timestamp is the time the blockchain recorded when the transaction was included. It is set by the network. It is not the same as the time Intain Markets shows from its own clock, and it cannot be edited afterward.

You will see blockchain times for:

- When the funding notice’s tokens were created
- When tokens were recorded to a lender
- When a loan NFT was created
- When a token approval was granted

The screen also shows the platform’s own time for the same event, in UTC. Use the platform time to read the history. Use the blockchain time when you need a time that the platform cannot change.

### Token IDs

A **token ID** is the number that picks out one loan NFT inside its token record.

- Token IDs are assigned as NFTs are minted
- The token record’s address plus the token ID identifies that loan
- Funding-notice tokens do not use a token ID per coin. The notice’s token address identifies the token, and each lender’s balance is the amount recorded to them
- Approving or transferring a loan NFT uses that loan’s token ID

If two loans share an address but have different token IDs, they are different loans. If a funding notice has an address and no token ID, you are looking at the draw’s tokens, not a single loan.

### Per-lender token tracking

When a funding notice reaches tokens generated, each lender has a row. The row shows:

| What you see | What it means |
|--------------|----------------|
| Lender | The lending organization |
| Tokens allocated | How many tokens that lender receives |
| Share | That lender’s portion of the commitment |
| Commitment amount | The amount they committed on the facility |
| Signature | Pending, or signed |
| Approval | Pending, Approved, or Rejected |
| Transfer | In progress until it is completed |
| Transaction reference | The blockchain step that recorded the transfer to this lender |

Each lender moves through signature and payment on their own row. When every lender’s transfer is completed, the notice moves on to tokens transferred.

## Where Token Information Appears

**Credit Facility → funding notice**

- The token address for that notice
- A table of lenders with their amounts, signature, approval, and transaction reference
- When the tokens were created and when they were transferred
- Signature progress, such as E-sign 2 of 3

**Loan certificates**

- The token address and the **token ID** for that loan
- The transaction reference for minting
- How the loan was verified, and the certificate details

**Transaction details (investors)**

- The transaction reference, often as a link
- The token ID when the asset is a loan NFT
- A way to open the same step on a blockchain explorer

**Activity log and the item’s history**

- Creating tokens, transferring them, and approving them appear as actions
- Each line shows who did it, when, and what happened
- The token address and the transaction reference are included when the step was on the blockchain

## Important Notes

**These references do not change.** A token address, a transaction reference, and a token ID stay as they were written. No one, including an administrator, can edit or delete them on the blockchain.

**You can check them outside Intain Markets.** Look up the address or the transaction reference on the blockchain explorer for the network the platform uses. That view shows the time and the parties without relying on the screen alone.

**The network is part of the record.** The platform remembers which network the step used, so a reference from a test environment is not confused with a live one.

**Two clocks.** The platform time is there so people can read the history. The blockchain time is the one that cannot be altered.

**Names follow the facility.** Tokens for a funding notice are named from the facility and the notice, so you can recognize them on the explorer as well as in Credit Facility.
