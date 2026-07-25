# Phase 3 - Multi-Site Active Directory Deployment

Deployed a multi-site Active Directory environment with two domain controllers supporting Head Office and Branch Office locations.

## Overview

The purpose of this phase was to deploy centralized identity management, authentication, and DNS services across multiple locations.

The environment simulates a real-world enterprise infrastructure where branch offices maintain local domain controllers while synchronizing Active Directory data with the Head Office.

---

## Objectives

- Deploy Active Directory Domain Services (AD DS)
- Deploy two domain controllers
- Create an Active Directory forest
- Configure DNS services
- Configure Global Catalog services
- Establish Active Directory replication between sites
- Prepare the environment for enterprise services

---

# Active Directory Architecture


---

# Domain Configuration

## Forest Name

- mvulamsp.local


---

## Domain Controllers

| Server | Location | IP Address | Roles |
| --- | --- | --- | --- |
| MVHOIT-DC1 | Head Office | 10.0.100.1 | AD DS, DNS, Global Catalog |
| MVBOIT-DC1 | Branch Office | 192.168.100.1 | AD DS, DNS, Global Catalog |

---

# Head Office Domain Controller

## Server Information

- Server Name: MVHOIT-DC1

- Location: Head Office

- Operating System: Windows Server 2022


## Network Configuration

- IP Address: 10.0.100.1

- Subnet: 255.255.255.0

- Gateway: 10.0.100.254

- PRIMARY DNS: 10.0.100.1


---

## Installed Roles

The following server roles were deployed:

- Active Directory Domain Services
- DNS Server
- Global Catalog

---

# Branch Office Domain Controller

## Server Information

- Server Name: MVBOIT-DC1

- Location: Branch Office

- Operating System: Windows Server 2019


## Network Configuration

- IP Address: 192.168.100.1

- Subnet: 255.255.255.0

- Gateway: 192.168.100.254

- PRIMARY DNS: 10.0.100.1


---

## Installed Roles

The following server roles were deployed:

- Active Directory Domain Services
- DNS Server
- Global Catalog

---

# Active Directory Deployment

## Forest Creation

The Active Directory forest was created on: MVHOIT-DC1


Configuration:
- Root Domain: mvulasmsp.local


---

## Additional Domain Controller Deployment

- MVBOIT-DC1 was deployed as an additional domain controller within the existing domain.


<img width="948" height="696" alt="Screenshot 2026-07-25 234841" src="https://github.com/user-attachments/assets/360d64d0-6d52-4c33-8d6a-ff76f59820b0" />


Configuration:

- Deployment Type: Additional Domain Controller

- The server was configured to replicate Active Directory data from: MVHOIT-DC1


<img width="945" height="695" alt="Screenshot 2026-07-25 235012" src="https://github.com/user-attachments/assets/35abc879-5129-418d-89a4-f98d81fac504" />


<img width="837" height="578" alt="Screenshot 2026-07-25 235658" src="https://github.com/user-attachments/assets/de9c1d6c-d79e-4b93-913a-8c891da30c82" />




---

# DNS Configuration

DNS was deployed on both domain controllers to provide internal name resolution.

## DNS Responsibilities

- Hostname resolution
- Active Directory service discovery
- Domain authentication support
- Replication of DNS zones

---

## DNS Servers

| Server | DNS Role |
| --- | --- |
| MVHOIT-DC1 | Primary DNS|
| MVBOIT-DC1 | Primary DNS |

Both DNS zones are configured as Active Directory Integrated zones. Which makes both the primary zones.

---

# Active Directory Replication

Active Directory replication was configured between both domain controllers.

Replication allows:

- User account synchronization
- Group policy synchronization
- Computer object replication
- DNS replication

Replication path:


MVHOIT-DC1

||
||
 v

MVBOIT-DC1


---

# Validation

The following tests were completed:

## Domain Controller Health Check

Command: dcdiag


<img width="977" height="512" alt="dcdiag - MVHOITDC1" src="https://github.com/user-attachments/assets/0ca8e2a7-0aeb-499f-bb90-06bfd50d3d3a" />


<img width="975" height="509" alt="dcdiag - MVBOITDC1" src="https://github.com/user-attachments/assets/a85487eb-8e06-476b-8ac4-18024c5dd83e" />


Validated:

- AD DS services running
- DNS health
- Domain controller availability

---

## Replication Verification

Command: repadmin /replsummary


<img width="977" height="508" alt="repadmin replsummary" src="https://github.com/user-attachments/assets/64a24bbc-3e12-4d1f-9366-488544c3b591" />


Validated:

- Successful replication
- No replication errors

---

## DNS Testing

Command: nslookup mvulasmsp.com


<img width="977" height="509" alt="DNS Validation - nslookup" src="https://github.com/user-attachments/assets/7dc12162-255c-42ad-b8df-9e305ac29bff" />


Validated:

- DNS resolution
- Domain controller discovery
- Internal name resolution

---

## Domain Authentication Testing

Validated:


<img width="689" height="444" alt="Screenshot 2026-07-26 003735" src="https://github.com/user-attachments/assets/4e128dcb-a232-4b43-8b6a-7a5543301e91" />


- User login functionality
- Domain join capability
- Active Directory connectivity

---

# Screenshots

## HQ Domain Controller


<img width="1023" height="495" alt="MVHOIT-DC1" src="https://github.com/user-attachments/assets/5fdcd018-3046-4a78-90b0-22c4d6ad95b0" />


---

## Branch Domain Controller


<img width="794" height="410" alt="Screenshot 2026-07-26 002528" src="https://github.com/user-attachments/assets/ff9397f2-67ac-4faf-8b40-a4591d6f142a" />


---

## Active Directory Users and Computers


<img width="851" height="528" alt="image" src="https://github.com/user-attachments/assets/c85d7cb9-c299-49ce-8888-b16e79e95856" />


---

## DNS Manager


<img width="895" height="528" alt="DNS -MVHOITDC1" src="https://github.com/user-attachments/assets/d1d0df3f-ee82-4bc6-a0ee-0f75167f9714" />


<img width="837" height="528" alt="DNS-MVBOITDC1" src="https://github.com/user-attachments/assets/63355f3e-417e-4d48-ac63-9549346d562e" />



---

## Replication Status


<img width="977" height="508" alt="repadmin replsummary" src="https://github.com/user-attachments/assets/3bc769de-c823-47ea-be3a-6ee8764cb95f" />


---


# Outcome

Successfully deployed a multi-site Active Directory environment with redundant domain controllers.

The environment now provides:

- Centralized authentication
- DNS redundancy
- Active Directory replication
- Branch office domain services
- Enterprise identity management foundation

This infrastructure is ready for the next phases:

- DHCP High Availability
- Group Policy Deployment
- File Services
- DFS Replication
- Microsoft 365 Integration







