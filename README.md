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

The following table summarizes the Decision Making Matrix (DMM) which uses a scoring system of 1 to 5 for the three evaluated blockchain platforms based on the criteria listed.

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

# Privacy-Preserving Technique Evaluation for Secure API Access Management

This project requires an evaluation and comparison of privacy-preserving techniques compatible with Hyperledger Fabric, such as Zero Knowledge Proofs (ZKPs), Secure Multi-Party Computation (MPC), and homomorphic encryption, to determine the most suitable techniques based on the requirements outlined above.

## Decision Making Matrix

I have created a Decision Making Matrix (DMM) to evaluate and compare the three privacy-preserving techniques. The DMM has a scoring system of 1 to 5 for the criteria of scalability, compliance, privacy, security, and efficiency. The breakdown and reasoning for each row are provided below the DMM.

| Technique                          | Scalability | Compliance | Privacy | Security | Efficiency |
|-----------------------------------|-------------|------------|---------|----------|------------|
| Zero Knowledge Proofs (ZKPs)      | 3           | 5          | 5       | 5        | 3          |
| Secure Multi-Party Computation    | 2           | 4          | 4       | 4        | 2          |
| Homomorphic Encryption            | 1           | 4          | 5       | 5        | 1          |

### Breakdown and Reasoning

**Zero Knowledge Proofs (ZKPs)**

- Scalability: 3 - ZKPs can be computationally expensive, which might affect scalability with large numbers of users.
- Compliance: 5 - ZKPs enable anonymous access to information, meeting the compliance requirements for DoD and HIPAA.
- Privacy: 5 - ZKPs provide strong privacy guarantees by enabling access without revealing underlying information.
- Security: 5 - ZKPs ensure secure access control and cryptographic requirements.
- Efficiency: 3 - ZKPs have computational overhead, which might affect overall system performance.

**Secure Multi-Party Computation (MPC)**

- Scalability: 2 - MPC suffers from latency and communication overhead when scaled to millions of users.
- Compliance: 4 - MPC offers a high level of security and privacy, but it may not fully address the specific requirements for IoT devices and health records.
- Privacy: 4 - MPC provides privacy by keeping inputs private during computation, but it might not be suitable for anonymous access control.
- Security: 4 - MPC ensures secure computation but may not fully address access control and cryptographic requirements.
- Efficiency: 2 - MPC incurs communication overhead, which might negatively affect overall system performance.

**Homomorphic Encryption**

- Scalability: 1 - Homomorphic encryption has significant computational overhead and may not be efficient for handling millions of users.
- Compliance: 4 - Homomorphic encryption provides strong privacy guarantees for data storage and retrieval, but it may not fully address the specific requirements for IoT devices and health records.
- Privacy: 5 - Homomorphic encryption offers high privacy levels by enabling computation on encrypted data without decryption.
- Security: 5 - Homomorphic encryption ensures secure data storage and retrieval, meeting cryptographic requirements.
- Efficiency: 1 - Homomorphic encryption has substantial computational overhead, which might significantly impact overall system performance.

## Conclusion

Based on the DMM, Zero Knowledge Proofs (ZKPs) is the best-fitting technique, as it has the highest overall score and best matches the given requirements. ZKPs meet the specific needs for managing API access for embedded IoT devices and health records, allowing anonymous access to information, and ensuring scalability and compliance with Department of Defense and HIPAA requirements. Although ZKPs might have limitations in terms of computational efficiency, they provide the necessary security, privacy, and compliance needed for this use case.

# gRPC API Schema for Secure Healthcare Communication

This document outlines the technical breakdown for designing a gRPC API schema to allow secure communication and access control between clients and the server for healthcare data exchange. The schema uses mTLS RSA-2048 or greater cryptography for data in transit and client verification using a whitelist. The API follows the HL7 FHIR API standard for healthcare and uses gRPC instead of RESTful APIs.

## Requirements

The gRPC API schema should include:

- API endpoints for creating, retrieving, updating, and deleting patient records and medical information.
- Data structures for patient records, medical information, and access control.
- Implementation of access control using client certificates and a whitelist.

Additionally, the following requirements and clarifications are necessary:

1. The server will be responsible for verifying the client certificate.
2. Example data structures for the requested FHIR resources are provided in JSON format. However, the Protobuf schema should be used.
3. Access control should be based on permissions.
4. Use gRPC framework built-in error handling mechanisms.
5. The response format for the API requests should be Protobuf.

## Design

### Data structures

The following Protobuf message types are defined in the gRPC API schema for healthcare data exchange:

```proto
syntax = "proto3";

package healthcare;

option java_multiple_files = true;
option java_package = "com.example.healthcare";
option java_outer_classname = "HealthcareProto";

message Identifier {
  string use = 1;
  string system = 2;
  string value = 3;
}

message Code {
  string system = 1;
  string code = 2;
  string display = 3;
}

message Coding {
  Code code = 1;
}

message CodeableConcept {
  repeated Coding coding = 1;
}

message Quantity {
  double value = 1;
  string unit = 2;
  string system = 3;
  string code = 4;
}

message Ratio {
  Quantity numerator = 1;
  Quantity denominator = 2;
}

message Period {
  string start = 1;
  string end = 2;
}

message Reference {
  string reference = 1;
}

message HumanName {
  string family = 1;
  repeated string given = 2;
}

message Patient {
  string id = 1;
  repeated Identifier identifier = 2;
  repeated HumanName name = 3;
  string gender = 4;
  string birthDate = 5;
}

message Practitioner {
  string id = 1;
  repeated Identifier identifier = 2;
  repeated HumanName name = 3;
  string gender = 4;
  string birthDate = 5;
  repeated Qualification qualification = 6;
}

message Qualification {
  CodeableConcept code = 1;
  Period period = 2;
}

message Encounter {
  string id = 1;
  string status = 2;
  CodeableConcept class = 3;
  Reference subject = 4;
  Period period = 5;
}

message Observation {
  string id = 1;
  string status = 2;
  CodeableConcept code = 3;
  Reference subject = 4;
  string effectiveDateTime = 5;
  Quantity valueQuantity = 6;
}

message Condition {
  string id = 1;
  Reference subject = 2;
  CodeableConcept code = 3;
  string onsetDateTime = 4;
  CodeableConcept clinicalStatus = 5;
  CodeableConcept verificationStatus = 6;
}

message Medication {
  string id = 1;
  CodeableConcept code = 2;
  string status = 3;
  repeated Ingredient ingredient = 4;
  CodeableConcept form = 5;
}

message Ingredient {
  CodeableConcept itemCodeableConcept = 1;
  Ratio strength = 2;
}

// Service definition
service HealthcareService {
  // Add RPC methods for each supported FHIR resource and operation (e.g., CreatePatient, GetPatient, etc.)
}
```

### API Endpoints

The API endpoints for creating, retrieving, updating, and deleting patient records and medical information are defined as follows:

```proto
service HealthcareService {
  rpc CreatePatient(Patient) returns (Patient) {}
  rpc GetPatientById(string) returns (Patient) {}
  rpc UpdatePatient(Patient) returns (Patient) {}
  rpc DeletePatient(string) returns (google.protobuf.Empty) {}
  rpc CreateMedicalInformation(MedicalInformation) returns (MedicalInformation) {}
  rpc GetMedicalInformationById(string) returns (MedicalInformation) {}
  rpc UpdateMedicalInformation(MedicalInformation) returns (MedicalInformation) {}
  rpc DeleteMedicalInformation(string) returns (google.protobuf.Empty) {}
}
```

### Access Control

Access control is based on permissions defined in the `Permission` message type. The `permissions` field is included in the `Patient` message type and is used to store the permissions for each practitioner in the system. The `has_permission` helper function is used to check if a practitioner has the required permission for a given operation. The server-side implementation verifies the client's permissions before allowing them to perform any operation on a specific resource type.

```python
def has_permission(practitioner, resource_type, operation):
    for permission in practitioner.permissions:
        if permission.resourceType == resource_type and permission.operation == operation:
            return True
    return False
```

In each RPC method, the `has_permission` helper function is used to check the client's permissions before processing the request:

```python
def CreatePatient(self, request, context):
    practitioner = get_practitioner_from_context(context)
    if not has_permission(practitioner, "Patient", "create"):
        context.abort(grpc.StatusCode.PERMISSION_DENIED, "Permission denied")

    # Proceed with creating the patient
    # ...
```
Here is an example of an extended `Practitioner` message type to include permissions:

```proto
message Practitioner {
  string id = 1;
  repeated Identifier identifier = 2;
  repeated HumanName name = 3;
  string gender = 4;
  string birthDate = 5;
  repeated Qualification qualification = 6;
  repeated Permission permissions = 7;
}
```

### Error Handling

The gRPC framework built-in error handling mechanisms are used to handle errors or unexpected requests.

### Response Format

The response format for the API requests is Protobuf.

### Security

The server is responsible for verifying the client certificate. The server is configured to use mTLS for secure communication and client verification. The appropriate SSL/TLS credentials, including the server's private key, certificate, and trusted CA certificates, are set up in the server code. The server also verifies that the client's certificate is signed by a trusted CA and matches an entry in the server's whitelist.

## Conclusion

The designed gRPC API schema for healthcare data exchange allows secure communication and access control between clients and the server. The schema uses mTLS RSA-2048 or greater cryptography for data in transit and client verification using a whitelist. The API follows the HL7 FHIR API standard for healthcare and uses gRPC instead of RESTful APIs. The schema includes API endpoints for creating, retrieving, updating, and deleting patient records and medical information. Data structures for patient records, medical information, and access control are defined. Access control is based on permissions, and the gRPC framework built-in error handling mechanisms are used to handle errors or unexpected requests. The response format for the API requests is Protobuf. The server is responsible for verifying the client certificate, and the appropriate SSL/TLS credentials are set up in the server code.