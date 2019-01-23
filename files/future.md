---
layout: post
title:  "Future Developments"
date:   2019-01-07 12:14:18
---
Future Developments
===========


# Privacy-Preserving Transactions {#privacy}

Transactions in blockchains are public by default. A company would not want its past transactions to be a matter of public record, thus solutions to make transactions completely private are important for user adoption. To introduce privacy-preserving transactions, developers in the blockchain ecosystem have offered up many competing solutions with different trade-offs and benefits such as Bulletproofs, Ring Signatures and Zero-knowledge proofs.

**zk-SNARKs**

The Tezos developer community has been particularly interested in implementing a specific type of zero-knowledge proof called the zk-SNARK, which enables private transactions. For example, [this project](https://gitlab.com/tezos/tezos/blob/1cd31972ed2de9deee77592b8ffc5fb3d0170d1a/vendors/ocaml-sapling/README.md) is an OCaml "wrapper" around the ZCash Sapling library, allowing Tezos to reuse the ceremony from ZCash's [Sapling](https://z.cash/upgrade/sapling/) upgrade.

# Consensus {#consensus}

Developers are actively exploring new consensus algorithms that other teams are developing to be included in the Tezos protocol. 

Tendermint, Avalanche, and Algorand/Dfinity have emerged as candidates for future Tezos consensus upgrades given Tezos' ability to swap out and upgrade core components of its protocol via the amendment process.

## Tendermint Consensus

One idea which has emerged is the possibility of using [Tendermint](https://github.com/tendermint/tendermint/wiki/Byzantine-Consensus-Algorithm), a pBFT-like consensus algorithm for Tezos block acceptance (a la finality gadget) and maintaining Nakamoto Consensus for block proposing. This idea is discussed [here](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f)

## Avalanche

The [Igloo project](https://bitsonline.com/igloo-edward-tate-avalanche-tezos/) by Edward Tate is exploring an Avalanche implementation for Tezos.

## Randomness
PVSS and VDFs have both been discussed as ways to improve the randomness in Tezos.

**Publicly Verifiable Secret Sharing (PVSS)**
* [Secret sharing](https://en.wikipedia.org/wiki/Secret_sharing) methods distribute a secret amongst a group of participants, with each individual allocated a share of the secret. In [PVSS](https://en.wikipedia.org/wiki/Publicly_Verifiable_Secret_Sharing), the distributor of the secrets posts public proof which verifies the validity of the shares of the secret. This can be used to strengthen the randomness and minimize bias in leader and/or committee election in the proof-of-stake context.
* An implementation of PVSS for Tezos exists [here](https://gitlab.com/tezos/tezos/blob/master/src/lib_crypto/pvss.ml) and here is an [explanation](https://www.reddit.com/r/tezos/comments/9gpiia/pvss_documentation/)

**Verifiable Delay Function (VDF)**

New cryptographic techniques such as [VDFs](https://eprint.iacr.org/2018/601.pdf) (Verifiable Delay Functions) to improve randomness have been [discussed](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) for Tezos. This is important because baker selection in Tezos relies on randomness. The stronger the randomness is, the more difficult it becomes to "game" the consensus algorithm, either to have supernormal profits to other bakers or to disrupt the network. 

[VDF ASIC research](https://vdfresearch.org/) is underway, led by Filecoin and the Ethereum Foundation.

# Layer 2 {#layer2}

Various layer 2 solutions are also being explored and proposed by various people on the Tezos network. 

**Velos (TezTech)**

[Velos](https://docs.google.com/document/d/18hKJnKB8sAZ_fpiHTzj-HJwbQu_SrqOAisjI3IqdM0A/edit#
), a plasma-like project, is being developed by [TezTech](https://teztech.io/), led by Stephen Andrews.

# Amendment Rules {#governance}

## Improving the Amendment Process

Another powerful feature of Tezos is the ability to change the amendment rules itself. This means that people can vote to change the way votes are carried out, since voting systems can sometimes be gamed and change in the governance mechanism itself may be necessary at times. 

Example ideas which are being explored in this domain are lengthening proposal periods, proposal fees, changing quorum floors, and moving vote counts from the beginning of a voting period to the end. This [blog post](https://medium.com/tezos/amending-tezos-b77949d97e1e) outlines a few ideas of how the amendment process might be improved in the future.

## Constitutionalism

Constitutionalism refers to the adherence to a set of rules regarding protocol upgrades. These set of rules would create additional safeguards for the Tezos blockchain during protocol upgrades. One such rule could state that certain files (such as the one handling the generation of new tokens) are elevated to a privileged status. These files would then require a higher vote threshold or a longer voting period to change.

One [idea which has been discussed](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) is based on a refactoring of the code so that every creation or destruction of a Tezos token has to happen through a single OCaml module, a rule which can be enforced via the type system. This module can then programmatically limit the yearly issuance of tez, making it straightforward to hold protocol amendments which modify the module to a higher vote threshold than amendments which do not.

Another method to enforce constitutionalism is to have a proof checker (e.g. Coq) embedded into the Tezos protocol. The proof checker works by employing a set of filters, where each filter ensures that some files are not modified or removed. By passing all the filters, it means that a protocol upgrade has not violated any of the rules stated in the constitution.

## Futarchy

Futarchy is a governance concept first proposed by [Robin Hanson](http://mason.gmu.edu/~rhanson/futarchy.html), who proposed the notion of "voting on values and betting on beliefs". 

As discussed in this [longer form piece](https://medium.com/tezos/towards-futarchy-in-tezos-54a7b8926967) on futarchy in Tezos, futarchy might be best adopted as a proposal filtering mechanism, while terminal decision-making is best left to a voting mechanism.

An example would be, having a proposal that increases the block size of the Tezos blockchain to 1 MB, which is agreed upon by most stakeholders; the proposal is then voted upon by the market if the proposal is beneficial for the Tezos blockchain. There would only be 2 outcomes in this betting market, if an increased block size is beneficial for Tezos ("Yes" or "No"). These outcomes are reflected in the price of the token; the price of a Tez increasing represents "Yes" while the price of a Tez decreasing represents "No".

The market-making in those contracts can be subsidized by issuing coins to market makers in order to improve price discovery and liquidity. In a tightly coupled futarchic mechanism, the amendment deemed most likely  by the market's price would be automatically adopted.

## Mempool management

One [discussed change](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) to mempool management is expected to increase throughput by 2-3x. This would entail including a transactions in a block based on whether its fee can be paid, without computing its effects. Invalid transactions would be included and treated as nops, as already done in Tezos.