# Genesis Information

# **🚨Phase I: Network Gains Stability 🚨**

One of the core ideologies around blockchains is immutability. This is the idea that we don’t go back and edit past state transitions. While this notion of immutability is implemented directly via consensus protocols in the software, it is ultimately upheld by social contract among participants.

That said, the technology underlying Terp Network was intentionally developed to enable low-friction forks and rollbacks. We’ve seen the community practice these techniques numerous times on the test networks. It’s likely they will need to be used on a mainnet as well, in scenarios where community members create & integrate useful software logic. Ultimately, they are a countervailing force to the risk of cartel takeover.

Reverting state is often seen as highly grievous, as it compromises the network’s economic finality. Hence it should only be used in extreme conditions, as witnessed in the case of Ethereum with the DAO Hard Fork. That said, in the early days of the Terp Network, transfers will not be active, and hence the severity of state reversions will be reduced, as state transitions will be much less “economically final”. If necessary in case of bugs, the state can be exported from a past height and the network restarted, as practiced on the testnets.

Once governance chooses to enable transfers, the importance of economic finality must be respected by the network.

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

### **Genesis Accounts**

In this section, initial allocation of tokens is defined. It is possible to add accounts manually by directly editing the genesis file, but it is also possible to use the following command:

```
terpd add-genesis-account <account-address> <amount><denom>
```

This command creates an item in the accounts list, under the app_state section.

 - `sequence_number`: This number is used to count the number of transactions sent by this account. It is incremented each time a transaction is included in a block, and used to prevent replay attacks. Initial value is 0.
 - `account_number`: Unique identifier for the account. It is generated the first time a transaction including this account is included in a block.
 - `original_vesting`: Vesting is natively supported by terpd. You can define an amount of token owned by the account that needs to be vested for a period of time before they can be transferred. Vested tokens can be delegated. Default value is null.
 - `delegated_free`: Amount of delegated tokens that can be transferred after they've been vested. Most of the time, will be null in genesis.
 - `delegated_vesting`: Amount of delegated tokens that are still vesting. Most of the time, will be null in genesis.
 - `start_time`: Block at which the vesting period starts. 0 most of the time in genesis.
 - `end_time`: Block at which the vesting period ends. 0 if no vesting for this account.
### **Bank**

The bank module handles tokens. The only parameter that needs to be defined in this section is whether transfers are enabled at genesis or not.

### **Staking**

The staking module handles the bulk of the Proof-of-Stake logic of the state-machine. This section should look like the following:

Let us break down the parameters:

 -`pool`
     - `not_bonded_tokens:` Defines the amount of tokens not bonded (i.e. delegated) in genesis. Generally, it equals the total supply of the staking token (uatom in this example).
     - `bonded_tokens:` Amount of bonded tokens in genesis. Generally 0.
 - `params`
     - `unbonding_time:` Time in 
     - `max_validators:` Maximum number of active validators.
     - `max_entries:` Maximum unbonding delegations and redelegations between a particular pair of delegator / validator.
     - `bond_denom:` Denomination of the staking token.
 - `last_total_power:` Total amount of voting power. Generally 0 in genesis (except if genesis was generated using a previous state).
 - `last_validator_powers:` Power of each validator in last known state. Generally null in genesis (except if genesis was generated using a previous state).
 - `validators:` List of last known validators. Generally null in genesis (except if genesis was generated using a previous state).
 - `bonds:` List of last known delegation. Generally null in genesis (except if genesis was generated using a previous state).
 - `unbonding_delegations:` List of last known unbonding delegations. Generally null in genesis (except if genesis was generated using a previous state).
 - `redelegations:` List of last known redelegations. Generally null in genesis (except if genesis was generated using a previous state).
 - `exported:` Wether this genesis was generated using the export of a previous state.
### **Mint**

The mint module governs the logic of inflating the supply of token. The mint section in the genesis file looks like the follwing:

Let us break down the parameters:

 - `minter`
     - `inflation:` Initial yearly percentage of increase in the total supply of staking token, compounded weekly. A 0.070000000000000000 value means the target is 7% yearly inflation, compounded weekly.
     - `annual_provisions:` Calculated each block. Initialize at 0.000000000000000000.
 - params
     - `mint_denom:` Denom of the staking token that is inflated.
     - `inflation_rate_change:` Max yearly change in inflation.
     - `inflation_max:` Maximum level of inflation.
     - `inflation_min:` Minimum level of inflation.
     - `goal_bonded:` Percentage of the total supply that is targeted to be bonded. If the percentage of bonded staking tokens is below this target, the inflation increases (following inflation_rate_change) until it reaches inflation_max. If the percentage of bonded staking tokens is above this target, the inflation decreases (following inflation_rate_change) until it reaches inflation_min.
     - `blocks_per_year:` Estimation of the amount of blocks per year. Used to compute the block reward coming from inflated staking token (called block provisions).
### **Distribution**

The distribution module handles the logic of distribution block provisions and fees to validators and delegators. The distribution section in the genesis file looks like the follwing:

Let us break down the parameters:

 - `fee_pool`
     - `community_pool:` The community pool is a pool of tokens that can be used to pay for bounties. It is allocated via governance proposals. Generally null in genesis.
 - `community_tax:` The tax percentage on fees and block rewards that goes to the community pool.
 - `base_proposer_reward:` Base bonus on transaction fees collected in a valid block that goes to the proposer of block. If value is 0.010000000000000000, 1% of the fees go to the proposer.
 - `bonus_proposer_reward:` Max bonus on transaction fees collected in a valid block that goes to the proposer of block. The bonus depends on the number of precommits the proposer includes. If the proposer includes 2/3rd precommits weighted by voting power (minimum for the block to be valid), they get a bonus of base_proposer_reward. This bonus increases linearly up to bonus_proposer_reward if the proposer includes 100% of precommits.
 - `withdraw_addr_enabled:` If true, delegators can set a different address to withdraw their rewards. Set to false if you want to disable transfers at genesis, as it can be used as a way to get around the restriction.
 - `delegator_withdraw_infos:` List of delegators withdraw address. Generally null if genesis was not exported from previous state.
 - `previous_proposer:` Proposer of the previous block. Set to "" if genesis was not exported from previous state.
 - `outstanding_rewards:` Outstanding (un-withdrawn) rewards. Set to null if genesis was not exported from previous state.
 - `validator_accumulated_commission:` Outstanding (un-withdrawn) commission of validators. Set to null if genesis was not exported from previous state.
 - `validator_historical_rewards:` Set of information related to the historical rewards of validators and used by the distribution module for various computation. Set to null if genesis was not exported from previous state.
 - `validators_current_rewards:` Set of information related to the current rewards of validators and used by the distribution module for various computation. Set to null if genesis was not exported from previous state.
 - `delegator_starting_infos:` Tracks the previous validator period, the delegation's amount of staking token, and the creation height (to check later on if any slashes have occurred). Set to null if genesis was not exported from previous state.
 - `validator_slash_events:` Set of information related to the past slashing of validators. Set to null if genesis was not exported from previous state.
### **Governance**

The gov module handles all governance-related transactions. The initial state of the gov section looks like the following:

Let us break down the parameters:

 - `starting_proposal_id:` This parameter defines the ID of the first proposal. Each proposal is identified by a unique ID.
 - `deposits:` List of deposits for each proposal ID. Set to null if genesis was not exported from previous state.
 - `votes:` List of votes for each proposal ID. Set to null if genesis was not exported from previous state.
 - `proposals:` List of proposals for each proposal ID: Set to null if genesis was not exported from previous state.
 - `deposit_params`
     - `min_deposit:` The minimum deposit required for the proposal to enter Voting Period. If multiple denoms are provided, the OR operator applies.
     - `max_deposit_period:` The maximum period (in 
 - voting_params
     - `voting_period:` Length of the voting period in 
 - tally_params
     - `quorum:` Minimum percentage of bonded staking tokens that needs to vote for the result to be valid.
     - `threshold:` Minimum percentage of votes that need to be YES for the result to be valid.
     - `veto:` Maximum percentage NO_WITH_VETO votes for the result to be valid.
     - `governance_penalty:` Penalty for validators that do not vote on a given proposal.
### **Slashing**

The slashing module handles the logic to slash delegators if their validator misbehave. The slashing section in genesis looks as follows:

Let us break down the parameters:

 - params
     - `max_evidence_age:` Maximum age of the evidence in 
     - `signed_blocks_window:` Moving window of blocks to figure out offline validators.
     - `min_signed_per_window:` Minimum percentage of precommitsthat must be present in the block window for the validator to be considered online.
     - `downtime_jail_duration:` Duration in 
     - `slash_fraction_double_sign:` Percentage of delegators bonded stake slashed when their validator double signs.
     - `slash_fraction_downtime:` Percentage of delegators bonded stake slashed when their validator is down.
 - `signing_infos:` Various infos per validator needed by the slashing module. Set to {} if genesis was not exported from previous state.
 - `missed_blocks:` Various infos related to missed blocks needed by the slashing module. Set to {} if genesis was not exported from previous state.
### **Genesis Transactions**

By default, the genesis file do not contain any gentxs. A gentx is a transaction that bonds staking token present in the genesis file under accounts to a validator, essentially creating a validator at genesis. The chain will start as soon as more than 2/3rds of the validators (weighted by voting power) that are the recipient of a valid gentx come online after genesis_time.

A gentx can be added manually to the genesis file, or via the following command:

Copy `terpd collect-gentxs`

This command will add all the gentxs stored in \~/.terp/config/gentx to the genesis file. In order to create a genesis transaction, click [here](https://hub.cosmos.network/main/validators/validator-setup.html#participate-in-genesis-as-a-validator).

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