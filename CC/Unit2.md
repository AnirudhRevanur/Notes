# Unit 2

## Virtualisation

- It is a technique of abstracting physical resources
  -Increases utilization and capability of the IT infrastructure
- Simplifies resource management by pooling and sharing resources
- Reduces downtime
- Improves performance on IT infrastructure

### Compute Virtualisation

- Also called as Server Virtualisation
- Framework of dividing the resources into mutliple execution environments
- Presenting and partitioning computing resources in a logical way

## VM

- Technique of abstracting physical resources into a logical view
- Increases utilization and capability
- Simplifies resources
- Reduces downtime
- Improves performance
- Logically identical to a Physical Machine
- One of the most prominent way in which compute resources are provisioned

## Compute Virtualisation

- Framework or methodology of dividing resources of computer into multiple execution environments

## Why VM?

- Server Consolidation
- Workload Mobility
- Dev and Test
- Business continuity management
- Support OS Diversity
- Security and Isolation
- Load Balancing
- Rapid Provisioning
- Encapsulation
- Lower Costs

## How to implement

- Hardware level virtualisation inserts VMM between real hardware and traditional OS
- VMM directly interacts with Hardware, and so it is called **Bare Metal VMM** or **Type 1 Hypervisor**
- Ex for Type 1: Xen, Windows Virtualisation
- VMM acts as a traditional OS
- Three requirements for a VMM:

  - Should provide env for programs which is identical to the original machine
  - Programs running in this env should show, at worst, minor reduction in performance
  - VMM should be in complete control of system resources

- When a VMM is implemented on top of OS, then it is called **Hosted VMM** or **Type 2 Hypervisor**
- Example for Type 2: VMWare or Oracle VirtualBox
- VMM can also be part of OS too
- Ex: KVM for Linux
- VMM implementation when supporting both bare-metal and as a hosted app is called Hybrid VMM
- Ex: MS Virtual Server

|      Criteria       |                        Type 1                        |                              Type 2                              |
| :-----------------: | :--------------------------------------------------: | :--------------------------------------------------------------: |
|     Definition      | Runs directly on the system with VMs running on them |                       Runs on a normal OS                        |
|   Virtualisation    |                       Hardware                       |                                OS                                |
|      Operation      |         Guest OS and apps on the hypervisor          |                Runs as an application on Host OS                 |
|     Scalability     |                  Better Scalability                  |              Not much because of underlying Host OS              |
|        Setup        |         Simple, as long as you have hardware         |              Very simple as you already have an OS               |
| System Independence |            Has direct access to hardware             |              Not allowed to directly touch hardware              |
|        Speed        |                         Fast                         |               Slow because of system's dependency                |
|     Performance     |      High performance, as there is no overhead       |             Reduced performance because of overhead              |
|      Security       |                     More secure                      | Less secure, as any problem in host OS can affect the Hypervisor |

## Other types of Virtualisation

### Paravirtualization

- Presents a software interface to VMs that is similar, but not identical to the actual hardware
- OS to be explicitly ported to be able to run on top of VMM/Hypervisor
- VMM provides APIs for guest OS
- Useful if the source code of the OS if modifiable
- Handles priviliged and sensitive instructions at compile time of guest OS
- The guest OS running in a guest domain may run at Ring 1 instead of Ring 0
- Priviliged instructions are implemented by hypercalls to the hypervisor
- After replacing instructions with hypercalls, the Guest OS emulates the behaviour of the original OS
- Compatability and portability are a problem
- Cost is very high
- Performance varies due to varying workload
- It is more easy and practical when compared to Full Virtualisation

### Full Virtualisation

- Provides complete simulation of the underlying hardware
- OS can run without modification
- Intercepts and emulates priviliged and sensitive instructions at runtime

## Trap and Emulate

- User mode is Ring 3
- Priviliged Mode is Ring 0
- Attempt to execute Priviliged instructions in Ring 3 leads to a trap
- Run the VM in User Mode, but the hypervisor in Priviliged mode
- VMM runs in Ring 0 and Guest OS will be running in Ring 1
- If Guest Application has to handle a special instruction, it traps to VMM
- VMM doesn't know how to trap
- VMM jumps to guest OS trap handler
- Trap is handled normally

### Problems

- Performance Overhead
- Trap costs may be high
- Not all architectures support it
- x86 was not easily virtualisable
- Some x86 instructions which change hardware state can run in both priviliged and unpriviliged states
- Guest OS might realise that it is running at lower privilige level
- Memory Protection is a challenge as physical memory is a shared resource

## Binary Translation Technique

- One specific approach to implementing full virtualisation that does not require hardware virtualisation
- Involves the hypervisor examining the virtual guest code for unsafe, but unpriviliged instructions, then converting this into safe instructions
- Supports virtualisation of x86 architecture

## Containers

- Linux Containersis an OS level virtualisation method for running multiple isolated containers, which can run multiple workloads, on a control host running a single Linux OS
- Provides a virtual environment that has its own processes and network space and does not create a full-fledged virtual machine
- Containers use a lightweight mechanism unlike VMs making isolation easier

### Characteristics

- Containers sit on top of a physical server and its host OS
- Containers are lightweight as they are only MB in size and take a few seconds to start

|                  VM                   |                  Container                  |
| :-----------------------------------: | :-----------------------------------------: |
|   Hardware level process isolation    |         OS level process isolation          |
|       Each VM has a separate OS       |         Containers can share an OS          |
|           Boots in Minutes            |              Boots in seconds               |
|            Few GBs of size            |         Containers are lightweight          |
|    Ready made VMs are hard to find    |    Pre built containers are easy to find    |
| VMs can be moved to a new host easily | Containers have to be destroyed and rebuilt |
|    Creating a VM takes a long time    |    Containers can be created in seconds     |

### Docker

- User a client-server architecture
- Docker client talks to the Docker daemon
- Dockerd does the heavy lifting of building running and distributing docker containers
- Client and Daemon can be on the same machine or client can access remote daemon
- Communicate suing REST API over UNIX sockets
- Docker compose is another Docker client
- Docker client is the primary way for users to interact with Docker
- "docker" command uses the docker API
- Docker client can communicate with more than one daemon
- Docker Host has the Dockerd running and can host or connect to a Docker registry which stores Docker images
- Docker Objects include things like:
  - Images
  - Containers
  - Networks
  - Volumes
  - Plugins
  - Other objects which are created while using docker
- Docker means having two programs in the user space at all times
- Docker engine => Should always be running
- Docker CLI => How users interact to start/stop/install software
- Docker uses Namespaces

#### Namespaces

- PID Namespace
  - Process isolation through identifiers
- UTS Namespace
  - Multiple hostnames on a singly physical host
- MNT Namespace
  - Isolates a set of mount points such that processes in different namespaces cannot see each other
  - Almost like chroot
- IPC Namespace
  - Provides isolation to container process comms over shared memory and having an ability to invite other processes to read from shared memory
- NET Namespace
  - Allows process inside each namespace to instance to have access to a new IP address along with full range of porst
  - Change in network access and structure
- USR Namespace
  - Provides username
  - UID mapping isolating changes in names from metadata within a container
- chroot
  - Controls the location of the filesystem root
- cgroups
  - Controlling and accounting resources
  - New cgroup with a root directory to isolate resources and not allow navigation
- CAP Drop
- Security Modules

#### Limit Resources

- Memory
- CPU
- Block I/O
- Devices
- Network
- When a process creates a child, the child stays in the same cgroup

#### Container Filesystem

- Programs running in container know nothing about image layers
- Inside the container, the filesystem operates as though it's on a physical machine
- Union Filesystem (UFS)
- Is part of a critical set of tools that combine to create isolation
- UnionFS permits the layering of file systems
- Files from separate branches can be overlaid
- Forms a single coherent FS
- May be read-only or read-write

## DevOps

- It is a set of practices that combines software development and IT operations
- It aims to shorten the development life cycle and increase an organizational ability to deliver applications and services
- Complementary with Agile software development
- Automates the process between software dev and IT teams, in order they can build, test and release software faster and more reliable
- Plan, Build, Deploy, Operate Cycle
- Docker, Kubernetes and Git are some of the most used DevOps tools

### Advantages

- Faster time to market
- Quality of Code/Release
- Frequent integratoin
- Deploy often
- Automated

### Principles

1. Every build is a potential release
2. Eliminate manual bottlenecks
3. Automate wherever possible
4. Have automated tests that can be trusted

## Kubernetes

- Containers offer a way to package code, runtime, system tools etc together
- Shipment is lightweight, standalone executable
- Application will be same no matter where it is run
- Container orchestration automates the deployment, management, scaling and networking of containers
- Managing the lifecycle of containers with orchestration supports DevOps teams to integrate into CI/CD workflows
- Kubernetes is the most pervasive container orchestration platform
- Open source container management tool
- Container deployment, scaling & descaling of containers and load balancing
- Manage complex application deployments quickly in a predictable and reliable manner
- Other orchestrators include:
  - Docker Swarm
  - Google Container Engine
  - Amazon ECS

### Pod

- Single or group of containers that share storage and network within a Kubernetes configuration
- There are groups of containers which are running microservices
- Pods share storage, namespaces, cgroups, IP, port address and can communicate with each other over localhost networking
- Not intended to live long
- Created, destroyed and re-created on demand
- Not made to self heal, if a pod fails, then delete it

### Advantages

- Horizontal Scaling
- Automated rollouts and rollbacks
- Service discovery and load balancing
- Storage Orchestration
- Secret and config management
- Self-healing
- Batch execution
- Automatic binpacking
