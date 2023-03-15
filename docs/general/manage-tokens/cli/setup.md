# Setup

## Download and Run

Download the latest release [here][cli-releases] and extract it to your
favorite application folder.

:::info

Oasis is currently providing official builds for x86 Linux only. If you want
to run it on another platform, you will have to [build it from source][cli-source].

:::

Run the Oasis CLI by typing `oasis`.

:::info

We suggest that you move into or put a symbolic link to `oasis` binary in your
system path, so you can access it globally.

:::

Running Oasis CLI for the first time will generate a configuration file and
populate it with the current Mainnet and Testnet networks. It will also
configure all [Oasis-supported ParaTimes][paratimes].

## Configuration

The configuration folder of Oasis CLI is located:

- on Windows:
  - `%USERPROFILE%\AppData\Roaming\Oasis\`
- on macOS:
  - `/Users/$USER/Library/Application Support/Oasis/`
- on Linux:
  - `$HOME/.config/oasis/`

There, you will find `cli.toml` which contains configuration of the networks,
ParaTimes and your wallet. Additionally, each file-based account in your wallet
will have a separate, password-encrypted `.toml` file in the same folder named
after the name of the account. 

[cli-releases]: https://github.com/oasisprotocol/cli/releases
[cli-source]: https://github.com/oasisprotocol/cli
[paratimes]: ../../../dapp/README.mdx
