---
layout: post
title:  "General FAQ"
date:   2019-01-07 12:14:18
---
General FAQ
===========

# What is Tezos? {#intro}

Tezos is a new blockchain that supports smart contracts and offers a platform to build decentralized applications. 

# What is XTZ? {#xtz}

XTZ, tez, or ꜩ (`\ua729`, "Latin small letter tz") is the base currency of the Tezos blockchain. XTZ aims to become programmable money through smart contracts on the Tezos blockchain.   

# Why is Tezos unique or interesting? {#unique}

1. **Self-Amendment**

    Tezos can upgrade itself through a series of votes. This means that forks are less common and stakeholders in the network are kept together over time. A robust network which can constantly upgrade itself will stand the test of time.  

2. **Formal Verification**

    Smart contracts on Tezos can be mathematically proven to be correct or bug-free. Large financial contracts (vaults, loans, etc.) that hold a lot of money require guarantees that the money will not be lost or frozen due to bugs in the contract. 

# What shortcomings of other blockchains is Tezos solving? {#shortcomings}

Many open-source software projects (blockchains included) face the difficulty of upgrading themselves. There are 3 main problems here:

1. A few volunteers maintain these open-source projects for little to no monetary gain, leading to slow progress or even stagnation. An example would be development of [Ethereum 2.0](https://twitter.com/preston_vanloon/status/1075174335554469888).

2. Upgrades are generally approved or declined by a small committee of people, who may or may not have aligned interests with the rest of the users of the project.

3. Upgrades often require every participant to run download and run new software (hard fork). This requires mass coordination through [social media](https://twitter.com/econoar/status/1081294794461044737) or other channels to notify users of the new change. Because of the high cost of coordination, upgrades are often bundled together and pushed less frequently. 

These problems are more dire for blockchains, as they can become billion-dollar networks. Tezos solves these problems by having an on-chain voting mechanism. Anyone can propose upgrades and put a price tag for developing it, any coin holder in the system can vote to approve/reject the upgrade, and Tezos nodes will automatically switch to the latest version of the protocol without requiring any communication. 

# What use cases are uniquely suited for Tezos? {#use-case}

Smart contract platforms like Tezos or Ethereum allow for any type of code to be executed in a trustless manner. However, certain applications would be uniquely suited to be built on Tezos instead of other blockchains. Here are some examples: 

1. **Digital assets**
    
    Assets like digital money, real estate tokens, stablecoins, digital collectibles, and so on are particularly well-suited to be built on the Tezos blockchain. On other blockchains, hard forks like the Ethereum/Ethereum Classic split could happen, and projects building on Ethereum pre-fork must now choose a fork to honor their assets on. Because of this, hard forks cause a split in value of the assets on the platform, making each fork less valuable. 
    
    This will cause even more problems when building applications that interact with multiple assets, such as a bank for digital collectibles. If half the assets honor fork A and half the assets honor fork B, the bank itself will need to split into 2, which is a massive headache for the owner of it. 
    
    Reducing forks from happening will preserve value, making Tezos an especially interesting blockchain for issuing digital assets.

2. **Trustless Financial Contracts**     

    Financial contracts such as decentralized exchanges, swaps, loans, and so on require an extremely high level of correctness. For example, there was a [bug](https://www.parity.io/parity-technologies-multi-sig-wallet-issue-update/) with Parity's Mulit-Sig Wallet, causing over 500,000 ETH ($150m at that time) to be lost permanently. Another [hack](http://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) of The DAO to the tune of $150m also occured due to a bug known as the recursive send exploit, which later caused the community to fork. 

    A list of Ethereum issues that resulted in lost or stuck funds can be found [here](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds).

    The programming language of Tezos, Michelson, allows for formal verification, which means that smart contracts on Tezos can be mathematically proven to behave exactly as specified ("bug-free"). Industries that require mission-critical software like aircrafts, nuclear reactors and automotive vehicles, often employ formal verification techniques. Writing smart contracts on the Tezos blockchain allows that level of rigor to be applied to digital money and decentralized applications.