# DNS

- Mainly designed to resolve a host name query to an IP address
- Users need a name, but internet needs IP address
- DNS is phonebook of the internet
- Anti-spam, Load Sharing and Privacy

## Namespace

- It is a structure of the DNS database
- Represented in the form of an inverted tree
- Each node in the tree has a label and the root node has a null label

### Name Servers

- Responsible for storing information about the namespace in the form of zones
- Multiple name servers and ones that load a complete zone are Authoritative Servers

#### Authoritative Name Servers

- Responses to DNS Queries
- Responsible for delivering original and definitive answers to each DNS Query
- **_Master Server:_** It stores the original copies of all records. Only Admin can make changes
- **_Slave Server:_** Keeps a copy of master server files. Used to share DNS server load and improve DNS zone availability

#### Caching Name Server

- Name Service closer to the user and improves overall name lookup performance
- Provides a comprehensive mechanism for providing private namespaces to local users
- Allowing users to obtain all names mapping from local caching

### Resolver

- Name resolver is required to find out the name and IP Address of the name servers for the root zone
- Root name servers store information about top-level zones and direct servers in whom to contact for all TLDs
- Resolver basically breaks the name into labels from right to left
- TLD is queried using a root server to obtain the designated Authoritative Server

## DNS Records

- Mapping files that associate DNS Server and IP Addersses each domain is associated with

### MX Records

- Identify servers that can exchange mails
- Priority is always associated with each of the records
- User can choose the primary and backup mail servers

### TXT Records

- Deliver a method to expand the information received from DNS
- Stores information about the SPF that can identify the authorized server to send email on your behalf

### CNAME

- Essentially domain and subdomain text aliases to bind traffic
- SFTP server is on the same system as Main server
- Important role when server is not under organization control

### PTR Records

- These provide the reverse binding from addresses to names
- Should exactly match forward maps

## Attacks

### DNS Cache Poisoning

- Attacker can take advantage of cached DNS Records and perform a spoofing by injecting a forged DNS Entry
- All users using that forged DNS entry until it expires

### Compromising a DNS Server

- DNS Server is heart of entire DNS infrastructure
- Attacker can use several attack vectors to compromise a DNS Server
- Provide IP Address of a malicious web server against each legitimate DNS query

### Man in the Middle

- Threat actor keeps listening to conversations between the clients and DNS Server
- After gathering information and sequence parameters, it starts spoofing the client

## Blockchain based Solutions

### DNSChain

- Blockchain based solution for DNS Software that replaces X.509 Public Key Infrastructure
- Delivers MITM Proofs of Authentication
- Internet users to set a public DNSChain server of DNS queries and access that server ending in .bit

### X.509 PKI Replacement

- Standard framework that defines the format of PKI to identify users and entities over the internet

### MITM Proof DNS

- Public key Pinning technique to get rid of MITM attack problem
- Specifies two pin-sha256 values

## DDoS

1. Reconnaissance: Identify target device and start searching for vulns in it
2. Weaponization: Attacker uses a remote took kit and malware such as a virus or worm
3. Delivery: Threat actor inject the cyberweapons to the victim through stuff like phishing emails, drive by download etc
4. Exploitation: Malware code is used to trigger the attack
5. Installation: Malware is not installed on the victim machine
6. Command and Control: Allows remote threat actor to gain access to victim machine
