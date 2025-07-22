# Lab 18 – Connectivity Troubleshooting  
**Simulator:** Cisco Packet Tracer | **Focus:** Static Route Debugging | **Level:** Intermediate

---

## 🧠 Objective  
Diagnose and resolve routing issues in a network where a ping from PC1 to PC3 fails. Use the `tracert` tool to pinpoint the failure, inspect static routes, and configure missing routes on the routers.

---

## 🧪 Lab Topology  
- 3 Routers (R1, R2, R3)
- 3 PCs (PC1, PC2, PC3)
- Appropriate Switches & Connections

---

## ⚙️ Devices & IP Configuration  

| Device | Interface | IP Address       | Subnet Mask     |
|--------|-----------|------------------|-----------------|
| PC1    | NIC       | 10.1.1.10        | 255.255.255.0   |
| PC2    | NIC       | 10.1.2.10        | 255.255.255.0   |
| PC3    | NIC       | 10.1.3.10        | 255.255.255.0   |
| R1     | G0/0      | 10.1.1.1         | 255.255.255.0   |
| R1     | G0/1      | 192.168.1.1      | 255.255.255.0   |
| R2     | G0/0      | 192.168.1.2      | 255.255.255.0   |
| R2     | G0/1      | 192.168.2.1      | 255.255.255.0   |
| R3     | G0/0      | 192.168.2.2      | 255.255.255.0   |
| R3     | G0/1      | 10.1.3.1         | 255.255.255.0   |

---

## 🔍 Tasks Performed  
1. Verified IP settings and connectivity on all devices.
2. Used `tracert` from PC1 to PC3 to locate where the packet failed.
3. Identified that R3 lacked a static route to reach PC1's network (10.1.1.0/24).
4. Added missing static route on R3:

```bash
R3(config)# ip route 10.1.1.0 255.255.255.0 192.168.2.1
