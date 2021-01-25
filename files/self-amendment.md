# Self Amendment

# What is Self Amendment? {#introduction}

Tezos is a self-amending blockchain network which incorporates an on-chain mechanism for proposing, selecting, testing, and activating protocol upgrades without the need to hard fork.

In simple terms, this means that Tezos is a blockchain that can improve itself over time by having a formalized process for protocol upgrades. In practice, this is similar to the structure of a corporation, where shareholders get to vote on the direction of the company. 

Many other blockchains do not have this type of formal governance structure, so the direction of these projects are often decided by a small group of developers or by a foundation, which may or may not represent all stakeholders fairly. 

# How Does It Work? {#how}

The self amendment process is split into 4 periods: Proposal Period, Exploration Vote Period, Testing Period and Promotion Vote Period. Each of these four periods lasts eight baking cycles (i.e. 32,768 blocks or roughly 22 days, 18 hours), comprising almost exactly three months from proposal to activation.

Should there be any failure to proceed for a period, the whole process reverts to the Proposal Period, effectively restarting the whole process.

![](../img/self-amendment.png)

## 1. Proposal Period

The Tezos amendment process begins with the Proposal Period, during which bakers can submit proposals on-chain. The baker submits the proposal by submitting the hash of the source code.

In each Proposal Period, bakers can submit up to 20 proposals. A proposal submission also counts as a vote, which is equivalent to the number of rolls in its staking balance at the start of the period. Other bakers can then vote on the proposals by during the Proposal Period up to 20 times.

At the end of the Proposal Period, the network counts the proposal votes and the most-upvoted proposal proceeds to the Exploration Vote Period. If no proposals have been submitted or if there is a tie between proposals, a new Proposal Period begins.

## 2. Exploration Vote Period

In the Exploration Vote Period, bakers may vote on the top-ranked proposal from the previous Proposal Period. Bakers get to vote either "Yay", "Nay", or "Abstain" on a specific proposal. "Abstain" just means to "not vote" on a proposal. As in the Proposal Period, a baker's vote is based on the number of rolls in its staking balance.

At the end of the Exploration Vote Period, the network counts the votes. If voting participation (the total of “Yay,” “Nay,” and “Abstains”) meets the target, and an 80% majority of non-abstaining baker approves, the proposal proceeds to the Testing Period.

The voting participation target tries to match the exponential moving average of the past participation rate. If the voting participation fails to achieve the target or the 80% supermajority are not met, the amendment process restarts to the beginning of the Proposal Period

## 3. Testing Period

If the proposal is approved in the Exploration Vote Period, the Testing Period begins with a testnet fork that runs in parallel to the main network for 48 hours. These forks have access to the standard library, but are sandboxed.

This Testing Period is used to determine whether a proposal is a worthy amendment to the protocol. The testnet fork ensures the upgrade does not corrupt the blockchain network, should the upgrade be adopted, the network would continue making valid state transitions.

## 4. Promotion Vote Period

At the end of the Testing Period, the Promotion Vote Period begins. In this period, the network decides whether to adopt the amendment based on off-chain discussions and its behavior during the Testing Period. As in the Exploration Vote Period, bakers submit their votes using the ballot operation, with their votes weighted proportionally to the number of rolls in their staking balance.

At the end of the Promotion Vote Period, the network counts the number of votes. If the participation rate reaches the minimum quorum and an 80% supermajority of non-abstaining bakers votes “Yay,” then the proposal is activated as the new mainnet. Otherwise, the process once more reverts back to the Proposal Period. The minimum vote participation rate is set based on past participation rates.

See [the full details of the governance process](https://medium.com/tezos/amending-tezos-b77949d97e1e).

# Off-chain governance {#offchain}

[Tezos Agora](https://www.tezosagora.org) provides off-chain discussion forum and explorer for community members and bakers.

# Arguments for and against on-chain governance {#arguments}
To get a sense of the various arguments for and against on-chain governance, here is a good list of resources to understand the different viewpoints:

- [Blockchain Governance: Programming Our Future](https://medium.com/@FEhrsam/blockchain-governance-programming-our-future-c3bfe30f2d74) by Fred Ehrsam 
- [Against on-chain governance](https://medium.com/@Vlad_Zamfir/against-on-chain-governance-a4ceacd040ca) by Vlad Zamfir
- [Blockchains should not be democracies](https://hackernoon.com/blockchains-should-not-be-democracies-14379e0e23ad) by Haseeb Qureshi
- [Blockchains are not startups](https://medium.com/tezos/blockchains-are-not-startups-16449e210a61) by Jacob Arluck
- [Notes on Blockchain Governance](https://vitalik.ca/general/2017/12/17/voting.html) by Vitalik Buterin
- [Governance, Part 2: Plutocracy Is Still Bad](https://vitalik.ca/general/2018/03/28/plutocracy.html) by Vitalik Buterin
- [Debate on Blockchain Governance Podcast](https://www.zeroknowledge.fm/52) with Gavin Wood & Vlad Zamfir
- [Web3 Summit Governance Panel with Vlad Zamfir, Gavin Wood, Arthur Breitman & Adrian Brink](https://www.youtube.com/watch?v=eO3fG_1YrE4) with Gavin Wood, Vlad Zamfir, & Arthur Breitman
- [Conspiratus Podcast #1: Protocol Governance with Vlad Zamfir and Arthur Breitman](https://www.youtube.com/watch?v=IDY_inT-q0U) with Arthur Breitman, Vlad Zamfir, Sunny Aggrawal, & Nate Rush
- [Epicenter #259 Gavin Wood: Substrate, Polkadot and the Case for On-Chain Governance](https://www.youtube.com/watch?v=eP4mT19S_jg) with Gavin Wood
