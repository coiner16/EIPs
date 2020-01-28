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

<!--You can leave these HTML comments in your merged EIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new EIPs. Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`. The title should be 44 characters or less.-->
<!--
This is the suggested template for new EIPs.
Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`.
The title should be 44 characters or less.
-->

## Simple Summary
<!--"If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the EIP.-->
<!--If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the EIP.-->
Reparo is a repair layer to fix contract bugs and major
erroraneous transactions with consensus from the community while ensuring the
security of the underlying blockchain. This EIP aims to integrate Reparo ( or a
version of Reparo) into the Ethereum Blockchain.

## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->
Our recent research work [Reparo: Publicly Verifiable Layer to Repair Blockchains](https://arxiv.org/abs/2001.00486) proposes a layered approach to perform repair operations on the contents in the Ethereum blockchain. With Reparo, you can fix bugs in smart contracts and redact illicit data (in conformation to GDPR), etc. These repair operations can be performed on existing contents in the Ethereum blockchain. Unlike other existing proposals, Reparo does not require a new chain with a fresh genesis block and new cryptographic features. Reparo can instead be plugged in as a layer to the existing Ethereum chain and contents from several years ago such as DAO, Parity Multisig Wallet Hack and other such hacks can be repaired with consensus from the community. Reparo does not require a soft fork for every repair which is an added bonus for the miners as there is no change in software/hardware required to implement a repair.

## Motivation
<!--The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.-->
<!--The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.-->
Drawing motivation from the problems faced by Ethereum users in [1](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds), it can be argued that for any real system there needs to be a mechanism to recover from erroraneous/buggy transactions. Especially with the move towards ETH 2.0, one wrong move can make most of the stakes adversarial i.e., make the adversary gain significant stakes in the system (possibly through a buggy contract). Therefore, a secure protocol like **Reparo** can go a long way in these situations instead of introducing ad-hoc fixes and forks (taking note from DAO, Spurious Dragon Fork).

## Specification
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->
TODO

## Rationale
<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->
<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->
TODO

## Backwards Compatibility
<!--All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EIP must explain how the author proposes to deal with these incompatibilities. EIP submissions without a sufficient backwards compatibility treatise may be rejected outright.-->
<!--All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EIP must explain how the author proposes to deal with these incompatibilities. EIP submissions without a sufficient backwards compatibility treatise may be rejected outright.-->
TODO

## Test Cases
<!--Test cases for an implementation are mandatory for EIPs that are affecting consensus changes. Other EIPs can choose to include links to test cases if applicable.-->
<!--Test cases for an implementation are mandatory for EIPs that are affecting consensus changes. Other EIPs can choose to include links to test cases if applicable.-->
TODO

## Implementation
<!--The implementations must be completed before any EIP is given status "Final", but it need not be completed before the EIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->
<!--The implementations must be completed before any EIP is given status "Final", but it need not be completed before the EIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.
-->
TODO

## Security Considerations
<!--All EIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. EIP submissions missing the "Security Considerations" section will be rejected. An EIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.-->
<!--All EIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. EIP submissions missing the "Security Considerations" section will be rejected. An EIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.
-->
TODO

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
