# Lab 29-1 – NAT Configuration  
**Simulator:** Cisco Packet Tracer | **Focus:** Static NAT, Dynamic NAT, PAT | **Level:** Intermediate

---

## 🧠 Objective  
Configure and verify **Static NAT**, **Dynamic NAT**, and **Port Address Translation (PAT)** to enable internal hosts to access external networks and allow public users to access internal services securely.

---

## 🧪 Lab Topology Overview  
- **R1**: WAN Edge Router (Connected to Service Provider SP1)
- **SP1**: Service Provider Router
- **Int-S1**: Internal Web Server (10.0.1.10)
- **Ext-S1**: External Host (203.0.113.20)
- **PC1, PC2**: Internal Client PCs (10.0.2.10, 10.0.2.11)

---

## ⚙️ IP Addressing Scheme  

| Device     | Interface | IP Address       | Subnet Mask       | Notes                         |
|------------|-----------|------------------|--------------------|-------------------------------|
| R1         | F0/0      | 203.0.113.2      | 255.255.255.240    | Internet-facing (NAT outside) |
| R1         | F0/1      | 10.0.1.1         | 255.255.255.0      | To internal web server        |
| R1         | F1/0      | 10.0.2.1         | 255.255.255.0      | To client PCs (inside NAT)    |
| SP1        | F0/0      | 203.0.113.1      | 255.255.255.240    | Default gateway               |
| Int-S1     | NIC       | 10.0.1.10        | 255.255.255.0      | Internal Web Server           |
| PC1        | NIC       | 10.0.2.10        | 255.255.255.0      | Internal Client               |
| PC2        | NIC       | 10.0.2.11        | 255.255.255.0      | Internal Client               |

---

## 🔍 Tasks Performed  

### 🔐 Static NAT
1. **Mapped Int-S1 (10.0.1.10)** to **203.0.113.3** for external web access.  
2. Verified accessibility using ping and web browser on Ext-S1.  
3. Confirmed NAT translation via `show ip nat translation`.

### 🔄 Dynamic NAT
4. Created a NAT pool from **203.0.113.4 – 203.0.113.12**.  
5. Allowed 10.0.2.0/24 clients to dynamically use the pool on a first-come, first-served basis.  
6. Observed NAT behavior using `debug ip nat` and translation table output.

### 🔁 PAT (Port Address Translation)
7. Reconfigured R1 to get public IP via **DHCP** from SP1.  
8. Enabled PAT to allow multiple clients to share a single IP with port numbers.  
9. Verified external access from PC1 and PC2 and confirmed translation entries.

### 🧹 Cleanup  
10. Removed static/dynamic NAT rules, ACLs, and NAT pool to reset configuration.

---

## 🔧 Sample NAT Configuration Snippets  

```bash
# Static NAT
R1(config)# interface f0/0
R1(config-if)# ip nat outside
R1(config)# interface f0/1
R1(config-if)# ip nat inside
R1(config)# ip nat inside source static 10.0.1.10 203.0.113.3

# Dynamic NAT
R1(config)# ip nat pool Flackbox 203.0.113.4 203.0.113.12 netmask 255.255.255.240
R1(config)# access-list 1 permit 10.0.2.0 0.0.0.255
R1(config)# ip nat inside source list 1 pool Flackbox

# PAT using single interface IP
R1(config)# ip nat inside source list 1 interface f0/0 overload
```

---

## 📈 Observations  

- **Static NAT** is required for persistent, externally accessible services like web servers.
- **Dynamic NAT** limits users to the number of available public IPs in the pool.
- **PAT** enables many internal clients to share a single IP using port numbers.

---

## 🧪 Verification Commands  

```bash
# View NAT translations
R1# show ip nat translation

# View NAT statistics
R1# show ip nat statistics

# Enable NAT debugging
R1# debug ip nat
```

---

## 🧼 Cleanup Commands  

```bash
R1(config)# no ip nat inside source static 10.0.1.10 203.0.113.3
R1(config)# no ip nat inside source list 1 pool Flackbox overload
R1(config)# no ip nat pool Flackbox
R1(config)# no access-list 1
R1(config)# interface f0/0
R1(config-if)# no ip nat outside
R1(config)# interface f0/1
R1(config-if)# no ip nat inside
R1(config)# interface f1/0
R1(config-if)# no ip nat inside
R1# clear ip nat translation *
```

---

## 📚 Summary  
This lab provided hands-on experience configuring all major types of NAT in Cisco routers: **Static NAT**, **Dynamic NAT**, and **PAT**. You learned how to manage public-private IP mappings, use address pools efficiently, and secure web services for external access.

