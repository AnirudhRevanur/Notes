# Unit 1

## Introduction to Cloud Computing

- Basically delivering computing at the Internet Scale
- Compute, Storage etc are made available within minutes and on-demand
- **_Cloud computing is a model for enabling ubiquitous, convenient, and on-demand network access to a shared pool of computing resources_**
- Can be rapidly provisioned and released with minimal management efforts
- **Data Centers** host the physical compute, storage and networking infrastructure
- Large clouds have functions distributed over multiple locations from central servers

### Features of Cloud Computing

- **On demand Self Service:** The compute, storage or platform resources are self-provisioned with minimal configuration
- **Broad network access:** Ubiquitous access to cloud appls from various devices
- **Resource Pooling:** Cloud services should share resources between users and clients to reduce costs
- **Scalability:** Accommodate larger or smaller loads while supporting expectations of QoS like response time
- **Elasticity:** Should be able to rapidly increase or decrease the computing resources needed
- **Measured:** "Pay as you go", consumer pays for resources used

### Benefits of Cloud Computing

- **Agility:** Quickly spin up resources when you need them to perform any given tasks
- **Elasticity:** Scale the resources up or down to instantly grow or shrink capacity
- **Cost savings:** Allows you to trade capital expenses for variable expenses
- **Deployment:** Expand to new geographic regions and deploy in minutes

## Evolution of Cloud Computing

### High Performance Computing

- Ability to process data and perform complex calculations at high speeds for short amount of time
- Usually clusters of MPPs
- Practice of aggregating computing power in such a way that it delivers much higher performance than normal
- Interest of small-to-medium sized companies
- Usually clusters of computers
- Expected to support for a shot amount of time

### High Throughput Computing

- Ability to handle large amounts of data for a prolonged period of time
- Peer-to-Peer network

### Distributed Computing

- Multiple Autonomous computers each having its own private memory, communicating through a network
- Information is passed through message passing
- Located on different networked computers that coordinate by pure HTTP, RPC-like connectors or message queues
- Independent failure of components and concurrency of components

### Clusters

- Set of loosely or tightly connected computers that work together so that they can be seen as a single system
- Clusters have each node set to perform the same task, controlled and scheduled by the software

### Parallel Computing

- All processors are tightly coupled with centralised memory or loosely coupled with distributed memory
- Inter-processor communication is accomplished through message passing or shared memory
- **Primary Goal:** Increase available computation power for faster application processing and problem solving
- Several processes simultaneously execute multiple, smaller calculations broken down from an overall larger complex problem
- Smaller calculations communicate through shared memory and results of each can be combined as part of overall program

#### Bit Level Parallelism

- Form of parallel computing which is based on increasing processor word size
- Increasing word size, reduces the number of instructions the processor must execute

#### Instruction Level Parallelism

- Instructions can be reordered and grouped which are later executed concurrently without affecting the result of the program
- Pipelining is a method of doing this, but we must exploit it even more to achieve parallel execution of the instructions in the stream

#### Data Parallelism

- Concurrent execution of same task on multiple computing cores

#### Task Parallelism

- Concurrent execution of different tasks on multiple cores

### Parallel Computing Terminologies

#### Multi-core Computing:

- Computer processor integrated circuit with two or more separate processing cores
- Each core executes program instructions in parallel

#### Symmetric multiprocessing:

- Multiprocessor computer hardware and software in which two or more independent, homogeneous, processors are controlled by a single Operating System
- Treats all processors equally, and is connected to a single, shared main memory with full access to all common resources and devices
- Each processor has private cache memory
- May be connected using on-chip mesh networks and can work any task

#### Massively Parallel Computing:

- Refers to the use of numerous computers/processors to simultaneously execute a set of computations in parallel
- Grouping several processors in a tightly structured, centralised computer cluster
- Another approach is grid computing, in which many distributed computers work together and communicate via internet to solve a problem

### Parallel Computing Solutions and Techniques

#### Application Checkpointing:

- Technique that provides fault tolerance for computing systems by recording all of the application's current variable states
- Enables the application to restore and restart from that point in the instance of failure

#### Automatic Parallelization:

- Conversion of sequential code into multi-threaded code in order to use multiple processors

#### Parallel Programming Languages:

- Typically classified as either distributed memory or shared memory
- Distributed memory programming languages uses message passing, shared memory programming languages communicates by manipulating shared memory variables

## Grid Computing

- "Coordinated Resource sharing and problem solving in dynamic cirtual organizations"
- Use of widely distributed computer resources to reach a common goal
- Can be thought of as a distributed system with non-interactive workloads that involve many files
- Grid computers have each node set to perform a different task
- Tend to be more heterogeneous and geographically dispersed
- Establishing trust and security models between resources pooled is of higher importance now
- Resource sharing agreements need to be formed among a set of participating parties

### Contrasts of Grid and Cloud Computing

- Enable computing to be delivered as a utility
- Meant to be used by users who gain access without knowing where the resource is located
- Initial technological focus of grid computing was to limit enabling shared use of resources with common protocols for access
- Uses concept of Virtual Organization, which is a dynamic collection of individulas from multiple administrative domains
- Used to enable flexible, coordinated, secure resource sharing among participating entities
- VO forms a basic unit for enabling access to shared resources
- Enables sharing of resource between parties who may not have any trust earlier

### Benefits

- Exploit underutilized resources
- Resource Load Balancing
- Virtualize resources across and enterprise
- Data, Compute Grids
- Enable collaboration for virtual orgs

- **_Computational Grid:_** It is a hardware and software infrastructure that provides dependable, consistent, pervasive and inexpensive access to high end computational capabilities
- **_Data Grid:_** Storage component of a grid computing system that deals with controlled sharing and management of large amounts of distributed data

## IaaS

- Infrastructure as a Service

### In this, you manage the following:

- Applications
- Data
- Runtime
- Middleware
- OS

### Others Manage

- Virtualisation
- Servers
- Storage
- Networking

### Advantages

- Flexible
- Control
- Pay-as-you-Go
- Speed
- Availability
- Scale
- Latency and Performance

### When to use

- Startups and small companies avoid spending money on hardware
- Larger companies want to use only what they consume
- Companies experiencing rapid growth
- Website Hosting
- Storage Backup and recovery
- High Performance Computing
- Big Data Analysis

### Limitations

- Security
- Multi-tenant Security
- Internal resources and training

## PaaS

- Includes not only abstracted infra(servers, storage, and network), but you also get middleware, development tools and Business Intelligence Services, DBMS etc.
- Designed to support Cloud Appl across the complete lifecycle

### Limitaitons

- Lack of Control
- Vendor Lockin
- Runtime Issues
- Framework versions might not be optimal with PaaS
- Data Security
- Integrations
- Customization of legacy Systems

### You Manage

- Applications
- Data

### Others Manage

- Runtime
- Middleware
- Operating System
- Virtualisation
- Services
- Storage
- Networking

## Distributed Computing

### Clusters

- Cluster is a low-latency, high-bandwidth interconnected network of standalone computers which work cooperatively as a single integrated computing resource
- All nodes in a cluster are set to perform the same task with resource being managed by their own OS
- Supports scaling by increasing the number of nodes in the cluster
- Cluster is connected to internet by a VPN

### Architectural Models

#### System Architecture

- How the components are placed across multiple machines
- How responsibilities are distributed across system components
- Ex: P2P and Client-Server Model

##### Peer-to-Peer

- Every node acts as both a client and as a server
- Peers act autonomously, join and leave the network whenever they want to
- No Master-Slave relation
- Self-organizing nodes
- Most general and flexible model, but securing it is a problem

##### Client-Server Model

- Set of machines called the "Servers" offer services to other set of machines called "Clients"
- Client asks Server for a service
- Distributes the functionality across different machines

#### Software Architecture

- Logical organization of software components and their interactions
- Ex: Three Tier Architecture

##### Three Tier Architecture

- Move client intelligence to a middle tier so that stateless clients can be used
- Simplifies deployment
- Most web apps are Three Tier

### Interaction Models

- How do we handle time?
- Are there limits on process execution?
- Ex: Synchronous and Asynchronous

#### Synchronous

- Shared clock
- Known upper and lower bounds on execution time
- Ordered Message delivery
- Lock step execution
- Not very practical
- Needs a global physical time
- Needs predictability in timing
- Possible and safe to use timeouts in order to detect failures

#### Asynchronous

- Clock may not be accurate, and can be out of sync
- No bound on machine or process execution time
- No constraints on time and order
- Each computer processes individually
- Most suitable for real life scenarios
- Cannot use timeouts for diagnosis
- Mechanisms like queues for async communication

### Fault Models

- What kind of faults can occur?
- Ex: Omission, Arbitrary, Timing Faults
- A system is said to fail when it cannot meet promises
- Failure occurs when there is an error in the system
- Cause of an error is called as fault
- Needed in order to build systems with predictable behaviour in case of faults

#### Transient Faults

- Appears once, then vanishes

#### Intermittent Faults

- Occurs and Vanishes with no real pattern
- Is the worst kind of fault

#### Permanent Faults

- Once occured, the only the replacement or the repair of the faulty component will allow the Distributed System to function normally

|                                  Types of Failure                                  |                                                                          Description                                                                          |
| :--------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                                   Crash Failure                                    |                                                       A server halts, but working correctly until halt                                                        |
|     Omission Failure <ul><li>Receive Omission</li><li>Send Omission</li></ul>      | A server fails to respond to incoming requests <ul><li>A server fails to receive incoming messages</li><li>A server fails to send outgoing messages</li></ul> |
|                                   Timing Failure                                   |                                                  A server's response is outside the specified time interval                                                   |
| Response failure <ul><li>Value Failure</li> <li>State Transition Failure</li></ul> |     The server's response is incorrect <ul><li>The value of the response is wrong</li><li>The server deviates from the correct flow of control</li></ul>      |
|                                 Arbitrary Failure                                  |                                                  A server may produce arbitrary responses at arbitrary times                                                  |

## Cloud Architecture

- Refers to the way in which tech components which makeup the cloud environment are engineered to leverage the power of cloud resources to solve business problems
- Defines the components and the relationships between them

### Frontend

- Client Side interfaces and applications that are required to access the cloud platforms
- Ex: Web Clients like Firefox, Thin and Fat Clients, Tablets and Mobile Devices

### Backend

- Part of the cloud architecture that is managed by the Service Provider
- Manages all the resources that are required to provide cloud services

#### Application

- It's the part offered for the client application that will use the cloud
- Can either be a software or a platform

#### Service

- This is a piece of software that determines and enables the appropriate service to accessed
- Could be an IaaS, PaaS, or a SaaS

#### Runtime Cloud

- Provides the execution and runtime environment to the Virtual Machine dependent on the service model

#### Storage

- One of the most important components of cloud computing
- Provides a huge amount of storage capacity in the cloud to store and manage data

#### Infrastructure

- Includes hardware and software components such as servers, storage, network devices etc

#### Management

- Components like application, services etc need to be managed and coordinated

#### Security

- It implements security mechanisms, for secure cloud resources, systems, files and infrastructure to end-users

### Internet

- Internet connection acts as the medium or bridge between the frontend and the backend
- Establishes a communication and interaction between frontend and backend

## Service Oriented Architecture

- Defines a way to make software components reusable via service interfaces
- Utilize common communication standards
- Each service in SOA embodies the code and data integrations required to execute a complete, discrete business function

### REST

- Representational State Transfer
- Architectural style for providing a set of rules to be used for building computer systems on the web
- Helps in building a client-friendly distributed systems that are simple to understand and scale
- An API which adheres to these constraints are considered RESTful and helps getting benefits of a Client Server distributed architecture
- Employed throughout the software industry and is a widely accepted set of guidelines for creating stateless, reliable web APIs
- Loosely based on HTTP methods to access resources
- Use of XML or JSON to transmit data

#### Separation of Concerns

- Client can change without having to change anything on the server, and vice-versa
- It is about how the client sends the server a message and how the server responds to the client

#### Stateless Client

- Communication between the client and server must be stateless at all times
- Each request should have all the information needed for the server to answer successfully
- Session State is kept completely on the Client

#### Cache Constraint

- Cache constraints are added to improve network efficiency
- If a response is cacheable, then the client cache is given the right to reuse that data for later similar requests

#### Uniform Interface Constraint

- Makes it generic and improves the overall visibility of interactions on how the client and server excahnge requests and responses
- Implementations are decoupled from the services they provide

#### Layered System Constraint

- Messages between a client and server can go through many intermediates
- Intermediate Components should not be able to see the next layer
- Interaction between client and server should not be affected by the middle layers

#### Operations

##### GET

- Retrieve representation of a resource
- Cannot change any of the data

##### PUT

- Create or update a resource value by replacing it
- Is dangerous, as it can completely erase existing data

##### POST

- Create or update a resource by partial update
- More secure version of PUT

##### DELETE

- Removes the resource

## Communication Mechanism

- Data flow can be happening through protocols like HTTP, AMQP or TCP
- Communication can be synchronous or asynchronous
- If the application is monolith, then a simple intra-system IPC may work

### Interaction Styles

#### Synchronous

- Also called request-response
- System expects an immediate response from the target machine
- Source sends request, then blocks until it receives a response
- There is a configured timeout, so that the source does not waste its resources

#### Asynchronous

- Client doesn't block other commands
- Supporst high rates of data flow
- Guaranteed delivery, Extensive Processing, Correlation and Time Series Analysis
- Could be of types like Publish Subscribe, Message Queues, Store and Forward

##### Advantages

- Reduced Coupling
- Multiple Subscribers
- Failure Isolation
- Load Leveling

##### Disadvantages

- Coupling with messinging infrastructure
- Latency if queue fills up
- Complexity
- Throughput is higher

## SaaS Characteristics

### Multi Tenant Architecture

- All users and applications share a single common infrastructure and code base that is maintained
- SaaS Privders can make upgrades more often with less customer risk and low cost
- Makes it easier to roll out new versions of software and features

### Easy Customization

- Each user can customize applications to fit their business processes without affecting the common infrastructure
- Customizations are unique to each company
- Most SaaS apps are preconfigured plug-and-ply where provider manages everything behind the app

### Advantages

- Lower up front costs
- Predictable ongoing costs
- Rapid deployment
- On-demand Scalability

### Disadvantages

- Security
- Latency Issue
- Dependency on the Internet
- Switching between SaaS vendors is hard

## Application Architectures

### Monolithic Architecture

- All the features are in a single codebase and use a single database
- All the components share the same resources and memory space
- Traditional way of building applications
- Single and indivisible unit
- Large, Long release cycles and have large teams

### Microservices Architecture

#### What is a Microservice?

- Small services that work together, but are independent of each other
- Components or processes of an application
- Benefits of dynamic scalability, reliability

#### Microservice Architecture

- Architectural approach of developing a single application as a small set of collaborating services
- Each service is running its own process and communicating with lightweight mechanisms
- Services are built around business capabilities and independently deployable
- Distributed and loosely coupled
- Bare minimum of centralised management of these services

#### Benefits

1. Flexibility
2. Reliability
3. Development Speed
4. Building Complex Apps
5. Dynamic Scalability
6. Continuous Deployment

#### Principles

- Single Responsibility Principle
- Modelled around Business Domain
- Isolate Failure
- Infrastructure Automation
- Deploy Independently

#### Limitations

- Building
- Testing
- Versioning
- Deployment
- Logging
- Monitoring
- Debugging
- Connectivity

|                      SOA                      |                Microservice                |
| :-------------------------------------------: | :----------------------------------------: |
|           Share as much as possible           |        Share as little as possible         |
| Importance is on business functionality reuse |   Importance is on Single Responsibility   |
|        Common governance and standards        | Focus on people, collaboration and freedom |
|         Service Bus for communication         |             Messaging systems              |
|          Multiple Message Protocols           |  Lightweight protocols like HTTP and REST  |
|         Maximizes service reusability         |           Focuses on decoupling            |

## Migration

### Migration Strategies

#### Re-host

- Lift and shift Migration strategy
- Apps are migrated to the cloud quickly
- Most suited for business needing to meet an objective quickly
- Limited scalability

#### Re-platform

- Lift, Tinker and Shift Migration strategy
- Basic architecture of application remains the same
- Some optimizations are made

#### Re-architecting

- Monolithic to SOA
- Monolithic to Microservice
- SOA to Microservice

#### Re-purchase

#### Retire

#### Retain
