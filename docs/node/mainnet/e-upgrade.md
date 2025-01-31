# E* Upgrade

:::info

This document is a work in progress and details around when the upgrade will be
proposed and how it will be called are still not known and will be determined
by the Oasis community.

The upgrade will first happen on Testnet and will only be proposed for Mainnet
after sufficient testing has been done to ensure everything will progress as
planned.

:::

This document provides an overview of the changes for the E* Mainnet
upgrade.

:::caution

The E* upgrade on Mainnet is scheduled at epoch TODO which will happen
around TODO.

:::

## Major Features

All features for the E* upgrade are implemented as part of
**Oasis Core 23.0.x** release series which is a consensus protocol-breaking
release.

Summary of the major features is as follows:

- **On-Chain Governance**:
  - The upgrade adds support for delegators to participate in on-chain
    governance. So far, only validators have been able to vote on governance
    proposals on upgrades. From now on, anyone who is staking will be able to
    override the votes of the validator.
  - Prior to this upgrade, validators could vote solely on one specific type of
    upgrade proposal. This upgrade adds support for voting on parameter changes.
    An example of such a change includes voting on the staking rewards schedule
    modifications.

- **Node Operators UX**:
  - With the enhancement of the P2P Stack in the latest upgrade, we've
    integrated support for state sync. This improvement simplifies the process
    of initiating a new node, enabling immediate synchronization without the
    need for manual RPC node configuration.
  - The upgrade lays the foundation for the system to distribute bundles
    automatically. While this update doesn't enable this feature, in the future
    nodes will have the capability to upgrade automatically to the appropriate
    version immediately after a governance vote passes.
  - Enhancements have been made to bolster security and optimize the efficiency
    of specific queries.

- **Key Rotations**:
  - The upgrade introduces major updates to facilitate key rotations, both for
    ephemeral and state keys.
    - Key derivation for ephemeral keys will be modified such that the master
      ephemeral key will be rotated on every epoch and old entropy will be
      discarded after a few epochs. As a result, past transaction keys will be
      irretrievable unless the user keeps additional data to enable disclosure
      of past transactions.
    - The upgrade introduces support for state key rotations, incorporating key
      generations. ParaTimes can now rotate state keys daily, and use new keys
      for newer state. This facilitates re-encryption and, in the event of a TCB
      recovery, helps to partially mitigate the effects of compromised nodes.

- **ParaTime Confidential Query Latency**:
  - The current confidential ParaTimes have a block delay when querying
    confidential state following transaction execution. This is due to the fact
    that the ParaTime needs to independently verify finalization in the
    consensus layer to guard against attacks. The upcoming version introduces
    same-block execution. As soon as a block gets finalized on the consensus
    layer, ParaTimes can promptly obtain the latest state root hash and verify
    the state without delay. This reduces latency for those looking to query
    outcomes of their transactions, e.g. dApp users and developers.

- **ParaTime Upgrades**:
  - The upgrade reduces downtime associated with upgrading confidential
    ParaTimes. Previously, an upgrade to Sapphire mandated an epoch of downtime.
    Now, as compute nodes transition to the new version, the upgrade will be
    instantaneous, ensuring no delays or downtime.

- **ParaTime Performance**:
  - The upgrade implements a series of modifications to enhance the robustness
    of runtimes. These improvements encompass better response mechanisms for SGX
    TCB recovery events, expanded support for new SGX platforms, and improved
    proof validation within runtimes.
  - The upgrade improves runtime performance, especially in scenarios involving
    node failures. Should nodes malfunction, the impact on performance will now
    be significantly reduced.

## Mechanics of the Upgrade

:::info

This section will be updated with the exact details as we get closer to the
upgrade. For now, please take a look at the related [Testnet upgrade].

:::

[Testnet upgrade]: ../testnet/upgrade-log.md
