---
layout: post
title:  "General FAQ"
date:   2019-01-07 12:14:18
---
General FAQ
===========

# What is Tezos? {#intro}

Tezos is a blockchain-based cryptocurrency and smart contracts platform for building decentralized applications (dApps).

# What is XTZ? {#xtz}

XTZ, tez, or ꜩ (`\ua729`, "Latin small letter tz") is the native currency of Tezos. XTZ is programmable money created by smart contract on the Tezos blockchain.   

# What makes Tezos unique or interesting? {#unique}

1. **Self-Amendment and Upgradability**

    Tezos can upgrade itself through an in-protocol amendment process without the need for a hard fork. This is in order to accelerate innovation, reduce the likelihood of contentious splits, and coordinate stakeholders within one network over a long period of time.
    
    For developers building on Tezos, upgradability provides a strong assurance that the protocol will operate smoothly long into the future. Tezos was built to stand the test of time.
    
    For details of the amendment mechanism, see [this post](https://medium.com/tezos/amending-tezos-b77949d97e1e).
    
2. **Proof-of-Stake**

    Baking is to Tezos what mining is to Bitcoin. Participants (i.e. "nodes") in Tezos provide the computational resources necessary to maintain the network. Proof-of-Stake (PoS) is the mechanism by which Tezos participants reach consensus on the state of the blockchain. This is in contrast, for example, with Bitcoin, in which the consensus mechanism is based on proof-of-work (i.e. mining).
    
    Tezos' proof-of-stake based mechanism is known as baking. Tezos also features optional delegation, which allows any stakeholder to participate in the consensus process.
    
    Proof-of-stake improves scalability and encourages incentive alignment. It also increases the cost of 51% attacks and avoids environmentally wasteful proof-of-work.
    
    Tezos launched in June 2018 as one of the first major Proof-of-Stake networks. As of January 19, 2019, Tezos now has nearly [460 bakers](https://tzscan.io/rolls-distribution) and more than [107 public delegation services](https://mytezosbaker.com/).

2. **Smart Contract Security and Formal Verification**

    No system can be universally secure. However, Tezos and its smart contract language, Michelson, were designed with security and formal verification in mind. 
    
    Formal verification allows developers to prove mathematically that code performs correctly, according to its formal specifications or certain properties. This is well suited to financial smart contracts of significant value (e.g. tokenized assets, loans, etc.), which require guarantees that funds will not be lost or frozen due to bugs in the code.

# What shortcomings of other blockchains does the Tezos' governance mechanism aim to address? {#shortcomings}

Many open-source software projects (especially decentralized blockchain networks) face difficulties upgrading. There are several generalizable governance challenges facing open blockchain networks:
*  Open source projects are often maintained by a few volunteers for little to no monetary gain, leading to slow progress and even stagnation. In other cases, infrastructure and public good providers are forced to seek donations, corporate sponsorship, or venture capital funding, all of which may produce incentives misaligned with the overall network.
*  Technical roadmaps (or lack thereof) are determined by a small group, who may or may not have interests aligned with the larger network.
*  Upgrades often require every node operator to download and run new software (hard fork). This requires mass coordination over social media or other channels to notify users of the new change. Because of the high cost of coordination, upgrades are often bundled together and pushed infrequently.
*  The miners (or validators) of a network can have incentives misaligned with the overall network.

These challenges are of great consequence for the evolution of blockchains networks, impacting all projects that build on top of them.

Tezos was designed to address these problems through its on-chain governance mechanism and proof-of-stake-based consensus algorithm:
*  Anyone can propose upgrades and invoice the network for developing it.
*  Token holders can participate in the amendment process to approve/reject the upgrade by selecting a baker.
*  Tezos nodes will automatically switch to the latest version of the protocol without the need for off-chain communication.
*  [Liquid proof-of-stake](https://medium.com/tezos/liquid-proof-of-stake-aec2f7ef1da7) in Tezos was designed to align network participants' incentives and any token holder can avoid dilution by inflation.

# What are some use cases for Tezos? {#use-case}

Turing-complete smart contract platforms like Tezos or Ethereum allow for arbitrary code to be executed in a trust-minimized manner. However, certain applications are uniquely suited to Tezos. Here are some examples:

1. **Digital Assets**
    
    Assets like digital money, tokenized real estate, stablecoins, digital collectibles, and so on are particularly well-suited for Tezos. 

    In blockchains without formal governance mechanisms, widely adopted asset projects are likely to gain significant soft power in protocol governance. In a contentious, sustainable split, assets would [exist on both forks](https://medium.com/@avsa/avoid-evil-twins-every-ethereum-app-pays-the-price-of-a-chain-split-e04c2a560ba8), but the issuer is likely to honor the asset on one fork and not the other. Avoiding contentious forks can preserve value and coordination around one network, making Tezos an especially interesting blockchain for issuing digital assets.
    
    Although no system can be universally secure, the Tezos smart contract language, Michelson, was designed with security and formal verification in mind. This is especially critical given the unforgiving nature of smart contracts bugs (more on this below).

2. **Trust-Minimized Financial Contracts**     

    Financial contracts such as decentralized exchanges, swaps, loans, and so on demand a high level of correctness. Decentralized blockchain networks derive their value from the absence of a trusted third party and so a loss of funds resulting from a bug in the code is particularly unforgiving. At large enough scale, smart contract exploits can pose challenges for blockchain governance:
    
    *   For example, a [bug](https://www.parity.io/parity-technologies-multi-sig-wallet-issue-update/) in Parity's Mulit-Sig Wallet caused over 500,000 ETH ($150m at that time) to be permanently lost, leading to the EIP-999 debate 
    
    *   Another famous [hack](http://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) of The DAO to the tune of $150m also occured due to a bug known as the recursive send exploit, eventually causing the Ethereum community to fork into Ethereum and Ethereum Classic.
    
    *   A list of Ethereum issues that resulted in lost or stuck funds can be found [here](https://github.com/ethereum/wiki/wiki/Major-issues-resulting-in-lost-or-stuck-funds).

    Tezos' smart contract language, Michelson, facilitates formal verification, by which Tezos smart contracts can be mathematically proven to behave exactly as specified ("bug-free"). Formal verification techniques are widely deployed in mission-critical software infrastructure, such as in aircrafts, nuclear reactors, and automotive vehicles. 
    
    Tezos aspires to bring this level of rigor to high-value smart contracts and decentralized applications.