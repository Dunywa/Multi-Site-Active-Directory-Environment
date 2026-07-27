# Phase 1 – Azure Environment Setup

## Overview

The objective of this phase was to build the cloud infrastructure that hosts the entire lab environment. Rather than deploying multiple Azure virtual machines, a single Microsoft Azure Windows Server 2022 virtual machine was provisioned and configured as the Hyper-V host. All subsequent infrastructure components, including Domain Controllers and client machines, are deployed as nested Hyper-V virtual machines within this host.

This approach reduces Azure costs while providing a flexible environment for simulating an enterprise Active Directory infrastructure.

---

## Objectives

- Create an Azure Resource Group
- Deploy a Windows Server 2022 Azure Virtual Machine
- Configure the VM as a Hyper-V host
- Prepare the environment for nested virtualization
- Provide a foundation for the remaining project phases

---

## Environment

| Component | Configuration |
|----------|---------------|
| Cloud Platform | Microsoft Azure |
| Resource Group | MULTI-SITE-RG1 |
| Operating System | Windows Server 2022 Datacenter |
| Hypervisor | Hyper-V |
| Host Name | MVITHOST1 |

---

## Architecture

```
Microsoft Azure
│
├── Resource Group
│
└── Azure VM (MVITHOST1)
      │
      └── Hyper-V
            ├── HQ Domain Controller
            ├── Branch Domain Controller
            ├── Windows Client
            └── Additional Lab Servers
```

---

## Tasks Completed

- Created an Azure Resource Group
- Deployed a Windows Server 2022 virtual machine
- Enabled nested virtualization
- Installed and configured the Hyper-V role
- Verified Hyper-V functionality
- Prepared the host for deploying virtual machines

---

## Skills Demonstrated

- Microsoft Azure
- Azure Virtual Machines
- Windows Server 2022
- Hyper-V
- Nested Virtualization
- Infrastructure Planning

---

## Screenshots

### Azure Resource Group

> *(Insert screenshot here)*

### Azure Virtual Machine

> *(Insert screenshot here)*

### Hyper-V Installed

> *(Insert screenshot here)*

---

## Outcome

A dedicated Azure-hosted Hyper-V environment was successfully deployed and prepared to host all virtual machines required for the multi-site Active Directory lab. This infrastructure serves as the foundation for the remaining phases of the project.
