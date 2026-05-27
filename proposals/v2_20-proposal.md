# v2_20 Proposal — Software Upgrade (Cosmos SDK 0.53.7)

### Release v2.20.0

A new release of the `terrad` client has been created. The release notes for this version can be viewed here:
https://github.com/Phoenix-Terra/documents/blob/main/chain-upgrades/v2_20_0.md

This release prepares the **Cosmos SDK 0.53** upgrade for Terra and includes the **`v2_20`** upgrade handler intended for mainnet.

Target dependency versions in this release candidate:
- Cosmos SDK `v0.53.7`
- CometBFT `v0.38.21`
- wasmd `v0.54.3`
- wasmvm `v2.2.4`

### Proposal

This proposal seeks validator and community approval to update the `terrad` client to `v2.20.0` (upgrade name `v2_20`). The chain will be halted at **21327100** which will approximately be processed on **Friday 5 June 2026 14:30 UTC**. The actual halt time is an early estimate, can vary, and depends on the chain's block speed until the specified height is reached.

Upon passing of this proposal, an automatic chain halt will be scheduled at the specified height. Validators are asked to install the new version of the `terrad` client after the chain halt occurred.

### Upgrade Instructions for Validators

As soon as the chain automatically halts at the designated upgrade block height, follow the upgrade procedure. Please **don't execute these commands before the chain has halted**:

```bash
$ git clone https://github.com/Phoenix-Terra/core core-v2.20.0
$ cd core-v2.20.0
$ git checkout v2.20.0
$ make build && make install
```

In case you already have a local copy of the repository inside the local folder `core`:

```bash
$ cd core
$ git stash
$ git fetch --all
$ git fetch --tags
$ git checkout v2.20.0
$ make build && make install
```

Check the correct installation:

```bash
$ terrad version
v2.20.0
```

After that, restart the client with `terrad start` or your system service and wait for consensus. During that period, **don't restart the client if not otherwise asked to do so**.

### Infrastructure Providers

Infrastructure providers (e.g. RPC/LCD/API providers and indexers) are advised to plan their own upgrade procedure around the same upgrade height and should rebuild any dependent services against the new `terrad` version where required.

### Testing and Rollback

#### Testnet Upgrade

Multiple upgrades to the `v2.20.0-rc.0` release candidate were conducted on local testnet, and the upgrade process completed successfully.

If, for any unforeseen reason, the new release is unable to resume block production on mainnet, validators may be asked to roll back to the previous state and temporarily run the prior release `v2.19.0` under the same upgrade name `v2_20` until a patched `v2.20.0` release is provided.

### Effects of Voting

- **YES** - you agree to schedule an upgrade to v2.20.0
- **NO** - you don't agree to schedule an upgrade to v2.20.0
- **ABSTAIN** - you want the proposal to reach quorum and align with the majority vote
- **VETO** - you strongly disagree and want the prop to fail with a 33.33% veto threshold