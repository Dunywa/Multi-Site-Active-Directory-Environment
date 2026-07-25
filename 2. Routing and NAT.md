# Phase 2 - Network Address Translation (NAT) Configuration

Configured Network Address Translation (NAT) on the Azure Windows Server 2022 Hyper-V host using Routing and Remote Access Service (RRAS).

## Overview

The purpose of this phase was to enable the Azure Hyper-V host to function as a router between isolated internal networks.

NAT allows internal Hyper-V networks to communicate through the Azure network interface while maintaining network separation between environments.

---

## Objectives

- Configure NAT using RRAS
- Define public and private network interfaces
- Enable routing between internal networks
- Provide connectivity between Head Office and Branch Office networks

---

## NAT Configuration

### NAT Router

- MVITHOST1

### Operating System

- Windows Server 2022

---

## Network Interfaces

The following interfaces were configured for NAT:

| Interface | Type | IP Address | Purpose |
| --- | --- | --- | --- |
| Ethernet | Public Interface | 10.0.0.4 | Azure Internet Connectivity |
| vEthernet (MVHOIT-SW1) | Private Interface | 10.0.100.254 | Head Office Network |
| vEthernet (MVBOIT-SW1) | Private Interface | 192.168.100.254 | Branch Office Network |

---

## NAT Rules

### Public Interface

Ethernet


Configuration:

- Public Interface Connected to the Internet

- NAT Enabled


---

### Private Interfaces

- Head Office: vEthernet (MVHOIT-SW1) - 10.0.100.0/24

- Branch Office: vEthernet (MVBOIT-SW1) - 192.168.100.0/24


---

## Validation

The NAT configuration was validated using:

### Network Configuration Check

ipconfig /all


Verified:

- Correct IP addressing
- Correct network adapters
- Gateway configuration

---

### Routing Verification


route print


Verified:

- Internal network routes
- Azure default route
- Network communication paths

---

### Connectivity Testing

Tested communication between internal networks:

ping 10.0.100.x

ping 192.168.100.x


Validated:

- NAT functionality
- Inter-network communication
- Router connectivity

---

## Screenshots

### RRAS NAT Server Status


<img width="1401" height="702" alt="NAT Server Status" src="https://github.com/user-attachments/assets/fc0f18d3-9889-40c6-8b26-966571126748" />


---

### NAT Interfaces


<img width="1119" height="569" alt="NAT Interfaces" src="https://github.com/user-attachments/assets/fd70ebbb-2c73-4d93-b79d-797c07c90cda" />


---

## Outcome

Successfully configured NAT on the Azure Hyper-V host using RRAS.

The server now provides routing capabilities between isolated Hyper-V networks, allowing future deployment of:

- Multi-site Active Directory
- DNS replication
- DHCP failover
- Branch office connectivity





