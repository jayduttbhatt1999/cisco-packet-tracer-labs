# Lab 23-1 – DHCP Configuration 🧩

## 📝 Objective

The objective of this lab is to configure Dynamic Host Configuration Protocol (DHCP) on a Cisco router to dynamically assign IP addresses to end devices within a network. This lab demonstrates how to create a DHCP pool, exclude specific addresses, and verify that DHCP clients receive correct IP settings.

---

## 🧠 Key Concepts

- Dynamic IP address allocation using DHCP
- DHCP pool creation and management
- IP address exclusion to prevent conflicts
- Verifying DHCP operation and troubleshooting

---

## 🖥️ Devices Used

| Device Type     | Hostname       | Quantity |
|------------------|----------------|----------|
| Router           | R1             | 1        |
| Switch           | S1             | 1        |
| End Devices      | PC1, PC2       | 2        |
| Server (Optional)| DHCP-SRV       | 1        |

---

## 🌐 Network Topology

```
[PC1]       [PC2]
   |           |
   +----[S1]---+
           |
         [R1]
```

- IP Range: 192.168.10.0/24
- Default Gateway: 192.168.10.1 (configured on R1)
- DHCP Pool: `LAN_POOL`

---

## ⚙️ Configuration Steps

### ➤ Step 1: Configure Router Interface (R1)
```bash
R1(config)# interface g0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# no shutdown
```

### ➤ Step 2: Exclude IP Addresses
```bash
R1(config)# ip dhcp excluded-address 192.168.10.1 192.168.10.10
```
> 🔒 These addresses will not be assigned to clients (reserved for servers, static devices, etc.)

### ➤ Step 3: Create DHCP Pool
```bash
R1(config)# ip dhcp pool LAN_POOL
R1(dhcp-config)# network 192.168.10.0 255.255.255.0
R1(dhcp-config)# default-router 192.168.10.1
R1(dhcp-config)# dns-server 8.8.8.8
```

### ➤ Step 4: Connect PCs and Set IP Configuration to DHCP
- On PC1 and PC2:
  - Go to **Desktop** → **IP Configuration**
  - Select **DHCP**
  - You should receive IP addresses in the range `192.168.10.11` to `192.168.10.254`

---

## 🔍 Verification

### ➤ From the PCs:
- Use `ipconfig` to check the assigned IP address
- Use `ping 192.168.10.1` to test gateway reachability

### ➤ On Router:
```bash
R1# show ip dhcp binding
```
> ✅ Confirms IP-to-MAC assignments

```bash
R1# show running-config | section dhcp
```
> 🔍 Shows DHCP configuration on the router

---

## ✅ Expected Results

- PC1 and PC2 receive IP addresses via DHCP within the correct range.
- Default gateway and DNS settings are correctly assigned.
- `show ip dhcp binding` displays active leases.
- Connectivity to gateway and other clients should be successful.

---

## 🧠 Learning Outcomes

- Understand the DHCP workflow and packet exchange (DORA process).
- Practice configuring and securing DHCP on Cisco routers.
- Gain confidence in deploying scalable IP assignment methods in enterprise networks.

---

## 📁 Files Included

- `Lab23-1-DHCP-Configuration.pkt` – Cisco Packet Tracer project file
- `README.md` – This documentation

---

⭐️ **Tip**: Always exclude reserved addresses to prevent IP conflicts and include DNS servers in DHCP pools for internet-ready clients.

