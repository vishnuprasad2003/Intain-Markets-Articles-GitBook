---
title: Token IDs and Timestamps
description: Comprehensive reference for understanding token identifiers, contract addresses, blockchain timestamps, and transaction hashes in Intain Markets
---

# Token IDs and Timestamps

## Overview

Every financial transaction on Intain Markets that involves tokens — whether fungible tokens (FT) for credit facility funding notices or non-fungible tokens (NFT) for loan-level collateral — is anchored to the blockchain with a set of permanent, verifiable identifiers. Understanding these identifiers is essential for audit, compliance, and independent verification. This article explains what each identifier means, where it comes from, and how to look it up.

## Reference Details

### Contract Addresses

A **contract address** is the on-chain location of a deployed smart contract. In Intain Markets, contract addresses appear in two main contexts:

**Fungible Token (FT) Contract Address (`ftContractAddress`)**

When a funding request is approved and the funding notice transitions from `PENDING_TOKEN_GENERATION` to `TOKEN_GENERATED`, the platform deploys a new ERC-20 fungible token contract on the Avalanche C-Chain. The resulting address — stored as `ftContractAddress` on the funding notice — is unique to that specific funding notice and never reused. This address is the definitive on-chain reference for the tokens associated with that drawdown.

- Each funding notice receives its own dedicated FT contract
- The FT contract name and symbol are generated automatically using the facility name and funding notice identifier (via `buildCreditFacilityFtTokenName` and `buildCreditFacilityFtSymbol` utilities)
- Once deployed, the contract address is permanent and immutable

**NFT Contract Address (`tokenContract`)**

For loan-level collateral, NFTs (ERC-721 tokens) are minted against a contract that represents the pool or deal. Each NFT carries a unique `tokenId` within that contract. The combination of `tokenContract` + `tokenId` uniquely identifies a specific loan's on-chain representation.

**Credit Facility Blockchain Deal Contract**

When a master commitment is finalized, the platform registers the facility on-chain by calling the `ScfDeal` contract. The resulting contract address and transaction hash are stored in the master commitment's `chain` field: `{ contract: contractAddress, txHash: transactionHash, chainId: chainId }`.

### Transaction Hashes (`transactionHash` / `txHash`)

A **transaction hash** is a unique identifier for a specific blockchain transaction. Every on-chain write operation in Intain Markets produces a transaction hash that can be used to verify the operation independently on a block explorer.

Transaction hashes are recorded at several points in the workflow:

| Event | Where the Hash Is Stored | What It Proves |
|-------|--------------------------|----------------|
| FT contract deployment | Funding notice record | Token contract was deployed |
| FT token transfer to lender | Lender's token distribution entry | Tokens were delivered to the lender |
| NFT minting | Loan certificate record | Collateral NFT was created |
| Master commitment registration | Master commitment `chain.txHash` | Facility was registered on-chain |
| ERC-20 approval | Approval transaction record | Spender was authorized |
| Settlement lock/transfer | Settlement record | Escrow or delivery completed |

Each hash follows the Ethereum-standard 66-character hexadecimal format (e.g., `0x5d941bc5effe6edef1...521f`) and can be searched on the Avalanche C-Chain block explorer to view the full transaction details, including sender, receiver, gas used, and block number.

### Block Timestamps (`blockTimestamp`)

A **block timestamp** is the time recorded by the blockchain when a transaction is included in a block. Unlike application-level timestamps (which come from the server clock), block timestamps are set by the network validators and cannot be altered after the fact.

Block timestamps are used in Intain Markets to provide tamper-proof evidence of when key events occurred:

- **Token creation time** — when the FT contract was deployed
- **Token transfer time** — when tokens were delivered to a specific lender
- **NFT mint time** — when a collateral NFT was created for a loan
- **Approval time** — when a token approval was granted on-chain

The platform stores both the application-level timestamp (e.g., `createdAt`, `updatedAt` using `DateUtils.nowUTC()`) and the blockchain timestamp. For audit purposes, the blockchain timestamp is the authoritative record.

### Token IDs (`tokenId`)

A **token ID** is a unique numeric identifier within an NFT contract. In the ERC-721 standard, each token within a contract has a distinct `tokenId`. In Intain Markets:

- NFT token IDs are assigned sequentially during minting
- The combination of `tokenContract` (contract address) and `tokenId` forms a globally unique identifier
- For ERC-20 fungible tokens, the concept of `tokenId` does not apply — the entire balance is tracked per wallet address, and the FT contract address is the identifier
- Token IDs are used during approval (`getApproved(tokenId)`) and transfer operations

### Per-Lender Token Tracking

When a funding notice reaches `TOKEN_GENERATED` status, the `tokenDistribution` array contains one entry per lender with the following tracked fields:

| Field | Description |
|-------|-------------|
| `lenderOrgId` | Organization identifier of the lender |
| `lenderName` | Display name of the lending organization |
| `tokensAllocated` | Number of tokens allocated to this lender |
| `participationPercentage` | Lender's share of the total commitment |
| `commitmentAmount` | Lender's commitment amount in the facility |
| `esignatureStatus` | E-signature status: `pending` or `ESIGN_COMPLETED` |
| `lenderApprovalStatus` | Approval status: `PENDING`, `APPROVED`, or `REJECTED` |
| `mintingStatus` | FT transfer status: tracked until `completed` |
| `transactionHash` | Blockchain hash of the FT transfer to this lender |

Each lender's entry is updated independently as they progress through the e-signature and fund transfer steps. When all lenders have `mintingStatus: 'completed'`, the funding notice transitions to `TOKEN_TRANSFERRED`.

## Where Token Information Appears

**Credit Facility → Funding Notice Details**
- FT contract address (`ftContractAddress`)
- Token distribution table with per-lender allocations, statuses, and transaction hashes
- Token generation and transfer timestamps
- E-signature progress counter (e.g., E-sign 2/3)

**Loan Certificates Section**
- NFT contract address and token ID per loan
- Mint transaction hash
- Verification source and certificate details

**Transaction Details View (Investors)**
- Transaction hash displayed as a clickable link
- Token ID shown for NFT-backed assets
- Block explorer link for independent verification

**Audit Trail / Status History**
- Every token-related action (deploy, transfer, approve) is appended to `actionHistory` and `statusHistory` arrays
- Each entry includes the actor (`updatedBy`), timestamp (`updatedAt`), and action description
- Blockchain event metadata (contract address, transaction hash, chain ID) is recorded in audit log entries

## Important Notes

**Immutability** — Contract addresses, transaction hashes, and token IDs are permanent blockchain records. They cannot be edited, deleted, or overridden by any party, including platform administrators.

**Independent Verification** — Any contract address or transaction hash can be looked up on the Avalanche C-Chain block explorer (Snowtrace or the subnet explorer) to verify the transaction details, timestamp, and participants without relying on the platform.

**Chain Configuration** — The platform records `chainId` alongside contract addresses so that records unambiguously identify which network (Avalanche C-Chain mainnet, subnet, or testnet) the transaction was executed on.

**Dual Timestamp Assurance** — The platform records both an application-level UTC timestamp (`DateUtils.nowUTC()`) and the blockchain block timestamp for every on-chain event. The application timestamp provides human-readable context; the blockchain timestamp provides cryptographic proof.

**Token Naming Convention** — FT tokens deployed for credit facility funding notices follow a systematic naming convention derived from the facility name and notice identifier, making them identifiable on-chain even without the platform UI.
