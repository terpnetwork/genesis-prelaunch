# Genesis Validator Ceremony
## Housekeeping for Validators: Submitting a gentx for mainnet

1\. You should have generated and secured the validator consensus key you are going to be validating under during mainnet.

2\. Be prepared to sign a transaction under an address in the genesis file.

3\. We will begin collecting Gentxs for mainnet once the recommended genesis allocations are published.

# Instructions


Welcome to the Terp Network Genesis Validator Ceremony!


## What is it?

This *is not* the launch of Terp Network. Before a blockchain like the Terp Network can launch, it needs to determine an initial validator set.

This is a ceremony to establish a decentralized initial validator set that can be recommended for the Genesis State of the Terp Network.
This validator set is computed from the set of signed `gentx` transactions with non-zero TERP's submitted during this genesis ceremony.

Before you consider participating in this ceremony, please read the entire document.

Genesis transactions will be collected on Github in this repository and checked for validity by an automated script.
Genesis file collection will terminate in **3 Days** after the genesis ceremony begins. The final recommended genesis file will be published shortly after that time.

By participating in this ceremony and submitting a gen-tx, you are making a commitment to your fellow Terpshashin.
that you will be around to bring your validator online by the recommended genesis time determinded by consensus. Note that you can start `terpd`  with the recommended genesis file before that time and, assuming you configure it successfully, it will automatically start the peer-to-peer and consensus processes once the genesis timestamp is reached.

Please keep the following things in mind.

1. This process is intended for technically inclined people who have participated in Terp testnets and other cosmosSDK network. If you aren't already familiar with this process, you are advised against participating due to the risks involved. There is no need for you to participate if you feel unprepared - 
 you can create a validator or stake TERP's any time after launch.
2. TERP's staked during genesis will be at risk of 5% slashing if your validator double signs. If you accidentally misconfigure your validator setup, this can easily happen, and slashed TERP's are not expected to be recoverable by any means. Additionally, if you double-sign, your validator will be [tombstoned](https://github.com/cosmos/cosmos-sdk/blob/master/docs/spec/slashing/07_tombstone.md) and you will be required to change operator and signing keys.
3. TERP's staked during genesis or after will be locked up as part of the defense against long range attacks for 3 weeks. They can be re-delegated or undelegated, but will not be transferrable until a hard-fork enables transfers.
   

## Genesis File

**WARNING: THIS IS NOT THE FINAL RECOMMENDATION FOR THE GENESIS FILE**


To understand how this file was compiled, please see [the gen-account-scripts folder](../gen-account-scripts/README.md).

A final recommendation will be available after consensus of the TestNET participants including a justification for
all components of the genesis file and scripts to recompute it.

Anyone who intends to participate in the genesis ceremony must submit a pull request
containing a valid `gen-tx` to this repository in the `/gentx` folder with a file name like `<moniker>.json`.

## Gen-TX Steps

### Initialize your Terp Node
```
terpd init <your-moniker>
```

### Add Keys 
make sure you are using the same keyring for your validator on main-net. 
```
terpd keys add <your-moniker> --recover
```
#
### Move genesis file to ~/.terp/config/genesis.json
from the root of the `gentx/` directory:
```
rm ~/.terp/config/genesis.json && cp genesis.json ~/.terp/config/genesis.json
```

### Create Gentx
To generate your gentx run the following command:
```
terpd gentx \
  --amount 1000000uterp \
  --min-self-delegation <min_self_delegation> \
  --commission-rate <commission_rate> \
  --commission-max-rate <commission_max_rate> \
  --commission-max-change-rate <commission_max_change_rate> \
  --pubkey <consensus_pubkey> \
  --name <key_name>
  ```

## A Note about your Validator Signing Key

Your validator signing private key lives at `~/.terp/config/priv_validator_key.json`. If this key is stolen, an attacker would be able to make
your validator double sign, causing a slash of 5% of your terp tokens  and the [tombstoning](https://github.com/cosmos/cosmos-sdk/blob/master/docs/spec/slashing/07_tombstone.md) of your validator. If you are interested in how to better protect this key please see the [`tendermint/kms`](https://github.com/tendermint/kms) (_*use at your own risk*_) repo. We will have a complete guide for how to secure this file soon after launch.

## Next Steps

Once all gentx files are collected, The TerpNET Foundation DAO team will recommend a particular genesis file and software version to the Test Network, but there is no guarantee a network will ever start from it - nodes and validators may
never come online, the community may disregard the recommendation and choose
different genesis files, and/or they may modify the software in arbitrary ways. Such
outcomes and many more are outside the TerpNET Foundation DAO's control and completely in the hands of the community.

On initialization of the software, Terp Network's Bonded Proof-of-Stake (Brought to you by comet-bft) system will kick in to determine the initial validator set (max 69 validators) from the set of `gentx` transactions.
More than 2/3 of the voting power of this set must be online and participating in consensus
in order to create the first block and Terp Network.

We expect and hope that TERP holders will exercise discretion in initial staking to ensure the network does not ever become excessively centralized. This is not a first of its kind experiment in bootstrapping a decentralized network. Other proof of stake networks have bootstrapped with the aid of a centralized foundation or other administrator. We hope to bootstrap as a decentralized community, building on the shared experiences of many many testnets.

See the [blog
post](https://blog.cosmos.network/the-3-phases-of-the-cosmos-hub-mainnet-fdff3a68c4c0) 
for more details on the three phases of launch.


# Disclaimer


Terp Network is *highly* experimental software. In these early days, we can
expect to have issues, updates, and bugs. The existing tools require advanced
technical skills and involve risks which are outside of the control of the
TerpNET Foundation DAO and/or the Permissionless Web Team. Any use of this open source Apache
2.0 licensed software is done at your *own risk and on a “AS IS” basis, without
warranties or conditions of any kind*, and any and all liability of the
TerpNET Foundation DAO and/or the Permissionless Web Team for damages arising in
connection to the software is excluded. **Please exercise extreme caution!**

Furthermore, it must be noted that it remains in the community's discretion to adopt or not
to adopt the Genesis State that TerpNET Foundation DAO (TFD) recommends within the Genesis Block
Software. Therefore, TFD *cannot* guarantee that (i) TERP's will be created and
(ii) the recommended allocation as set forth herein will actually take place.