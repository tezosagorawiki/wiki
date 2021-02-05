---
layout: post
title:  "General FAQ"
date:   2019-01-07 12:14:18
---
General FAQ
===========

# What is Tezos? {#intro}

Tezos is an open-source, blockchain-based cryptocurrency and a smart contracts platform for assets and decentralized applications (dApps).

# What is XTZ? {#xtz}

XTZ, tez, or ꜩ (`\ua729`, "Latin small letter tz") is the native currency of Tezos.

# What makes Tezos unique? {#unique}

1. **Self-Amendment and Upgradability**

    Tezos can upgrade itself through an in-protocol amendment process without the need for a hard fork. Performing upgrades in this fashion accelerates innovation, reduces the likelihood of contentious splits, and coordinates stakeholders within the Tezos ecosystem over a long period of time.

    For developers building on Tezos, upgradability provides a strong assurance that the protocol will operate smoothly long into the future. **Tezos was built to stand the test of time**.

    For details of the amendment mechanism, see [this post](https://medium.com/tezos/amending-tezos-b77949d97e1e).

    Everything in Tezos, including the amendment mechanism itself is subject to being changed by the proposal amendment process. Of note, the latest proposal [Edo #008](https://www.tezosagora.org/period/39) is seeking to add a 5th proposal period, known as the "Adoption" phase. The extra proposal period is aimed to provide an additional window for bakers, indexers, and end-users to upgrade their nodes once a protocol upgrade goes live

2. **Proof-of-Stake**

    Baking is to Tezos what mining is to Bitcoin. Participants (i.e. "nodes") in Tezos provide the computational resources necessary to maintain the availability and integrity of the Tezos network. Proof-of-Stake (PoS) is the mechanism by which Tezos participants reach consensus on the state of the blockchain. This is in contrast, for example, with Bitcoin, in which the consensus mechanism is based on proof-of-work (i.e. mining).

    Tezos' proof-of-stake based mechanism is known as baking and features optional delegation, allowing any stakeholder to participate in consensus without giving up custody of their tokens. Tezos' approach to consensus has been described as [Liquid Proof of Stake](https://medium.com/tezos/liquid-proof-of-stake-aec2f7ef1da7). Tezos allows its stakers (a.k.a. delegators) to earn rewards by delegating their tez coins without any lock-in or freeze mechanism. This gives the "liquid" nature to Tezos's proof-of-stake implementation.

    Proof-of-stake improves scalability and encourages incentive alignment. It also increases the cost of 51% attacks and avoids environmentally wasteful proof-of-work.

    Tezos launched in June 2018 as one of the first major Proof-of-Stake networks. As of January 11, 2021, Tezos now has nearly [425 bakers](https://tzkt.io/delegates) and more than [216 public delegation services](https://baking-bad.org/) on all six major continents.

3. **Smart Contract Security and Formal Verification**

    While no system can be universally or unconditionally secure, Tezos and its smart contract language, Michelson, were designed with security and formal verification in mind.

    Formal verification allows developers to mathematically prove that code performs correctly, according to its formal specification or certain properties. This is well-suited to financial smart contracts representing significant real-world value (e.g. tokenized assets, loans, etc.), which require guarantees that funds will not be lost or frozen due to bugs in the code.

# Why formal governance? {#shortcomings}

**Decentralized blockchain networks (and most open source software) face inherent challenges with sustainability, upgradability, and incentive alignment:**

*  Open source projects are often maintained by a few volunteers for little to no monetary gain, leading to slow progress and even stagnation. In other cases, infrastructure and public good providers are forced to seek donations, corporate sponsorship, or venture capital funding, all of which may produce incentives misaligned with the overall network.
*  Technical roadmaps (or lack thereof) are determined by a small group, who may or may not have interests aligned with the larger network.
*  Upgrades often require every node operator to download and run new software (hard fork). This requires mass coordination over social media or other channels to notify users of the new change. Because of the high cost of coordination, upgrades are often bundled together and pushed infrequently.
*  The miners (or validators) of a network can have incentives misaligned with the overall network.

How (or if) a network addresses these challenges **determines a network's evolution** and **impacts all projects that build on top**.

**Tezos was designed to address these challenges through its on-chain governance mechanism and proof-of-stake-based consensus algorithm:**
*  Token holders can participate in the amendment process to approve/reject the upgrade by selecting a baker
*  Tezos nodes will automatically switch to the latest version of the protocol without the need for off-chain communication
*  [Liquid Proof-of-Stake](https://medium.com/tezos/liquid-proof-of-stake-aec2f7ef1da7) in Tezos was designed to align network participants' incentives and any token holder can avoid dilution by inflation

<!---

# Which use cases are well-suited to Tezos? {#use-case}

Turing-complete smart contract platforms like Tezos or Ethereum allow for arbitrary code to be executed in a trust-minimized manner. However, certain applications may be well suited for Tezos based on formal governance and focus on smart contract security. Below are some preliminary examples:

1. **Digital Assets**

    Assets like digital money, tokenized real estate, stablecoins, digital collectibles, and so on are particularly well-suited for Tezos.

    In blockchains without formal governance mechanisms, widely adopted asset projects are likely to gain significant soft power in protocol governance. Assets would theoretically [exist on both forks](https://medium.com/@avsa/avoid-evil-twins-every-ethereum-app-pays-the-price-of-a-chain-split-e04c2a560ba8) in a contentious, sustainable split, but an issuer is likely to honor the asset on only one fork. Avoiding contentious forks can preserve value and coordination around one network, making Tezos a compelling platform for issuing digital assets.

    Although no system can be unconditionally secure, the Tezos smart contract language, Michelson, was designed with security and formal verification in mind. This is especially critical for smart contracts representing high value assets, given the unforgiving nature of smart contracts bugs.

2. **Trust-Minimized Financial Contracts**     

    Financial contracts such as decentralized exchanges, swaps, loans, and so on demand a high-level of correctness. Decentralized blockchain networks derive their value from the absence of a trusted third party, which makes a loss of funds from a bug in the code particularly unforgiving. At large enough scale, smart contract exploits can pose challenges for blockchain governance:

    * The infamous [hack](https://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) of The DAO to the tune of $150m occurred due to a bug known as the recursive send exploit, eventually causing the Ethereum community to fork into Ethereum and Ethereum Classic.  
    * A [bug](https://www.parity.io/parity-technologies-multi-sig-wallet-issue-update/) in Parity's Mulit-Sig Wallet caused over 500,000 ETH ($150m at that time) to be frozen, leading to the EIP-999 debate. A list of Ethereum issues resulting in lost or stuck funds can be found [here](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds).

    Tezos' smart contract language, Michelson, facilitates formal verification, a technique which, if deployed correctly, mathematically proves the correctness of the code, boosting the security of the most sensitive or financially weighted smart contracts and reducing the likelihood of bugs. Formal verification techniques are widely deployed in mission-critical software infrastructure, such as in aircrafts, nuclear reactors, and automotive vehicles.

    Tezos aspires to bring this level of rigor to the realm of high-value smart contracts and decentralized applications.

--->

# Tezos Nomenclature {#nomenclature}

The following is adapted from this [Agora post](https://forum.tezosagora.org/t/nomenclature/2376) by Tezos Co-founder Arthur Breitman. As noted in the post, there is no official body which can authoritatively set Tezos nomenclature, but the following is recommended:

**Tezos**

Used somewhat interchangeably, either as a noun or an adjective to designate:

- A open-source project and software (as in, “contributing to the Tezos codebase”)

- A peer to peer network of nodes maintaining a blockchain (as in “a Tezos node”)

- The specific Tezos chain with the most economic relevance (as in “the Tezos chain”). Typically, this would be today the chain whose [millionth block](https://tzkt.io/BKtC4QCWoF73kxLj773vFpQuuwrnye6PS7T1aM3XEPvFXiQbNu7/endorsements) had hash BKtC4QCWoF73kxLj773vFpQuuwrnye6PS7T1aM3XEPvFXiQbNu7.


To be avoided:

- Tezos is **_not_** a unit of cryptocurrency. “I sent you 1 Tezos” is incorrect

- Tezos is **_not_** an entity. As a decentralized network, Tezos can not partner with a company or institution.

**Tez**

A unit of the cryptocurrency native to a Tezos chain (e.g. “I sent you 2 tez”). Tez is invariable. It is not capitalized (except at the beginning of a sentence or when you would otherwise capitalize a noun). “I sent you 2 tez” and not “2 Tez”.

**XTZ**

“XTZ” is an ISO-4217-compatible code for representing tez on the most economically relevant Tezos chain. Unless there is a very specific reason to use an ISO code for it, the term tez should be preferred. Situations where the ISO code might be useful typically involve accounting systems, exchange rates with other currencies, and anything that might need some sort of standardized code. Generally speaking, as of the day of this post, “XTZ” is vastly overused in situations where “tez” or even “Tezos” would be appropriate.
