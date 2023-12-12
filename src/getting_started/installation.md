# Installation

## Rust

Go [here](https://www.rust-lang.org/tools/install) to install Rust.

## Solana

Go [here](https://docs.solana.com/cli/install-solana-cli-tools) to install Solana and then run `solana-keygen new` to create a keypair at the default location. Anchor uses this keypair to run your program tests.

## Yarn

Go [here](https://yarnpkg.com/getting-started/install) to install Yarn.

## Anchor

### Installing Anchor

```
cargo install --git https://github.com/coral-xyz/anchor avm --locked --force
```

Install the 0.29.0 version of the CLI using `avm`, and then set it to be the version to use.

```
avm install 0.29.0
avm use 0.29.0
```

## Bolt

### Installing Bolt

Install `Bolt` using Cargo.

```
cargo install --git https://github.com/magicblock-labs/bolt  --locked --force
```

On Linux systems you may need to install additional dependencies if cargo install fails. E.g. on Ubuntu:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install -y pkg-config build-essential libudev-dev
```

Verify the installation.

```
bolt -h
```