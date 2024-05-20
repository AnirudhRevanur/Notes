# Unit 2

- Three pillars of Blockchain:
  - Distributed Systems
  - Crypto
  - Economic Models

## Distributed Consensus

- A procedure to reach a common agreement in a distributed or decentralized multi-agent platform
- Important for a message passing system
- Need consensus for reliability and fault tolerance
- Consensus can be hard in certain scenarios if a node behaves differently
- If there is no failure, then easy, apply voting and call it a day
- Cannot ensure both "Safety" and "Liveness" together

## Types of Faults

- **_Crash Fault_**: A node suddednly crashes or becomes unavailable
- **_Network Partition Fault_**: A network fault causes partition
- **_Byzantine Fault_**: Node behaves maliciously

## Properties

- **_Termination_**: Every correct individual decides some value at the end of the consensus protocol
- **_Validity_**: If all the individuals propose the same value, then all the correct individuals decide on that value
- **_Integrity_**: Every correct individual decides at mose one value and the decided value must be proposed by some individuals

## Limitations

- Message passing is not a good idea
- Anonymous entities
- Open Network

### Puzzle Solving

- We need a leader
- No one knows each other
- Network gives a puzzle and everyone tries to solve it
- Whoever solves it first becomes the leader
- Whatever the leader says, everyone agrees
- Difficult to solve, easy to verify

## Consensus in Bitcoin

- Every node has a block of transactions that has already reached into the consensus
- The nodes also has a list of outstanding transactions that need to be validated against the block of committed transactions
- Block Based consensus
- Broadcast the info then apply choice
- May not be feasible cause there is no global clock
- Any valid block can be accepted, even if it proposed by only one miner

## Consensus Algorithms

- If there are multiple decision makers, then there is a need to come to collective agreement ie, come to consensus
- Consensus is hard, then Nodes may crash, or may be malicious
- Network is imperfect &rarr; Not all pairs of nodes connected &rarr; Faults in networks &rarr; Latency
- Many Algorithms like PoW, PoS, DelegatedPOs, Proof of Authority, Proof of Elapsed Time, Proof of Scope, Proof of Space, Proof of Burn, RAFT, PAXOS, Byzantine Fault Tolerance, PBFT
- PAXOS and RAFT are Crash Fault Tolerant
- BFT and PBFT are part of Byzantine Fault Tolerance

### Permissioned Blockchain

- Depends on factors like extent of decentralization required
- How much the participants in a netowrk trust each other
- The number of permissions that must be granted
- PBFT and its variants

### Permissionless Blockchain

- Proof of Work, Proof of Elapsed Time
- Crucial to choose the right consensus model for your specific blockchain
- Assume that more than 50% are honest nodes

### Challenges

- Participants do not know each other
- Anyone can propose a new block
- Network is asynchronous &rarr; Node may see blocks in different order
- Any type of monopoly has to be prevented
- No fixed number of transactions per block
- Limit on the Block Size

### Safety vs Liveness

- **_Safety 1_**: Next block should be correct in practice &rarr; transactions are verified, block has right Hash and Nonce
- **_Safety 2_**: All miners should agree on a single block &rarr; Next block should be selected unanimously
- **_Liveness_**: Add a block as long as it is correct &rarr; Verify conflicts later

## Proof of Work

- Find or generate a value which is hard to generate, but it is easy to verify
- Hash should have "N" leading zeroes, more the value of "N", higher the difficulty
- Each miner needs to solve math puzzle to propose transactions
- Lots of computation, power and time
- Finding hash value based on the input message + hash value of the previous block
- Math puzzle should be less than the difficulty level of the systems
- If Block 3 has to be added, then find the hash of (Block 3, Hash 2, Nonce)
- Nonce is the only variable
- Increment nonce to meet requirements
- Miner node will say nonce value, others will verify
- If 51% of the miners agree with the given nonce, then the winner's block is considered to be correct
- Miner with correct answer will be rewarded
- Majority of nodes do not agree, then no reward is given
- Miners have no incentive to cheat
- Adding a node to the network increases security by 1/N

### Bitcoin

- Bitcoin uses SHA-256 Hashing Algorithm and Hashcash Proof of Work system as the mining bias
- Header contains:
  - Recipient's email address
  - Date of the message
  - Information proving that the required computation has been performed
- Date allows receipient to record headers received recently and to ensure that the header is unique to the email
- Header contains:
  - Version
  - Bits
  - Date
  - Resource
  - Extension
  - Random string
  - Counter

### Pros

- Protected from corruptions as long as 51% or more of the blockchain network is legitimate
- It has been working from 2009 and it still works
- Slower and Safer &rarr; transaction will not reset
- Trustless &rarr; no one can block your transaction from porcessing

### Cons

- 51% risk
- It is slow
- It is costly
- Miners can pool together, and can lead to centralization

## Proof of Stake

- Competitive Consensus Algorithm
- Alternative to PoW
- Peercoin was the first currency to use PoS
- Proposed as an alternative to Proof of Work
- Removes the guessing game from consensus
- Mining no longer requires specialized and powerful hardware
- Less energy intensive form of consensus
- Can be performed from any device
- Small upside for being honest, and a major loss if dishonest
- Block of transactions created
- When it is time for group consensus, everyone who wishes to participate lock up funds in a stake
- A "random" player is selected
- Player's block data is shown to all other participants
- Other players stake on the validity of the block transactions
- If majority agree, then the random player is rewarded
- If the majority disagree, then the player gets no reward and loses their stake
- New player is then randomly selected to share their block data
- Ethereum started as PoW, and now working as PoS
- Stake a minimum of 32 Ethereum
- At least 128 validators
- Allows for sharding

### Pros

- It is energy efficient and does not burn electricity when mining
- Can be more expensive to attack than PoW
- Need to purchase a large portion of native cryptocurrency
- Scales easily to handle load

### Cons

- Rewards are weighted to those who stake the longest
- Netowkr allows wealthy to control more of the network and this may cuase centralization

## Delegated Proof of Stake

- Reputation scores, bettwe website and social media accounts are used to select set of validators
- Stakeholders elect witnesses who will validate transactions and create blocks
- EOS is one of the most popular DPoS Blockchains
- Paid fees for producing blocks
- Produce blocks one at a time in round robin fashion or by random selection

### Pros

- It is energy efficient
- It is fast

### Cons

- It is a centralized system &rarr; May corrupt

## Proof of Authority

- Useful for Private networks
- Testing phase when a network is created
- Rights to generate new blocks are awarded to the nodes that have the rights/authority to do so
- Process is automated and does not require vaalidators to be constantly monitoring
- Leverages value of identities
- Staking their own reputation

### Common Attacks

- **_DDoS_**
- Attacker sends a large number of transactions and blocks targeted to one node in the network
- Makes it impossible to defende against DDoS, as network nodes are pre authenticated
- **_51% Attack_**
- Obtaining power of nodes ina permissioned blockchain is much harder than a permissionless blockchain
- Risk of serious damage is only when authority node is disrupted

### Pros

- Energy efficient
- Fast
- High risk tolerance as long as 51% of the nodes are non-malicious
- Interval of time in which block is created is predictable
- High transaction rate

### Cons

- Not decentralized, making centralized system more efficient
- Validators are visible to anyone
- Knowing validators can lead to third party manipulation
