# Ledger OriginTrail App

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GithubActions](https://github.com/zondax/ledger-origintrail/actions/workflows/main.yml/badge.svg)](https://github.com/Zondax/ledger-origintrail/blob/main/.github/workflows/main.yaml)

---

![zondax_light](docs/zondax_light.png#gh-light-mode-only)
![zondax_dark](docs/zondax_dark.png#gh-dark-mode-only)

_Please visit our website at [zondax.ch](https://www.zondax.ch)_

---

This project contains the OriginTrail app (https://origintrail.io/) for Ledger Nano S and X.

- Ledger Nano S/X BOLOS app
- Specs / Documentation
- C++ unit tests
- Zemu tests

For more information: [How to build](docs/build.md)

## ATTENTION

Please:

- **Do not use in production**
- **Do not use a Ledger device with funds for development purposes.**
- **Have a separate and marked device that is used ONLY for development and testing**
# OriginTrail 1.105.x

## System

| Name                    | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                         |
| ----------------------- | ------ | --------- | --------- | ------- | --------------------------------- |
| Fill block              |        |           |           |         | `Perbill`ratio<br/>               |
| Remark                  |        |           |           |         | `Vecu8`remark<br/>                |
| Set heap pages          |        |           |           |         | `u64`pages<br/>                   |
| Set code                |        |           |           |         | `Vecu8`code<br/>                  |
| Set code without checks |        |           |           |         | `Vecu8`code<br/>                  |
| Set storage             |        |           |           |         | `VecKeyValue`items<br/>           |
| Kill storage            |        |           |           |         | `VecKey`keys<br/>                 |
| Kill prefix             |        |           |           |         | `Key`prefix<br/>`u32`subkeys<br/> |
| Remark with event       |        |           |           |         | `Vecu8`remark<br/>                |

## ParachainSystem

| Name                     | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                        |
| ------------------------ | ------ | --------- | --------- | ------- | -------------------------------- |
| Set validation data      |        |           |           |         | `ParachainInherentData`data<br/> |
| Sudo send upward message |        |           |           |         | `UpwardMessage`message<br/>      |
| Authorize upgrade        |        |           |           |         | `Hash`code_hash<br/>             |
| Enact authorized upgrade |        |           |           |         | `Vecu8`code<br/>                 |

## Timestamp

| Name | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments            |
| ---- | ------ | --------- | --------- | ------- | -------------------- |
| Set  |        |           |           |         | `Compactu64`now<br/> |

## Balances

| Name                | Nano S             | Nano S XL          | Nano SP/X          | Nesting            | Arguments                                                                                               |
| ------------------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------------------------------------------------------------------------------------------- |
| Transfer            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/>                                        |
| Set balance         |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`who<br/>`CompactBalance`new_free<br/>`CompactBalance`new_reserved<br/>      |
| Force transfer      | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`source<br/>`LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/> |
| Transfer keep alive | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | `LookupasStaticLookupSource`dest<br/>`CompactBalance`amount<br/>                                        |
| Transfer all        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | `LookupasStaticLookupSource`dest<br/>`bool`keep_alive<br/>                                              |
| Force unreserve     |                    | :heavy_check_mark: | :heavy_check_mark: |                    | `LookupasStaticLookupSource`who<br/>`Balance`amount<br/>                                                |

## Vesting

| Name                  | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                |
| --------------------- | ------ | --------- | --------- | ------- | -------------------------------------------------------------------------------------------------------- |
| Vest                  |        |           |           |         |                                                                                                          |
| Vest other            |        |           |           |         | `LookupasStaticLookupSource`target<br/>                                                                  |
| Vested transfer       |        |           |           |         | `LookupasStaticLookupSource`target<br/>`VestingInfo`schedule<br/>                                        |
| Force vested transfer |        |           |           |         | `LookupasStaticLookupSource`source<br/>`LookupasStaticLookupSource`target<br/>`VestingInfo`schedule<br/> |
| Merge schedules       |        |           |           |         | `u32`schedule1_index<br/>`u32`schedule2_index<br/>                                                       |

## Treasury

| Name             | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                               |
| ---------------- | ------ | --------- | --------- | ------- | ----------------------------------------------------------------------- |
| Propose spend    |        |           |           |         | `CompactBalance`amount<br/>`LookupasStaticLookupSource`beneficiary<br/> |
| Reject proposal  |        |           |           |         | `Compactu32`proposal_id<br/>                                            |
| Approve proposal |        |           |           |         | `Compactu32`proposal_id<br/>                                            |
| Spend            |        |           |           |         | `CompactBalance`amount<br/>`LookupasStaticLookupSource`beneficiary<br/> |
| Remove approval  |        |           |           |         | `Compactu32`proposal_id<br/>                                            |

## Assets

| Name                  | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                                                                                                                                                                |
| --------------------- | ------ | --------- | --------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Create                |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`admin<br/>`Balance`min_balance<br/>                                                                                                                                                                      |
| Force create          |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`owner<br/>`bool`is_sufficient<br/>`Compactu128`min_balance<br/>                                                                                                                                          |
| Destroy               |        |           |           |         | `Compactu128`id<br/>`DestroyWitness`witness<br/>                                                                                                                                                                                                         |
| Mint                  |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`beneficiary<br/>`Compactu128`amount<br/>                                                                                                                                                                 |
| Burn                  |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`who<br/>`Compactu128`amount<br/>                                                                                                                                                                         |
| Transfer              |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`target<br/>`Compactu128`amount<br/>                                                                                                                                                                      |
| Transfer keep alive   |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`target<br/>`Compactu128`amount<br/>                                                                                                                                                                      |
| Force transfer        |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`source<br/>`LookupasStaticLookupSource`dest<br/>`Compactu128`amount<br/>                                                                                                                                 |
| Freeze                |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`who<br/>                                                                                                                                                                                                 |
| Thaw                  |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`who<br/>                                                                                                                                                                                                 |
| Freeze asset          |        |           |           |         | `Compactu128`id<br/>                                                                                                                                                                                                                                     |
| Thaw asset            |        |           |           |         | `Compactu128`id<br/>                                                                                                                                                                                                                                     |
| Transfer ownership    |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`owner<br/>                                                                                                                                                                                               |
| Set team              |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`issuer<br/>`LookupasStaticLookupSource`admin<br/>`LookupasStaticLookupSource`freezer<br/>                                                                                                                |
| Set metadata          |        |           |           |         | `Compactu128`id<br/>`Vecu8`name<br/>`Vecu8`symbol<br/>`u8`decimals<br/>                                                                                                                                                                                  |
| Clear metadata        |        |           |           |         | `Compactu128`id<br/>                                                                                                                                                                                                                                     |
| Force set metadata    |        |           |           |         | `Compactu128`id<br/>`Vecu8`name<br/>`Vecu8`symbol<br/>`u8`decimals<br/>`bool`is_frozen<br/>                                                                                                                                                              |
| Force clear metadata  |        |           |           |         | `Compactu128`id<br/>                                                                                                                                                                                                                                     |
| Force asset status    |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`owner<br/>`LookupasStaticLookupSource`issuer<br/>`LookupasStaticLookupSource`admin<br/>`LookupasStaticLookupSource`freezer<br/>`Compactu128`min_balance<br/>`bool`is_sufficient<br/>`bool`is_frozen<br/> |
| Approve transfer      |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`delegate<br/>`Compactu128`amount<br/>                                                                                                                                                                    |
| Cancel approval       |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`delegate<br/>                                                                                                                                                                                            |
| Force cancel approval |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`owner<br/>`LookupasStaticLookupSource`delegate<br/>                                                                                                                                                      |
| Transfer approved     |        |           |           |         | `Compactu128`id<br/>`LookupasStaticLookupSource`owner<br/>`LookupasStaticLookupSource`destination<br/>`Compactu128`amount<br/>                                                                                                                           |
| Touch                 |        |           |           |         | `Compactu128`id<br/>                                                                                                                                                                                                                                     |
| Refund                |        |           |           |         | `Compactu128`id<br/>`bool`allow_burn<br/>                                                                                                                                                                                                                |

## XcAssetConfig

| Name                           | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                        |
| ------------------------------ | ------ | --------- | --------- | ------- | -------------------------------------------------------------------------------- |
| Register asset location        |        |           |           |         | `BoxVersionedMultiLocation`asset_location<br/>`Compactu128`asset_id<br/>         |
| Set asset units per second     |        |           |           |         | `BoxVersionedMultiLocation`asset_location<br/>`Compactu128`units_per_second<br/> |
| Change existing asset location |        |           |           |         | `BoxVersionedMultiLocation`new_asset_location<br/>`Compactu128`asset_id<br/>     |
| Remove payment asset           |        |           |           |         | `BoxVersionedMultiLocation`asset_location<br/>                                   |
| Remove asset                   |        |           |           |         | `Compactu128`asset_id<br/>                                                       |

## Authorship

| Name       | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                  |
| ---------- | ------ | --------- | --------- | ------- | -------------------------- |
| Set uncles |        |           |           |         | `VecHeader`new_uncles<br/> |

## CollatorSelection

| Name                   | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                |
| ---------------------- | ------ | --------- | --------- | ------- | ------------------------ |
| Set invulnerables      |        |           |           |         | `VecAccountId`new\_<br/> |
| Set desired candidates |        |           |           |         | `u32`max<br/>            |
| Set candidacy bond     |        |           |           |         | `Balance`bond<br/>       |
| Register as candidate  |        |           |           |         |                          |
| Leave intent           |        |           |           |         |                          |

## Session

| Name       | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                        |
| ---------- | ------ | --------- | --------- | ------- | -------------------------------- |
| Set keys   |        |           |           |         | `Keys`keys<br/>`Bytes`proof<br/> |
| Purge keys |        |           |           |         |                                  |

## XcmpQueue

| Name                              | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                            |
| --------------------------------- | ------ | --------- | --------- | ------- | ---------------------------------------------------- |
| Service overweight                |        |           |           |         | `OverweightIndex`index<br/>`Weight`weight_limit<br/> |
| Suspend xcm execution             |        |           |           |         |                                                      |
| Resume xcm execution              |        |           |           |         |                                                      |
| Update suspend threshold          |        |           |           |         | `u32`new\_<br/>                                      |
| Update drop threshold             |        |           |           |         | `u32`new\_<br/>                                      |
| Update resume threshold           |        |           |           |         | `u32`new\_<br/>                                      |
| Update threshold weight           |        |           |           |         | `Weight`new\_<br/>                                   |
| Update weight restrict decay      |        |           |           |         | `Weight`new\_<br/>                                   |
| Update xcmp max individual weight |        |           |           |         | `Weight`new\_<br/>                                   |

## PolkadotXcm

| Name                             | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                                                                                 |
| -------------------------------- | ------ | --------- | --------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Send                             |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedXcmTuple`message<br/>                                                                                                    |
| Teleport assets                  |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>                               |
| Reserve transfer assets          |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>                               |
| Execute                          |        |           |           |         | `BoxVersionedXcmTasSysConfigCall`message<br/>`Weight`max_weight<br/>                                                                                                      |
| Force xcm version                |        |           |           |         | `BoxMultiLocation`location<br/>`XcmVersion`xcm_version<br/>                                                                                                               |
| Force default xcm version        |        |           |           |         | `OptionXcmVersion`maybe_xcm_version<br/>                                                                                                                                  |
| Force subscribe version notify   |        |           |           |         | `BoxVersionedMultiLocation`location<br/>                                                                                                                                  |
| Force unsubscribe version notify |        |           |           |         | `BoxVersionedMultiLocation`location<br/>                                                                                                                                  |
| Limited reserve transfer assets  |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>`WeightLimit`weight_limit<br/> |
| Limited teleport assets          |        |           |           |         | `BoxVersionedMultiLocation`dest<br/>`BoxVersionedMultiLocation`beneficiary<br/>`BoxVersionedMultiAssets`assets<br/>`u32`fee_asset_item<br/>`WeightLimit`weight_limit<br/> |

## DmpQueue

| Name               | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                            |
| ------------------ | ------ | --------- | --------- | ------- | ---------------------------------------------------- |
| Service overweight |        |           |           |         | `OverweightIndex`index<br/>`Weight`weight_limit<br/> |

## TemplatePallet

| Name         | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments           |
| ------------ | ------ | --------- | --------- | ------- | ------------------- |
| Do something |        |           |           |         | `u32`something<br/> |
| Cause error  |        |           |           |         |                     |

## EVM

| Name     | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                                                                                                                            |
| -------- | ------ | --------- | --------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Withdraw |        |           |           |         | `H160`address<br/>`Balance`amount<br/>                                                                                                                                                                               |
| Call     |        |           |           |         | `H160`source<br/>`H160`target<br/>`Vecu8`input<br/>`U256`value<br/>`u64`gas_limit<br/>`U256`max_fee_per_gas<br/>`OptionU256`max_priority_fee_per_gas<br/>`OptionU256`nonce<br/>`VecTupleH160VecH256`access_list<br/> |
| Create   |        |           |           |         | `H160`source<br/>`Vecu8`init<br/>`U256`value<br/>`u64`gas_limit<br/>`U256`max_fee_per_gas<br/>`OptionU256`max_priority_fee_per_gas<br/>`OptionU256`nonce<br/>`VecTupleH160VecH256`access_list<br/>                   |
| Create2  |        |           |           |         | `H160`source<br/>`Vecu8`init<br/>`H256`salt<br/>`U256`value<br/>`u64`gas_limit<br/>`U256`max_fee_per_gas<br/>`OptionU256`max_priority_fee_per_gas<br/>`OptionU256`nonce<br/>`VecTupleH160VecH256`access_list<br/>    |

## Ethereum

| Name     | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                     |
| -------- | ------ | --------- | --------- | ------- | ----------------------------- |
| Transact |        |           |           |         | `Transaction`transaction<br/> |

## EvmAccounts

| Name                  | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                       |
| --------------------- | ------ | --------- | --------- | ------- | --------------------------------------------------------------- |
| Claim account         |        |           |           |         | `EvmAddress`eth_address<br/>`Eip712Signature`eth_signature<br/> |
| Claim default account |        |           |           |         |                                                                 |

## BaseFee

| Name                 | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                |
| -------------------- | ------ | --------- | --------- | ------- | ------------------------ |
| Set base fee per gas |        |           |           |         | `U256`fee<br/>           |
| Set is active        |        |           |           |         | `bool`is_active<br/>     |
| Set elasticity       |        |           |           |         | `Permill`elasticity<br/> |

## Scheduler

| Name                 | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                                                                                                                           |
| -------------------- | ------ | --------- | --------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Schedule             |        |           |           |         | `BlockNumber`when<br/>`OptionschedulePeriodBlockNumber`maybe_periodic<br/>`schedulePriority`priority<br/>`BoxCallOrHashOfT`call<br/>                |
| Cancel               |        |           |           |         | `BlockNumber`when<br/>`u32`index<br/>                                                                                                               |
| Schedule named       |        |           |           |         | `Vecu8`id<br/>`BlockNumber`when<br/>`OptionschedulePeriodBlockNumber`maybe_periodic<br/>`schedulePriority`priority<br/>`BoxCallOrHashOfT`call<br/>  |
| Cancel named         |        |           |           |         | `Vecu8`id<br/>                                                                                                                                      |
| Schedule after       |        |           |           |         | `BlockNumber`after<br/>`OptionschedulePeriodBlockNumber`maybe_periodic<br/>`schedulePriority`priority<br/>`BoxCallOrHashOfT`call<br/>               |
| Schedule named after |        |           |           |         | `Vecu8`id<br/>`BlockNumber`after<br/>`OptionschedulePeriodBlockNumber`maybe_periodic<br/>`schedulePriority`priority<br/>`BoxCallOrHashOfT`call<br/> |

## Sudo

| Name                  | Nano S | Nano S XL | Nano SP/X | Nesting | Arguments                                           |
| --------------------- | ------ | --------- | --------- | ------- | --------------------------------------------------- |
| Sudo                  |        |           |           |         | `Call`call<br/>                                     |
| Sudo unchecked weight |        |           |           |         | `Call`call<br/>`Weight`weight<br/>                  |
| Set key               |        |           |           |         | `LookupasStaticLookupSource`new\_<br/>              |
| Sudo as               |        |           |           |         | `LookupasStaticLookupSource`who<br/>`Call`call<br/> |
