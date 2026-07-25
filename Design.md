# Phase 1 - Design

Designed the architecture, networking, storage, VMware, and Active Directory components.

## Overview

This project was designed to simulate a small-to-medium enterprise VMware environment hosted within Microsoft Azure. The objective was to gain hands-on experience with virtualization, identity services, storage, networking, high availability, and infrastructure troubleshooting in a controlled lab environment.

The design emphasizes enterprise best practices by separating management, storage, virtualization, and workload services into dedicated components.

---

# Objectives

## Primary Objectives

- Build a VMware environment in Microsoft Azure
- Deploy centralized identity services
- Implement shared storage
- Configure VMware High Availability (HA)
- Configure Distributed Resource Scheduler (DRS)
- Deploy production-style workloads
- Simulate real-world infrastructure incidents
- Document deployment and troubleshooting processes

## Learning Objectives

- VMware Administration
- Azure Infrastructure
- Active Directory Administration
- DNS Administration
- Storage Management
- Virtual Networking
- Root Cause Analysis
- Incident Management

---

# Solution Architecture

## High-Level Architecture

```
Azure Subscription
│
├── Resource Group
│   └── RG-VMWARE-LAB
│
├── Virtual Network
│   └── VNET-VMWARE-LAB
│
├── Management Services
│   ├── Jump01
│   ├── DC01

│
├── Storage Services
│   └── Storage01
│
├── VMware Infrastructure
│   ├── ESXI01
│   └── ESXI02
│
└── Workload Virtual Machines
    |── vCenter01
    ├── APP01
    ├── SQL01
    ├── WEB01
    ├── FILE01
    └── TEST01
```
## Architecture Diagram

<img width="1536" height="1024" alt="Architecture Diagram 2" src="https://github.com/user-attachments/assets/8df56d03-57e6-468c-a35d-a1fcf23f1160" />

---

# Infrastructure Components

## Azure Resources

| Component | Purpose |
| --- | --- |
| Resource Group | Logical container for lab resources |
| Virtual Network | Network connectivity |
| Subnets | Network segmentation |
| Network Security Groups | Traffic control |

---

## Identity Services

### DC01

Purpose:

- Active Directory Domain Services
- DNS Services
- Authentication Services

Domain:

```
corp.local
```

---

## Storage Services

### Storage01

Purpose:

- iSCSI Target Server
- Shared VMware Storage

Datastores:

```
DS-PROD01
DS-PROD02
```

---

## VMware Infrastructure

### ESXI01

Purpose:

- VMware Hypervisor Host

### ESXI02

Purpose:

- VMware Hypervisor Host

### vCenter01

Purpose:

- Centralized VMware Management
- Cluster Management
- Performance Monitoring
- HA and DRS Administration

---

# Network Design

## Address Space

```
10.0.0.0/16
```

---

## Subnets

### Management Subnet

```
10.0.1.0/24
```

Purpose:

- DC01
- vCenter01
- Jump01

---

### Server Subnet

```
10.0.2.0/24
```

Purpose:

- Storage01
- Workload Servers

---

### VMware Subnet

```
10.0.3.0/24
```

Purpose:

- ESXI01
- ESXI02

---

# VMware Cluster Design

## Datacenter

```
LAB-DC
```

## Cluster

```
LAB-CLUSTER
```

Enabled Features:

- High Availability (HA)
- Distributed Resource Scheduler (DRS)

---

# Workload Design

| Server | Function |
| --- | --- |
| vCenter01 | vCenter Server Appliance |
| APP01 | Application Server |
| SQL01 | Database Server |
| WEB01 | Web Server |
| FILE01 | File Server |
| TEST01 | Testing Environment |

---

# Enterprise Incident Scenarios

The environment was intentionally designed to support realistic infrastructure troubleshooting.

## Planned Incident Simulations

### Incident 01

CPU Contention

### Incident 02

Datastore Capacity Exhaustion

### Incident 03

Snapshot Consolidation Failure

### Incident 04

VLAN Misconfiguration

### Incident 05

Cluster Resource Imbalance

### Incident 06

Storage Latency

---

# Risks and Considerations

| Risk | Mitigation |
| --- | --- |
| Resource Constraints | Proper Azure VM sizing |
| Storage Exhaustion | Capacity monitoring |
| Network Misconfiguration | Segmented design |
| Service Outages | HA configuration |

---

# Success Criteria

The project will be considered successful when:

- Active Directory is operational
- VMware hosts are deployed
- Shared storage is available
- vCenter is operational
- HA and DRS are functional
- Workload VMs are deployed
- Incident scenarios can be reproduced and resolved

---




# Outcome

A complete enterprise VMware-on-Azure solution was designed prior to implementation, providing a structured roadmap for deployment, operations, and troubleshooting while aligning with industry-standard infrastructure practices.
