---
layout: post
title:  "Future Developments"
date:   2019-01-07 12:14:18
---
Future Developments
===========


# Privacy-Preserving Transactions {#privacy}

Transactions in blockchains are public by default. A company may not want its past transactions to be a matter of public record, thus solutions to make transactions completely private are important for user adoption. To introduce privacy-preserving transactions, developers in the blockchain ecosystem have offered up many competing solutions with different trade-offs and benefits such as Bulletproofs, Ring Signatures and Zero-knowledge proofs.

**zk-SNARKs**

The Tezos developer community has been particularly interested in enabling private transactions by implementing a specific type of zero-knowledge proof called zk-SNARKs. [**An implementation currently being explored**](https://gitlab.com/tezos/tezos/blob/1cd31972ed2de9deee77592b8ffc5fb3d0170d1a/vendors/ocaml-sapling/README.md) uses the same circuits and trusted setup from Zcash's recent "Sapling" upgrade through OCaml bindings to the original Rust libraries. Sapling is based on a near-optimal proof system developer by Jens Groth and the BLS12-381 pairing-friendly elliptic curve and is over an order of magnitude faster than earlier SNARK implementations (read more about Sapling [**here**](https://z.cash/upgrade/sapling/)). 

These SNARKs are also much more succint (as little as 144 bytes), which may be useful in the future for the recursive SNARK scaling techniques described in the ["Scaling Tezos"](https://hackernoon.com/scaling-tezo-8de241dd91bd) blog post from 2017. 

This approach is also now being explored by the [Coda Protocol](https://codaprotocol.com/) and can be implemented as a Tezos sidechain.

# Consensus {#consensus}

Some developers are currently exploring new consensus algorithms. These, in turn, are being developed by other teams so that they may be included in the Tezos protocol. 

Tendermint, Avalanche, and Algorand/Dfinity have emerged as candidates for future Tezos consensus upgrades given Tezos' ability to swap out and upgrade core components of the protocol via the amendment process.

## Tendermint

One idea which has emerged is the possibility of using [Tendermint](https://github.com/tendermint/tendermint/wiki/Byzantine-Consensus-Algorithm), a pBFT-like consensus algorithm for Tezos block acceptance (à la finality gadget), as well as maintaining Nakamoto Consensus for block proposing. These ideas are discussed [here](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f)

Cryptium Labs has presented Tendermint on Tezos:

* **Video:** https://www.youtube.com/watch?v=7L01IxKlVu0z
* **Slides:** https://drive.google.com/file/d/19gjvf89bhVt7yAKpzIuGQ9ensbiHG7FX/view

## Avalanche

The [Igloo project](https://bitsonline.com/igloo-edward-tate-avalanche-tezos/) by Edward Tate is exploring Avalanche implementation for Tezos.

## Scalability

**Sharding**

A [research project](https://tezos.foundation/wp-content/uploads/2018/08/20180809_Tezos_Foundation_Research_Grants_announcement-1.pdf) focused on Tezos sharding is underway at Cornell University.

## Randomness
PVSS and VDFs have both been discussed as ways to improve randomness in Tezos.

**Publicly Verifiable Secret Sharing (PVSS)**
* [Secret sharing](https://en.wikipedia.org/wiki/Secret_sharing) methods distribute a secret amongst a group of participants. Each individual is allocated a share of the secret. In [PVSS](https://en.wikipedia.org/wiki/Publicly_Verifiable_Secret_Sharing), the distributor of the secret posts public proof verifying the validity of the shares of the secret. This can be used to strengthen randomness and to minimize bias in leader and/or committee election in proof-of-stake context
* An implementation of PVSS for Tezos exists [here](https://gitlab.com/tezos/tezos/blob/master/src/lib_crypto/pvss.ml), and here is an [explanation](https://www.reddit.com/r/tezos/comments/9gpiia/pvss_documentation/)

**Verifiable Delay Function (VDF)**

New cryptographic techniques such as [VDFs](https://eprint.iacr.org/2018/601.pdf) (Verifiable Delay Functions) have been [discussed](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) as a way to improve randomness on Tezos. This is important because baker selection on Tezos relies on randomness. The stronger the randomness, the more difficult it is to "game" the consensus algorithm, either in order to give supernormal profits to other bakers or in order to disrupt the network more generally. 

[VDF ASIC research](https://vdfresearch.org/) is underway, led by Filecoin and the Ethereum Foundation.

## Mempool management

One [discussed change](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) to mempool management is expected to increase throughput by 2-3x. This would entail including a transactions in a block based on whether its fee can be paid, without computing its effects. Invalid transactions would be included and treated as nops, as already done in Tezos.

# Layer 2 {#layer2}

Various layer 2 solutions are also being explored and proposed by developers who are building on Tezos. 

**Velos (TezTech)**

[Velos](https://docs.google.com/document/d/18hKJnKB8sAZ_fpiHTzj-HJwbQu_SrqOAisjI3IqdM0A/edit#
), a plasma-like project, is being developed by [TezTech](https://teztech.io/), which is led by Stephen Andrews.

# Amendment Rules {#governance}

## Improving the Amendment Process

Another powerful feature of Tezos is that amendment rules can themselves be amended. This means that people can vote to change the way in which votes are carried out. This is important because voting systems can sometimes be gamed, and a change in the governance mechanism itself may at times be necessary. 

Examples of ideas which are being explored in this domain are lengthened proposal periods, proposal fees, changes to quorum floors, and the moving of vote counts from the beginning of a voting period to the end. This [blog post](https://medium.com/tezos/amending-tezos-b77949d97e1e) outlines a few ways in which the amendment process might be improved in the future.

## Constitutionalism

Constitutionalism refers to the adherence to a set of rules regarding protocol upgrades. Theis set of rules would create additional safeguards for the Tezos blockchain during protocol upgrades. One such rule might be that certain files (such as the one that handles the generation of new tokens) are elevated to a privileged status. These files would then require a higher vote threshold or a longer voting period to be changed.

One [idea which has been discussed](https://medium.com/tezos/a-few-directions-to-improve-tezos-15359c79ec0f) is a refactoring of the code so that every creation or destruction of a Tezos token has to happen through a single OCaml module, a rule which could be enforced via the type system. This module would then programmatically limit the yearly issuance of tez. Protocol amendments which modify the module would be held to a higher vote threshold than amendments which do not.

Another method to enforce constitutionalism would be to have a proof checker (e.g. Coq) embedded into the Tezos protocol. The proof checker works by employing a set of filters. Each filter ensures that certain files are not modified or removed. A protocol upgrade that passes all the filters has been shown not to violate any of the rules stated in the constitution.

## Futarchy

Futarchy is a governance concept first proposed by [Robin Hanson](http://mason.gmu.edu/~rhanson/futarchy.html), who proposed the notion of "voting on values and betting on beliefs." 

As discussed in this [longer form piece](https://medium.com/tezos/towards-futarchy-in-tezos-54a7b8926967) on futarchy in Tezos, futarchy might be best adopted as a proposal filtering mechanism, with terminal decision-making best left to a voting mechanism.

For example, suppose that there is a proposal increasing the block size of the Tezos blockchain to 1 MB. Suppose also that this proposal has been agreed upon by most stakeholders. The market would then vote on whether the proposal would be beneficial to the Tezos blockchain. There would only be 2 possible outcomes in this betting market: a "Yes" or "No" answer to the question of whether an increased block size would be beneficial to Tezos. The outcome would be reflected in the price of the token. An increase in the price of a Tez would represent an overall "Yes", while an decrease in the price of a Tez would represent an overall "No."

The market-making in these contracts would be subsidized by issuing coins to market makers. This would improve price discovery and liquidity. In a tightly coupled futarchic mechanism, the amendment deemed most likely by the market's price would be automatically adopted.