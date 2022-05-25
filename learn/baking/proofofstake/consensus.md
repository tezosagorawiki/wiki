# The Tezos Consensus Algorithm

## Tenderbake, the consensus algorithm in Tezos <a href="#consensus" id="consensus"></a>

Before Tenderbake, there was [Emmy\*](https://gitlab.com/tzip/tzip/-/blob/master/drafts/current/draft\_emmy-star.md), a Nakamoto-style consensus consisting of a series of improvements of the one in the [Tezos whitepaper](https://whitepaper.io/document/376/tezos-whitepaper).

Emmy\*, like any Nakamoto-style consensus algorithm (such as [Bitcoin](https://bitcoin.org/bitcoin.pdf) or [Ouroboros](https://eprint.iacr.org/2016/889)), offers _probabilistic_ finality: forks of arbitrary length are possible but they collapse with a probability that increases rapidly with fork length.

[Tenderbake](https://arxiv.org/abs/2001.11965) instead, like any classic BFT-style consensus algorithm (such as [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf) or [Tendermint](https://arxiv.org/abs/1807.04938)), offers _deterministic_ finality: a block that has just been appended to the chain of some node is known to be final once it has two additional blocks on top of it, regardless of network latency.

### Overview

The starting point for Tenderbake is [Tendermint](https://arxiv.org/abs/1807.04938), the first classic-style algorithm for blockchains.

Tenderbake adapts Tendermint to the Tezos blockchain, but the adjustments required are [substantive](https://blog.nomadic-labs.com/a-look-ahead-to-tenderbake.html#the-tezos-architecture):

* Tenderbake is tailored to match the Tezos architecture by using only communication primitives and network assumptions which Tezos supports.
* Tenderbake makes weaker network assumptions than Tendermint, at the price of adding the extra assumption that participants have loosely synchronized clocks — which is fine, because Tezos already uses them.

The design of Tenderbake and its rationale are described at length in the [technical report](https://arxiv.org/abs/2001.11965) and in a [Nomadic Labs’s blog post](https://blog.nomadic-labs.com/a-look-ahead-to-tenderbake.html). Here we only provide a user/developer perspective.

Tenderbake is executed for each new block level by a “committee” whose members are called _validators_, which are delegates selected at random based on their stake, in the same way as endorsers are selected in Emmy\*. We let `CONSENSUS_COMMITTEE_SIZE` be the number of validator [slots](https://tezos.gitlab.io/alpha/proof\_of\_stake.html#rights-alpha) per level. Furthermore, we use `CONSENSUS_THRESHOLD` to denote two thirds of `CONSENSUS_COMMITTEE_SIZE`.

For each level, Tenderbake proceeds in rounds. Each _round_ represents an attempt by the validators to agree on the content of the block for the current level, that is, on the sequence of non-consensus operations the block contains. We call this sequence the block’s _payload_.

Each round has an associated duration. Round durations are set to increase so that for any possible message delay, there is a round that is sufficiently long for all required messages to be exchanged. Round durations depend on protocol parameters `MINIMAL_BLOCK_DELAY` and `DELAY_INCREMENT_PER_ROUND`. These parameters specify round durations as follows:

$$round_duration(0)=minimal_block_delayround_duration(r+1)=round_duration(r)+delay_increment_per_round=minimal_block_delay+(r+1)∗delay_increment_per_round$$

Round durations thus increase linearly with `DELAY_INCREMENT_PER_ROUND`.

Schematically, a round consists in the following steps:

* a validator designated for that round injects a _candidate block_ (representing a proposal) and consensus operations (representing votes) into the node to which it is attached, which then
* diffuses those blocks and consensus operations to other nodes of the network, and thus
* communicates them to the validators attached to those nodes, to carry out voting on which block to accept.

Unlike Emmy\*, Tenderbake has [two types of votes](https://blog.nomadic-labs.com/a-look-ahead-to-tenderbake.html#why-do-we-need-preendorsements): before endorsing a block `b`, a validator preendorses `b`. Furthermore, to be able to endorse, a validator must have observed a preendorsement _quorum_, that is a set of preendorsements from validators having at least `CONSENSUS_THRESHOLD` validator slots. Similarly, to be able to decide, a validator must have observed an endorsement quorum, that is, a set of endorsements from validators having at least `CONSENSUS_THRESHOLD` validator slots. The endorsement quorum for a block `b` is included in a block `b'` on top of `b`, serving as a certification that `b` has been agreed upon. We also say that block `b'` confirms block `b`.

The validator’s whose turn is to inject a candidate block at a given round is called the _proposer_ at that round. Proposers in Tenderbake are selected similarly to bakers in Emmy\*: the proposer at round `r` is the validator who has the validator slot `r`. A proposer who has observed a preendorsement quorum for a candidate block in a previous round, is required to propose a block with the same _payload_ as the initial block. We talk about a _re-proposal_ in this case.\
\
For more information please see: [https://tezos.gitlab.io/active/consensus.html](https://tezos.gitlab.io/active/consensus.html)&#x20;
