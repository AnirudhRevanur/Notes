# Hyperledger Fabric

## Introduction

- Linux foundation founded this project
- It has a ledger, uses smart contracts, and is a system by which participants manage transaction
- It is **_not_** open permission
- Enroll through a trusted Membership Service Provider
- Highly Modular, Decentralized LedgerTechnology that was designed by IBM
- Hyperledger Fabric is private and requires permission to access
- Business can segregate information and the transactions can now be sped up, because load on a node has reduced
- **_Fabric 2.0_** made faster transactions, updated smart contract tech and streamlined data sharing

## Benefits

- Data Protection and Consistency
  - Use permissions to ensure accountability
- Confidential transactions
  - Give business the security to make transactions visible to certain parties
- No Cryptocurrency
  - No expensive mining for transactions
- Programmable
  - Embedded logic in the smart contracts to automate business work

## Participants

- Blockchain User
  - Blockchain to Blockchain Transactions
- Certificate Authority
  - Access Security Certifications
- Traditional Data Sources
  - Access to Data
- Traditional Processing Platforms
  - Access to logic
- Blockchain Network Operator
  - Operates
- Blockchain Developer
  - Creates applications
- Regulator
  - Performs oversight

## Architecture

- Committing Peer:
  - Maintains ledger and state
  - Commits transactions
  - May hold chaincode/smart contract
- Endorsing Peer:
  - Specialized committing peer that receives a transaction for endorsement
  - Responds granting or denying endorsement
  - Must hold smart contract
- Ordering Node:
  - Approves the inclusion of transaction blocks into the ledger and communicates with committing and endorsing peers
  - Doesn't hold smart contract
  - Doesn't hold ledger
- Transaction Flow:
  1. Endorse
  2. Order
  3. Validate

## Transaction Flow

1. Propose Transaction

- Application Proposes transaction
- Endorsement Policy
- Client application submits a transaction proposal for Smart Contract

2. Execute Proposed Transaction

- E0, E1, E2 will each execute the proposed transaction
- None of these executions will update the ledger
- Each execution will capture the set of Read and Write data(RW Set)
- RW set will now flow in the fabric
- Transactions can be signed and encrypted

3. Proposal Response

- RW Sets are asynchronously returned to application
- RW sets are signed by each endorser, and includes a record version number

4. Order Transaction

- Responses submitted for ordering
- Application submits responses as a transaction to be ordered
- Ordering happens across the fabric in parallel

5. Deliver Transactions

- Orderer delivers to committing peers
- Ordering service collects transactions into proposed blocks for distribution to committing peers
- Peers can deliver to other peers in a hierarchy
- Different ordering algos possible

6. Validate Transaction

- Committing peers validate transactions
- Every committing peer validates against endorsement policy
- Check RW set are still valid for current world state
- Validated transactions are applied to the world state and retained on ledger
- Invalid transaction are retained on ledger, but do not update world state

7. Notify Transaction

- Committing peers notify applications
- Applications can register to be notified when transaction fails or succeeds
- Applications will be notified by each peer that the are connected to

## Core Components

### Ordering Service

- Packages transactions into blocks to be delivered to peers
- Communication with service is via channels
- Different configuration options include
- **_SOLO_** for single node development
- **_Kafka_** for crash fault tolerant consensus. Needs minimum 3 peers and prefers an odd number of nodes

### Channel

- Provide privacy between different ledgers
- Ledgers exist in the scope of a channel
- Channels can be shared across entire network of peers
- Can be permissioned for a set of participants
- Chaincode is installed on peers to access worldstate
- Chaincode is instantiated on specific peers
- Peers can participate in multiple channels
- Concurrect execution for performance and scalability

#### Single Channel Network

- All peers connect to the same system channel
- All peers have the same chaincode and maintiain the same ledger

#### Multi-Channel Network

- Different peers connect to different channels, with different chaincodes

#### Fabric Peer

- Each peer connects to one or more channels
- Maintains one or more ledgers for each channel
- Chaincodes are instantiated in separate containers
- Chaincodes are shared across channels
- Local Membership Service Provider provides crypto material
- Emits events

### Client Application

- Each client application uses Fabric
- Connects over channels to one or more peers
- Connects over channels to one or more orderer nodes
- Receives events from peers
- Local MSP provides crypto material

### Fabric Certificate Authority

- Default Certificate Authority within fabric network for issuin E-certs
- Supports clustering for HA characteristics
- Supports LDAP for user Authentication
- Supports HSM for security
- Can be configured as an intermediate CA
- Provides certs to all

## Organizations

- Each organization defines:
  - Membership Service Provider
  - Admins
  - Users
  - Peers
  - Orderers
- A network can include many organizations representing a consortium
- Each org has an ID

### Consortium Network

- Organizations 1 and 3 run peers
- Organization 2 provides the ordering service only

### Membership Service Provider

- An MSP manages aset of identities within a distributed Fabric Network
- Provides identity for
  - Peers and orderers
  - Client Applications
  - Administrators
- Identities can be given by:
  - Fabric CA
  - External CA
- Provides: Auth, Validation, Signing and Issuance
- Supports different crypto standards with pluggable interface
- Network can include multiple MSPs
- TLS Crypto material for encrypted communications

### TLS

- Transport Security Layer
- Cryptographic protocols that provide communications over a network
- Provides privacy and data integrity
- Symmetric cryptography is used to encrypt data transmitted
- Public Key cryptography is used to authenticate
- Include message integrity checks to prevent loss or alteration of data
- All communication in Fabric is secured using TLS

### User Identities

- Each local MSP includes:
  - Keystore: Private key for signing transactions
  - Signcert:Public x.509 certificate
- May also include TLS credentials
- Can be backed by a Hardware Security Module

### Peer and Orderer Identities

- Each peer and orderer has a local MSP
- Each local MSP includes:
  - Keystore: Private key for signing transactions
  - Signcert:Public x.509 certificate
- In addition to Peer/Orderer MSPs identify authorized administrators:
  - admincerts: List of administrator certificates
  - cacerts: The CA public cert for verification
  - crls: List of revoked certificates
- Peers and Orderers also receive channel MSP info
- Can be backed by Hardware Security Module

### Channel MSP Information

- Channels include additional organizational MSP information
- Determines which orderers or peers can join the channel
- Determines client applications read or write access to the channel
- Stored in config blocks in the ledger
- Each channel MSP Includes:
  - admincerts: List of administrator certificates
  - cacerts: The CA public cert for verification
  - crls: List of revoked certificates
- Does not include any private keys for identities

### New User Registration and Enrolment

- Admin registers new user with Enroll ID
- User Enrolls and receives credentials
- Additional offline registration and enrollment options available

### Endorsement Policies

- Describes the conditions by which a transaction can be endorsed
- A transaction can be considered valid if it has been endorsed according to its policy
- Each chaincode is deployed with and Endorsement Policy
- `AND('Org1.member','Org2.member','Org3.member')` => Sign from members of all 3 organizations
- `OR('Org1.member', 'Org2.member')` => From any one of the organization's members
- Can chain both OR and AND together to make more rules

## Use Cases

### Interoperability of Assets

#### Description

- Interoperability of assets means the exchange of assets among a group of people

#### Problem Statement

- If an organization requires 20000 units of asset B but instead of asset A, it needs a way to exchange asset A for asset B
- The current market might not offer enough liquidity to fulfill this trade quickly
- There can be liquidity between asset A and C, and between C and B

#### Solution

- A chain network connects buyers with "buried" sellers
- Finds the best match and executes transaction
- So basically a business network of a group of individuals can be set up on the Hyperledger Fabric and the assets can be exchanged among the buyer and sellers
