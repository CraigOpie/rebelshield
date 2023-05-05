# Getting Started

All steps come from the [Hyperledger Fabric documentation](https://hyperledger-fabric.readthedocs.io/en/latest/getting_started.html) files.

## Prerequisite software

The following prerequisites are required to run a Docker-based Fabric test network on your local machine.

## Mac

### Homebrew

For macOS, we recommend using Homebrew to manage the prereqs.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew --version # => Homebrew 2.5.2
```

The Xcode command line tools will be installed as part of the Homebrew installation. Once Homebrew is ready, installing the necessary prerequisites is very easy:

### Git

Install the latest version of git if it is not already installed.

```bash
brew install git
git --version # => git version 2.23.0
```

### cURL

Install the latest version of cURL if it is not already installed.

```bash
brew install curl
curl --version # => curl 7.64.1 (...)
```

### Docker

Install the latest version of Docker Desktop if it is not already installed. Since Docker Desktop is a UI application on Mac, use `cask` to install it.

#### Homebrew v2.x

```bash
brew cask install --appdir="/Applications" docker
```

#### Homebrew v3.x

```bash
brew install --cask --appdir="/Applications" docker
```

Docker Desktop must be launched to complete the installation so be sure to open the application after installing it:

```bash
open /Applications/Docker.app
```

Once installed, confirm the latest versions of both `docker` and `docker-compose` executables were installed.

```bash
docker --version # => Docker version 19.03.12, build 48a66213fe
docker-compose --version # => docker-compose version 1.27.2, build 18f557f9
```

Note: Some users have reported errors while running Fabric-Samples with the Docker Desktop `gRPC FUSE for file sharing` option checked. Please uncheck this option in your Docker Preferences to continue using `osxfs for file sharing`.

### Go

Optional: Install the latest Fabric supported version of Go if it is not already installed (only required if you will be writing Go chaincode or SDK applications).

```bash
brew install go@1.20.3
go version # => go1.20.3 darwin/amd64
```

### JQ

Optional: Install the latest version of jq if it is not already installed (only required for the tutorials related to channel configuration transactions).

```bash
brew install jq
jq --version # => jq-1.6
```

## Linux (Ubuntu/Debian based distro)

Prerequisites: git, cURL, Docker

```bash
sudo apt-get install git curl docker-compose -y

# Make sure the Docker daemon is running.
sudo systemctl start docker

# Add your user to the Docker group.
sudo usermod -a -G docker <username>

#Check version numbers
docker --version
docker-compose --version

# Optional: If you want the Docker daemon to start when the system starts, use the following:
sudo systemctl enable docker
```

### Go

Optional: Install the latest version of Go (only required if you will be writing Go chaincode or SDK applications).

### JQ

Optional: Install the latest version of jq (only required for the tutorials related to channel configuration transactions).

## Windows

### Docker

Install the latest version of Docker Desktop if it is not already installed.

### WSL2

Both the Fabric documentation and Fabric samples rely heavily on a `bash` environment. The recommended path is to use WSL2 (Windows Subsystem for Linux version 2) to provide a native Linux environment and then you can follow the Linux prerequisites section (excluding the Linux Docker prerequisite as you already have Docker Desktop) and install them into your WSL2 linux distribution.

WSL2 may not be installed by default; you can check and install WSL2 by going into “Programs and Features”, clicking on “Turn Windows features on or off” and ensuring that both “Windows Subsystem For Linux” and “Virtual Machine Platform” are selected.

Next you will need to install a Linux distribution such as Ubuntu-20.04 and make sure it’s set to using version 2 of WSL. Refer to Install WSL for more information.

Finally, you need to ensure Docker Desktop has integration enabled for your distribution so it can interact with Docker elements, such as a bash command window. To do this, open the Docker Desktop gui and go into settings, select `Resources` and then `WSL Integration` and ensure the checkbox for enable integration is checked. You should then see your WSL2 linux distribution listed (if you don’t then it is probably because it is still a WSL1 distribution and needs to be converted to WSL2) and you can then toggle the switch to enable integration for that distro. Refer to Docker Desktop WSL2 backend for more information

### Microsoft VS Code (Optional)

Microsoft VS Code provides an IDE that has tight integration with WSL2 Linux Distibutions. Search the Microsoft Marketplace in VS Code for the Remote Development extension pack for more information. This pack includes, among other things, the `Remote - WSL extension` and the `Remote - Containers` extension.

### Git For Windows (Optional)

Although not required, if you do decide to install Git on Windows and manage the Fabric repositories natively (as opposed to within WSL2 and its Git installation), then make sure you configure Git as follows:

Update the following `git` configurations:

```bash
git config --global core.autocrlf false
git config --global core.longpaths true
```

You can check the setting of these parameters with the following commands:

```bash
git config --get core.autocrlf
git config --get core.longpaths
```

These output from these commands should be false and true respectively.

## Notes

These prerequisites are recommended for Fabric users. If you are a Fabric developer, please refer to the instructions for Setting up the development environment.

# Install Fabric and Fabric Samples

Please install the prerequisites before following these install instructions.

We think the best way to understand something is to use it yourself. To help you use Fabric, we have created a simple Fabric test network using Docker compose, and a set of sample applications that demonstrate its core capabilities.

We also have precompiled Fabric CLI tool binaries and Fabric Docker Images which will be downloaded to your environment, to get you going.

The cURL command in the instructions below sets up your environment so that you can run the Fabric test network. Specifically, it performs the following steps:

1. Clones the hyperledger/fabric-samples repository.
2. Downloads the latest Hyperledger Fabric Docker images and tags them as latest
3. Downloads the following platform-specific Hyperledger Fabric CLI tool binaries and config files into the fabric-samples /bin and /config directories. These binaries will help you interact with the test network:
  - configtxgen
  - configtxlator
  - cryptogen
  - discover
  - idemixgen
  - orderer
  - osnadmin
  - peer
  - fabric-ca-client
  - fabric-ca-server

## Download Fabric samples, Docker images, and binaries
A working directory is required - for example, Go Developers use the `$HOME/go/src/github.com/<your_github_userid>` directory. This is a Golang Community recommendation for Go projects.

```bash
mkdir -p $HOME/go/src/github.com/<your_github_userid>
cd $HOME/go/src/github.com/<your_github_userid>
```

To get the install script:

```bash
curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh
```

Run the script with the `-h` option to see the options:

```bash
./install-fabric.sh -h
Usage: ./install-fabric.sh [-f|--fabric-version <arg>] [-c|--ca-version <arg>] <comp-1> [<comp-2>] ... [<comp-n>] ...
        <comp>: Component to install one or more of  d[ocker]|b[inary]|s[amples]. If none specified, all will be installed
        -f, --fabric-version: FabricVersion (default: '2.5.0')
        -c, --ca-version: Fabric CA Version (default: '1.5.6')
```

### Choosing which components

To specify the components to download, add one or more of the following arguments. Each argument can be shortened to its first letter:

- `docker` to use Docker to download the Fabric Container Images
- `podman` to use podman to download the Fabric Container Images
- `binary` to download the Fabric binaries
- `samples` to clone the fabric-samples GitHub repository to the current directory

To pull the Docker containers and clone the samples repo, run one of these commands, for example:

```bash
./install-fabric.sh docker samples binary
```

or

```bash
./install-fabric.sh d s b
```

If no arguments are supplied, then the arguments `docker`, `binary`, and `samples` are assumed.

### Choosing which version

By default, the latest version of the components are used; these can be altered by using the options `--fabric-version` and `-ca-version`. `-f` and `-c` are the respective short forms.

For example, to download the v2.5.0 binaries, run this command:

```bash
./install-fabric.sh --fabric-version 2.5.0 binary
```

You have completed installing Fabric samples, Docker images, and binaries to your system.

If you are looking to set up your environment to start contributing to Fabric, please refer to the instructions for [Setting up the contributor development environment](https://hyperledger-fabric.readthedocs.io/en/latest/CONTRIBUTING.html#setting-up-your-development-environment).

Note: This is an updated install script with the same end-result as the existing script, but with an improved syntax. This script adopts the positive opt-in approach to selecting the components to install. The original script is still present at the same location `curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/bootstrap.sh| bash -s`.

If you need help, post your questions and share your logs on the `fabric-questions` channel on [Hyperledger Discord Chat](https://discord.gg/6zvhb5R) or on [Stack Overflow](https://stackoverflow.com/questions/tagged/hyperledger-fabric).

# Fabric Contract APIs and Application APIs

## Fabric Contract APIs

Hyperledger Fabric provides various APIs to support the development of smart contracts (chaincode) in different programming languages. Smart contract APIs are available for Go, Node.js, and Java.

- Go contract API and documentation.
- Node.js contract API and documentation.
- Java contract API and documentation.

## Fabric Application APIs

Hyperledger Fabric offers a Fabric Gateway client API to support the development of applications in Go, Node.js, and Java. This API uses the Gateway peer capability introduced in Fabric v2.4 to interact with the Fabric network and is an evolution of the new application programming model introduced in Fabric v1.4. The Fabric Gateway client API is the preferred API for developing applications for Fabric v2.4 onwards.

- Fabric Gateway client API and documentation.

Legacy application SDKs also exist for various programming languages and can be used with Fabric v2.4. These application SDKs support versions of Fabric prior to v2.4 and do not require the Gateway peer capability. They also include some functionality, such as administrative actions for managing enrollment of identities with a Certificate Authority (CA), that are not offered by the Fabric Gateway API. Application SDKs are available for Go, Node.js, and Java.

- Node.js SDK and documentation.
- Java SDK and documentation.
- Go SDK and documentation.

Prerequisites for developing with the SDKs can be found in the Node.js SDK README, Java SDK README, and Go SDK README.

In addition, there is one other application SDK that has not yet been officially released for Python, but is still available for downloading and testing:

- Python SDK.