# Enterprise Multi-Branch Network Design & Routing Simulation

An end-to-end multi-branch enterprise network simulated in **Cisco Packet Tracer**, demonstrating VLSM subnet planning, dynamic routing with RIPv2, 802.1Q Inter-VLAN routing, and centralized network services.

---

## 📌 Topology Overview

![Network Topology](Packet Tracer.png)

The topology models a distributed enterprise environment with three primary segments:
1. **Branch Office**: Departmental network segmented into multiple VLANs (IT, HR, Sales, and Branch DHCP) using a Cisco 2960 Switch and 2911 Router.
2. **Headquarters (HQ)**: Core network managing WAN transit links, WLAN infrastructure via Access Points, and centralized servers (DNS, DHCP).
3. **Web Network**: Dedicated network segment hosting the organization's Web Server.

---

## ⚙️ Key Technical Implementations

* **VLSM & IP Subnetting**: Designed an efficient IP scheme using Variable Length Subnet Masking (VLSM) and CIDR notations to prevent address waste across LAN and WAN segments.
* **VLAN Segmentation & 802.1Q Trunking**: Isolated department broadcast domains and configured **Router-on-a-Stick** sub-interfaces on Cisco routers to enable controlled Inter-VLAN routing.
* **Dynamic Routing (RIPv2)**: Implemented RIP version 2 across serial links with `no auto-summary` enabled to support discontiguous subnets and classless routing.
* **Network Infrastructure Services**:
  * **DHCP**: Centralized and branch DHCP pools for dynamic host IP assignment.
  * **DNS Resolution**: Custom DNS server configured with an 'A' record resolving `ict.com` to the internal Web Server (`192.168.100.100`).
  * **Wireless LAN**: Integrated Access Points bridging wireless laptop clients into the HQ network.

---

## 📊 IP Addressing & Subnet Plan

| Subnet / Purpose | Network Address | CIDR | Usable Host Range | Broadcast Address |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN 10 (IT)** | `192.168.10.0` | `/25` | `192.168.10.1 - 192.168.10.126` | `192.168.10.127` |
| **VLAN 20 (HR)** | `192.168.10.128` | `/26` | `192.168.10.129 - 192.168.10.190` | `192.168.10.191` |
| **VLAN 30 (Sales)** | `192.168.10.192` | `/27` | `192.168.10.193 - 192.168.10.222` | `192.168.10.223` |
| **VLAN 40 (DHCP)** | `192.168.10.224` | `/27` | `192.168.10.225 - 192.168.10.254` | `192.168.10.255` |
| **DNS Server Network** | `172.16.10.0` | `/30` | `172.16.10.1 - 172.16.10.2` | `172.16.10.3` |
| **HQ Wireless / DHCP** | `192.169.1.0` | `/24` | `192.169.1.1 - 192.169.1.254` | `192.169.1.255` |
| **Web Server LAN** | `192.168.100.0` | `/24` | `192.168.100.1 - 192.168.100.254` | `192.168.100.255` |
| **WAN: Branch ↔ HQ** | `10.1.1.0` | `/30` | `10.1.1.1 - 10.1.1.2` | `10.1.1.3` |
| **WAN: HQ ↔ WEB** | `10.2.1.0` | `/30` | `10.2.1.1 - 10.2.1.2` | `10.2.1.3` |

---

## 🗂 File Structure

```text
├── topology.pkt          # Complete Cisco Packet Tracer simulation file
├── topology.png          # Network topology architecture screenshot
└── README.md             # Project documentation and specifications
