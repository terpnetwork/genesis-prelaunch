# Genesis Prelaunch Introduction
Welcome! This process ensures that the decision-making process is transparent, fair, and inclusive decentralized protocol bootstrapping.
- [**Genesis Introduction**](./docs/genesis-intro.md)
- [**Gentx Folder**](./gentxs/)
## Genesis Launch Checklist
- [] Genesis Launch Documentaion: [Link](./docs/genesis-intro.md)
- [] Solventless Terp Airdrop Cycles Documentation: [Link](./docs/distribution.md)
- [] Gentx Process: [Link](./docs/gentxs/README.md)
- [] Foundation Delegation Policy: [Link]()
## Post Launch Checklist
- [] 2nd Airdrop Cycle Proposal
- [] Smart Contract Upload Proposals


## Current Proposed Genesis Parameters Configuration

### Inital Supply Parameters
- TERP: `420 Million`
- THIOL: `420 Million`
### Inital Distribution Parameters
- Protocol Treasury Tokens: `284,025,703UTERP, 284,025,703UTHIOL`
- Airdrop Cycle One: `72,974,297UTERP & 72,974,297UTHIOL`
- TerpNET Foundation DAO: `63000000UTERP & 63000000UTHIOL`
- community_tax: `2%`
- base_proposer_reward: `1%`
- bonus_proposer_reward: `4%`
- withdraw_addr_enabled: `true`
- inflation: `93%`
- mint_denom: `uthiol`
- inflation_max: `93%`
- inflation_min: `93%`
- goal_bonded: `0.000100000000000000`
- blocks_per_year: `6311520`
- send_enabled: `true`
- receive_enabled: `true`

### Inital Vesting Parameters
Only the TerpNET Foundation DAO & 10 inital validators will have any tokens in circulation at genesis. 
- TerpNET Foundation DAO: `50% at 7 years.`
- Every Bitcanna, CosmosHub, TerpOG, & Scavenger Hunt Reward: `100% at 6 months from 4/20/2023` 
### Initial Delegation Parameters
- unbonding_time: `3 weeks`
- max_validators: `69`
- max_entries: `7`
- historical_entries: `10000`
- bond_denom: `uterp`
### Initial Governance Parameters
- min_deposit: `100TERP`
- max_deposit_period: `3 days`
- voting_period: `4 days`
- quorum: `33.4%`
- threshold: `50%`
- veto_threshold: `33.4%`
## Initial Smart Contract Parameters
- code_upload_access: `Nobody`
- instantiate_default_permission: `Nobody`
### Initial ICA (Inter-Chain Accounts) Parameters
- controller_enabled: `true`
- host_enabled: `true`
### Inital Slashing Parameters
- signed_blocks_window: `12,000`
- min_signed_per_window: `25%`
- downtime_jail_duration: `600 seconds`
- slash_fraction_double_sign: `5%`
slash_fraction_downtime: `.1%`

The current proposed genesis to be used to collect gentxs for Main Network 1 is located [here.](../gentxs/genesis.json). The scripts used to make this genesis file can be found [here](./gen-account-scripts/).


# **Disclaimer**

Terp Network is *highly* experimental software. In these early days, we can expect to have issues, updates, and bugs. The existing tools require advanced technical skills and involve risks which are outside of the control of the Terp Network and/or the TerpNET Foundation team . Any use of this open source Apache 2.0 licensed software is done at your *own risk and on a “AS IS” basis, without warranties or conditions of any kind*, and any and all liability of the teams for damages arising in connection to the software is excluded. **Please exercise extreme caution!**

Furthermore, it must be noted that it remains in the community's discretion to adopt or not to adopt the Genesis State that the TerpNET Foundation DAO recommends within the Genesis Block Software. Therefore, The dev team *cannot* guarantee that (i) TERPS will be created and (ii) the recommended allocation as set forth herein will actually take place.