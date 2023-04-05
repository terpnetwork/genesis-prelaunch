# Genesis Information

# **🚨Phase I: Network Gains Stability 🚨**

One of the core ideologies around blockchains is immutability. This is the idea that we don’t go back and edit past state transitions. While this notion of immutability is implemented directly via consensus protocols in the software, it is ultimately upheld by social contract among participants.

That said, the technology underlying Terp Network was intentionally developed to enable low-friction forks and rollbacks. We’ve seen the community practice these techniques numerous times on the test networks. It’s likely they will need to be used on a mainnet as well, in scenarios where community members create & integrate useful software logic.  Ultimately, they are how Terp Network can become future proof to innovations within cryptography and technology.

Reverting state is often seen as highly grievous, as it compromises the network’s economic finality. Hence it should only be used in extreme conditions, as witnessed in the case of Ethereum with the DAO Hard Fork. That said, in the early days of the Terp Network, all functions to add smart contract logic on chain are permissioned, and hence the severity of state reversions will be reduced, as state transitions will be much less “economically final”. If necessary in case of bugs, the state can be exported from a past height and the network restarted, as practiced on the testnets.

Once governance chooses to enable permissionless, the importance of economic finality must be respected by the network.

To summarize, if there are errors or vulnerabilities in the Terp Network in the days before transfers are enabled, users should expect arbitrary state rollbacks even to genesis. Once transfers are enabled, state rollbacks will be much more difficult to justify. 


---

## **What is a Genesis File**

A genesis file is a JSON file which defines the initial state of your blockchain. It can be seen as height 0 of your blockchain. The first block, at height 1, will reference the genesis file as its parent. The state defined in the genesis file contains all the necessary information, like initial token allocation, genesis time, default parameters, and more. Let us break down these information.

## **Genesis Time and Chain_id**

The genesis_time is defined at the top of the genesis file. It is a UTC timestamps which specifies when the blockchain is due to start. At this time, genesis validators are supposed to come online and start participating in the consensus process. The blockchain starts when more than 2/3rd of the genesis validators (weighted by voting power) are online.

The chain_id is a unique identifier for your chain. It helps differentiate between different chains using the same version of the software.


## **Consensus Parameters**

Next, the genesis file defines consensus parameters. Consensus parameters regroup all the parameters that are related to the consensus layer, which is Tendermint in the case of Terp Network. Let us look at these parameters:

 - block
     - max_bytes: Maximum number of bytes per block.
     - max_gas: Gas limit per block. Each transaction included in the block will consume some gas. The total gas used by transactions included in a block cannot exceed this limit.
 - evidence
     - max_age: An evidence is a proof that a validator signed two different blocks at the same height (and round). This is an explicitly malicious behaviour that is punished at the state-machine level. The max_age defines the maximum number of 
 - validator
     - pub_key_types: The types of pubkey (ed25519, secp256k1, ...) that are accepted for validators. Currently only ed25519 is accepted.
## **Application State**

The application state defines the initial state of the state-machine.

### **Genesis Transactions**

By default, the genesis file do not contain any gentxs. A gentx is a transaction that bonds staking token present in the genesis file under accounts to a validator, essentially creating a validator at genesis. The chain will start as soon as more than 2/3rds of the validators (weighted by voting power) that are the recipient of a valid gentx come online after genesis_time.

## Current Proposed Genesis Parameters Configuration

The current proposed genesis to be used to collect gentxs for Main Network 1 is located [here.](../gentxs/genesis.json) 

# Overview | Initial Validator Coordination

## **What is it?**

This validator set is computed from the set of signed gentx transactions during this genesis transaction, and initially includes various validators who were considered reputable by the TerpNET Foundation. This initial validator set will 

### What this means for users:

The Team will recommend a particular genesis file and software version, but there is no guarantee a network will ever start from it - nodes and validators may never come online, the community may disregard the recommendation and choose different genesis files, and/or they may modify the software in arbitrary ways. Such outcomes and many more are outside the teams control and completely in the hands of the community.

On initialization of the software, the Terp Network Bonded Proof-of-Stake system will kick in to determine the initial validator set (max TBD) from the set of gentx transactions. More than 2/3 of the voting power of this set must be online and participating in consensus in order to create the first block and start Terp Network.

We expect and hope that TERP holders will exercise discretion in initial staking to ensure the network does not ever become excessively centralized as we move steadily to the target of 66% TERPS staked. This is not a first of its kind experiment in bootstrapping a decentralized network, however other proof of stake networks have bootstrapped with the aid of a foundation or other administrator. We hope to bootstrap as a decentralized community, building on the shared experiences of many many testnets.

# **Phase II: Governance Consensus Begins**

Summary: Once mainnet is deemed sufficiently stable, bonded Terp holders will vote to decide whether or not Terp-Core functions like uploading contracts & others should be enabled. This procedure will happen through on-chain governance. 

The best way to check on the status of governance proposals is to view them through Terp explorers. A list of explorers can be found on the launch page: [*terp.network/launch*](https://terp.network/launch).

What this means for users: If the proposal is accepted and transfers are enabled, then it becomes possible to transfer This will not enable the transfers of vesting tokens, which most inital Terp Token holders will have. 

# **Disclaimer**

Terp Network is *highly* experimental software. In these early days, we can expect to have issues, updates, and bugs. The existing tools require advanced technical skills and involve risks which are outside of the control of the Terp Network and/or the TerpNET Foundation team . Any use of this open source Apache 2.0 licensed software is done at your *own risk and on a “AS IS” basis, without warranties or conditions of any kind*, and any and all liability of the teams for damages arising in connection to the software is excluded. **Please exercise extreme caution!**

Furthermore, it must be noted that it remains in the community's discretion to adopt or not to adopt the Genesis State that the TerpNET Foundation DAO recommends within the Genesis Block Software. Therefore, The dev team *cannot* guarantee that (i) TERPS will be created and (ii) the recommended allocation as set forth herein will actually take place.