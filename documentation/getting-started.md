# Getting Started

All steps come from the [Hyperledger Fabric documentation](https://hyperledger-fabric.readthedocs.io/en/latest/getting_started.html) files.

However, I primarily use a DISA-STIG RHEL 8.6-FIPS for my general server and Fedora (most recent core) for my daily driver.  This project will be completed using Fedora Core 38.

## Prerequisite software

The following prerequisites are required to run a Docker-based Fabric test network on your local machine.

### Podman

Fedora Core 38 primarily uses Podman instead of Docker and so this project will too.  Podman offers several benefits over Docker, including enhanced security and better resource management, making it a suitable choice for the privacy-focused and resource-sensitive nature of the project.

One of the primary advantages of Podman is its rootless operation, which means containers can be run without requiring root privileges. This greatly reduces the attack surface and the potential for unauthorized access or privilege escalation. In contrast, Docker runs as a root daemon, which can expose the system to increased security risks. Additionally, Podman supports SELinux natively, further enhancing the security by providing mandatory access control at the kernel level.

Podman also offers better resource management and isolation by using cgroups v2, which improves the overall performance and efficiency of the system. It provides a more fine-grained control over resources such as CPU, memory, and I/O usage, ensuring that the nodes in the blockchain network can function optimally.

Another advantage of using Podman is its compatibility with the OCI (Open Container Initiative) standard, which ensures that container images built with Podman can be seamlessly deployed on other OCI-compliant container runtimes. This promotes interoperability and makes it easier to migrate to or from other containerization solutions if needed.

In summary, Podman's enhanced security features, resource management capabilities, and compatibility with OCI standards make it an ideal choice for the RebelShield project. Its rootless operation and support for SELinux provide a secure environment for managing API access in embedded IoT devices and healthcare data, aligning with the project's privacy and compliance objectives.

**Install Podman:**

```bash
sudo dnf -y install podman
```

**Create an alias** to allow docker commands to work as podman commands, or just call podman instead of docker everytime docker appears in this project.

```bash
vim ~/.bashrc
```

Add the following line to your .bashrc file:

```bash
alias docker=podman
```

### JQ

Install the latest version of jq for channel configuration transactions:

```bash
sudo dnf -y install jq
```

## Install Fabric

From the root project directory, run the following command:

```bash
./scripts/install-fabric.sh podman binary
```

This command will create the bin, builders, and config directories.

## Add Fabric Binaries to PATH

Add the following to your .bashrc file:

```bash
# RebelShield PATH
if ! [[ "$PATH" =~ "$HOME/<installation path>/rebelshield/bin:" ]]
then
    PATH="$HOME/<installation path>/rebelshield/bin:$PATH"
fi
export PATH
export FABRIC_CFG_PATH="$HOME/<installation path>/rebelshield/network/config"
```

Source the Fabric binaries:

```bash
source ~/.bashrc
```

## Generate Cryptographic Materials

Generate cryptographic materials using cryptogen tool:

```bash
cd network/config && cryptogen generate --config=crypto-config.yaml
```

Create the genesis block and channel configuration transaction using the configtxgen tool:

```bash
cd ../.. && configtxgen -profile RSGenesis -channelID system-channel -outputBlock ./network/config/genesis.block
```
