# Request for Consensus: Initial State Params - Terp Network 

Welcome! This proposal is a request from the [TerpNET Foundation DAO](https://daodao.zone/dao/juno1wpq03vzv4f9fczss0sqt4xxfmxel6zmhdxal68lg8qpa7cgzj25sy3k3dt/proposals/A1) to the Terp Network community for consensus on the initial state parmeters of Terp Network. This includes the [genesis-prelaunch repository](https://github.com/terpnetwork/genesis-prelaunch), being the source of truth for this proposal, and also including the [scripts used for generating inital recommended balance & distribution](https://github.com/terpnetwork/genesis-prelaunch/tree/main/gen-account-scripts), and the [gentx repo](https://github.com/terpnetwork/genesis-prelaunch/tree/main/gentxs), with a bit of [documentation](https://github.com/terpnetwork/genesis-prelaunch/tree/main/docs) as well.

## Final Reccommended Genesis File & Process
We are proposing that the final genesis file includes the gentxs of each validator who has participated & submitted a gentx & also a member within the [Validation subDAO](https://daodao.zone/dao/juno1wpq03vzv4f9fczss0sqt4xxfmxel6zmhdxal68lg8qpa7cgzj25sy3k3dt/proposals/A1). The final reccommended genesis file will end up [here](https://github.com/terpnetwork/genesis-prelaunch/blob/main/gentxs/final-genesis.json). The final reccomended genesis, including all gentxs from TerpNET Validation DAO members, may not be available by the time this proposal goes up, however we can enforce these intial parameters nonetheless. 

## Inital App Params

### Reccommended Binary
- [V1.0.0](https://github.com/terpnetwork/terp-core/pull/47)
- chain-id: morocco-1
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
- TerpNET Foundation DAO: `50% at 7 years`
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
- burn_proposal_deposit_prevote: `false`
- burn_vote_quorum: `false`
- burn_vote_veto: `true`
- min_initial_deposit_ratio: `0.000000000000000000`
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
### Initial TokenFactory Denom Fee
- denom_creation_fee: `100thiol` 


BY VOTING YES, you agree to all of the reccommended initial genesis state above, including and the inital valset, the verifiable location of the final-genesis file, and all of the inital Terp-Core params found [here](https://github.com/terpnetwork/genesis-prelaunch/blob/main/gentxs/genesis.json). Also by voting YES you agree you understand that at the time of this proposal the final genesis may not include 100% of the expected gentx from validator in the Validation subDAO. 


BY VOTING NO, you disagree to any of the recommended initital genesis state above. 