# Should I bake or delegate?

## Should I bake or delegate? <a id="bakeordelegate"></a>

Self-baking lets a baker earn a higher yield, but requires technical expertise and time in setting up a baker and running the baking software reliably with as little downtime as possible. By delegating Tezos tokens, a token holder avoids this process altogether but usually earns a lower yield. In the current protocol, token holders with less than 8,000 XTZ can only participate in baking by delegating to another baker.

## How much can I earn by baking or delegating? <a id="earn"></a>

The current Tezos protocol increases the token supply by approximately 5.51% in the first year \(based on constant block rewards of 16 XTZ/block and 2 XTZ/endorsement\).

This means that if **all** Tezos token holders bake with all of their tokens \(i.e. the entire Tezos supply\), baking rewards would be near ~5.51% per year. However, given variance in time preferences, knowledge, and capabilities, it is unlikely that all token holders will bake and the expected return on baking is in practice greater than 5.51% a year. By illustration, if 50% of the Tezos token supply is being staked, the baking reward will be closer to 11% \(double the inflation rate\).

In practice, the rewards for token holders who delegate are less than that of baking directly, because delegates share only part of their baking rewards with delegators. The portion they keep is often called a “fee” and ranges between 5% and 20%, varying by the baker.

## How should I select a baker to delegate with? <a id="bakerselection"></a>

[Baking Bad](https://baking-bad.org/docs/where-to-stake-tezos) or [Tezos Nodes](https://tezos-nodes.com/) allow you to browse through bakers. There are a few factors to consider when choosing a baker to delegate with:

1. **Fees**. How much of the rewards the baker is keeping? 
2. **Capacity**. Each baker has a capacity of how many coins it can accept, which is based on how many coins it currently holds itself. A baker is "overdelegated" when it has exceeded the amount of delegation it can take considering the coins they currently hold.    
3. **Reliability + Responsiveness**. Does this baker pay out on time? Does this baker pay correctly? Will this baker respond to my questions about their services? Many bakers operate forums and chat rooms in which they engage with delegators.
4. **Security**. Is this baker's staking setup secure? Does this baker have a track record? Has this baker double-baked in the past and lost coins?

## Baking Resources <a id="resources"></a>

### Baking Tools

Now that you have a Tezos baker running, welcome to the ecosystem! There are more

open-source tools available to automate processes and make your bakery running smoothly,

including an automated reward distributor for your delegates and a remote signer for

cloud-based HSMs such as Azure/ Amazon AWS.

**Rewards Distribution Tools**

* [https://github.com/tezos-reward-distributor-organization/tezos-reward-distributor](https://github.com/tezos-reward-distributor-organization/tezos-reward-distributor)
* [https://github.com/cryptiumlabs/backerei](https://github.com/cryptiumlabs/backerei)
* [https://github.com/TezosRio/taps](https://github.com/TezosRio/taps)
* [https://github.com/dakk/tezpool](https://github.com/dakk/tezpool)
* [https://github.com/figment-networks/tezos-batch-payments](https://github.com/figment-networks/tezos-batch-payments)

**Remote Signers**

* [Tezos Remote Signer](https://github.com/tacoinfra/remote-signer) - tacoinfra \(Github\)
* [Tezos Remote Signer](https://gitlab.com/polychainlabs/tezos-hsm-signer) - Polychain Engineering \(Gitlab\)
* [Tezos Remote Signer](https://github.com/tezzigator/azure-tezos-signer) \(Azure\) - Tezzigator \(Github\)
* [Tezos Remote Signer](https://github.com/ecadlabs/signatory) - Signatory by ECAD Labs \(Github\)

### Other Baking Resources

* [Getting started with Tezos on the Ledger Nano S](https://medium.com/@obsidian.systems/getting-started-with-tezos-on-the-ledger-nano-s-c011517b0f3c)
* [Expected Rewards from Solo Baking Tezos](https://medium.com/cryptium/coquito-tezem-ergo-sum-expected-rewards-from-solo-baking-tezos-fcb4616b97dc)
* [Storing XTZ in Ledger Nano S while delegating](https://medium.com/cryptium/how-to-store-your-tezos-xtz-in-your-ledger-nano-s-and-delegate-with-tezbox-wallet-8fb4ac2d3355)
* [Double Baking -- How a baker can lose it's XTZ](https://medium.com/cryptium/half-baked-is-always-better-than-double-baked-what-is-at-stake-in-the-tezos-protocol-6619ce4a5f87)

