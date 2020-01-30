---
eip: <to be assigned>
title: Reparo Integration
author: Adithya Bhat <bhat24@purdue.edu>, Sri Aravinda Krishnan Thyagarajan <sri.aravinda.thyagarajan@fau.de>, Bernardo Magri <magri@cs.au.dk>, Daniel Tschudi <tschudi@cs.au.dk>, and Aniket Kate <aniket@purdue.edu>
status: Draft
type: Standards Track
category Core
created: (2020-02-01)
requires (*optional): <EIP number(s)>
replaces (*optional): <EIP number(s)>
---

<!--
This is the suggested template for new EIPs.
Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`.
The title should be 44 characters or less.
-->

## Simple Summary
<!--"If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the EIP.-->
Reparo is a repair layer to fix contract bugs and major
erroraneous transactions with consensus from the community while ensuring the
security of the underlying blockchain. This EIP aims to integrate Reparo ( or a
version of Reparo) into the Ethereum Blockchain.

## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->
Our recent research work [Reparo: Publicly Verifiable Layer to Repair Blockchains](https://arxiv.org/abs/2001.00486) proposes a layered approach to perform repair operations on the contents in the Ethereum blockchain. With Reparo, you can fix bugs in smart contracts and redact illicit data (in conformation to GDPR), etc. These repair operations can be performed on existing contents in the Ethereum blockchain. Unlike other existing proposals, Reparo does not require a new chain with a fresh genesis block and new cryptographic features. Reparo can instead be plugged in as a layer to the existing Ethereum chain and contents from several years ago such as DAO, Parity Multisig Wallet Hack and other such hacks can be repaired with consensus from the community. Reparo does not require a soft fork for every repair which is an added bonus for the miners as there is no change in software/hardware required to implement a repair.

## Motivation
<!--The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.-->
Drawing motivation from the problems faced by Ethereum users in [1](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds), it can be argued that for any real system there needs to be a mechanism to recover from erroraneous/buggy transactions. Especially with the move towards ETH 2.0, one wrong move can make most of the stakes adversarial i.e., make the adversary gain significant stakes in the system (possibly through a buggy contract). Therefore, a secure protocol like **Reparo** can go a long way in these situations instead of introducing ad-hoc fixes and forks (taking note from DAO, Spurious Dragon Fork).

## Specification
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->
TODO

<!--## Rationale-->
<!--[>The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.<]-->
<!--[>The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.<]-->
<!--TODO-->

## Backwards Compatibility
<!--All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EIP must explain how the author proposes to deal with these incompatibilities. EIP submissions without a sufficient backwards compatibility treatise may be rejected outright.-->
Reparo does not introduce any backward incompatibilities.

## Test Cases
<!--Test cases for an implementation are mandatory for EIPs that are affecting consensus changes. Other EIPs can choose to include links to test cases if applicable.-->
Test cases can be worked on after the policy is determined and if the proposal
is accepted.

## Implementation
<!--The implementations must be completed before any EIP is given status "Final", but it need not be completed before the EIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.
-->

A high level overview of the implementation involves creating two precompiled
contracts: RequestRepair and Vote at addresses `0x0a` and `0x0b` respectively.  

A repair transaction `repairTx` consists of a request whose data is the hash of
the old transaction (32 bytes) followed by the new transaction `H(tx)||tx'`.
The validation for repairTx checks if the first 32 bytes of the data field is a
valid un-repaired transaction and the new transaction is semantically valid. We
then create a memory database to store H(H(tx)||H(tx')) as key with the value 0
as the number of votes that support this repair. 

A vote transaction `voteTx` consists of a transaction whose data is
`H(H(tx)||H(tx'))`. The validation for this transaction involves checking if a
memory database is present and checking if the data is present as a key. If it
is valid and the policy permits this user to vote then increment the vote by 1.

At every block, update the age of every repairTx by 1. If any repairTx is mature
(age = l), then we process (accept or reject) the repairTx and remove the
transaction from the memory database. If the database is empty, we tear it
down.

When accepting a repair, we have the following options depending on what policy
for repair is approved:
- If the policy states that we can fix contracts by injecting code/state to an
  address (with the bug addressed), we do so accordingly.
- If the policy states that we recompute the new state from scratch, then we do
  so. In order to achieve better throughput, we start a parallel thread to
  recompute the state and we can apply the final state after delay blocks = depth/(a constant).

## Security Considerations
<!--All EIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. EIP submissions missing the "Security Considerations" section will be rejected. An EIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.
-->

Reparo is a secure repair layer under the assumption that 51% of the
miners/stakeholders are honest. When this is violated, it can be clearly seen
that the blockchain is vulnerable to double-spending, censoring and other
attacks before making harmful edits to the chain. However, these harmful edits are public
and can be later fixed (after removing the malicious players) unlike the other
attacks which are irreversible.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
