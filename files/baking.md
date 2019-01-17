# Baking

# What is baking? {#what}
Baking is the way blocks are produced on the Tezos blockchain. To bake blocks, you need to take part in the [Tezos Proof-of-stake system](files/proofofstake.md#consensus), which requires a minimum of 10,000 XTZ. The more XTZ you own, the higher your chances are at baking blocks and earning baking rewards. 

# How much can I earn by baking or delegating? {#earn}
The Tezos protocol inflates tokens by approximately 5.5% a year. This means that if *everyone* who owns XTZ bakes, each person will earn ~5.5% a year. However, not everyone bakes, so your expected return on baking should be more than 5.5% a year. If 50% of XTZ is staked, your return from baking should be approximately 10.6%.

The rewards from delegating is less than that of baking because you are delegating your coins to another baker and having a revenue share agreement. Usually, bakers charge upwards of 10% fees on baking rewards. 

# Should I bake or delegate? {#bakeordelegate}
Baking lets you earn a higher yield, but requires technical expertise in setting up a server and running the baking software 24/7 with as little downtime as possible. By delegating your coins to a baker, you avoid this process altogether but you earn a lower yield as a result. If you have less than 10,000 XTZ, your only option to stake is by delegating to another baker.

A list of bakers can be found at [this page](https://mytezosbaker.com/) for you to compare fees and decide which baker to delegate your coins to. 

# What is the difference between implicit and originated accounts? {#implicit}
Implicit accounts are accounts that can take part in the baking process. Implicit accounts can bake with its own coins as well as the coins delegated by other people. 

Originated coins cannot bake directly, but can delegate their coins to an implicit account. Originated accounts use their manager key to specify a delegate key, which is the same as choosing a delegate to represent the

# How should I select a baker to delegate with? {#bakerselection}
First, use [this page](https://mytezosbaker.com/) to browse through bakers. There a few factors to consider when choosing a baker to delegate with:

1. **Fees**. How much fees is this baker charging? 
2. **Capacity**. Each baker has a capacity of how many coins it can accept, which is based on how many coins it currently holds itself. 
3. **Reliability + Customer Support**. Does this baker pay out on time? Will this baker respond to my questions about their services? 
4. **Security**. Is this baker's staking setup secure? Does this baker have a track record? Has this baker double baked in the past and lost coins?

# Baking Resources {#resources}
- [Expected Rewards from Solo Baking Tezos](https://medium.com/cryptium/coquito-tezem-ergo-sum-expected-rewards-from-solo-baking-tezos-fcb4616b97dc)
- [Storing XTZ in Ledger Nano S while delegating](https://medium.com/cryptium/how-to-store-your-tezos-xtz-in-your-ledger-nano-s-and-delegate-with-tezbox-wallet-8fb4ac2d3355)
- [Double Baking -- How a baker can lose it's XTZ](https://medium.com/cryptium/half-baked-is-always-better-than-double-baked-what-is-at-stake-in-the-tezos-protocol-6619ce4a5f87)