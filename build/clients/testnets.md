# Testnets



Before putting new software in production, as a developer or baker, you need to test it in environments where trying and breaking things doesn't cost much, in terms of time, computing resources or even fees.

A number of possibilities are made available thanks to tools and services provided by the Tezos ecosystem. In this document, we will briefly introduce them, present their specificities, and what use cases they are suitable for.

### Testing without a node

If you are a smart contract developer, testing contracts is a big part of your work. More time is spent testing contracts than writing them. You will often need to test new versions of your contracts, and run many tests starting from their deployment to calling every entry point in all kinds of ways.

Waiting for the next block every time you inject a new transaction takes a lot of time.

To make testing a lot faster, options are available, depending on the the language and tools you are using, that don't use a network or even a single node at all, and skip all the consensus mechanism steps.

* The **michelson interpreter** is an OCaml function that can be used by tools to simulate a call to any entry point of any smart contract, given an initial value of the storage and parameters. Some programming languages like **Ligo** or **Smartpy** use this as part of their testing frameworks.
* The **mockup mode** of `tezos-client` can be used to test contract calls and other features such as some RPC calls, all without running an actual node, saving the time of going through the consensus mechanism and waiting to get blocks created and validated. Tools like **Completium**, built by the team behind the **Archetype** language, use this for ther testing framework. Find out more in the [documentation of the mockup mode](https://tezos.gitlab.io/user/mockup.html).

### Testing with local nodes

The **sandboxed mode** of `tezos-client` makes it possible to test your contracts or other projects while interacting with actual nodes, but without using a public test network or creating your own private network. In sandboxed mode, `tezos-client` can create one or more local nodes for this.

This is convenient if you want to run all your tests locally but in a mode where blocks are actually created through the consensus mechanism. In particular, if your contracts or tests must stay confidential until you decide to put them into production.

In this mode, you can't use public services such as public block explorers or indexers. You may however install your own.

Find out more in the [documentation of the sandboxed mode](https://tezos.gitlab.io/user/sandbox.html)

### Testing with a public test network

If you want to test in conditions that very closely resemble the main network, you can use one of a number of public networks.

These behave like `mainnet`, with a few differences:

* You can use faucets to obtain tez for free on these networks, so you don't need to (and can't) spend actual tez.
* There are fewer nodes and bakers than on `mainnet`.
* Tools like public block explorers or indexers may or may not be available, depending on the network.
* They don't follow the regular amendment process.
* Different test networks run on different versions of the protocol.

Depending on your needs, you may pick between the three types of networks listed below. In all cases, if you need to do intense testing, we recommend that you run your own nodes on these networks, as public nodes may have availability issues and limitations.

#### **Permanent test networks**

_Permanent test networks_ are networks that are meant to run indefinitely. In particular, they migrate to new versions of the protocol when proposals are adopted.

One difference with `mainnet` is that that the governance is controlled by a single entity that manages the network, with a special upgrade mechanism.

At the moment, the main such network is `ghostnet`. It follows the amendments of `mainnet`, and is controlled by the Oxhead Alpha team.

For developers, using a permanent network like `ghostnet` is convenient compared to other public networks, as it makes it possible to keep contracts running for a long time, and not having to deal with the trouble of setting things up on a new network when the previous ones gets shut down. Services such as indexers, explorers or public nodes also tend to keep running more reliably on `ghostnet` than on non-permanent networks.

For bakers, it is also a good idea to run tests on a permanent network, as it is the environment that is the closest to `mainnet`. On the other hand, as transactions and blocks keep accumulating over time, synchronizing with this network can take some time, and the context size gets bigger. This means testing a restart and resynchronization can be time and ressource consuming.

As the protocol on `ghostnet` migrates to the newly adopted amendment just a few hours or days before `mainnet`, it can serve as a dress-rehearsal for the actual migration on `mainnet` when this new protocol gets activated. Both bakers and developers can check that they are ready for the migration, and that nothing in their configuration breaks when it happens.

#### **Protocol test networks**

_Protocol test networks_ are networks that are created specifically for a given version of the protocol.

When an amendment is proposed, a corresponding network is usually created by the Oxhead Alpha team. This network gets joined by more bakers as the proposal is selected and moves through the different periods of the self-amendment process. If the protocol is not adopted, it usually gets discarded. Otherwise, it remains active until a different protocol is adopted.

This means there is usually one or two such running networks: one for the current version of the protocol running on `mainnet`, and possibly one for the proposed protocol that is going through the amendment process, if there is one.

Whether you are a developer or a baker, testing on the network for a new proposal before it potentially gets activated, enables you to check that all your software, smart contracts, dApps or other tools work well with this new proposal.

It also enables you to test any new features of this proposal, so that you can prepare to use them. This can also help you form your own opinion about this proposal and discuss it with the community before voting on it.

Once the protocol is activated, the corresponding protocol test network can be a good network for a baker to do some tests, with the current version of the protocol, and doing so on a network that is lightweight to bootstrap, and with reduced context sizes.

On the other hand, it may be less convenient for smart contract or dApp developers to use, as it has a limited life span, and tends to be less supported by services like indexers and other tools.

#### **Periodic test networks**

Periodic test networks are used by the developers, and in particular core developer teams to test new features as they are being developed, before they are even part of a new proposal.

Such networks are a very short life span, as they are often restarted as changes are made to the protocol and Octez suite.

Testing on such networks is useful for developers that need to test the latest features early, and prepare for tools that need to be ready early to support them.\
\
You can learn more in this [article](https://medium.com/the-aleph/continuous-tezos-protocol-testing-with-dailynet-and-mondaynet-92d4b084a9f6) on Mondaynet and Dailynet.

#### **Public nodes and faucets**

To connect to existing public nodes, for these networks, or get some fake tez on these nodes from a faucet, check [https://teztnets.xyz](https://teztnets.xyz/), a page maintained by [Oxhead Alpha](https://www.oxheadalpha.com/).

Other sources of public nodes include:

* [RPC Nodes](https://tezostaquito.io/docs/rpc\_nodes) from Ecad labs.
* [SmartPy nodes](https://smartpy.io/nodes).

### Testing with your own private network

In some special cases, you may want to run your own private network for your testing. This could be true if you are developing tools that you want to keep confidential until you put them in production, and if the `sandboxed mode` is not sufficient for your situation.

Check our Private blockchain section to learn how to setup your own network.

### Further reading

* Tezos reference:
  * [Test networks](https://tezos.gitlab.io/introduction/test\_networks.html)
  * [Mockup mode](https://tezos.gitlab.io/user/mockup.html)
  * [Sandboxed mode](https://tezos.gitlab.io/user/sandbox.html)
* Medium post: [Introducing ghostnet](https://medium.com/the-aleph/introducing-ghostnet-1bf39976e61f)
