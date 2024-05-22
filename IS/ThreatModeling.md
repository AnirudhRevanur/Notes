# Threat Modeling

- Think about security issues early
- Understand your requirements better
- Don't write bugs in the code

## Framework

- What are you building? => Define the scope of the Threat Model
- What can go wrong?
- What should you do about those things that can go wrong?
- Did you do a decent job of analysis?
- **_Trust Boundary_** is a place where entities with different privileges interact

## Actions

- Mitigate
- Eliminate
- Transfer
- Accept
- Find mitigations for each threats instead of choosing other options

## Ways to find Security Issues

### Static Analysis

- Method of debugging by automatically examining source code before a program is run
- Analyzing aa set of code against a set of coding rules

### Find bugs early

- SpotBugs plugin for security audits of Java web apps and Android apps
- Detect 128 different vuln tupes
- Also works with Groovy, Scala and Kotlin

### Pen Test

- Ethical Hacking
- Simulated cyber attack on a computer system
- Performed to evaluate the security of the system

### Bug reports

- Release the program and wait for people to find bugs in the system

## Threats

### Network

- Information Gathering => Port scanning, Trace routing, broadcast requests
- Eavesdropping => Packet sniffers to steal passwords
- DoS => SYN Flood, ICMP, Malformed packets
- Spoofing => Packets with spoofed address

### Host

- Arbitrary code exec
- File disclosure
- DoS
- Unauthorized access
- Exploitation of open ports and protocols

### Application

- SQL Injection
- XSS
- Hidden field tampering
- Eavesdropping
- Session Hijack
- Identity Spoofing
- Information disclosure

## STRIDE

### Spoofing

- Authentication is violated
- Impersonating someone else

### Tampering

- Integrity is violated
- Modifying data or code

### Repudiation

- Non-repudiation is violated
- Claiming to have not perform an action

### Information Disclosure

- Confidentiality is broken
- Exposing Information to someone not authorized to see it

### Denial of Service

- Availability is violated
- Deny or degrade service to users

### Elevation of Privileges

- Authorization is violated
- Gain capabilities without proper authorizatoin
