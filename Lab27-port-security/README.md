# Lab 27-1 – Port Security Configuration

In this lab you will configure Port Security on a small campus network to restrict unauthorized hosts from accessing the network through unused ports and control access on active ports.

---

## 1. Disable Unused Ports

- Identify unused ports on SW1 using the command:
SW1#show ip interface brief


- Interfaces FastEthernet0/1 and FastEthernet0/2 are in use.
- Shutdown all other FastEthernet ports:
SW1(config)#interface range f0/3 - 24
SW1(config-if-range)#shutdown

- Shutdown all GigabitEthernet ports:
SW1(config-if-range)#interface range g0/1 - 2
SW1(config-if-range)#shutdown

---

## 2. Configure Port Security on FastEthernet0/1

- Set the interface to access mode:
SW1(config)#interface f0/1
SW1(config-if)#switchport mode access


- Enable port security, set maximum allowed MAC addresses to 2, and manually add PC1’s MAC address (`0000.1111.1111`):
SW1(config-if)#switchport port-security
SW1(config-if)#switchport port-security maximum 2
SW1(config-if)#switchport port-security mac-address 0000.1111.1111


> **Important:** Do not send traffic (such as ping) before manually adding PC1’s MAC address. Otherwise, Packet Tracer may learn the MAC dynamically and cause “Found duplicate mac-address” errors. If this happens, shut down the interface, save config, reload, add MAC, then enable the interface again.

---

## 3. Enable Port Security on FastEthernet0/2 with Default Settings

- Set interface to access mode and enable port security with defaults:
SW1(config)#interface f0/2
SW1(config-if)#switchport mode access
SW1(config-if)#switchport port-security

---

## 4. Generate Traffic Between PCs

- From PC1 or PC2, generate traffic (e.g., ping PC1 from PC2) to verify connectivity.

---

## 5. Verify Port Security MAC Address Learning

- On SW1, verify that the MAC address of PC2 (`0000.2222.2222`) has been learned:
SW1#show port-security interface f0/2

---

## 6. Verify Full Port Security Configuration on Interfaces

- Display port security details for both interfaces (do not use `show running-config` for this):
SW1#show port-security interface f0/1
Port Security : Enabled
Port Status : Secure-up
Violation Mode : Shutdown
Maximum MAC Addresses : 2
Total MAC Addresses : 1
Configured MAC Addresses : 1
Last Source Address:Vlan : 0000.1111.1111:1
Security Violation Count : 0

SW1#show port-security interface f0/2
Port Security : Enabled
Port Status : Secure-up
Violation Mode : Shutdown
Maximum MAC Addresses : 1
Total MAC Addresses : 1
Configured MAC Addresses : 0
Last Source Address:Vlan : 0000.2222.2222:1
Security Violation Count : 0


---

**End of Lab 27-1**
