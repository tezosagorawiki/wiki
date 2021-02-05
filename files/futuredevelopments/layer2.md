# Layer 2 {#layer2}


### zkChannels
zkChannels is a Lightning-like protocol that enables scalable and anonymous off-chain transactions using a combination of commitments, blind signatures and efficient zero-knowledge proof techniques (in addition to multi-party computation techniques). In particular, for Tezos, zkChannels rely on a randomizable blind signature scheme with efficient zero-knowledge protocols. The randomizable signature scheme is based on [Pointcheval-Sanders (PS)](https://eprint.iacr.org/2015/525.pdf) and instantiated on the BLS12-381 curve as well.

For some background, zkChannels allows a customer and a merchant to open an asymmetric payment channel (unlike Lightning). The merchant is at most pseudonymous and remains identifiable across all channels; the customer is at most pseudonymous during channel establishment and closure, but has the ability to make payments anonymously as long as they have an open channel with sufficient balance. That is, the customer’s anonymity set for a payment is the set of all customers with whom the given merchant has a channel open.

All payments must be initiated by the customer and the anonymous channels are bi-directional only in the sense that payment values can be positive or negative. At any point while the channel is open, the merchant or customer are able to initiate channel closure.

* zkChannels library implementation for Tezos is [here](https://github.com/boltlabs-inc/libzkchannels)
* Tutorial for testing the contract in a Tezos sandbox is [here](https://github.com/boltlabs-inc/libzkchannels/blob/master/tezos-sandbox/tutorial_pt1_setup.md)
* An implementation of PS signature verifier for Tezos exists (via SmartPy) in [here](https://github.com/boltlabs-inc/libzkchannels/blob/master/tezos-sandbox/tests_python/zkchannels_contract_v2/zkchannel_smartpy_script.py)

zkChannels is still being actively developed, led by [Bolt Labs, Inc](https://boltlabs.tech).

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
