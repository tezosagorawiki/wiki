# Tezos Governance Overview



## An introduction to Tezos Governance <a href="#an-introduction-to-tezos-governance" id="an-introduction-to-tezos-governance"></a>

Tezos is a self-amending blockchain software which uses an on-chain process to propose, select, test, and activate protocol upgrades [without the need to hard fork](https://medium.com/tezos/there-is-no-need-for-hard-forks-86b68165e67d). In practice, this enables Tezos to improve itself over time via a structured, yet decentralized process while preserving a high level of consensus.

Tezos also allows stakeholders to upgrade the amendment process itself. As a result, details of the mechanism described below represent the current mechanism and are subject to change. This page will evolve as the network evolves.

### Voters / Bakers <a href="#voters--bakers" id="voters--bakers"></a>

Baking is how blocks are produced and validated on a Tezos blockchain using Liquid Proof-of-Stake. One can register to become a Baker once they have 6,000 ꜩ. After that the frequency with which they are selected to bake a block is proportional to their stake (including delegations).&#x20;

As the maintainers of a Tezos network, **bakers are also the voters in a Tezos formal upgrade process**, with their votes proportional to the size of their stake (including delegations).

### Delegators <a href="#delegators" id="delegators"></a>

If someone does not have 6,000 ꜩ or does not want to set up computing infrastructure to bake blocks, they may delegate their tokens to a baker. The baker does not own or control the delegated tokens in any way. In particular, it cannot spend them. However, if and when one of these tokens is randomly selected to bake a block, that right will belong to the baker. In practice, bakers usually share the additional revenue generated from the delegated tokens with the coin holder.

### The Five Stages of Tezos Governance <a href="#the-four-stages-of-tezos-governance" id="the-four-stages-of-tezos-governance"></a>

The self-amendment process is split into 5 periods: Proposal Period, Exploration Vote Period, Cooldown Period, Promotion Vote Period, and Adoption Period. Each of these five periods lasts five baking cycles (i.e.  40,960 blocks or roughly 14 days, 5 hours), comprising roughly 2 months and 10 days.

As summarized in the flowchart diagram below, any failure to proceed to the subsequent period reverts the network back to a Proposal Period. In other words, failure to proceed restarts the entire amendment process.

#### Proposal Period <a href="#proposal-period" id="proposal-period"></a>

The Tezos amendment process begins with the Proposal Period, during which bakers can submit proposals on-chain using the _proposals_ operation, which involves specifying one or multiple protocol hashes, each one representing a tarball of concatenated .ml/.mli source files.

Bakers may submit up to 20 proposals in each Proposal Period. When submitting a proposal, the baker is also submitting a vote for that proposal, equivalent to the number of rolls in its staking balance at the start of the period.

For those wanting to follow along, Tezos Agora and other Tezos block explorers such as [TzStats](https://tzstats.com/) allow you to watch incoming proposals.

Other bakers can then vote on proposals by submitting _proposals_ operations of their own. As described in the [whitepaper](https://tezos.com/static/white\_paper-2dc8c02267a8fb86bd67a108199441bf.pdf), the Proposal Period vote is done via approval voting, meaning each baker may vote once on up to 20 proposals. Think of it as a form of “upvoting.”

At the end of the Proposal Period, the network counts the proposal votes. For any proposal to be considered valid, it must have enough upvotes to meet a 5% quorum. If the most upvoted proposal has at least 5% of the number of possible votes supporting it, the proposal proceeds to the Exploration Period. If the 5% quorum is not met, no proposals have been submitted, or there is a tie between proposals, the amendment process resets to a new Proposal Period.

#### Exploration Period <a href="#exploration-period" id="exploration-period"></a>

In the Exploration Period, bakers may vote on the top-ranked proposal from the previous Proposal Period using the _ballot_ operation. Bakers get to vote either "Yay", "Nay", or "Pass" on a specific proposal. "Pass" just means to abstain from voting for or against a proposal. As in the Proposal Period, a baker's vote is based on the number of rolls in its staking balance at the start of the period.

At the end of the Exploration Period, the network counts the votes. If voting participation meets the quorum, and an 80% supermajority of non-abstaining bakers approves, the proposal proceeds to the Testing Period.

If the voting participation fails to achieve the quorum or the 80% supermajority is not met, the amendment process restarts to the beginning of the Proposal Period.

Regardless of the outcome of the vote, the quorum is updated based on past participation rates.

****\
**Cooldown period**

On-chain nothing specific happens during this period. Off-chain the delegates can read the proposal with more scrutiny, the community can discuss finer points of the proposal, the developers can perform additional tests, etc.

At the end of this period, the process moves to the **promotion period**.

#### Promotion Period <a href="#promotion-period" id="promotion-period"></a>

At the end of the Testing Period, the Promotion Period begins. In this period, the network decides whether to adopt the amendment based on off-chain discussions and its behavior during the Testing Period. As in the Exploration Period, bakers submit their votes using the _ballot_ operation, with their votes weighted proportionally to the number of rolls in their staking balance.

At the end of the Promotion Period, the network counts the number of votes. If the participation rate reaches the quorum and an 80% supermajority of non-abstaining bakers votes “Yay,” then the proposal is activated as the new mainnet.

Regardless of the outcome of the vote, the process reverts back to the Proposal Period and the quorum is updated based on past participation rates.

#### Adoption Period

The Adoption Period provides a "cool-down" allowing developers and bakers some additional time to adapt their code and infrastructure to the upgrade based on the results of the Promotion Vote Period. Adoption period: at the end of the period the proposal is activated as the new protocol and we go back to a proposal period.

Following the adoption period the protocol is activated. After this step the blocks added to the chain are interpreted in the newly activated protocol. As a result gas costs (and other such details of operation inclusion) may differ.

### The Supermajority and Quorum Requirements <a href="#the-supermajority-and-quorum-requirements" id="the-supermajority-and-quorum-requirements"></a>

#### Proposal Period <a href="#proposal-period-1" id="proposal-period-1"></a>

A proposal submitted during a Proposal Period needs to reach a quorum (minimum participation rate) in order to advance to the Exploration Period.

**Quorum requirement:** The number of votes for the most upvoted proposal divided by the number of possible votes must be greater than or equal to 5%.

#### Exploration & Promotion Periods <a href="#exploration--promotion-periods" id="exploration--promotion-periods"></a>

A vote during a voting period (Exploration & Promotion) needs to reach both a supermajority and a quorum (minimum participation rate) in order to succeed.

**Supermajority requirement:** The number of "Yay" votes divided by the number of "Yay" and "Nay" votes must be greater than or equal to 80%.

**Quorum requirement:** The number of "Yay", "Nay", and "Pass" votes divided by the number of possible votes must be greater than or equal to the current quorum.

Unlike the supermajority requirement which is fixed at 80%, the quorum requirement is updated at the end of each voting period using the following formula, where Q is the quorum in the voting period and q is the participation rate in the voting period:

In other words, the quorum tries to match the exponential moving average of the past participation rate.\


![](https://www.tezosagora.org/static/quorum\_average\_formula.26d43be1.png)

Second, the quorum for the given period (Qt) is calculated with the following parameters:

* t : current voting period
* A(t) : average participation in the current period
* 𝑞⋀ : minimum quorum (lower cap), currently set to 20%
* 𝑞⋁ : maximum quorum (upper cap), currently set to 70%

![](https://www.tezosagora.org/static/quorum\_update\_formula.1716f4d7.png)

More details about the quorum calculation can be found in this [Medium post](https://medium.com/metastatedev/meanwhile-at-cryptium-labs-1-part-ii-607227fc6d65).

### Flowchart of the Tezos Amendment Process <a href="#flowchart-of-the-tezos-amendment-process" id="flowchart-of-the-tezos-amendment-process"></a>

![](https://www.tezosagora.org/static/Tezos\_governance\_mechanism.2e932662.png)

## Tezos Client Commands <a href="#commands" id="commands"></a>

### Voting During a Proposal Period <a href="#proposals" id="proposals"></a>

```
$ tezos-client submit proposals for <delegate> <proposal1> <proposal2> ...
```

### Voting During an Exploration or Promotion Period <a href="#ballot" id="ballot"></a>

```
$ tezos-client submit ballot for <delegate> <proposal> <yay|nay|pass>
```

### Checking the Status of a Voting Period <a href="#status" id="status"></a>

```
$ tezos-client show voting period
```

## Additional Resources <a href="#additional-resources" id="additional-resources"></a>

* [The Voting Process](https://tezos.gitlab.io/whitedoc/voting.html) from Nomadic Labs
* [Amending Tezos](https://medium.com/tezos/amending-tezos-b77949d97e1e) from Jacob Arluck
  * [Chinese translation](https://tezos.org.cn/amendingtezos/)
