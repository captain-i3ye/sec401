# Defensible Network Architecture
---
# Network Designs
### Conceptual Design
	- high level design
	- includes core components
	- overall purpose of network
	- major technology system, external systems for data flow, general functionality, high level system behaviour.
	- black box diagramming - single component, general role.

### Logical Design
	- detailed, inludes major components + their relationships
	- detailed data flows & connections mapped
	- for developers and security architects
	- included {services, application names, relevant dev info}
	- should not be included {server names / addresses}

### Physical Design
	- all major systems within pre-defined server areas.
	- last design before implementation.
	- details {OS, patches, versions, etc.}
	- physical constraints+limitations identfied - server components/data flows/connections.

### Communication Flow
	- Begins with logical architecture
	- Shows how data flows in and out of network
	- Maps every communication flow, exchange + control messages
	- Understand exposure and visibility of key components
	- Foundation of threat mapping

### Valuable Data
	- Begins with logical architecture
	- Where does valuable data reside?
	- Critical Intellectual Property:
		- What is the critical information?
		- Where is it stored?
		- Who has access?
		- Who should have access?
	
### Note: 
	- CIA: Confidentiality, Integrity & Availability
	- Remember: You are only as strong as your weakest link

# Attack against network devices

### Threat Enumeration
	- Process of tracking and understanding critical threats to the system or network.
	- List all possible threat agents
	- List the attack methods
	- List the System-level Objectives {(Access Data, Unintended Commands: SQLi, LDAPi), (browser script, session hijack: XSS), etc}

### Threat Agents
	- Individual, Organization or group capable and motivated to carry out an attack of one sort or another.
	- Different groups, different systems, different ways, different reasons.

## _Attacks against Router_

### Denial of Service (DoS):
	- router flooded with requests
	- large amount of ICMP packets sent, affecting availability

### Distributed Denial of Service (DDoS):
	- uses zombies hosts to achieve DoS

### Packet Sniffing:
	- capture data using program that monitors network

### Packet Misrouting:
	- malicious code injected in the router to mistreat packets
	- router unable - carry out - own routing process
	- hard to find and fix: loops, DoS, etc on network

### SYN Flooding:
	- TCP synchronization packet - for malicious reasons
	- server unable to establish connection, address unreachable
	- kinda like DoS.

### TCP Reset Attack:
	- attacker terminates TCP connection with spoofed packets
	- using RST(reset) bit
	- attacker sniffs TCP connection to get Source/Dest. IP, port numbers and specifically sequence number.
	- fake TCP packet created with same info but a reset(RST) bit is added.
	- data flow disrupted till new connection established.

### Routing Table Poisoning
	-Routing Table:
		- how router moves packets in network
		- created by exchanging info b/w routers
	- RTP - unwanted edits to routing table
	- broadcasted by routers

## _Attacks against Switches_

### CDP Manipulation
	- Cisco Discovery Packets
	- enabled by default on Cisco Switches
	- transmitted in clear
	- contains info about network devices
	- solution: disable CDP on non-mgmt devices

### MAC Flooding
	- Content Addressable Memory Table filled with MAC addresses.
	- Switch storage capacity overwhelmed.
	- switch acts as HUB.
	- sniff traffic along network segment.

### DHCP Spoofing
	- MITM
	- attacker-listens-DHCP	requests
	- responds-attacker IP-default gateway

### STP attacks
	- Spanning Tree Protocol
		- port altering
		- block/forward conditions to linked segments
	- Different STP attacks
	- RAW config of BPDU(Bridge Protocol Data Unit) packets
	- transitted in LAN to detect loops in Net. Topologies

### VLAN Spoofing
	- 802.1Q tags used
	- attacker- send- packets from one VLAN to another w/o passing through router

### Telnet Attack
	- Actually, distributed SYN attack.
	- Windows OS - accessible telnet executable - set up TCP session
	- conditions created for DoS attacks

---
---
# Network Topologies and Design
---

#### Physical Topologies
	- layout of how systems are connected

#### Logical topologies
	- process, protocols follow to send data

### Ethernet
	- most popular media access control protocol used in LANs
	- uses CSMA/CD
		- checks if network/wire is busy.
		- rest if busy, send frames if not. Avoid collisions

## Approaches to Network Design

### Segmenetation
	- Network Segmentation:
		- splitting a computer network from rest of the network using hub, repeater, switch, router, etc.
		- Firewalls and VLANs are used to partition as well
	- Implement Controls at Multiple Levels:
		- more segmentation layers (structured), more security.
		- common sense approach + easily manageable
	- Least Privilege Rule: Only access to needed ones.
	- Segmentation based on Security Requirements: where to store what type of data
	- Whitelisting instead of Blacklisting: narrowing down the authenticated users.
### Protected Enclave
	- segment - internal network - defined by some set of rules

### Software Defined Network (SDN)
	- uses software-based controllers or APIs to communicate with hardware and direct traffic on a network.
	- segment networks virtually
	- controls routing through centralized server
	- Control: speed + flexibility increased
	- Customizable Network Structure: prioritization, data flow optimiztion.
	- Micro Segmentation

### Prioritization protection
	- separation between endpoints/desktops and servers that hold critical data.
	- separation between desktops to limit reconniassance and worm propagation

### Data/Net Flow Analysis
	- monitor types of devices
	- nerwork visibility at a specific location
	- relies on algorithms and behaviours rather than signature.
	- helps to detect unsignatured attacks.

### Network Sections
	- Public: Internet (cannot be trusted)
	- Semi-Public (DMZ): Company contributions.. Web, Email, DNS servers - reachable from internet and can send to the internet.
		- cannot contain sensitive information.
	- Middleware: Separate DMZ from Private network. Contains Proxy Servers: filters & block unauthorized access.
	- Private: Conmpany's internal system. No sharing. Most protected.
		- can be accessed only through Middleware.

#### Where to place Firewall
	- At intersections of paths.
	- Private <-- --> Internet
	- Private <-- --> Semi-Public
	- Semi-Public <-- --> Internet

#### Firewall assists
	- Border Router:
		- filters network traffic
		- ingoing and outgoing
		- uses ACL - Access Control List

### Final Design
	- it is based upon the rules and advices above
---
---
---