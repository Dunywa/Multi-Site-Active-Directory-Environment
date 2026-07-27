# Phase X – DHCP Failover (Replication)

## Overview

This phase focuses on implementing **DHCP high availability** within the multi-site Active Directory environment.

Two DHCP servers were configured on separate Domain Controllers to provide automatic lease synchronization and ensure continuous IP address allocation during server outages.

The implementation uses **DHCP Failover in Load Balance mode**, allowing both DHCP servers to actively provide IP addresses while maintaining synchronized lease information.

---

# Objectives

- Install and configure the DHCP Server role
- Create and configure DHCP scopes
- Configure DHCP Failover between Domain Controllers
- Enable automatic DHCP lease replication
- Validate DHCP availability during server failure scenarios

---

# Environment

| Component | Configuration |
|-----------|---------------|
| DHCP Server 1 | MVHOIT-DC1 |
| DHCP Server 2 | MVBOIT-DC1 |
| Domain | mvulasmsp.local |
| DHCP Mode | Load Balance |
| Replication Type | DHCP Failover |
| Platform | Hyper-V hosted on Azure VM |

---

# Architecture

```
Microsoft Azure
│
└── MVITHOST1 (Windows Server 2022)
      │
      └── Hyper-V Environment
            │
            ├── MVHOIT-DC1
            │      ├── Active Directory
            │      ├── DNS
            │      └── DHCP Server
            │
            └── MVBOIT-DC1
                   ├── Active Directory
                   ├── DNS
                   └── DHCP Server


        DHCP Failover Relationship
        ┌────────────────────────┐
        │                        │
        ▼                        ▼

   MVHOIT-DC1  ◄──────────►  MVBOIT-DC1

          DHCP Lease Replication
          Scope Synchronization
```

---

# Implementation

## 1. Install DHCP Server Role

The DHCP Server role was installed on both Domain Controllers.

### Installed Role:

```
DHCP Server
```

### Verification:

```
Server Manager → Tools → DHCP
```

---

# 2. DHCP Scope Configuration

A DHCP scope was created to provide automatic IP addressing for client machines.

Example:

| Setting | Value |
|---------|-------|
| Scope Name | HQ-Scope |
| Network | 10.0.1.0/24 |
| Address Range | 10.0.1.100 - 10.0.1.200 |
| DNS Server | Domain Controller |
| Domain Name | mvulasmsp.local |

---

# 3. Configure DHCP Failover

The DHCP Failover relationship was configured between both DHCP servers.

## Configuration:

| Setting | Value |
|---------|-------|
| Partner Server | MVBOIT-DC1 |
| Mode | Load Balance |
| Load Distribution | 50/50 |
| Shared Secret | Configured |
| Replication | Automatic |

---

# Validation & Testing

## DHCP Replication Test

After configuring failover, the DHCP scope was verified on the partner DHCP server.

Validation:

```
DHCP Console
    ↓
IPv4
    ↓
Scope replicated successfully
```

---

## Lease Synchronization Test

A client device was connected to the environment and received an IP address from DHCP.

Validation commands:

```powershell
ipconfig /release

ipconfig /renew
```

Confirmed:

- IP address assignment
- DNS configuration
- Domain connectivity

---

# Failure Scenario Testing

## Scenario: Primary DHCP Server Offline

### Test:

1. Stop DHCP service on MVHOIT-DC1
2. Request a new DHCP lease from the client

Command:

```powershell
ipconfig /renew
```

### Expected Result:

The client receives an IP address from MVBOIT-DC1.

### Result:

✅ DHCP service remained available  
✅ Lease assignment continued  
✅ DHCP failover successfully maintained availability

---

# Troubleshooting

## Issue: DHCP Scope Not Replicating

### Investigation:

Checked:

- DHCP authorization in Active Directory
- Network connectivity between DHCP servers
- Failover relationship status

### Resolution:

- Re-established DHCP failover relationship
- Verified scope synchronization

---

# Skills Demonstrated

- DHCP Server Administration
- DHCP Failover Configuration
- High Availability Design
- Windows Server Administration
- Active Directory Integration
- Infrastructure Troubleshooting
- Service Continuity Testing

---

# Screenshots

## DHCP Role Installation

`/screenshots/dhcp/dhcp-role-installed.png`

---

## DHCP Scope Configuration

`/screenshots/dhcp/dhcp-scope-created.png`

---

## DHCP Failover Relationship

`/screenshots/dhcp/dhcp-failover-configured.png`

---

## DHCP Replication Validation

`/screenshots/dhcp/dhcp-replication-success.png`

---

# Outcome

DHCP high availability was successfully implemented using DHCP Failover. Both Domain Controllers are capable of maintaining synchronized DHCP scopes and providing continuous IP address allocation during service interruptions.

This configuration demonstrates enterprise-level DHCP resilience commonly used in multi-site Windows Server environments.
