# Lab 14 – Cisco Router and Switch Basics

> 📅 Lecture: 14  
> 🧠 Focus: Initial Configuration, CDP, Speed/Duplex Troubleshooting  
> 🧪 Simulator: Cisco Packet Tracer v8.2+  

## 📝 Objective  
Learn how to configure Cisco routers and switches, verify connectivity, analyze Cisco Discovery Protocol (CDP) output, and troubleshoot interface speed and duplex mismatches.

## 🗺️ Topology  
- 2 Routers: R1, R2  
- 1 Switch: SW1  
- Connected in a star topology using FastEthernet ports

## ⚙️ Key Configurations

- Hostnames on all devices  
- IP configuration on routers and switch VLAN  
- Management default gateway on switch  
- Interface descriptions  
- Manual duplex/speed settings  
- CDP configuration and cache management  

## 🔧 Commands Used

```bash
# Hostname Configuration
Router(config)#hostname R1
Switch(config)#hostname SW1

# IP Addressing
R1(config)#interface f0/0
R1(config-if)#ip address 10.10.10.1 255.255.255.0
R1(config-if)#no shutdown

R2(config)#interface f0/0
R2(config-if)#ip address 10.10.10.2 255.255.255.0
R2(config-if)#no shutdown

# Switch VLAN Interface and Gateway
SW1(config)#interface vlan1
SW1(config-if)#ip address 10.10.10.10 255.255.255.0
SW1(config-if)#no shutdown

SW1(config)#ip default-gateway 10.10.10.2

# Descriptions
SW1(config)#interface f0/1
SW1(config-if)#description Link to R1
SW1(config)#interface f0/2
SW1(config-if)#description Link to R2

# Speed and Duplex Settings
SW1(config)#interface f0/2
SW1(config-if)#speed 100
SW1(config-if)#duplex full

R2(config)#interface f0/0
R2(config-if)#speed 100
R2(config-if)#duplex full
