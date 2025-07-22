# Lab 19-1 – IGP Fundamentals Configuration (RIP & EIGRP)  
**Simulator:** Cisco Packet Tracer | **Focus:** Dynamic Routing Protocols | **Level:** Intermediate

---

## 🧠 Objective  
Configure and verify Interior Gateway Protocols (**RIP** and **EIGRP**) on a multi-router network. Observe route advertisement, neighbor formation, and administrative distance behavior.

---

## 🧪 Lab Topology  
- 3 Routers (R1, R2, R3)  
- 3 PCs (PC1, PC2, PC3)  
- Switches connecting each PC to its respective router

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
1. Configured **RIP v2** on R1 and R2 to enable dynamic routing.  
2. Configured **EIGRP** on R2 and R3 with Autonomous System 100.  
3. Verified routing tables using `show ip route`.  
4. Checked neighbor relationships using `show ip rip database` and `show ip eigrp neighbors`.  
5. Observed administrative distances to determine protocol preference when overlapping routes existed.

---

## 🔧 Sample Commands  

```bash
R1(config)# router rip
R1(config-router)# version 2
R1(config-router)# network 192.168.1.0
R1(config-router)# network 10.0.0.0

R3(config)# router eigrp 100
R3(config-router)# network 10.0.1.0
R3(config-router)# network 192.168.3.0
R3(config-router)# no auto-summary
