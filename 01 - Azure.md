# Phase 1 - Azure Infrastructure

Created Resource Groups, Virtual Networks, and Azure virtual machines.

## Overview

The Azure environment provides the foundational infrastructure required to host the VMware lab.

## Objectives

- Create a dedicated Resource Group
- Create a Virtual Network
- Configure subnet segmentation
- Deploy management servers

## Components Deployed

### Resource Group

RG-VMWARE-LAB

<img width="955" height="567" alt="RG-VMWARE-LAB" src="https://github.com/user-attachments/assets/00bb157e-ac0d-4df8-a9db-0a312b2af580" />

### Virtual Network

VNET-VMWARE-LAB

<img width="951" height="601" alt="VNET-VMWARE-LAB" src="https://github.com/user-attachments/assets/78e94649-3ab0-4014-a771-674a4c73578e" />


#### Address Space

```
10.0.0.0/16
```

---

### Subnets

<img width="954" height="496" alt="Subnets" src="https://github.com/user-attachments/assets/979edbb1-1608-48d8-ab43-320e58f39cec" />

***Management Subnet***

```
10.0.1.0/24
```

Purpose:

- DC01

- Jump01

---

***Server Subnet***

```
10.0.2.0/24
```

Purpose:

- Storage01
- Workload Servers

---

***VMware Subnet***

```
10.0.3.0/24
```

Purpose:

- ESXI01
- ESXI02
- vCenter01

- 
###  Azure Virtual Machines
Deployed JumpBox01 PC in Management Subnet

Purpose:
- To manage the environment

<img width="1236" height="680" alt="JumpBox01" src="https://github.com/user-attachments/assets/66aa371c-1e1a-4e63-b9fd-886b7f6d0ccb" />

Deployed DC01 Server in the Management Subnets

Purpose:
- To install Active Directory to centrally manage workloads

<img width="1366" height="496" alt="DC01" src="https://github.com/user-attachments/assets/bd964cf3-d8e2-4c04-bfa6-5d2c4e9b3db8" />

## Outcome

Successfully deployed the Azure infrastructure required to support the VMware environment and future workload expansion.
