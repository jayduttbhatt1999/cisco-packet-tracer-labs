# Lab 12 – The Life of a Packet: DNS & ARP Discovery

> 📅 Lecture: 12  
> 🧠 Focus: DNS Resolution & ARP Process  
> 🧪 Simulator: Cisco Packet Tracer v8.2+  

## 📝 Objective  
Understand how a packet travels through a network from source to destination by analyzing each layer of the communication process — including DNS resolution and ARP discovery — using ICMP (ping) as a test method.

## 🗺️ Topology  
- 🖥️ PC-A (DNS Client)  
- 🖥️ PC-B (Web Server)  
- 🌐 DNS Server  
- 🛣️ 2 Routers (R1 & R2)  
- 🧩 Switches connecting PCs to Routers  

## ⚙️ Key Configurations  
- IP address configuration on all devices  
- Static routing between routers  
- DNS client setup on PC-A  
- Hostname mapping on DNS Server  
- ARP inspection before and after ping  
- Use of `ping`, `arp -a`, and DNS tools for observation  

## 🔧 Commands Example

```bash
PC> ping webserver.local
R1(config)# ip host webserver.local 192.168.2.10
R2# show ip arp
PC> arp -a
```

## 🔍 Learning Outcomes  
- ✅ How DNS translates a hostname to an IP address  
- ✅ How ARP discovers the MAC address of a destination  
- ✅ How to inspect ARP tables and observe changes  
- ✅ Layer-by-layer understanding of packet movement  
- ✅ Gained troubleshooting practice using real-time tools  

## 🧠 Skills Strengthened  
- Network protocol analysis  
- Hands-on DNS/ARP behavior  
- Cisco CLI navigation  
- Packet lifecycle troubleshooting  
- Understanding protocol dependencies

---
