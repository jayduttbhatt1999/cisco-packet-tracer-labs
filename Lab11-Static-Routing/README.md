# Lab 11 – Static Routing Configuration

> 📅 Lecture: 11  
> 🧠 Focus: Static Routing  
> 🧪 Simulator: Cisco Packet Tracer v8.2+  

## 📝 Objective
Manually configure static routes between routers so that different networks can communicate without using dynamic protocols.

## 🗺️ Topology
- 3 Routers (R1, R2, R3)
- 3 Switches
- 3 PCs (one per router)
- Serial links between routers

## ⚙️ Key Configurations
- Interface IP addressing
- Static route configuration using `ip route`
- `ping` and `traceroute` testing

## 🔧 Commands Example

```bash
R1(config)# ip route 192.168.3.0 255.255.255.0 10.0.0.2
R2(config)# ip route 192.168.1.0 255.255.255.0 10.0.0.1
R3(config)# ip route 192.168.1.0 255.255.255.0 10.0.1.1
