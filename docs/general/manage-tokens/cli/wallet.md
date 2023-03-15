# Wallet Management

`oasis wallet` command is used to manage your file-based or hardware wallet
accounts. Oasis CLI supports the following account kinds:

- `ed25519-adr8`: Ed25519 keypair using [ADR-8] derivation path to obtain
  a private key from mnemonic. This is the default setting suitable for
  accounts on the Oasis consensus layer.
- `secp256k1-bip44`: Secp256k1 Ethereum-compatible keypair using [BIP-44]
  with ETH coin type to derive a private key. This setting is
  used for accounts living on EVM-compatible ParaTimes. The same account can
  be imported into Metamask and other Ethereum wallets.
- `ed25519-legacy`: Ed25519 keypair using a legacy 5-component derivation path.
  This is the preferred kind for Oasis accounts stored on
  a hardware wallet like Ledger. It is called legacy, because it was
  implemented before [ADR-8] was standardized.
- `ed25519-raw` and `secp256k1-raw`: Ed25519 and Secp256k1 respective keypairs
  imported directly from Base32 or Hex-encoded private key. These kinds
  do not use a derivation path.

:::tip

For compatibility with Ethereum, each `secp256k1` account has two addresses:

- 20-byte hex-encoded Ethereum-compatible address, e.g. `0xDCbF59bbcC0B297F1729adB23d7a5D721B481BA9`
- Bech32-encoded Oasis native address, e.g. `oasis1qq3agel5x07pxz08ns3d2y7sjrr3xf9paquhhhzl`.

There exists a mapping from Ethereum address to the native Oasis address as in
the example above, but there is no reverse mapping.

:::

[ADR-8]: ../../../adrs/0008-standard-account-key-generation.md
[BIP-44]: https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki

## Create or Import wallet

`oasis wallet create` will generate a new mnemonic and derive a keypair for
you. For optimal security, you can connect your Ledger wallet and create an
account which uses a private key stored on the hardware wallet.

If you already have a mnemonic or a raw private key, you can import it
as a new account by running `oasis wallet import`. You will then need to
provide a mnemonic or the raw private key in the corresponding format.

## View wallets

You can list all available wallets with `oasis wallet list`:

```
$ oasis wallet list
ACCOUNT                         KIND                            ADDRESS                                        
emerald_test                    file (secp256k1-raw)            oasis1qq3agel5x07pxz08ns3d2y7sjrr3xf9paquhhhzl
john                            file (ed25519-raw)              oasis1qrec770vrek0a9a5lcrv0zvt22504k68svq7kzve
oasis_hackathon                 file (ed25519-adr8:0)           oasis1qptx7ytle3xlccyvk9w27f47jq4pfqxrug2dzwtv
sapphire_test                   file (secp256k1-raw)            oasis1qpupfu7e2n6pkezeaw0yhj8mcem8anj64ytrayne
sapphire_tictactoe1             file (secp256k1-bip44:0)        oasis1qqd333zt6lrx734szrcay2cjzek9uumlf5rrmmr7
sapphire_tictactoe2             file (secp256k1-bip44:1)        oasis1qrk58a6j2qn065m6p06jgjyt032f7qucy5wqeqpt
```

Above, you can see native Oasis addresses of all local accounts. You can see
the public key of an account and for `secp256k1` accounts their Ethereum
addresses by using `oasis wallet show`:

```
$ oasis wallet show emerald_test
Unlock your account.
? Passphrase: 
Name:             emerald_test
Public Key:       A8JDpTiCnrq+zFUsAHrHY/xuFVsyt48sC1Srkp62r7Yx
Ethereum address: 0xDCbF59bbcC0B297F1729adB23d7a5D721B481BA9
Native address:   oasis1qq3agel5x07pxz08ns3d2y7sjrr3xf9paquhhhzl
```

To print the account's mnemonic or the private key, run `oasis wallet export`:

```
$ oasis wallet export emerald_test
WARNING: Exporting the account will expose secret key material!
Unlock your account.
? Passphrase: 
Name:             eth_0
Public Key:       A8JDpTiCnrq+zFUsAHrHY/xuFVsyt48sC1Srkp62r7Yx
Ethereum address: 0xDCbF59bbcC0B297F1729adB23d7a5D721B481BA9
Native address:   oasis1qq3agel5x07pxz08ns3d2y7sjrr3xf9paquhhhzl
Export:
0x0b5e6994430f9d3a5b6619b97e6af146b88f06457372764b36cdcff10c1c64f8
```

## Test wallets

Oasis CLI comes with the following hardcoded testing accounts:

- `test:alice`: Ed25519 test account by Oasis core tests
- `test:bob`: Ed25519 test account by Oasis core tests
- `test:charlie`: Secp256k1 test account
- `test:cory`: Ed25519 account used by `oasis-net-runner`
- `test:dave`: Secp256k1 test account
- `test:erin`: Sr25519 test account
- `test:frank`: Sr25519 test account

Those accounts are often used for your Localnet development or when
reporting bugs to oasis-core team for reproducibility. You can access the
private key of a test account the same way as you would for ordinary accounts
by running `oasis wallet export` command.

[oasis-core]: https://github.com/oasisprotocol/oasis-core
