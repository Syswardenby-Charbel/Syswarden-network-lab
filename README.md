# 🌐 Enterprise Network Lab — SysWarden

> **Built by Charold | Network & Systems Administrator | SysWarden**

---

## 📋 Project Overview

This lab simulates a real enterprise network with multi-VLAN architecture, inter-VLAN routing, DHCP, ACLs, SSH management, and NAT. Built entirely in **EVE-NG** using Cisco IOU images.

---

## 🗺️ Network Topology

```
                        Internet
                            |
                          RTR
                    (Router-on-a-Stick)
                    (NAT | DHCP | ACLs | SSH)
                            |
                        SW-DIST
                    (Distribution Switch)
                       /         \
                SW-RDCL-1        SW-R1
              (Access Switch)  (Access Switch)
               /        \        /        \
          PC-V10-LEFT  PC-V20  PC-V10-RIGHT  SRV-V30
```

---

## 📌 VLAN Design

| VLAN | Name | Network | Gateway |
|------|------|---------|---------|
| 10 | USERSVLAN10 | 192.168.10.0/24 | 192.168.10.1 |
| 20 | USERSVLAN20 | 192.168.20.0/24 | 192.168.20.1 |
| 30 | SERVERSVLAN30 | 192.168.30.0/24 | 192.168.30.1 |
| 40 | MGMT | 192.168.40.0/24 | 192.168.40.1 |

---

## 🔒 Security Policies (ACLs)

| Rule | Action |
|------|--------|
| VLAN10 → VLAN20 | ❌ BLOCKED |
| VLAN20 → VLAN10 | ❌ BLOCKED |
| VLAN10, 20, 30 → Internet | ✅ ALLOWED |
| All devices → SSH | ✅ ALLOWED |

---

## 🖥️ Device Management IPs

| Device | Management IP | Access |
|--------|--------------|--------|
| RTR | 192.168.10.1 | SSH |
| SW-DIST | 192.168.40.2 | SSH |
| SW-RDCL-1 | 192.168.10.2 | SSH |
| SW-R1 | 192.168.10.3 | SSH |

---

## ✅ Features Implemented

- [x] Multi-VLAN configuration (VLANs 10, 20, 30, 40)
- [x] 802.1Q Trunk ports between all switches
- [x] Router-on-a-Stick inter-VLAN routing
- [x] DHCP server per VLAN on RTR
- [x] Extended ACLs for VLAN isolation
- [x] SSH v2 on all network devices
- [x] NAT overload for Internet access
- [x] Management VLAN (VLAN 40)

---

## 🛠️ Tools Used

- **EVE-NG Community Edition** — Network emulation
- **Cisco IOU L2/L3** — Switch and Router images
- **VPCS** — Virtual PC simulation
- **MobaXterm** — SSH/Console access

---

## 📁 Configuration Files

| File | Description |
|------|-------------|
| [RTR.txt](configs/RTR.txt) | Router config — NAT, DHCP, ACLs, SSH |
| [SW-DIST.txt](configs/SW-DIST.txt) | Distribution switch config |
| [SW-RDCL-1.txt](configs/SW-RDCL-1.txt) | Access switch left config |
| [SW-R1.txt](configs/SW-R1.txt) | Access switch right config |

---

## 👤 Author

**Charold** | Network & Systems Administrator  
🔗 SysWarden — IT & Cybersecurity Services  
📧 Available on Fiverr | Upwork | Comeup
