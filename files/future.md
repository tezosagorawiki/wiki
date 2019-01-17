---
layout: post
title:  "Future Developments"
date:   2019-01-07 12:14:18
---
Future Developments
===========


# Privacy-Preserving Transactions {#privacy}

Transactions in blockchains are public by default. A company would not want its past transactions to be a matter of public record, thus solutions to make transactions completely private are very important. To solve the problem of privacy-preserving transactions, there have been many competing solutions with different trade-offs and benefits.

## Non-interactive Zero Knowledge Proof

The usage of zero knowledge proofs with the zk-SNARK technique enables transactions to be broadcasted privately. How it works simplistically is that the commitments of each transaction are stored in the Merkle tree, which the recipients transact with using a zero knowledge proof. This technique leads to transactions that are private and concise but require a trusted setup. 

# Consensus {#consensus}

## Tendermint Consensus
Tezos is actively exploring new consensus algorithms that other teams are developing to be included in the Tezos protocol. Tendermint is the primary candidate for this because it provides fast finality which is not existent in the current version of Tezos. 

This is where Tezos truly shines as a protocol — being able to swap out core pieces of the protocol like the consensus algorithm to improve itself, depending on a community vote. Whereas for other projects, it may take years to change a big piece of the protocol like consensus. 

## Randomness
There are proposals for using new cryptographic techniques such as [VDFs](https://eprint.iacr.org/2018/601.pdf) (Verifiable Delay Functions) to improve randomness in Tezos. This is important because baker selection in Tezos relies on randomness. The stronger the randomness is, the more difficult it becomes to "game" the consensus algorithm, either to have supernormal profits to other bakers or to destroy the network. 

# Layer 2 {#layer2}

Various layer 2 solutions are also being explored and proposed by various people on the Tezos network. For example, the equivalent of Ethereum's Plasma called [Velos](https://docs.google.com/document/d/18hKJnKB8sAZ_fpiHTzj-HJwbQu_SrqOAisjI3IqdM0A/edit#
) is proposed by Tezos community member Stephen Andrews. 

# Amendment Rules {#governance}

## Improving Amendment Process

Another powerful feature of Tezos is the ability to change the amendment rules itself. This means that people can vote to change the way votes are carried out, since voting systems can sometimes be gamed and change in the system itself may be necessary at times. 

Example ideas which are being explored in this domain are lengthening proposal periods, proposal fees, changing quorum floors, and so on. This [blog post](https://medium.com/tezos/amending-tezos-b77949d97e1e) outlines a few ideas of how the amendment process can be improved in the future.

## Constitutionalism

Constitutionalism refers to the adherence to a set of rules regarding protocol upgrades. These set of rules would create additional safeguards for the Tezos blockchain for protocol upgrades. One such rule could state that certain files (such as the one handling the generation of new tokens) are elevated to a privileged status. These files would then require a larger majority vote and a prolonged voting period to change.

A method to enforce constitutionalism is to have a proof checker embedded into the Tezos node. The proof checker works by employing a set of filters, where each filter ensures that some files are not modified or removed. By passing all the filters, it means that a protocol upgrade has not violated any of the rules stated in the constitution.

## Futarchy

Futarchy is a governance concept first proposed by [Robin Hanson](http://mason.gmu.edu/~rhanson/futarchy.html). The idea is that proposals and upgrades should be voted by the majority, however the choice of adopting the proposal/upgrade should be left to a betting market. An example would be, having a proposal that increases the block size of the Tezos blockchain to 1 MB, which is agreed upon by most stakeholders; the proposal is then voted upon by the market if the proposal is beneficial for the Tezos blockchain. There would only be 2 outcomes in this betting market, if an increased block size is beneficial for Tezos ("Yes" or "No"). These outcomes are reflected in the price of the token; the price of a Tez increasing represents "Yes" while the price of a Tez decreasing represents "No".

The market-making in those contracts can be subsidized by issuing coins to market makers in order to improve price discovery and liquidity. In the end, the amendment deemed most likely  by the market's price would be automatically adopted.