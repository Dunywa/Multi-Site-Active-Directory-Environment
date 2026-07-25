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

Each subnet is connected via a site-to-site link (VPN or static route between routers).
So DC1 and DC2 can ping each other across subnets.

Each RRAS server acts as:

- WAN router/gateway

- Firewall

- VPN tunnel endpoint

- Inter-subnet router

---

## ⚙️ Requirements / Environment
| Component | Description |
|------------|--------------|
| **DC Servers** | Windows Server 2022 and Windows Server 2025 |
| **Clients** | Windows 10 Pro (2x) |
| **Firewalls / Routers** | Windows Server 2019 and 2022 |
| **Hypervisor** | Hyper-V |
| **Other Tools** | PowerShell, Server Manager, Event Viewer |

---

## 🧩 Design Plan / Steps Overview

- Configured site-to-site VPN (IPSec Tunnel) to connect the two sites  
- Promote two Windows Servers as Domain Controllers  
- Configure DHCP scopes per subnet  
- Configure DNS replication  
- Test site-to-site communication and failover

---

## 🛠️ Implementation (Execution)
Document how you **implemented** each major step.  
Focus on **what was done**, key **PowerShell commands**, and **screenshots** — not click-by-click instructions.

**Example Format:**
### Step 1: Configure PFsense VPN
- Created IPSec VPN tunnel between sites.  
- Allowed required AD and DNS ports.  
- Verified connectivity with ICMP.

**Example Screenshot:**
`![PFsense VPN Config](./pfsense-vpn.png)`

**Example Command:**
```powershell
Test-Connection -ComputerName DC2 -Count 4

