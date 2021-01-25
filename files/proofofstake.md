---
layout: post
title:  "Proof of Stake Consensus"
date:   2021-01-25 12:14:18
---
# Proof-of-Stake Consensus

## Proof-of-Stake {#intro}

Proof-of-Stake (PoS) refers to a category of algorithms that are used to come to consensus in a blockchain system. In precise terms, Proof-of-Stake is a mechanism that prevents Sybil-attacks (i.e. prevents a single participant from masquerading as N others). In a PoS system, a participant's vote in a system is linked directly to the number of coins they have, so that a person who only has 100 coins cannot pretend to be 1000 different people with 100 coins each.

For a blockchain to make progress, new blocks must be created and added to chain. Who has the right to make these new blocks? In a Proof-of-Work system, miners compete for this right by expending computing power to solve random cryptographic puzzles. The winner gets to create the next block, and earns some reward for doing so. In this paradigm, the more computing power a miner has, the more likely they are to create the next block. By contrast, PoS systems revolve around the idea that the more coins a miner/validator/block producer has, the more likely they are to create the next block.

Broadly, there are 2 classes of proof-of-stake algorithms:

1. **Nakamoto-style Proof-of-Stake**

    As with Bitcoin, one validator is randomly selected in each time slot to create a block that builds on the longest chain (longest/heaviest chain). However, instead of selecting a validator based on who solves the cryptographic puzzles first, the likelihood of selection is weighted according to how many coins they lock-up, or "stake."

2. **Byzantine Fault Tolerant (BFT) Proof-of-Stake**

    Instead of a random validator getting the right to create a block which every other participant must accept, BFT systems introduce the idea of *proposing* and *accepting*. Like in Nakamoto-style PoS, a (possibly randomly) selected validator (weighted by stake) is chosen to propose a block to the other validators. All the validators must communicate with each other until agreement is reached. Once validators are in agreement, they accept the block and it is finalized as the latest block.

# Emmy<sup>+</sup>, the consensus algorithm in Tezos {#consensus}

Tezos uses a Nakamoto-style PoS algorithm for consensus, which since Babylon, is
called Emmy<sup>+</sup>. To understand it, we will break it up into six main
sections:

1. **Block Creation (Baking)**

    Block creation is the way that the blockchain makes progress. In Tezos,
    participants who create blocks are called bakers. To be considered a baker,
    a participant needs to own at least 8,000 ꜩ (1 roll). The more rolls
    someone has, the higher their chance of being given the rights to bake the
    next block. If there are 10 rolls activated at some point in time, and a
    baker owns 2/10 of those rolls, they have a 20% chance of being given the
    rights to create the next block. This means that if a baker has 8,000 ꜩ or
    15,999 ꜩ, they have the same baking rights in the system.

    Baking rights are set in terms of priorities. For example, if there are 10 rolls, the protocol could randomly select a priority list as follows:

        Priority1 = Roll 6
        Priority2 = Roll 9
        Priority3 = Roll 4
        Priority4 = Roll 3
        .
        .
        .
        Priority10 = Roll 7

    This means that the person who owns Roll 6 will have first priority in proposing the block. If they do not create and broadcast a block within a certain period (detailed below TODO-link), the person who owns Roll 9 may take over. The more rolls one owns, the greater one's chances of being given high priority. Furthermore, a baker may receive several priorities.

2. **Endorsing**

   Besides baking, a participant has the right to endorse a block. Endorsing
   rights are set in the same way as baking rights. At every block height, 32
   random rolls are selected to endorse a block. Endorsing serves as a vote on a
   block. Endorsements on a block are included in the next block. Endorsing is a
   sign of activity so the more endorsements blocks contain, the healthier the
   chain.

3. **Block Delay Rule** {#block-delay}

   The priority of a block and the number of endorsements included in it
   determine the minimal time at which the next block can be baked. The higher
   the priority and the more endorsements, the quicker the next block can be
   baked.

4. **Delegating**

    If someone does not have 8,000 ꜩ or does not want to set up computing infrastructure to bake blocks, they can delegate their coins to a baker. Delegating lets coin holders "lend" their coins to a baker. As a result, the baker has a higher probability of being selected, and the baker in turn shares the additional revenue with the coin holder. Importantly, this process does not actually transfer ownership of coins. The baker cannot spend the ꜩ delegated to them, and bakers cannot run away with other people's money.

    Groups have sprung up offering competitive rates for their baking services, and most charge ~10-20% fees on the rewards that people obtain by delegating to them.

5. **Fork Choice Rule**

    The last key thing to understand about the Tezos consensus algorithm is how
    the protocol decides which chain fork is the "correct" one. The fork choice
    rule in Tezos is based on the longest chain like in Nakamoto-style
    blockchains but it includes also the check that blocks are not baked sooner
    than [allowed](#block-delay).

6. **Incentives**

    To encourage participation, baking and endorsing are rewarded by the
    protocol in the form of newly minted ꜩ. Since
    [Carthage](https://blog.nomadic-labs.com/a-new-reward-formula-for-carthage.html),
    the rewards for a block of priority `p` with `e` endorsements is a function
    of `p` and `e`. For priority 0, the baking reward and the endorsing reward
    are equal to `1.25 x e ꜩ`. This choice of design prevents against
    [deflationary
    baking](https://blog.nomadic-labs.com/a-new-reward-formula-for-carthage.html).
    For priority 1 and above, the baking reward for a block with `e`
    endorsements is `0.1875 x e ꜩ` and the endorsing reward is `0.8(3) x e ꜩ`.

    To prevent the Nothing-at-Stake problem[^nos], baking and endorsing require
    a security deposit (skin in the game). The security deposit for baking is
    512 ꜩ Security deposits are locked up for 5 cycles (~14 days). Security
    deposits are slashed in case of double baking/endorsing if an accusation is
    included as evidence in a future block. Precisely, assume that *z* caught
    *x* double-baking and assume that *x* has in total *y* ꜩ in security deposit
    and future rewards. Then half of *y* is burnt and half goes to *z* in the
    form of a reward.

[^nos]: In PoW systems, when there are 2 chain forks, a miner has 2 options —
they can either split their mining power between the two forks or mine on a
single fork. However, in PoS-secured systems, there is no concept of hash
power. As such, validators can theoretically sign multiple blocks at the same
block height. Hence, in a naively implemented PoS network, validators can
generate and maintain multiple forks at no cost to themselves.


**To summarize:** The Tezos PoS protocol called Emmy<sup>+</sup> uses a
  Nakamoto-style PoS consensus. Bakers (people who own 8,000 ꜩ) are given the
  responsibility of creating and endorsing blocks. They are rewarded for their
  action. They are also required to stake some of their own capital in order to
  ensure honest behavior.

<!--
# What is the Nothing-at-Stake Problem and how does Tezos solve it? {#nothing-at-stake}

In PoW systems, when there are 2 chain forks, a miner has 2 options — they can either split their mining power between the two forks or mine on a single fork. However, in PoS-secured systems, there is no concept of hash power. As such, validators can theoretically sign multiple blocks at the same block height. Hence, in a naively implemented PoS network, validators can generate and maintain multiple forks at no cost to themselves.

To solve this problem, the Tezos protocol includes some slashing conditions. Bakers that bake or endorse multiple blocks of the same height (vote on multiple forks) lose their security deposits. If someone observes another baker "double-baking," they can include an accusation in a future block containing the evidence. This will cause the "double-baker" to forfeit their security deposit and future rewards up to that point in the cycle. Half of this is burned, while the other half goes to the accuser in the form of a block reward. This incentivizes bakers to keep check on other bakers and to accuse them when they observe a double-bake. Because of this, bakers are disincentivized from baking or endorsing blocks on multiple forks. The risk of losing one's own coins minimizes the Nothing-at-Stake Problem.
-->

# Finality in Tezos {#finality}

Emmy<sup>+</sup>, being a Nakamoto-style consensus, offers only *probabilistic*,
not *deterministic* finality. The implication is that forks can have arbitrary
length — but forked states become exponentially unstable and tend to collapse
down to a single branch ([assuming decent bounds on network
latency](https://blog.nomadic-labs.com/emmy-in-the-partial-synchrony-model.html)).

By gathering information from missing endorsements, missing blocks, and from
future assigned baking rights, an observer can determine whether or not an actor
controlling a given ammount of the rolls is able to re-organize a given
block. For instance, as shown experimentally in a [previous
analysis](https://blog.nomadic-labs.com/analysis-of-emmy.html), a user may be
_reasonably sure_[^fin] that a block is final if it has <a name="6"></a>6
confirmations (that is, blocks on top of it) over a healthy chain[^healthy] when
considering a Byzantine attacker with a stake fraction of 33% of the total
active stake. Given that in a healthy chain blocks are baked every minute, 6
confirmations are equivalent to 6 minutes.

[^fin]: Here, _reasonably sure_ means "with probability smaller than some
reasonable threshold", which we quantify as `5 * 1e-9`, which puts our
expectation of being wrong about a block being final at roughly once every two
centuries.

[^healthy]: We say a chain is *healthy* over a period of time if in this period
blocks have priority 0 and (almost) all its endorsement slots are filled. A
concrete healthiness measure is the delay of the chain with respect to the ideal
chain where each block has a delay of one minute with respect to the previous
block.

# Scalability {#scalability}

Currently, Tezos does around 30-40 transactions per second.

# Further resources {#resources}

Please check the [consensus
entry](file:///home/lacra/git_repos/tezos/docs/_build/008/proof_of_stake.html)
in the Tezos developer documentation.

[Nomadic Labs](https://www.nomadic-labs.com/) published a series of [blog
posts](https://blog.nomadic-labs.com/) analyzing Emmy<sup>+</sup>:

* [the motivation behind
  Emmy<sup>+</sup>](https://blog.nomadic-labs.com/emmy-an-improved-consensus-algorithm.html)
* [a first analysis of
  Emmy<sup>+</sup>](https://blog.nomadic-labs.com/analysis-of-emmy.html)
  providing confirmations numbers such as <a href="#6">6</a> and some insights
  on choosing the existing constants
* [an update of rewards in
  Carthage](https://blog.nomadic-labs.com/a-new-reward-formula-for-carthage.html)
  to take into account inflation and to deal with deflationary baking
* [a review of a research paper on
  Emmy<sup>+</sup>](https://blog.nomadic-labs.com/on-defending-against-malicious-reorgs-in-tezos-proof-of-stake.html)
  expanding on the choices made in the [initial
  analysis](https://blog.nomadic-labs.com/analysis-of-emmy.html) to show the
  benefits with respect to the changes proposed in the research paper
* [Emmy<sup>+</sup> in partial
  synchrony](https://blog.nomadic-labs.com/emmy-in-the-partial-synchrony-model.html)
  extending the first analysis to consider a more realistic network model where
  messages can be delayed arbitrarily; the conclusion is that to be able to have
  decent numbers of confirmations, one needs to have a good estimation on
  message delays
* [an analysis of mixed
  forks](https://blog.nomadic-labs.com/the-case-of-mixed-forks-in-emmy.html)
  showing that scenarios where an attacker tries to maintain a (malicious) fork
  for as long as possible do not have a significant impact on the [previous
  analysis](https://blog.nomadic-labs.com/emmy-in-the-partial-synchrony-model.html)

# The past and future of Emmy<sup>+</sup>

Before Emmy<sup>+</sup>, there was Emmy. In Emmy, the more endorsements in a
block, the fittest the block was. This design was somewhat problematic in that a
baker hesitated if to wait for more endorsements or to bake the block with the
endorsements it already had.

Emmy<sup>+</sup> addressed this problem by simply making fitness not depend on
the number of endorsements in a block: the fitness increases by 1 unit with each
level. In turn, the number of endorsements in a block reflects in the block
delay rule.

The rewards in Emmy<sup>+</sup> have been updated in Carthage to address
deflationary baking.

[Emmy<sup>&#9733;</sup> is
proposed](https://gitlab.com/tzip/tzip/-/merge_requests/134) to follow
Emmy<sup>+</sup>. offer faster finality, about twice as fast as in
Emmy<sup>+</sup>.
