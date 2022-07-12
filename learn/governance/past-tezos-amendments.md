---
description: A list of past successful protocol upgrades and their features.
---

# Past Tezos Amendments

## ****[**Athens**](https://www.tezosagora.org/proposal/1) **(Pt24m4xiP)**

Athens was the first proposed protocol amendment for Tezos. Two proposals -  “[Athens A](https://forum.tezosagora.org/t/athens-a-pt24m4xip/29)” and “[Athens B](https://forum.tezosagora.org/t/athens-b-psd1ynubh/33)” were injected by the development team, [Nomadic Labs](https://blog.nomadic-labs.com/athens-our-proposals-for-the-first-voted-amendment.html) in February 2019.&#x20;

Of the two proposals, Athens A sought to increase the gas limit and reduce the roll size required to bake from 10,000 tez to 8,000 tez. Athens B sought to just increase the gas limit. Athens A was autonomously [activated](https://twitter.com/TezosAgoraBot/status/1133901612790034432?s=20) onto the protocol in May 2019.&#x20;

For a full list of changes be sure to read the corresponding blog [post](https://blog.nomadic-labs.com/athens-proposals-injected.html) from Nomadic Labs and [reflection](https://medium.com/tqtezos/reflecting-on-athens-the-first-self-amendment-of-tezos-4791ab3b1de1) by Jacob Arluck.&#x20;

## [**Babylon**](https://forum.tezosagora.org/t/babylon-2-0-1-psbabym1/1311) **(PsBABY5nk)**

The Babylon [proposal](https://forum.tezosagora.org/t/babylon-psbaby5nk/1171) was [injected](https://blog.nomadic-labs.com/babylon-proposal-injected.html) in August 2019 with contributions by development teams Nomadic Labs, Cryptium Labs (Metastate), and Marigold.&#x20;

Notable changes included a new consensus algorithm variant (Emmy+), addition of new Michelson features to aid smart contract developers, an account rehaul that enabled clearer distinction between tz and kt accounts, as well as refinements to the quorum formula and addition of a 5% proposed quorum threshold.&#x20;

Babylon was autonomously [activated](https://twitter.com/adrian\_brink/status/1185137422432161792?s=20) onto the protocol in October 2019.&#x20;

For a full list of changes be sure to read the corresponding blog posts from [Nomadic Labs](https://blog.nomadic-labs.com/babylon-proposal-injected.html), and [Cryptium Labs](https://medium.com/metastatedev/on-babylon2-0-1-58058d9d2106) (Metastate).&#x20;

## [**Carthage**](https://www.tezosagora.org/proposal/7) **(PtCarthav)**

The Carthage [proposal](https://forum.tezosagora.org/t/carthage-ptcarthav/1466) was [injected](https://twitter.com/adrian\_brink/status/1204447665230102529?s=20) in December 2019 with contributions by development teams Nomadic Labs and Cryptium Labs (Metastate).&#x20;

Notable changes included increasing the gas limit per block and operation by 30%, improving the accuracy of the formula used for calculating baking and endorsing rewards, as well as several minor improvements to Michelson.&#x20;

Carthage was autonomously [activated](https://twitter.com/tezos/status/1235590757416751105?s=20) onto the protocol in March 2020.&#x20;

For a full list of changes be sure to read the corresponding [changelog](https://tezos.gitlab.io/protocols/006\_carthage.html#changelog) and blog posts from [Nomadic Labs](https://blog.nomadic-labs.com/carthage-changelog-and-testnet.html) and [Cryptium Labs](https://medium.com/metastatedev/updating-the-potential-carthage-proposal-and-resetting-the-carthagenet-test-network-f413a792571f) (Metastate).&#x20;

## [**Delphi**](https://www.tezosagora.org/proposal/8) **(PsDELPH1K)**

The Delphi [proposal](https://forum.tezosagora.org/t/delphi-psdelph1k/2157) was [injected](https://twitter.com/CryptiumLabs/status/1301819142018826242?s=20) in September 2020 with contributions by development teams Nomadic Labs, Metastate, and Gabriel Alfour.&#x20;

Notable changes included improving the performance of the Michelson interpreter, improving gas costs by adjusting the gas model, reducing storage costs by 4x, and various other small fixes.&#x20;

Delphi was autonomously [activated](https://twitter.com/tezos/status/1326877616322859009?s=20) as the new Tezos protocol in November 2020.&#x20;

For a full list of changes be sure to read the corresponding [changelog](https://blog.nomadic-labs.com/delphi-changelog.html#007-delphi-changelog) and blog post from [Nomadic Labs](https://blog.nomadic-labs.com/delphi-official-release.html).&#x20;

## [**Edo**](https://www.tezosagora.org/proposal/9) **(PtEdoTezd)**

The Edo proposal was injected in November 2020 with contributions by Nomadic Labs, Metastate, and Gabriel Alfour.

Edo adds two major features for Tezos smart contracts

* Sapling and BLS12-381 to enable privacy-preserving smart contracts
* Tickets for native on-chain permissions and asset issuance

Among other features, Edo also updates the Tezos amendment process by lowering period length to 5 cycles and by adding a 5th Adoption Period. A full changelog is available [here](https://tezos.gitlab.io/protocols/008\_edo.html).

Edo was [activated](https://www.tezosagora.org/period/40) as the new Tezos protocol in February 2021.

## [Florence](https://www.tezosagora.org/period/46) (PsFLorena)

The Florence proposal was a joint effort from Nomadic Labs, Marigold, DaiLambda, and Tarides.

Florence's notable bug fixes and improvements are:

* Increasing maximum operation size
* Improved gas consumption for execution of more complex smart contracts
* Changing intercontract calls to a depth first ordering, as opposed to breadth first
* The elimination of the test chain activation

Baking Accounts were also included in the feature set, however, ongoing testing had uncovered some important and previously undocumented breaking changes in the Baking Account proposal. Baking Accounts should be postponed until a thorough audit of functionality is complete, or an alternative implementation produced. [The version of Florence without Baking Accounts is considered a safer choice.](https://blog.nomadic-labs.com/baking-accounts-proposal-contains-unexpected-breaking-changes.html)

A full changelog is available [here](http://doc.tzalpha.net/protocols/009\_florence.html).&#x20;

## [Granada](https://www.tezosagora.org/period/51) (PtGRAND)

The Granada proposal injected in May of 2021 was a joint effort from Nomadic Labs, Marigold, TQ, Tarides and DaiLambda.\
\
Granada contains several major improvements to the protocol, as well as numerous bug fixes and minor improvements:

* &#x20;**Emmy\*:** will generally halve the time between blocks, **from 60 seconds to 30 seconds**, allows transactions to achieve significantly faster finality than under the previous consensus algorithm.
* **Liquidity Baking:** will incentivize large amounts of decentralized liquidity provision between tez and tzBTC by minting a small amount of tez every block and depositing it inside of a constant product market making smart-contract.
* &#x20;**Gas improvements:** A number of substantial improvements to performance have been made, which in turn result in dramatic reductions in gas consumption. Improvements by a factor of 3 to 6 ( sometimes 8 ) have been improved. &#x20;

A full changelog can be found [here](http://doc.tzalpha.net/protocols/010\_granada.html).

## [Hangzhou](https://www.tezosagora.org/proposal/PtHangzHogokSuiMHemCuowEavgYTP8J5qQ9fQS793MHYFpCY3r/57) (PtHangzHo)



**Important: revision 011\_PtHangzH of protocol Hangzhou contains a bug that is corrected in the latest version 011\_PtHangz2**

The code can be found in the [src/proto\_011\_PtHangz2](https://gitlab.com/tezos/tezos/-/tree/master/src/proto\_011\_PtHangz2) directory of the `master` branch of Tezos.

The Hangzhou proposal features several major improvements to the protocol, as well as numerous minor improvements. Below, we present some of the most interesting and important changes:

* [New Environment Version (V3)](https://tezos.gitlab.io/protocols/011\_hangzhou.html#new-environment-version-v3)
* [Receipts, Balance Updates](https://tezos.gitlab.io/protocols/011\_hangzhou.html#receipts-balance-updates)
* [RPC Changes](https://tezos.gitlab.io/protocols/011\_hangzhou.html#rpc-changes)
* [Timelock](https://tezos.gitlab.io/protocols/011\_hangzhou.html#timelock)
* [Michelson On-Chain Views](https://tezos.gitlab.io/protocols/011\_hangzhou.html#michelson-on-chain-views)
* [Global Constants](https://tezos.gitlab.io/protocols/011\_hangzhou.html#global-constants)
* [Cache](https://tezos.gitlab.io/protocols/011\_hangzhou.html#cache)
* [Context Storage Flattening](https://tezos.gitlab.io/protocols/011\_hangzhou.html#context-storage-flattening)
* [Bug Fixes](https://tezos.gitlab.io/protocols/011\_hangzhou.html#bug-fixes)
* [Minor Changes](https://tezos.gitlab.io/protocols/011\_hangzhou.html#minor-changes)

A full changelog can be found[ here](https://tezos.gitlab.io/protocols/011\_hangzhou.html#protocol-hangzhou).

## [Ithaca](https://www.tezosagora.org/period/65) (Psithaca2)



**Important**: revision _PsiThaCaT…jVP_ of protocol Ithaca contains [bugs](https://research-development.nomadic-labs.com/announcing-ithaca-2.html) that have been corrected in the latest version _Psithaca2…z6A_.

The code can be found in the [src/proto\_012\_Psithaca](https://gitlab.com/tezos/tezos/-/tree/master/src/proto\_012\_Psithaca) directory of the `master` branch of Tezos.\
\
Ithaca most notably implemented the Tenderbake upgrade amongst other improvements. The details of which can be found here:&#x20;

* [New Environment Version (V4)](https://tezos.gitlab.io/protocols/012\_ithaca.html#new-environment-version-v4)
* [Tenderbake](https://tezos.gitlab.io/protocols/012\_ithaca.html#tenderbake)
* [Precheck of operations](https://tezos.gitlab.io/protocols/012\_ithaca.html#precheck-of-operations)
* [Michelson](https://tezos.gitlab.io/protocols/012\_ithaca.html#michelson)
* [Tickets Hardening (ongoing)](https://tezos.gitlab.io/protocols/012\_ithaca.html#tickets-hardening-ongoing)
* [Bug Fixes](https://tezos.gitlab.io/protocols/012\_ithaca.html#bug-fixes)
* [Minor Changes](https://tezos.gitlab.io/protocols/012\_ithaca.html#minor-changes)

A full changelog can be found [here](https://tezos.gitlab.io/protocols/012\_ithaca.html).\


## [Jakarta](https://www.tezosagora.org/period/71) (PtJakart2)



**Important**: revision _PtJakarta…nGw_ of protocol Jakarta contains [two critical bugs](https://research-development.nomadic-labs.com/we-found-two-bugs-in-torus-jakarta.html) that have been corrected in the latest version _PtJakart2…SqY_.

The code can be found in the [src/proto\_013\_PtJakart](https://gitlab.com/tezos/tezos/-/tree/master/src/proto\_013\_PtJakart) directory of the `master` branch of Tezos.\
\
The Jakarta protocol proposal includes Transaction Optimistic Rollups, fixes for Sapling integration, a Liquidity Baking toggle as well as:&#x20;

* [New Environment Version (V5)](https://tezos.gitlab.io/protocols/013\_jakarta.html#new-environment-version-v5)
* [Liquidity Baking](https://tezos.gitlab.io/protocols/013\_jakarta.html#liquidity-baking)
* [Transaction Optimistic Rollups](https://tezos.gitlab.io/protocols/013\_jakarta.html#transaction-optimistic-rollups)
* [Smart Contract Optimistic Rollups (ongoing)](https://tezos.gitlab.io/protocols/013\_jakarta.html#smart-contract-optimistic-rollups-ongoing)
* [Tickets Hardening](https://tezos.gitlab.io/protocols/013\_jakarta.html#tickets-hardening)
* [Voting procedure](https://tezos.gitlab.io/protocols/013\_jakarta.html#voting-procedure)
* [Breaking Changes](https://tezos.gitlab.io/protocols/013\_jakarta.html#breaking-changes)
* [Bug Fixes](https://tezos.gitlab.io/protocols/013\_jakarta.html#bug-fixes)
* [Minor Changes](https://tezos.gitlab.io/protocols/013\_jakarta.html#minor-changes)
* [Michelson](https://tezos.gitlab.io/protocols/013\_jakarta.html#michelson)
* [RPC Changes](https://tezos.gitlab.io/protocols/013\_jakarta.html#rpc-changes)
* [Internal](https://tezos.gitlab.io/protocols/013\_jakarta.html#internal)

A full changelog can be found[ here](https://tezos.gitlab.io/protocols/013\_jakarta.html).
