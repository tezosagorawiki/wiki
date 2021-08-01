# Tezos Clients

## CLI and RPC

### Connecting to the network

The _tezos-client_ and Tezos RPC need to be connected to a Tezos node. You can connect to your own [tezos node](https://opentezos.com/deploy-a-node) or you can use a community node on the Tezos mainnet or testnet.

You can find a list of community nodes [here](https://tezostaquito.io/docs/rpc_nodes/).

If you use a testnet you can download a free faucet file with test XTZ on it [here](https://faucet.tzalpha.net/).

### Tezos RPC \(Remote Procedure Call\)

RPC [\[1\]](https://opentezos.com/tezos-basics/introduction_to_cli_and_rpc#references) is a client-server protocol where the requesting program is the client and the program providing the service is the server.

Tezos nodes provide a JSON/RPC interface to interact with the Tezos network. Note that although it uses RPC and is JSON based, it does not follow the `JSON-RPC` protocol.

A complete list of RPC calls is available [here](http://tezos.gitlab.io/shell/rpc.html#rpc-index-shell). Make sure to check the protocol version before using these calls. The calls available in the Edo protocol are available [here](http://tezos.gitlab.io/008/rpc.html#id1).

#### RPC call examples

**Get block**

This call is used to find all the information about a block. The associated metadata may not be present depending on the history mode and block's distance from the head.

`GET NodeUrl/chains/[chain_id]/blocks/[blocks_id]`

Example: To get the block number _1400114_ from the mainnet using giganode, do as follows:

`GET https://mainnet-tezos.giganode.io/chains/main/blocks/1400114`

**Get contract storage**

This call is used to access the storage of the contract.

`GET NodeUrl/chains/[chain_id]/blocks/[blocks_id]/context/contracts/[contract_id]/storage`

Example: To get the storage of contract _KT1Hkg5qeNhfwpKW4fXvq7HGZB9z2EnmCCA9_ from block number _1400114_ on the mainnet using giganode, do as follows:

`GET https://mainnet-tezos.giganode.io/chains/main/blocks/1400114/context/contracts/KT1Hkg5qeNhfwpKW4fXvq7HGZB9z2EnmCCA9/storage`

### Tezos-client \(CLI\)

_Tezos-client_ is the official client when interacting with a Tezos node via RPC. Let's take a look at some examples and how to use it.

#### How to install

* On Mac OS with [Homebrew](https://brew.sh/):

`$ brew install tezos-client`

* On Ubuntu with binaries:

`$ sudo add-apt-repository ppa:serokell/tezos && sudo apt-get update  
$ sudo apt-get install -y tezos-client`

* On Fedora with binaries:

`$ dnf copr enable -y @Serokell/Tezos && dnf update -y  
$ dnf install -y tezos-client`

* [From sources with OPAM](https://tezos.gitlab.io/introduction/howtoget.html#building-from-sources-via-opam).

#### Account activation

Activate your account by replacing `#accountName` and `#faucet` below with an account name and the path to your downloaded faucet file.

`$ tezos-client activate account #accountName with ~/Downloads/#faucet.json`

Example :

`$ tezos-client activate account user1 with ~/Downloads/tz1VH3sHQ5SNby95S9EtPQBqZrhgv2DqjPvy.json`

#### Client manual

* For global options

`$ tezos-client --help`

* For command options

`$ tezos-client [global options] command --help`

* For version information

`$ tezos-client --version`

The full documentation on _Tezos-client_ can be found [here](https://tezos.gitlab.io/008/cli-commands.html#cli-commands).

#### Client examples

This is a non-exhaustive list of possible commands with _tezos-client_. To discover more commands please refer to the [CLI manual](https://tezos.gitlab.io/008/cli-commands.html#cli-commands).

**Get balance**

To get the balance of your account you can execute the following command:

`$ tezos-client get balance for #accountName`

**Get timestamp**

This call is useful to check if the node is synchronized. It returns the UTC time of the latest downloaded block, timezones may differ from your local time.

`$ tezos-client get timestamp`

**List known addresses**

This call lists implicit accounts registered in your _tezos-client_.

`$ tezos-client list known addresses`

**List known contracts**

This call lists all accounts \(implicit and smart contract\) registered in your _tezos-client_.

`$ tezos-client list known contracts`

**Transfers and receipts**

The command line below makes a transaction of 42ꜩ from the account _user1_ to _user2_ \(you can also just use the tezos addresses directly\):

`$ tezos-client transfer 30 from user1 to user2 --burn-cap 0.5`

Notice that `--burn-cap` specifies the maximum fee the user is willing to pay for this operation. The actual fee is determined by the network.

You can also add `--dry-run` if you just want to practice by running a transaction simulation instead of a real transaction.

The recipe of this command is as follows:

`Current head: BM3smBpBVtHD (timestamp: 2021-03-12T09:42:28.000-00:00, validation: 2021-03-12T09:42:38.372-00:00)Node is bootstrapped.Estimated gas: 1000 units (will add 100 for safety)Operation successfully injected in the node.Operation hash is 'oo4745Q5mq8snHYAxUYWedBCVb7yQJ7jvFhKECPN9xqgwE4Ni8A'Waiting for the operation to be included...Operation found in block: BKnKoaYqCz3dTWr66x4X1mvXC95kuozRkdd23LDuM5ZA1ayF5mi (pass: 3, offset: 0)This sequence of operations was run: Manager signed operations: From: tz1gWQz5iTP6UDkWjm1jnKsCq1HHG4hgEmJn Fee to the baker: ꜩ0.000369 Expected counter: 1412932 Gas limit: 1100 Storage limit: 0 bytes Balance updates: tz1gWQz5iTP6UDkWjm1jnKsCq1HHG4hgEmJn ............. -ꜩ0.000369 fees(tz1aWXP237BLwNHJcCD4b3DutCevhqq2T1Z9,248) ... +ꜩ0.000369 Revelation of manager public key: Contract: tz1gWQz5iTP6UDkWjm1jnKsCq1HHG4hgEmJn Key: edpktpMjpmsK6fLKGrXzhp67tRdu2m5HyzGrp1tuS8ZJBc7dGqBeAq This revelation was successfully applied Consumed gas: 1000`

You can observe your actions on the block explorers :

* Mainnet: [https://tzstats.com](https://tzstats.com/)
* Edonet: [https://edo.tzstats.com](https://edo.tzstats.com/)
* DelphiNet: [https://delphi.tzstats.com](https://delphi.tzstats.com/)

### Tezos-admin-client

The admin client allows you to interact with the peer-to-peer layer in order to:

* check the status of the connections
* force connections to known peers
* ban/un-ban peers

#### How to install

* On Mac OS with [Homebrew](https://brew.sh/):

`$ brew install tezos-admin-client`

* On Ubuntu with binaries:

`$ sudo add-apt-repository ppa:serokell/tezos && sudo apt-get update$ sudo apt-get install -y tezos-admin-client`

* On Fedora with binaries:

`$ dnf copr enable -y @Serokell/Tezos && dnf update -y$ dnf install -y tezos-admin-client`

* [From sources with OPAM](https://tezos.gitlab.io/introduction/howtoget.html#building-from-sources-via-opam).

#### Admin-client manual

* Global options:

`$ tezos-admin-client --help`

* Command options:

`$ tezos-admin-client [global options] command --help`

* Version information:

`$ tezos-admin-client --version`

The full documentation on Tezos-admin-client can be found [here](https://tezos.gitlab.io/shell/cli-commands.html).

#### Admin-client examples

This is a non-exhaustive list of possible commands with tezos-admin-client. To discover more commands please refer to the [CLI manual](https://tezos.gitlab.io/shell/cli-commands.html).

**Commands for the low level RPC layer**

* List RPCs under a given URL prefix:

`$ tezos-admin-client rpc list [URL]`

* Get the input and the output JSON schemas of an RPC:

`$ tezos-admin-client rpc schema [HTTP method] [url]`

* Get the readable input and output formats of an RPC:

`$ tezos-admin-client rpc get [url]`

* Call an RPC with the POST method and input params:

`$ tezos-admin-client list protocols`

**Commands for managing protocols**

* List protocols known by the node:

`$ tezos-admin-client rpc post [url] with [input]`

* Inject a new protocol into the node: \(_given\_dir_ is the directory containing the sources of a protocol\)

`$ tezos-admin-client inject protocol [given_dir]`

**Commands to report the node's status:**

* The last heads that have been considered by the node:

`$ tezos-admin-client list heads [-o --output [path]]`

**Commands for editing and viewing the client's config file:**

* Show the current config file content and command line arguments:

`$ tezos-admin-client config show`

* Update the config based on the current CLI values:

`$ tezos-admin-client config update`

* A useful command to debug a node that is not syncing:

`$ tezos-admin-client tezos-admin-client p2p stat`

### 



