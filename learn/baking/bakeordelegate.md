# Should I bake or delegate?

## Should I bake or delegate? <a href="#bakeordelegate" id="bakeordelegate"></a>

Self-baking lets a baker earn a higher yield, but requires technical expertise and time in setting up a baker and running the baking software reliably with as little downtime as possible. By delegating Tezos tokens, a token holder avoids this process altogether but usually earns a lower yield. In the current protocol, token holders with less than 6,000 XTZ can only participate in baking by delegating to another baker.

## How much can I earn by baking or delegating? <a href="#earn" id="earn"></a>

There are three kinds of rewards: baking rewards, endorsing rewards, and a bonus for including extra endorsements.

The baking rewards are treated in the same way as fees: they go to the _payload_ producer and are distributed immediately.

To encourage fairness and participation, the _block_ proposer receives a bonus for the extra endorsements it includes in the block. The bonus is proportional to the number of validator slots above the threshold of $$⌈CONSENSUS_COMMITTEE_SIZE×23⌉$$ that the included endorsements represent. The bonus is also distributed immediately.

The endorsing rewards are distributed at the end of the cycle. The endorsing reward may be received even if not all of the validator’s endorsements are included in a block and is proportional to the validator’s active stake (in other words, to its _expected_ number of validator slots, and not its actual number of slots). However, two conditions must be met:

> * the validator has revealed its nonce, and
> * the validator has been present during the cycle.

Not giving rewards in case of missing revelations is not new as it is [adapted](https://tezos.gitlab.io/jakarta/proof\_of\_stake.html#random-seed-jakarta) from Emmy\*. The second condition is new. We say that a delegate is _present_ during a cycle if the endorsing power (that is, the number of validator slots at the corresponding level) of all the endorsements included by the delegate during the cycle represents at least `MINIMAL_PARTICIPATION_RATIO` of the delegate’s expected number of validator slots for the current cycle (which is `BLOCKS_PER_CYCLE * CONSENSUS_COMMITTEE_SIZE * active_stake / total_active_stake`).

Regarding the concrete values for rewards, we first fix the total reward per level, call it `total_rewards`, to `80 / blocks_per_minute` tez. Assuming `blocks_per_minute = 2`, `total_rewards` is 40 tez. We define:

* `BAKING_REWARD_FIXED_PORTION := baking_reward_ratio * total_rewards`
* `bonus := (1 - baking_reward_ratio) * bonus_ratio * total_rewards` is the max bonus
* `endorsing_reward := (1 - baking_reward_ratio) * (1 - bonus_ratio) * total_rewards`

where:

* `baking_reward_ratio` to `1 / 4`,
* `bonus_ratio` to `1 / 3`.

Thus, we obtain `BAKING_REWARD_FIXED_PORTION = 10` tez, (maximum) `bonus = 10` tez, and `endorsing_rewards = 20` tez. The bonus per additional endorsement slot is in turn `bonus / (CONSENSUS_COMMITTEE_SIZE / 3)` (because there are at most `CONSENSUS_COMMITTEE_SIZE / 3` validator slots corresponding to the additional endorsements included in a block). The rewards per endorsement slot are `endorsing_rewards / CONSENSUS_COMMITTEE_SIZE`. Assuming `CONSENSUS_COMMITTEE_SIZE = 7000`, we obtain a bonus per slot of `10 / (7000 / 3) = 0.004286` tez and an endorsing rewards per slot of `20 / 7000 = 0.002857` tez.

Let’s take an example. Say a block has round 1, is proposed by delegate B, and contains the payload from round 0 produced by delegate A. Also, B includes endorsements with endorsing power `5251`. Then A receives the fees and 10 tez (the `BAKING_REWARD_FIXED_PORTION`) as a reward for producing the block’s payload. Concerning the bonus, given that `CONSENSUS_COMMITTEE_SIZE = 7000`, the minimum required validator slots is `4667`, and there are `2333 = 7000 - 4667` additional validator slots. Therefore B receives the bonus `(5251 - 4667) * 0.004286 = 2.503` tez. (Note that B only included endorsements corresponding to 584 = 5251 - 4667 additional validator slots, about a quarter of the maximum 2333 extra endorsements it could have theoretically included.) Finally, consider some delegate C, whose active stake at some cycle is 5% of the total stake. Note that his expected number of validator slots for that cycle is `5/100 * 8192 * 7000 = 2,867,200` slots. Assume also that the endorsing power of C’s endorsements included during that cycle has been `3,123,456` slots. Given that this number is bigger than the minimum required (`2,867,200 * 2 / 3`), it receives an endorsing reward of `2,867,200 * 0.002857 = 8191.59` tez for that cycle.

\


## How should I select a baker to delegate with? <a href="#bakerselection" id="bakerselection"></a>

[Baking Bad](https://baking-bad.org/docs/where-to-stake-tezos) or [Tezos Nodes](https://tezos-nodes.com/) allow you to browse through bakers. There are a few factors to consider when choosing a baker to delegate with:

1. **Fees**. How much of the rewards the baker is keeping?&#x20;
2. **Capacity**. Each baker has a capacity of how many coins it can accept, which is based on how many coins it currently holds itself. A baker is "overdelegated" when it has exceeded the amount of delegation it can take considering the coins they currently hold.   &#x20;
3. **Reliability + Responsiveness**. Does this baker pay out on time? Does this baker pay correctly? Will this baker respond to my questions about their services? Many bakers operate forums and chat rooms in which they engage with delegators.
4. **Security**. Is this baker's staking setup secure? Does this baker have a track record? Has this baker double-baked in the past and lost coins?
