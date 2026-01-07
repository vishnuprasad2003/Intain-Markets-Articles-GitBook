---
title: Token IDs and Timestamps
description: Understand how FT tokens are tracked with unique identifiers and timestamps in Intain Markets
---

# Token IDs and Timestamps

## Overview

FT tokens created for funding notices have unique contract addresses and timestamps. Each token has a unique contract address, and all token events are timestamped.

## Token Creation and Identification

**FT Contract Address** - Each funding notice generates a unique FT contract:
- ftContractAddress field stores the blockchain contract address
- Contract address is unique for each funding notice
- Links to blockchain records for verification

**Token Distribution** - Tokens allocated to lenders in tokenDistribution array:
- Each lender receives tokensAllocated amount
- tokensAllocated calculated from lender votingPercentage
- Individual lender allocations tracked separately
- Total tokens equal the drawdown amount

**Token Generation Timestamps** - Token creation timestamped:
- ftCreatedAt records when tokens were created
- ftCreationTransactionHash records the blockchain transaction
- totalTokensMinted records the total amount created
- ftTotalSupply records the total supply with decimals

## Token Approval Tracking

**Borrower Token Approval** - When borrower approves token transfer:
- approvedAt timestamp records approval time
- approvalTransactionHash records the blockchain transaction
- issuedAt timestamp records when approval was processed
- Status changes to TOKEN_APPROVED after approval

**Approval Details** - Includes borrower wallet address (issuerAddress), Intain admin wallet address, approved token amount, blockchain transaction details

## Per-Lender Token Tracking

**Individual Lender Allocations** - Each lender's tokens tracked:
- tokensAllocated shows amount allocated
- votingPercentage determines allocation percentage
- commitmentAmount shows lender's commitment
- lenderOrgId and lenderName identify the lender

**Lender Token Status** - Token status tracked per lender:
- mintingStatus: 'pending' or 'completed'
- lenderApprovalStatus: 'PENDING', 'APPROVED', or 'REJECTED'
- amountTransferred: 'pending' or 'transferred'
- esignatureStatus: 'pending' or 'ESIGN_COMPLETED'

**Timestamps Per Lender** - Each lender's actions timestamped:
- updatedAt timestamp for each status change
- updatedBy field records who made the change
- Individual timestamps for approval, rejection, and fund transfer

## Blockchain Integration

**Avalanche C-Chain** - Tokens created on Avalanche C-Chain:
- FT contracts deployed on Avalanche network
- Contract addresses link to Avalanche blockchain records
- Transaction hashes enable blockchain verification

**Solana Integration** - Users can choose Solana for FT transfers:
- Platform supports both Avalanche and Solana networks
- Users select preferred blockchain during token generation
- Solana tokens follow same tracking principles
- Contract addresses and transaction hashes tracked similarly

**Blockchain Verification** - Token contract addresses link to blockchain records, enabling independent verification.

## Where Token Information Appears

**Funding Notice Details** - Shows ftContractAddress, token distribution with lender allocations, token generation timestamps, approval timestamps and transaction hashes

**Token Distribution Array** - Shows each lender's tokensAllocated amount, individual lender status and timestamps, per-lender approval and transfer status

**Audit Trail** - Token activities recorded in status history, action history, complete timeline of token events, blockchain transaction references

## Important Notes

**Unique Contract Addresses** - Each funding notice has a unique FT contract address. Contract addresses are permanent.

**Timestamping** - All token events timestamped: creation, distribution, approval, transfer. Timestamps use standardized formats.

**Audit Trail** - Token IDs and timestamps create audit trails. All token activities tracked from creation through transfer.

**Blockchain Verification** - Token contract addresses link to blockchain records, enabling independent verification.

**Permanent Records** - Token information is permanent. Contract addresses, transaction hashes, and timestamps remain accurate.

**Network Choice** - Users can choose between Avalanche and Solana networks for FT tokens. Both networks provide tracking and verification.
