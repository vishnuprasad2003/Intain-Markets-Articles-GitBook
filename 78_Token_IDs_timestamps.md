---
title: Token IDs and Timestamps
description: >-
  Reference for token identifiers, contract addresses, blockchain timestamps, and transaction hashes in Intain Markets
---

# Token IDs & Timestamps

## Types of References

| Reference | What it is | Where it appears |
|---|---|---|
| **Contract address** | Blockchain location of the token record for a notice or loan set | Funding notice, loan certificate, facility |
| **Transaction reference** | Unique code (starts with `0x`) for one blockchain step | Notice, certificate, settlement record, activity log |
| **Token ID** | Number identifying one loan NFT within its contract | Loan certificate, transaction details |
| **Block timestamp** | Time the blockchain network recorded the transaction | Shown alongside platform UTC time |

## Contract Addresses

- **Funding notice** — one contract address created per notice when tokens are generated; not reused for another notice
- **Loan NFTs** — each loan has a token ID within the pool/deal's contract address; address + token ID = one unique loan
- **Facility** — recorded on-chain when finalized; address + transaction reference show the registration

## Transaction References

Every on-chain action produces a transaction reference you can verify independently.

| Event | Where to find it |
|---|---|
| Tokens created for funding notice | Funding notice |
| Tokens recorded to a lender | That lender's row on the notice |
| Loan NFT minted | Loan certificate |
| Facility registered | Facility details |
| Token approval | Approval record |
| Settlement / delivery | Settlement record |

Open the reference on a blockchain explorer to see who sent it, who received it, and the network-recorded time.

## Per-Lender Token Tracking (Funding Notice)

Each lender has a row on the funding notice showing:

| Column | Meaning |
|---|---|
| Tokens allocated | Number of tokens for this lender |
| Share | Their portion of the commitment |
| Signature | Pending or signed |
| Approval | Pending, Approved, or Rejected |
| Transfer | In progress or completed |
| Transaction reference | Blockchain step for this lender's transfer |

## Two Clocks

- **Platform time (UTC)** — shown in the platform history for readability
- **Block timestamp** — set by the blockchain network; cannot be edited; use this when you need a time the platform cannot alter

## Key Notes

- Contract addresses, transaction references, and token IDs are permanent — no one can edit them on the blockchain
- You can verify any reference on the blockchain explorer for the platform's network
- Funding-notice tokens do not have per-coin token IDs; the notice address identifies the draw and each lender's balance is the amount recorded to them
