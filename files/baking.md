# Baking

# What is baking? {#what}
Baking is how blocks are produced and validated on the Tezos blockchain. To bake blocks, you need to take part in [Tezos Proof-of-stake system](proofofstake.md#consensus), which requires a minimum of 8,000 XTZ (1 roll). The more XTZ you own, the higher your chances are at baking blocks and earning baking rewards. 

# What is delegating? {#delegate}
If someone does not have 8,000 XTZ or does not want to set up computing infrastructure to bake blocks, they may delegate their coins to a baker (aka "delegate"). Delegating lets coin holders (i.e. "delegators") "lend" their coins to a baker (i.e. a "delegate"), giving the baker a higher probability of being selected to bake and endorse blocks. In practice, bakers usually share the additional revenue generated from the delegated tokens with the coin holder. Importantly, this process does not actually transfer ownership of coins and hence the baker cannot spend or control the XTZ delegated to it, ensuring that bakers cannot appropriate the delegators' funds. 

# Should I bake or delegate? {#bakeordelegate}
Self-baking lets a baker earn a higher yield, but requires technical expertise and time in setting up a baker and running the baking software reliably with as little downtime as possible. By delegating Tezos tokens, a token holder avoids this process altogether but usually earns a lower yield. In the current protocol, token holders with less than 8,000 XTZ can only participate in baking by delegating to another baker.

# How much can I earn by baking or delegating? {#earn}
The current Tezos protocol increases the token supply by approximately 5.51% in the first year (based on constant block rewards of 16 XTZ/block and 2 XTZ/endorsement). 

This means that if **all** Tezos token holders bake with all of their tokens (i.e. the entire Tezos supply), baking rewards would be near ~5.51% per year. However, given variance in time preferences, knowledge, and capabilities, it is unlikely that all token holders will bake and the expected return on baking is in practice greater than 5.51% a year. By illustration, if 50% of the Tezos token supply is being staked, the baking reward will be closer to 11% (double the inflation rate).

In practice, the rewards for token holders who delegate are less than that of baking directly, because delegates share only part of their baking rewards with delegators. The portion they keep is often called a “fee” and ranges between 5% and 20%, varying by the baker. 

# How should I select a baker to delegate with? {#bakerselection}
First, use [Baking Bad](https://baking-bad.org/docs/where-to-stake-tezos) or [Tezos Nodes](https://tezos-nodes.com/) to browse through bakers. There are a few factors to consider when choosing a baker to delegate with:

1. **Fees**. How much of the rewards the baker is keeping? 
2. **Capacity**. Each baker has a capacity of how many coins it can accept, which is based on how many coins it currently holds itself. A baker is "overdelegated" when it has exceeded the amount of delegation it can take considering the coins they currently hold.    
3. **Reliability + Responsiveness**. Does this baker pay out on time? Does this baker pay correctly? Will this baker respond to my questions about their services? Many bakers operate forums and chat rooms in which they engage with delegators.
4. **Security**. Is this baker's staking setup secure? Does this baker have a track record? Has this baker double-baked in the past and lost coins?

# How do I setup a secure Baker? 
First, let's make sure you have the minimum requirements to run a node on your PC. It takes about 15 minutes to setup a node, just follow the step-by-step instructions and you will be be Baking in no time. Additionally, you can bake using an application called Kiln, in which you can easily setup a Baker through the GUI, but first let's go through the traditional route using command line. 

**System Requirements**
- Disk: 100 GB SSD (SSD is highly recommended over HDD)
- Memory: Recommended RAM for running a Tezos Node is 8GB
- CPU: Running with at least 2 cores is recommended
- Wallet: Hardware Security Modules (HSMs), such as a Ledger Nano S or X

Tezos nodes are run on many different systems, including AWS and Azure. For reference, we are offering two setups: one on Ubuntu Linux, which is suitable also for a 24x7x365 server, andone on macOS, which is suitable for learning about the Tezos ecosystem.

**Ubuntu Linux:**

**Install the libraries that Tezos is dependent on (~1 minute)**

```
sudo apt-get install build-essential git m4 unzip rsync curl
bubblewrap libev-dev libgmp-dev pkg-config libhidapi-dev
jbuilder -y
```
**Pull down the source code from the git repository (~1 minute)**

```
git clone https://gitlab.com/tezos/tezos.git
cd tezos
git checkout latest-release
git rev-parse HEAD
cd
```
> The resulting hash of “git rev-parse HEAD” should be the same as the one above and if you have a later version of the software then these instructions may not be complete.

**Install the OPAM the package manager for OCaml (~2 minutes)**

```
sudo add-apt-repository ppa:avsm/ppa
sudo apt update
sudo apt install opam
opam init
opam update
eval $(opam env)
```
> answer with ‘y’ or just return to all prompts

**Building Tezos from source (~4 minutes)**
> Note: When you run ‘make build-deps’ you will see: ‘[ERROR] No repository tezos found’, you can ignore this error.
```
cd tezos
make build-deps
make
```
> answer ‘y’ to all prompts

**Setting up your Tezos Node**

**Create the node identity (~1 minute)**

The identity information and chain are stored in the directory ./tezos-node in your home directory.

``./tezos-node identity generate``

**Start-up the node**

If you want to run the node and baking processes in their own process not attached to a
terminal process then install [screen](https://linuxize.com/post/how-to-use-linux-screen/). The advantage of using ‘screen’ is that the process
continues to run even if the terminal is closed.

`sudo apt install screen -y`

Run from a terminal (currently takes over a week to sync). You can also redirect the output to a
log file so you can monitor the process.


```
screen -S TezosMainNode
./tezos-node run --connections 20 --log-output $HOME/tezos.log`
Ctrl+a d
```


> The “Ctrl+a d” (press and hold down the control key and then press the letter a, release both
> and press the letter d) takes you out of the screen process but you can see the tezos node
> process running using the ps command.

`ps -ef | grep tezos`

To re-enter the screen process then you just re-attach to that screen. Useful if you want to kill
the process.

`screen -r TezosMainNode`

If you want to view the logs in real-time then you can tail the log file.

`tail -f $HOME/tezos.log`

**Generating a Tezos Key**

The keys are stored in the directory ./tezos-client in your home directory. This is an important
directory to backup. The -f option “forces” the key to be encrypted and so you will be prompted
for a password, without it will create an unencrypted key.

`./tezos-client gen keys my_account -f`

**Let’s start Baking!**

The first step is to activate the account for baking so that you start to get baking and
endorsement rights. It will take at least 2 cycles before you get rights in a snapshot and 5 cycles
before you start to bake (a cycle is just under 3 days). So once you have activated, you won’t
need to start your baker and endorsement processes for 21 days although it doesn’t matter if
you start them straight away so they are ready to go. You also need to fund your baking
address with at least 1 roll (1 roll = 8,000 tez); you don’t want to miss your first block or
endorsement!

`./tezos-client register key <baking_address> as delegate`

to run a baker, endorser, and accuser in screen processes then replace <baking_address> with
your baking address below.

```
screen -S TezosBaker
./tezos-baker-008-PsEDO run with local node ~/.tezos-node
<baking_address>
Ctrl+a d
screen -S TezosEndorser
./tezos-endorser-008-PsEDO run <baking_address>
Ctrl+a d
screen -S TezosAccuser
./tezos-accuser-008-PsEDO run
Ctrl+a d
```

**Using MacOS**

This section only applies to you if you want to bake using MacOS, most of the steps are the
same as above except you will need to install the package managers in order to set up your
node.

**Homebrew package manager (~1 minute)**

The macOS doesn’t have any installed package managers so the first step is to install the
homebrew package manager.

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

**Install the libraries that Tezos is dependent on (~1 minute)**

`brew install hidapi libev`

On Catalina you may see the following error if you have xcode installed:

`“xcrun: error: invalid active developer path(/Library/Developer/CommandLineTools), missing xcrun at:/Library/Developer/CommandLineTools/usr/bin/xcrun”`
If this is the case then run the following command to update your xcode install and restart the
terminal (~5 minutes)

`xcode-select --install`

You are now ready to go ahead and install the node from the instructions above!

# Do I need to sync the whole blockchain to set up a node? 

**Fast sync from a mainnet snapshot**

No! You don't need to sync the entire blockchain, a snapshot will allow you to sync the chain in a few minutes, when setting up a new node you will
by default download the entire history of the chain. You can skip this section if you are not starting
from a snapshot and syncing the full chain. If you do start a node from a snapshot then an
up-to-date snapshot can be downloaded from [Tezos Giganode](https://snapshots-tezos.giganode.io). An imported up-to-date
snapshot will bring the disk space down from 50GB to 12GB

# How do I particpate in the on-chain voting as Baker? 

**Voting**

With a baker up and running, a vital part of participation is voting on proposals to upgrade the
Tezos protocol. Proposals for Tezos go through a governance mechanism with 4 periods:
Proposal > Exploration > Testing > Promotion. You can track the latest proposals and learn
about Tezos governance at [Tezos Agora](https://www.tezosagora.org).

**When new proposals are injected you can vote with the following commands**

`tezos-client submit proposals for <YOUR_ADDRESS> <proposal_name>`

When submitting a proposal, the baker is also submitting a vote for that proposal, equivalent to
the number of rolls in its staking balance at the start of the period.

Once reaching a 5% Quorum in the proposal phase, then the proposal will go to the next phase
which is Exploration, which requires a baker to vote. If reaching quorum with ‘yay’, then testing
will apply which requires no action from the baker. After the testing phase, the proposal goes
through its final phase which is Promotion, which requires bakers to vote and reach quorum. If
the proposal reaches quorum with ‘yay’, then the proposal will automatically be implemented
and upgrade the Tezos protocol. The quorum is a minimum participation threshold; so if a baker
votes ‘yay’, ‘nay’, or ‘pass’, that contributes to the quorum of the governance mechanism.

Voting Command for Exploration and Promotion phase

`tezos-client submit ballot for <YOUR_ADDRESS> <proposal_name> <yay|nay|pass>`

# Baking with Kiln {#kiln}

[Kiln](https://tezos-kiln.org) is a tool for baking on the Tezos blockchain through an easy-to-use UI. Installing Kiln on
MacOS, Ubuntu, and other Debian Linux distributions is easy, intuitive, and does not require the
use of the command line. Kiln enables anyone to set up a Tezos node and start baking!

- [How to install Kiln on MacOS Catalina](https://medium.com/tezos-kiln/how-to-install-kiln-on-macos-catalina-ce0821f97dcf)
- [How to Install Kiln Ubuntu](https://medium.com/kiln/how-to-install-kiln-and-bake-on-ubuntu-a13d17df63c)

# Baking Resources {#resources}
- [Getting started with Tezos on the Ledger Nano S](https://medium.com/@obsidian.systems/getting-started-with-tezos-on-the-ledger-nano-s-c011517b0f3c)
- [Expected Rewards from Solo Baking Tezos](https://medium.com/cryptium/coquito-tezem-ergo-sum-expected-rewards-from-solo-baking-tezos-fcb4616b97dc)
- [Storing XTZ in Ledger Nano S while delegating](https://medium.com/cryptium/how-to-store-your-tezos-xtz-in-your-ledger-nano-s-and-delegate-with-tezbox-wallet-8fb4ac2d3355)
- [Double Baking -- How a baker can lose it's XTZ](https://medium.com/cryptium/half-baked-is-always-better-than-double-baked-what-is-at-stake-in-the-tezos-protocol-6619ce4a5f87)
