# Oasis CLI

Oasis command-line interface (CLI) is a powerful all-in-one tool for
interacting with the Oasis Network. You can download the latest release
binaries from the [GitHub repository].

It boasts a number of handy features:

- Flexible setup:
  - supports Mainnet, Testnet, Localnet or any other Oasis network deployment
  - consensus layer configuration with arbitrary token
  - configuration of custom ParaTimes with arbitrary token
  - connecting to remote (via TCP/IP) or local (Unix socket) Oasis node
    instance
- Powerful wallet features:
  - standard token operations (transfers, allowances, deposits, withdrawals and
    balance queries)
  - file-based wallet with password protection
  - full Ledger hardware wallet support
  - address book
  - generation, signing and submitting transactions in non-interactive mode
  - offline transaction generation for air-gapped machines
  - transaction encryption with Deoxys-II envelope
  - Ed25519 and Ethereum-compatible Secp256k1 encryption schemes
  - raw, BIP-44, ADR-8 and Ledger's legacy derivation paths
- Developer and devops features:
  - Oasis node inspection and healthchecks
  - official testing accounts for Oasis Localnet, test runners and debugging
  - WebAssembly smart contract code deployment, instantiation, management and
    calls
  - debugging tools for deployed WebAssembly contracts

[GitHub repository]: https://github.com/oasisprotocol/cli/releases
