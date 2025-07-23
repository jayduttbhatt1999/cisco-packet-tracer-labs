# Lab 20-1 – OSPFv2 Configuration  
**Simulator:** Cisco Packet Tracer | **Focus:** OSPFv2 Setup & Verification | **Level:** Intermediate

---

## 🧠 Objective  
Configure and verify OSPFv2 (Open Shortest Path First version 2) on a multi-router network. Demonstrate dynamic route advertisement and path calculation across interconnected subnets.

---

## 🧪 Lab Topology  
- 3 Routers (R1, R2, R3)
- 3 PCs (PC1, PC2, PC3)
- Switches for each LAN
- Full-mesh router connectivity

---

## ⚙️ Devices & IP Configuration  

| Device | Interface | IP Address       | Subnet Mask     |
|--------|-----------|------------------|-----------------|
| PC1    | NIC       | 192.168.10.10    | 255.255.255.0   |
| PC2    | NIC       | 192.168.20.10    | 255.255.255.0   |
| PC3    | NIC       | 192.168.30.10    | 255.255.255.0   |
| R1     | G0/0      | 192.168.10.1     | 255.255.255.0   |
| R1     | G0/1      | 10.10.10.1       | 255.255.255.0   |
| R2     | G0/0      | 192.168.20.1     | 255.255.255.0   |
| R2     | G0/1      | 10.10.10.2       | 255.255.255.0   |
| R2     | G0/2      | 10.20.20.1       | 255.255.255.0   |
| R3     | G0/0      | 192.168.30.1     | 255.255.255.0   |
| R3     | G0/1      | 10.20.20.2       | 255.255.255.0   |

---

## 🔧 OSPFv2 Configuration Steps  

1. Assigned IP addresses and verified connectivity.
2. Enabled OSPF routing on all routers.
3. Used `network` statements to advertise connected networks.
4. Verified neighbor adjacencies with `show ip ospf neighbor`.
5. Checked the routing table with `show ip route`.

---

## 🧾 Sample OSPF Commands  

```bash
R1(config)# router ospf 1
R1(config-router)# network 192.168.10.0 0.0.0.255 area 0
R1(config-router)# network 10.10.10.0 0.0.0.255 area 0
