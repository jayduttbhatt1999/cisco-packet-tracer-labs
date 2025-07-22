# Lab 11 – Static Routing Configuration

> 📅 Lecture: 11  
> 🧠 Focus: Static Routing  
> 🧪 Simulator: Cisco Packet Tracer v8.2+  

---

## 📝 Objective

Understand how to manually configure static routes between routers to enable communication between different networks.

---

## 🗺️ Topology

- 3 Routers (R1, R2, R3)
- 3 Switches
- 3 PCs (one per router)
- Point-to-point links between routers

---

## ⚙️ What Was Done

- Assigned IP addresses to router interfaces and PCs
- Configured static routes manually on each router
- Verified network connectivity using `ping` and `show` commands

---

## 💻 Commands Example

```bash
R1(config)# ip route 192.168.3.0 255.255.255.0 10.0.0.2
R2(config)# ip route 192.168.1.0 255.255.255.0 10.0.0.1
R3(config)# ip route 192.168.1.0 255.255.255.0 10.0.1.1
