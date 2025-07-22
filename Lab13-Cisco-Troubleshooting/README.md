# Lab 13 – The Cisco Troubleshooting Methodology

> 📅 Lecture: 13  
> 🧠 Focus: DNS Connectivity Troubleshooting  
> 🧪 Simulator: Cisco Packet Tracer v8.2+  

## 📝 Objective  
Apply the Cisco troubleshooting methodology to identify and resolve DNS connectivity issues in a multi-router environment.

## 🗺️ Topology  
- 3 Routers: R1, R2, R3  
- 1 Server (configured as a DNS server with IP 10.10.10.10)  
- End devices connected through routers  
- R2 connects the DNS server to the network  

## ⚙️ Key Configurations and Issues  
- Telnet and ping diagnostics  
- Interface status check (`show ip int brief`)  
- `traceroute` for path verification  
- DNS service verification  
- Correct DNS IP configuration on R3

## 🛠️ Troubleshooting Steps  

1. **Initial Symptom**:  
   Users report DNS not working. Telnet from R3 to 10.10.10.10 fails with timeout.

2. **Connectivity Check**:  
   Ping from R3 to DNS server fails (`U.U.U` pattern).  
   Traceroute shows failure beyond R2.

3. **Router Interface Status**:  
   On R2, `FastEthernet0/0` (facing DNS) is **administratively down**.  
   ➤ Fixed using:  
   ```bash
   R2(config)# interface f0/0  
   R2(config-if)# no shutdown
