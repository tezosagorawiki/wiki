---
layout: post
title:  "General FAQ"
date:   2019-01-07 12:14:18
---
General FAQ
===========

# What is Tezos? {#intro}

Tezos is a new blockchain network that supports smart contracts and a platform to build decentralized applications. 

# What is XTZ? {#xtz}

XTZ, tez, or ꜩ (`\ua729`, "Latin small letter tz") is the native currency of Tezos. XTZ becomes programmable money through smart contracts on the Tezos blockchain.   

# What makes Tezos unique or interesting? {#unique}

1. **Self-Amendment and upgradability**

    Tezos can upgrade itself through an in-protocol amendment process without the need for a hard fork. This is designed to accelerate innovation, reduce the likelihood of contentious hard forks, and to better coordinate stakeholders within one network over time.
    
    For developers building on Tezos, upgradability provides a stronger assurance that a protocol will exist long into the future. Tezos was built to stand the test of time.
    
2. **Proof-of-Stake**

    Baking is to Tezos what mining is to Bitcoin. 
    
    Tezos launched in June 2018 as one of the first major blockchain network in which block publishing rights are allocated by stake. Contrast this with Bitcoin, in which block publishing rights are allocated by mining (i.e. proof-of-work). Tezos' proof-of-stake based mechanism is known as baking and features optional delegation, allowing any stakeholder to participate in the consensus process. 
    
    Proof-of-stake also offers greater protections against 51% attack, as an attacker must acquire (at great cost) greater than 51% of the stake, rather than 51% of the hash power.
    
    As of January 19, 2019, Tezos now has nearly [460 bakers](https://tzscan.io/rolls-distribution) and more than [107 public delegation services](https://mytezosbaker.com/).

2. **Formal Verification**

    The Tezos smart contract language, Michelson, was designed with formal verification and security in mind. Formal verification allows developers to mathematically prove that code performs correctly, according to its formal specification or certain properties. This is well-suited to financial smart contracts representing significant value (e.g. tokenized assets, loans, etc.), which require guarantees that value will not be lost or frozen due to bugs in the contract.

# What shortcomings of other blockchains is Tezos solving? {#shortcomings}

Many open-source software projects (blockchains included) face difficulties in upgrading themselves. There are 3 generalizable problems facing blockchain networks:

1. A few volunteers maintain these open-source projects for little to no monetary gain, leading to slow progress and even stagnation. In other cases, infrastructure and public good providers are limited by having to seek funding by donation or by venture capital, which may have incentives misaligned with the overall network.

2. Technical roadmaps (or lack thereof) are governed by a small committee of people, who may or may not have aligned interests with the rest of the users of the project.

3. Upgrades often require every node operator to run download and run new software (hard fork). This requires mass coordination over social media or other channels to notify users of the new change. Because of the high cost of coordination, upgrades are often bundled together and pushed less frequently. 

These challenges are of great consequence for blockchains networks, many of which aim to become major, internet-native value protocols with many downstream projects affected by decisions about the base layer. Tezos was aimed to address these problems through its on-chain governance mechanism. Anyone can propose upgrades and invoice the network for developing it, any coin holder in the system can participate to approve/reject the upgrade, and Tezos nodes will automatically switch to the latest version of the protocol without the need off-chain communication.

# What use cases are uniquely suited for Tezos? {#use-case}

Turing-complete smart contract platforms like Tezos or Ethereum allow for arbitrary code to be executed in a trust-minimized manner. However, certain applications are uniquely suited for Tezos. Here are some examples: 

1. **Digital assets**
    
    Assets like digital money, real estate tokens, stablecoins, digital collectibles, and so on are particularly well-suited for Tezos. In blockchains without formal governance mechanisms, the risk of a contentious fork like the Ethereum/Ethereum Classic split are much higher, and in a future contentious split, projects may need to choose a fork on which to honor their assets.
    
    This will cause even more problems when building applications that interact with multiple assets, such as a bank for digital collectibles. If half the assets honor fork A and half the assets honor fork B, the bank itself will need to split into 2, which is a massive headache for the owner of it. 
    
    Avoiding contentious forks can preserve value and coordination around one network, making Tezos an especially interesting blockchain for issuing digital assets.

2. **Trustless Financial Contracts**     

    Financial contracts such as decentralized exchanges, swaps, loans, and so on demand an extremely high level of correctness. Decentralized blockchain networks derive their value from the absence of a trusted third party and so a loss of funds resulting from a bug in the code is particularly unforgiving. For example, a [bug](https://www.parity.io/parity-technologies-multi-sig-wallet-issue-update/) in Parity's Mulit-Sig Wallet caused over 500,000 ETH ($150m at that time) to be lost permanently and the governance of decentralized networks is even more experimental than the underlying technology itself. Another famous [hack](http://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) of The DAO to the tune of $150m also occured due to a bug known as the recursive send exploit, which later caused the community to fork.

    A list of Ethereum issues that resulted in lost or stuck funds can be found [here](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds).

    The programming language of Tezos, Michelson, allows for formal verification, which means that smart contracts on Tezos can be mathematically proven to behave exactly as specified ("bug-free"). Industries that require mission-critical software like aircrafts, nuclear reactors and automotive vehicles, often employ formal verification techniques. Writing smart contracts on the Tezos blockchain allows that level of rigor to be applied to digital money and decentralized applications.