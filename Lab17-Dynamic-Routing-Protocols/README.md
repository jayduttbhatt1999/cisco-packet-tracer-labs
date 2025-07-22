# Lab 17 – Dynamic Routing Protocols 🔄

## 🧠 Objective

In this lab, we implement and compare three key dynamic routing protocols—**RIP**, **EIGRP**, and **OSPF**—in a multi-router topology. You'll explore how routers exchange routing information automatically, adapt to topology changes, and optimize path selection dynamically.

---

## 🛠️ Topology & Devices Used

- 3 Routers (R1, R2, R3)
- 3 Switches (S1, S2, S3)
- 3 PCs (PC1, PC2, PC3)
- Cisco Packet Tracer Version: **8.2**

The routers are interconnected to simulate a multi-network enterprise scenario with end devices in each subnet.

---

## 🔧 Configuration Overview

### Common Setup
- IP addressing on all interfaces
- Proper subnetting for each segment
- Basic hostname and interface descriptions

### RIP (Router Information Protocol)
- Enabled on R1 and R2
- `version 2` with `no auto-summary`
- Included networks with `network` command

### EIGRP (Enhanced Interior Gateway Routing Protocol)
- Configured on R2 and R3
- AS number `100`
- Passive interfaces enabled for security
- Verification with `show ip protocols`, `show ip route eigrp`

### OSPF (Open Shortest Path First)
- Configured on R1 and R3
- Area 0
- Router IDs manually set
- Network wildcard masks for accurate interface matching

---

## 🧪 Verification

- `ping` and `traceroute` across different segments
- `show ip route` to verify learned routes
- `debug ip rip/eigrp/ospf` (when needed) for protocol behavior

---

## 🧵 Key Learning Outcomes

- Understand the advantages and differences of dynamic protocols
- Configure multiple protocols in a hybrid network
- Use passive interfaces and administrative distance appropriately
- Validate dynamic route learning and convergence

---

## ✅ Deliverables

- 📁 `Lab17-Dynamic-Routing-Protocols.pkt` – Packet Tracer file
- 📘 `README.md` – This documentation

---

> ⚠️ **Note**: All configurations were tested using Cisco Packet Tracer v8.2+. Ensure you're using a compatible version for best results.
