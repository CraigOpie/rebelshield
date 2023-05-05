# RebelShield

RebelShield is a cutting-edge, privacy-preserving API for blockchain-based authentication and access control using gRPC. The project aims to provide a secure and efficient solution for managing API access in various applications while ensuring privacy and compliance with international data protection standards.

## Components

- `blockchain`: The blockchain system implementation for user registration, authentication, and access control. Includes smart contracts, DIDs, and verifiable credentials.
- `grpc-api`: The gRPC API implementation for secure communication between clients and the server, including server and client code based on protobuf schema.
- `privacy-preserving`: Integration of privacy-preserving techniques like zero-knowledge proofs, secure multi-party computation, or homomorphic encryption.

## Getting Started

To get started with the RebelShield project, please follow the installation and usage instructions provided in the README files of each component.

## Contributing

At this time, RebelShield is a private project and not open for contributions. For inquiries about licensing or permission to use this software, please contact the project owner.

## License

RebelShield is copyrighted software, and all rights are reserved by the project owner. Unauthorized use, reproduction, modification, or distribution is strictly prohibited. Please refer to the LICENSE file for more information.

# gRPC API Component for RebelShield

This component of the RebelShield project provides the gRPC API implementation for secure communication between clients and the server. It includes server and client code generated from the protobuf schema and handles user authentication, request signing, and API responses.

## Prerequisites

- gRPC and Protocol Buffers
- A running instance of the blockchain component (see the `blockchain` folder for setup instructions)

## Installation

1. Clone the repository and navigate to the `grpc-api` directory.
2. Install the necessary dependencies for gRPC and Protocol Buffers.
3. Generate the server and client code from the protobuf schema using the provided gRPC tools.

## Usage

1. Set up and run the gRPC server to expose the API and handle incoming requests securely.
2. Implement and run the gRPC client to interact with the server, handling user authentication, signing requests, and processing API responses.

## Testing

Thoroughly test the gRPC API component for security, privacy, and performance. Identify and address any potential weaknesses or bottlenecks.

## License

Unauthorized use, reproduction, modification, or distribution of this component is strictly prohibited. Please refer to the main project's LICENSE file for more information.

# Private Blockchain Platform Evaluation for Secure API Access Management

This project aims to evaluate and compare potential private blockchain platforms for their suitability in providing a secure and efficient solution for managing API access for embedded IoT devices used for the United States Department of Defense and/or patient information for health records while ensuring privacy and compliance with all United States data protection standards, DISA-STIG, and HIPAA requirements.

## Network Requirements

The private blockchain network should be able to support a minimum of three nodes and up to 100,000 nodes, with each node verified as authorized using mTLS RSA-2048 signature verification. Nodes not in the mTLS whitelist will not be allowed to participate. The project requires anonymous access to information, using Zero Knowledge Proofs for Identity and Access Management, and the ability to securely store immutable encrypted data in the blockchain or a distributed file system.

## Scalability

The platform should be scalable to handle tens of users to millions of users simultaneously, with data size and types for each API call yet to be determined but implemented using gRPC. The project strives to satisfy use cases requiring high availability, fast response, and large use volume, while also being low power consuming.

## Budget and Hardware

The project has a budget of $500 for computing hardware and is expected.

## Blockchain Identification

This project requires the evaluation and comparison of three potential private blockchain platforms: Hyperledger Fabric, R3 Corda, and Quorum. Each platform has its own strengths and weaknesses, and the following information outlines their features, scalability, and privacy support to assist in the decision-making process.

## Hyperledger Fabric

Hyperledger Fabric is an open-source, permissioned blockchain platform developed by IBM. It has a modular architecture that allows for customizable consensus algorithms, identity services, and data storage. Hyperledger Fabric supports chaincode (smart contracts) written in Go, JavaScript, and Java. Rust, C#, and C/C++ are not officially supported. It features a distributed file system called IPFS (InterPlanetary File System) for storing large files and supports gRPC for communication between nodes. Hyperledger Fabric provides mTLS for securing communication between nodes and client applications. It also supports Zero Knowledge Proofs via its Identity Mixer library. 

Hyperledger Fabric can be run on Raspberry Pi 4, but performance may not be optimal for large-scale deployments.

## R3 Corda

R3 Corda is a permissioned blockchain platform designed specifically for financial and healthcare industries. It has a focus on privacy, scalability, and legal compatibility. R3 Corda supports writing smart contracts in Java and Kotlin, but not Rust, C#, or C/C++. It implements a custom storage solution that can be easily replaced with a distributed file system like IPFS. R3 Corda uses gRPC for communication between nodes and supports mTLS. It also provides support for Zero Knowledge Proofs using SGX (Software Guard Extensions).

R3 Corda can run on Raspberry Pi 4, but it may not be the most efficient solution for large-scale deployments.

## Quorum

Quorum is a permissioned variant of Ethereum designed for enterprise use cases. It features a high degree of privacy and performance. Quorum supports smart contracts written in Solidity, but not Rust, C#, or C/C++. It integrates with IPFS for storage of large files. Node communication is not based on gRPC, but it can be adapted to use gRPC if needed. Quorum offers mTLS support for securing communication between nodes and supports Zero Knowledge Proofs through the integration of zk-SNARKs (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge).

Raspberry Pi 4 compatibility is uncertain, and performance may be limited for large-scale use cases.

## Decision Making Matrix

The following table summarizes the Decision Making Matrix (DMM) for the three evaluated blockchain platforms based on the criteria listed.

| Criteria                           | Hyperledger Fabric | R3 Corda | Quorum |
|-----------------------------------|--------------------|-------------|----------|
| Development language support      | 3                  | 3           | 2        |
| Communication protocol support    | 5                  | 4           | 3        |
| Privacy support                   | 4                  | 4           | 4        |
| Scalability                        | 4                  | 4           | 4        |
| Data storage                       | 4                  | 4           | 4        |
| Compatibility with Raspberry Pi 4 | 3                  | 3           | 2        |
| Ease of Development                | 4                  | 3           | 3        |
| Consensus Mechanism Flexibility   | 5                  | 4           | 3        |
| Industry Adoption                 | 4                  | 4           | 3        |

### Breakdown for each row in the Decision Making Matrix

**Development language support:**

Hyperledger Fabric: 3 (Supports Go, JavaScript, and Java, but no native Rust, C#, or C/C++)
R3 Corda: 3 (Supports Java and Kotlin, but no native Rust, C#, or C/C++)
Quorum: 2 (Supports Solidity, but no native Rust, C#, or C/C++)

**Communication protocol support:**

Hyperledger Fabric: 5 (Native gRPC support)
R3 Corda: 4 (Can be adapted to use gRPC)
Quorum: 3 (No native gRPC support, but can be adapted if needed)

**Privacy support:**

Hyperledger Fabric: 4 (Supports Zero Knowledge Proofs via Identity Mixer and mTLS)
R3 Corda: 4 (Supports Zero Knowledge Proofs using SGX and mTLS)
Quorum: 4 (Supports Zero Knowledge Proofs via zk-SNARKs and mTLS)

**Scalability:**

Hyperledger Fabric: 4 (Proven scalability for large networks)
R3 Corda: 4 (Designed to handle large-scale financial and healthcare applications)
Quorum: 4 (Ethereum-based and suitable for large-scale deployments)

**Data storage:**

Hyperledger Fabric: 4 (Integrated with IPFS for distributed file storage)
R3 Corda: 4 (Custom storage solution, can be replaced with IPFS or other distributed file systems)
Quorum: 4 (Integrated with IPFS for distributed file storage)

**Compatibility with Raspberry Pi 4:**

Hyperledger Fabric: 3 (Can run on Raspberry Pi 4, but performance may be limited for large-scale deployments)
R3 Corda: 3 (Can run on Raspberry Pi 4, but performance may be limited for large-scale deployments)
Quorum: 2 (Uncertain compatibility with Raspberry Pi 4 and performance limitations)

**Ease of Development:**

Hyperledger Fabric: 4 (Good ecosystem and documentation)
R3 Corda: 3 (Decent ecosystem and documentation)
Quorum: 3 (Ethereum-based but not as mature as the other two platforms)

**Consensus Mechanism Flexibility:**

Hyperledger Fabric: 5 (Highly flexible and modular architecture)
R3 Corda: 4 (Notary-based consensus with some customization)
Quorum: 3 (Limited to RAFT and Istanbul BFT)

**Industry Adoption:**

Hyperledger Fabric: 4 (Widely adopted across various industries)
R3 Corda: 4 (Strong adoption in financial and healthcare sectors)
Quorum: 3 (Limited adoption compared to the other two platforms)

## DMM Research Summary

Based on the Decision Making Matrix, Hyperledger Fabric and R3 Corda score similarly in most criteria, with Hyperledger Fabric having a slight advantage in communication protocol support. Quorum lags behind due to its uncertain compatibility with Raspberry Pi 4 and lack of native gRPC support. Therefore, Hyperledger Fabric and R3 Corda are the top contenders for this project.

Overall, Hyperledger Fabric has a rich ecosystem, modular architecture, and strong privacy features. R3 Corda is designed for financial and healthcare industries, has easily replaceable storage solutions, and supports Java and Kotlin. Both platforms have proven scalability and support Zero Knowledge Proofs.  I will be moving forward with the Hyperledger Fabric Blockchain for this project.