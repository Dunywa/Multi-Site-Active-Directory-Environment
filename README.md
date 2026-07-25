# Multi-Site Active Directory Deployment

![Azure](https://img.shields.io/badge/Azure-Virtual%20Network-0078D4?logo=microsoftazure)
![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-0078D6?logo=windowsserver)
![Active Directory](https://img.shields.io/badge/Active%20Directory-DS-00A300)
![DNS](https://img.shields.io/badge/DNS-Server-0066CC)
![DHCP](https://img.shields.io/badge/DHCP-Server-FF8C00)
![Hyper-V](https://img.shields.io/badge/Hyper--V-Hypervisor-7030A0)
![RRAS](https://img.shields.io/badge/RRAS-Routing%20%26%20NAT-red)
![Networking](https://img.shields.io/badge/Networking-TCP%2FIP-orange)

## Project Overview

This project simulates a real-world enterprise environment consisting of a **Head Office and Branch Office connected through routed networking**.

The objective was to design, deploy, and troubleshoot a multi-site Active Directory infrastructure similar to what an MSP Level 2 Technician would support.

The environment includes:

- Multi-site Active Directory Domain Services
- DNS infrastructure
- DHCP High Availability
- Hyper-V virtualization
- Windows Server routing and NAT
- AD replication between locations
- Enterprise network segmentation
- Client workstation management
- Real-world troubleshooting scenarios

---

# Architecture Overview


This project demonstrates proficiency across Microsoft infrastructure, routing, VPN, and enterprise network design.

<img width="1306" height="1204" alt="Multisite AD Environment" src="https://github.com/user-attachments/assets/cb2bac5b-275a-4318-9e01-587ae3618c1e" />

---

## 🌐 Network Topology Diagram
|  Site                |  Domain Controller  |  LAN Subnet      | DC Server IP   | Router IP       | Description   | 
|----------------------|---------------------|------------------|----------------|---------------  |---------------|
| Headquarters (HQ)    | MVHOIT-DC1          | 10.0.1.0/24      | 10.0.100.1     | 10.0.100.254    | Main DC Site  |
|Branch Office (BO)    | MVBOIT-DC1          | 192.168.100.0/24 | 192.168.100.1  | 192.168.100.254 | Remote DC Site| 

---

# Technologies Implemented

## Networking

- Hyper-V Virtual Networking
- RRAS Routing
- NAT Configuration
- TCP/IP Subnetting
- Network Segmentation

## Active Directory

- Active Directory Domain Services
- Multi-site Domain Controllers
- DNS Integration
- Global Catalog
- AD Replication
- AD Sites and Services

## DHCP

- DHCP Server Deployment
- DHCP Scopes
- DHCP Failover
- High Availability Configuration

---

# Infrastructure Details

## Domain
mvulasmsp.local


## Domain Controllers

| Server | Location | IP Address |
|---|---|---|
| MVHOIT-DC1 | Head Office | 10.0.100.1 |
| MVBOIT-DC1 | Branch Office | 192.168.100.1 |

---

# Project Phases

## Phase 1 - Azure/Hyper-V Infrastructure

- Created virtual networking environment
- Deployed Windows Server infrastructure

## Phase 2 - Routing and NAT

- Configured RRAS
- Enabled NAT
- Connected isolated office networks

## Phase 3 - Active Directory Deployment

- Created Active Directory forest
- Deployed two domain controllers
- Configured DNS and replication

## Phase 4 - DHCP High Availability

- Configured DHCP scopes
- Implemented DHCP failover
- Tested redundancy

---

# Skills Demonstrated

✅ Active Directory Administration  
✅ DNS Troubleshooting  
✅ DHCP Configuration  
✅ Windows Server Management  
✅ Network Routing  
✅ Hyper-V Virtualization  
✅ Enterprise Troubleshooting  
✅ MSP Infrastructure Support  

---

# Planned additions:

- Group Policy Management
- File Server Deployment
- DFS Replication
- Print Server
- Microsoft Intune Integration
- Azure AD Connect
- Backup and Monitoring Solutions

---

## Author

**Mvula Dunywa**

L2 IT Support Technician Portfolio Project

