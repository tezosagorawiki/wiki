# What is Tezos?

Tezos is an open-source, blockchain-based cryptocurrency and a smart contracts platform for asset settlement and decentralized applications \(dApps\) which benefit from censorship resistance, decentralization, or user-control.

## What is XTZ? <a id="xtz"></a>

XTZ, tez, or ꜩ \(`\ua729`, "Latin small letter tz"\) is the native currency of Tezos.

## What makes Tezos unique? <a id="unique"></a>

1. **Self-Amendment and Upgradability**

   Tezos can upgrade itself through an in-protocol amendment process without the need for a hard fork. Performing upgrades in this fashion accelerates innovation, reduces the likelihood of contentious splits, and coordinates stakeholders within the Tezos ecosystem over a long period of time.

   For developers building on Tezos, upgradability provides a strong assurance that the protocol will operate smoothly long into the future. **Tezos was built to stand the test of time**.

   For details of the amendment mechanism, see [this post](https://medium.com/tezos/amending-tezos-b77949d97e1e).

   Everything in Tezos, including the amendment mechanism itself is subject to being changed by the proposal amendment process. Of note, the latest proposal [Edo \#008](https://www.tezosagora.org/period/39) is seeking to add a 5th proposal period, known as the "Adoption" phase. The extra proposal period is aimed to provide an additional window for bakers, indexers, and end-users to upgrade their nodes once a protocol upgrade goes live

2. **Proof-of-Stake**

   Baking is to Tezos what mining is to Bitcoin. Participants \(i.e. "nodes"\) in Tezos provide the computational resources necessary to maintain the availability and integrity of the Tezos network. Proof-of-Stake \(PoS\) is the mechanism by which Tezos participants reach consensus on the state of the blockchain. This is in contrast, for example, with Bitcoin, in which the consensus mechanism is based on proof-of-work \(i.e. mining\).

   Tezos' proof-of-stake based mechanism is known as baking and features optional delegation, allowing any stakeholder to participate in consensus without giving up custody of their tokens. Tezos' approach to consensus has been described as [Liquid Proof of Stake](https://medium.com/tezos/liquid-proof-of-stake-aec2f7ef1da7). Tezos allows its stakers \(a.k.a. delegators\) to earn rewards by delegating their tez coins without any lock-in or freeze mechanism. This gives the "liquid" nature to Tezos's proof-of-stake implementation.

   Proof-of-stake improves scalability and encourages incentive alignment. It also increases the cost of 51% attacks and avoids environmentally wasteful proof-of-work.

   Tezos launched in June 2018 as one of the first major Proof-of-Stake networks. As of January 11, 2021, Tezos now has nearly [425 bakers](https://tzkt.io/delegates) and more than [216 public delegation services](https://baking-bad.org/) on all six major continents.

3. **Smart Contract Security and Formal Verification**

   While no system can be universally or unconditionally secure, Tezos and its smart contract language, Michelson, were designed with security and formal verification in mind.

   Formal verification allows developers to mathematically prove that code performs correctly, according to its formal specification or certain properties. This is well-suited to financial smart contracts representing significant real-world value \(e.g. tokenized assets, loans, etc.\), which require guarantees that funds will not be lost or frozen due to bugs in the code.

## Why formal governance? <a id="shortcomings"></a>

**Decentralized blockchain networks \(and most open source software\) face inherent challenges with sustainability, upgradability, and incentive alignment:**

* Open source projects are often maintained by a few volunteers for little to no monetary gain, leading to slow progress and even stagnation. In other cases, infrastructure and public good providers are forced to seek donations, corporate sponsorship, or venture capital funding, all of which may produce incentives misaligned with the overall network.
* Technical roadmaps \(or lack thereof\) are determined by a small group, who may or may not have interests aligned with the larger network.
* Upgrades often require every node operator to download and run new software \(hard fork\). This requires mass coordination over social media or other channels to notify users of the new change. Because of the high cost of coordination, upgrades are often bundled together and pushed infrequently.
* The miners \(or validators\) of a network can have incentives misaligned with the overall network.

How \(or if\) a network addresses these challenges **determines a network's evolution** and **impacts all projects that build on top**.

**Tezos was designed to address these challenges through its on-chain governance mechanism and proof-of-stake-based consensus algorithm:**

* Token holders can participate in the amendment process to approve/reject the upgrade by selecting a baker
* Tezos nodes will automatically switch to the latest version of the protocol without the need for off-chain communication
* [Liquid Proof-of-Stake](https://medium.com/tezos/liquid-proof-of-stake-aec2f7ef1da7) in Tezos was designed to align network participants' incentives and any token holder can avoid dilution by inflation

