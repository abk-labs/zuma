# Zuma

Project Zuma is an innovative, Debian-based OS distribution designed specifically for running Solana validator and RPC clients, including Anza and Firedancer. Tailored for flexibility, robustness, and ease of use, Zuma targets various environments, including bare metal servers, virtual machines, and containerized platforms.

## Features

- **Validator Appliance:** Simplifies the operation and version control of Solana nodes. Provides community-tested configuration setups for seamless deployment and management.

- **Cluster Management:** Enables scalable, low-effort management of large validator and RPC clusters. Supports both permissioned and permissionless Solana clusters, catering to diverse user needs.

- **Developer Tooling:** Accelerates application development on the Solana Virtual Machine (SVM). Offers a suite of tools to streamline the building, launching, and maintaining of SVM forks.

- **On-Chain Permissions System:** Facilitates secure, scalable permission management for institutional customers. Ensures compliance and security in regulated environments.

- **Seamless Bridge to Mainnet:** Provides easy access to Solana Mainnet liquidity. Ensures interoperability and smooth transitions between different Solana environments.

## Objectives

- **Lowering Expertise Barriers:** Zuma drastically reduces the technical expertise required to deploy and manage Solana nodes, making blockchain technology more accessible to a broader audience.

- **Community-Driven Development:** By involving strategic partners and early customers, Zuma leverages community feedback to continuously improve and adapt to real-world needs.

- **Comprehensive Management Solution:** Zuma aims to be the go-to solution for installing and managing both permissioned and permissionless Solana clusters, with built-in mechanisms for easy bridging between them.

## Vision

Our vision for Project Zuma is to empower developers and institutions alike to harness the power of Solana's blockchain technology with minimal friction. By providing a robust, user-friendly platform, we strive to drive widespread adoption and foster innovation within the SVM ecosystem.

## Installing

Follow the steps below to install Zuma on your system:

1. Update your package lists:

```bash
sudo apt-get update
```

2. Install the necessary prerequisites:

```bash
sudo apt-get install -y curl gnupg
```

3. Add the Zuma repository to your system's software repository list:

```bash
echo "deb https://apt.abklabs.com/zuma dev main" | sudo tee /etc/apt/sources.list.d/zuma.list
```

4. Import the repository's GPG key:

```bash
curl -s https://apt.abklabs.com/keys/abklabs-archive-dev.asc | sudo apt-key add -
```

5. Update your package lists again:

```bash
sudo apt-get update
```

6. Install Zuma:

```bash
sudo apt-get install zuma-agave-validator
```

After the installation you will have the Agave validator client and zuma CLI on the host. Verify the installation:

```bash
zuma --version

This should display the installed version of Zuma and Agave.
```

## Getting started

```shell
# A serious of command prompts to configure the host and validator.
sudo zuma init
# Starts the validator using systemd after preflight checks.
zuma run
```

```toml
# Example Zuma.toml
[rpc]
port = 8899

[network]
entrypoints = [
  "entrypoint.mainnet-beta.solana.com:8001",
  ...
  "entrypoint5.mainnet-beta.solana.com:8001"
]
validators = [
  "7cVfgArCheMR6Cs4t6vz5rfnqd56vZq4ndaBrY5xkxXy",
  ...
  "CakcnaRDHka2gXyfbEd2d3xsvkJkqsLw2akB3zsN1D2S"
]

[metrics]
host = "https://metrics.solana.com:8086"
db = "mainnet-beta"
username = "mainnet-beta_write"
password = "password"
```

```shell
# Reload the Zuma.toml. You will be prompted if the change requires a validator restart.
zuma reload
```

```shell
# Print health check report
zuma health
# Follow the validator logs
zuma logs
```
