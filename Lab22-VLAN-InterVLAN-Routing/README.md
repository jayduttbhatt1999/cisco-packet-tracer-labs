# Lab 22-1 – VLAN and Inter-VLAN Routing Configuration  
**Simulator:** Cisco Packet Tracer | **Focus:** VLANs, VTP, Trunking, and Inter-VLAN Routing | **Level:** Advanced

---

## 🧠 Objective  
Design and configure a campus LAN topology implementing VLANs, VTP (Server, Client, Transparent modes), access/trunk ports, native VLANs, and three methods of inter-VLAN routing:
1. Separate Router Interfaces  
2. Router-on-a-Stick  
3. Layer 3 Switch SVI routing

---

## 🧪 Lab Topology  
- 3 Switches (SW1, SW2, SW3)
- 1 Router (R1)
- 6 PCs: Eng1, Eng2, Eng3 (VLAN 10) & Sales1, Sales2, Sales3 (VLAN 20)

---

## ⚙️ Devices & Configuration Overview  

### 🔸 VLANs  
| VLAN | Name   | Purpose       |
|------|--------|---------------|
| 10   | Eng    | Engineering   |
| 20   | Sales  | Sales Dept    |
| 199  | Native | Native VLAN   |

- VLANs configured on:
  - **SW1** (VTP Server)
  - **SW2** (VTP Transparent)
  - **SW3** (VTP Client - learns VLANs from SW1)

---

### 🔸 VTP Modes  
| Switch | VTP Mode     | Domain     |
|--------|--------------|------------|
| SW1    | Server       | Flackbox   |
| SW2    | Transparent  | Flackbox   |
| SW3    | Client       | Flackbox   |

---

### 🔸 Trunk Links  
- Trunk ports configured using `dot1q`
- Native VLAN set to `199` on all trunk links

---

## 🛠️ Configuration Steps  

### 1️⃣ VLAN & VTP Setup  
- Verified default VLAN status  
- Configured VTP domain and modes  
- Created VLANs 10, 20, and 199 on SW1 and SW2  
- Verified VLAN propagation on SW3

### 2️⃣ Trunk & Access Port Configuration  
- Converted inter-switch links to trunk mode  
- Set native VLAN to 199 for enhanced security  
- Assigned access ports:
  - PCs in VLAN 10 (Eng): `Fa0/1-2`
  - PCs in VLAN 20 (Sales): `Fa0/3` on respective switches

---

## 🌐 Inter-VLAN Routing Scenarios  

### Option 1: Router with Separate Interfaces  
- `R1`:
  - `Fa0/0`: 10.10.10.1 (VLAN 10)
  - `Fa0/1`: 10.10.20.1 (VLAN 20)
- Access ports on SW2 connected to router interfaces
- Verified connectivity between VLANs

### Option 2: Router-on-a-Stick  
- Sub-interfaces on `R1`:
  - `Fa0/0.10`: Encapsulation `dot1q 10`, IP `10.10.10.1`
  - `Fa0/0.20`: Encapsulation `dot1q 20`, IP `10.10.20.1`
- Trunk port on SW2 to router
- Verified Eng ↔ Sales communication

### Option 3: Layer 3 Switch Routing  
- Enabled IP routing on SW2  
- Created SVIs:
  - `VLAN 10`: IP `10.10.10.1`
  - `VLAN 20`: IP `10.10.20.1`
- PCs used SVI IPs as default gateways  
- Verified end-to-end VLAN routing without external router

---

## ✅ Verification  

Used the following tools for testing connectivity:
- `ping` between Eng and Sales VLANs
- Verified routing tables and trunking using:
  - `show vlan brief`
  - `show vtp status`
  - `show ip route`
  - `show interfaces trunk`
  - `show mac address-table`

---

## 🎓 Key Learning Outcomes  
- VLAN segmentation and access/trunk port configuration  
- Proper use of VTP modes for centralized VLAN management  
- Secure trunking via native VLAN reassignment  
- Inter-VLAN routing via multiple architectural options  
- Practical understanding of Layer 2 vs Layer 3 switching

---

## 📁 Files Included  
- `Lab22-VLAN-InterVLAN-Routing.pkt` – Cisco Packet Tracer simulation file  
- `README.md` – This documentation

---

⭐️ *This lab is part of the CCNA-level networking simulation series. For optimal results, open using Cisco Packet Tracer v8.2+.*
