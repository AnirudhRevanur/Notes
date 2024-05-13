# Unit 3

## Storage

- Different types of storages

### File Storage

- Data is organized as a single piece of information in a folder
- Data stored in files is organized and retrieved using a limited amount of metadata
- NAS and DAS use this
- Scaling is scale out as there is a limit to add to the system

### Block Storage

- Chunks data into arbitrarily organized, evenly sized volumes
- Data is chopped into blocks, and each block has unique identifier
- Usually a SAN environment
- Efficient and reliable way to store data
- Works well with enterpeises
- Expenisve and has limited capability to handle metada

### Object Storage

- Flat structure with data broken into discrete units called objects and these are kept in single repository
- Each is a self-contained repository that owns the data, a unique identifier and metadata
- Metadata is important and includes details at two levels
- To retrieve, the storgae uses the metadata and identifiers, which distributes the load better

### RAID

- Redundant Array of Independent Disks
- Data storage virtualisation
- Combines multiple physical disk drives into one or more logical units

### Magnetic Disk

1. Dsik controller positions head assembly at cylinder containing the track => Seek time
2. Controller waits while first sector moves under the head => Rotational Latency
3. All sectors and gaps between them pass while the controller reads/writes => Transfer time

## Cloud Storage

- Users see a rich interface, but underlying tech is very simple
- Translation is done by web service
- Ability to an application running elsewhere to save data and files in an off-site location
- Storage virtualisation helps in supporting access, utilization, availability and other features
- Storage systems having capability of virtual storage pool and multi tenancy
-
