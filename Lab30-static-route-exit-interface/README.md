# Lab 30 – Static Route with Exit Interface  
**Simulator:** Cisco Packet Tracer | **Focus:** Static Routing (Exit Interface) | **Level:** Beginner

---

## 🧠 Objective  
Configure static routing using the **exit interface** method to enable end-to-end communication across a three-router network.

---

## 🧪 Lab Topology  
- 3 Routers (R1, R2, R3)  
- 3 PCs (PC1, PC2, PC3)  
- Switches connecting each PC to a router

---

## ⚙️ Devices & IP Configuration  

| Device | Interface | IP Address       | Subnet Mask     |
|--------|-----------|------------------|-----------------|
| PC1    | NIC       | 192.168.1.10     | 255.255.255.0   |
| PC2    | NIC       | 192.168.2.10     | 255.255.255.0   |
| PC3    | NIC       | 192.168.3.10     | 255.255.255.0   |
| R1     | G0/0      | 192.168.1.1      | 255.255.255.0   |
| R1     | G0/1      | 10.0.0.1         | 255.255.255.0   |
| R2     | G0/0      | 10.0.0.2         | 255.255.255.0   |
| R2     | G0/1      | 10.0.1.1         | 255.255.255.0   |
| R3     | G0/0      | 10.0.1.2         | 255.255.255.0   |
| R3     | G0/1      | 192.168.3.1      | 255.255.255.0   |

---

## 🔍 Tasks Performed  
1. Assigned IP addresses to all router interfaces and end devices.  
2. Configured static routes on all routers using **exit interface method**:
   - R1: Route to 192.168.2.0/24 and 192.168.3.0/24 via `G0/1`
   - R2: Route to 192.168.1.0/24 via `G0/0`, and to 192.168.3.0/24 via `G0/1`
   - R3: Route to 192.168.1.0/24 and 192.168.2.0/24 via `G0/0`  
3. Verified static routes using `show ip route`.  
4. Verified end-to-end connectivity with `ping` from each PC to the others.

---

## 🔧 Sample Commands  

```bash
R1(config)# ip route 192.168.2.0 255.255.255.0 g0/1
R1(config)# ip route 192.168.3.0 255.255.255.0 g0/1

R2(config)# ip route 192.168.1.0 255.255.255.0 g0/0
R2(config)# ip route 192.168.3.0 255.255.255.0 g0/1

R3(config)# ip route 192.168.1.0 255.255.255.0 g0/0
R3(config)# ip route 192.168.2.0 255.255.255.0 g0/0
```

---

## ✅ Result  
All PCs were able to successfully communicate with each other across routers using static routes with exit interfaces. Routing tables showed appropriate 'S' entries.

---
