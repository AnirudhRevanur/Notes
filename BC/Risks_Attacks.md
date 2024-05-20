# Risks

## Risks in Blockchain Operation Mechanism

- 51% Vulnerability
- Private Key Security
- Criminal Activity
- Double Spending
- Transaction privacy leakage

### Smart Contract Execution

- Criminal Smart Contract
- Vulnerabilities in Smart Contract
- Under-optimized smart contract
- Under-priced operations

### Attack Surfaces

- Blockchain Network
- User Wallets
- Smart Contract
- Transaction Verification Mechanism
- Mining Pool

### Cybersec Vulnerabilities

1. Clients' Vulnerabilities
2. Consensus Mechanisms Vulnerabilities
3. Mining Pool Vulnerabilities
4. Network Vulnerabilities
5. Smart Contract Vulnerabilities

## Attacks on Blockchain Network

1. DDoS
2. Transaction Malleability
3. Time Jacking
4. Routing attacks
5. Sybil Attacks
6. Eclipse Attacks
7. Long range attacks

### DDoS

- Hard to execute on a blockchain network
- Hackers intend to bring down a server by consuming all its processing resources with numerous requests
- Aim to disconnect a network's mining pools, e-wallets, crypto exchanges, and other financial services
- A blockchain can also be hacked with DDoS at its application layer using DDoS botnets
- In 2017, Bitfinex suffered a massive DDoS Attack
- Inconvenient for IOTA Foundation
- In 2020, Bitfinex experienced another DDoS attack just a day after OKEx

### Transaction Malleability Attacks

- Intended to trick the victim into paying twice
- If attackers manage to alter a transaction's ID, they can broadcast the transaction with a changed hash
- Have the fake/altered transaction confirmed before the original transaction
- If the attack succeeds, then the sender will believe the transaction has failed, but funds will be withdrawn
- If sender repeats transaction, then the same amount will be debited twice
- Hack is successful once two transactions are confirmed by miners
- Mt. Gox went bankrupt because of a malleability attack in 2014

### Time Jacking

- Exploits a theoretical vulnerability in Bitcoin timestamp heading
- During a time jacking attack, hacker alters the network time counter of the node and forces the node to accept an alternative blockchain
- This can be achieved when a malicious user adds multiple fake peers to the network with inaccurate timestamps
- Time jacking can be prevented by restricting acceptance time ranges or using the node's system time

### Routing Attacks

- A routing attack can impact both individual nodes and the whole network
- Idea of this hack is to tamper with transactions before pushing them to peers
- Nearly impossible for other nodes to detect this tampering
- Hacker divides the network into partitions that are unable to communicate with each other
- Partition Attack: Divides the network nodes into separate groups
- Delay Attack: Tampers with propagating messages and sends them to the network

### Sybil Attacks

- Arranged by assigning several identifiers to the same nodes
- No trusted nodes, so request is sent everywhere
- During a Sybil Attack, hacker takes control of multiple nodes in the network
- Victim is surrounded by fake nodes that close up all their transactions
- Victim is then open to double spending attacks
- It is difficult to detect and prevent
- Increasing the cost of creating a new identity
- Requiring for some type of trust for joining the network
- Determining user power based on reputation

### Eclipse Attacks

- Requires a hacker to control a large number of IP Addressess or have a botnet
- Attacker overwrites the address in the "tried" table of the victim node and waits until the victim node is restarted
- After restarting, all outgoing connections of the victim node will be redirected to the IP address controlled by the attacker
- This makes the victim unable to obtain transactions they are interested in
- Researchers from Boston Uni were able to initiate Eclipse Attack on Ethereum Network and did it with a very few number of machines

### Long Range Attack

- Target Networks that use proof of stake consensus algorithm
- Simple: A naive implementation of proof of stake protocol, when nodes don't check block timestamps
- Posterior corruption: An attempt to mint more blocks than the main chain in the given time frame
- Stake Bleeding: Copying a transaction from the honestly maintained blockchain to a private blockchain maintained by the attacker
- Hacker uses a purchced or stolen private key of a sizable token balance
- Hacker can generate an alternate history of blockchain and increase rewards

## Attack on Smart Contract

- Three main properties => Ability to hold value, transparency and immutability are essential for them to work
- Issues are related to bugs in source code, network's virtual machine, runtime environment and the blockchain itself

### Vulnerabilities in Source Code

- If smart contract has risks, then risky to parties that sign
- Bugs discovered in Ethereum costed almost 80 million USD
- Most common is that Solidity opens a possibility to delegate control to untrusted functions from other smart contracts
- This is called **_reentrancy attack_**
- Contract A calls a function from contract B that has undefined behaviour

### Vulnerabilities in Virtual Machine

- EVM is distributed stack based computer
- All smart contracts are run on EVM

#### Immutable defects

- Blockchain is immutable by nature
- Once Smart Contract is launched, it cannot be changed
- If Smart Contract has any bugs, cannot be fixed
- Cybercriminals can exploit this to steal Ether or create a new fork like the DAO attacck

#### Cryptocurrency lost in transfer

- If Ether is transferred to an orphaned address that doesn't have any owner or contract

#### Bugs in access control

- Missed modifier bug that allows a hacker to get sensitive functionality in a contract

#### Short Address Attack

- EVM can accept incorrectly padded arguments
- Hackers can exploit this vuln by sending crafted addresses to victims
- Happened to Coindash in 2017

### Front running

- Also called as Transaction Ordering Dependence
- "Entity benefits from prior access to privileged market info about upcoming transactions and trades"
- Ex: If we know that a very large purchase is going to happen, then bad actor can purchase that token in advance and sell for even more
- Issue in financial markets and coming up in cryptocurrency markets as well
- It can be hard to protect

### DoS with Block Gas Limit

- All blocks have a gas limit
- This is made so that no infinite transaction loop is created
- If gas goes above limit, transaction fails
- Sending money to an array of addresses can block the gas limit even without any malicious intent
- This situation can also lead to an attack
- If a bad actor decides to create a significan amount of addresses, then transaction can be blocked indefinitely

### Block Stuffing

- An attacker can fill several blocks before a transaction can be processed by using a high gas price
- If the gas price is high enough and and the transactions consume enough gas, they can fill blocks and prevent other transactions from being processed
- To prevent attacks, it's important to consider if it is safe to incorporate time-based actions

### DoS with Unexpected Revert

- When you try to send funds to a user and functionality relies on that transfer being successful
- If bad actor makes smart contract, then he can write fallback function that reverts all payments

### Forcibly sending Ether to contract

- It is unwanted for users to be able to send Ether to smart contract
- It is possible to bypass a contract fallback and forcibly send Ether

### Gas Griefing

- Malicious user plays a game in an unintended way to bother other players
- This can be used to prevent transactions from being performed as intended
- Attacks can be done on contracts which accept data and use it in a subcall on another contract
- Multisignature wallets ans well as transaction relayers
- If subcall fails, the transaction is reverted, or execution is continued

### Reentrancy

- When a bug can allow a function to proceed multiple times, which it should not
- Can be used to drain funds from a smart contract
- Vector used in the DAO Attack
- Single function reentrancy: Vulnerable function is the same function an attacker is trying to recursively call
- Cross function reentrancy: Vulnerable function shares a state with a function an attacker can exploit

## CIA Triad

### Confidentiality

- Way to keep to information hidden from unauthorized people
- Security Agencies break confidentiality so they can perform forensics
- Use Hyperledger Fabric to achieve this, as it is not possible to do so in a public network

### Integrity

- Protect information from being tampered
- Mandatory complaicnce
- Maintain consistency, accuracy and trust
- This is done by cryptographically hashing
- Not possible to understand message from just digest
- Ethereum uses Keccack-256 and Bitcoin uses SHA-256
- Can also be done with Hyperledger Fabric
- Committing a peer always validates the new block before adding it to the ledger

### Availability

- On-time and reliable access to data
- DDoS and Ransomware are some of the most powerful weapons that block this
- Web App firewalls, DDoS Protection, Content Delivery Network and Disaster Recovery
- Decentralized nature of Blockchain makes it harder to disrupt the network
- There is no single point of failure
