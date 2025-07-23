
# Lab 27-1 – Port Security Configuration

In this lab, you will configure Port Security on a small campus network to restrict unauthorized devices from connecting to switch ports and enhance network security.

---

## 1. Disable Unused Ports

Disable all unused ports on SW1 to prevent unauthorized access.

- Check interface status:
SW1#show ip interface brief

markdown
Copy
Edit
- Interfaces `FastEthernet0/1` and `FastEthernet0/2` are in use.
- Shutdown all other FastEthernet and GigabitEthernet interfaces:
SW1(config)#interface range f0/3 - 24
SW1(config-if-range)#shutdown

SW1(config-if-range)#interface range g0/1 - 2
SW1(config-if-range)#shutdown

yaml
Copy
Edit

---

## 2. Configure Port Security on FastEthernet0/1

- Set interface to access mode:
SW1(config)#interface f0/1
SW1(config-if)#switchport mode access

pgsql
Copy
Edit
- Enable port security, allow maximum 2 MAC addresses, and manually add PC1’s MAC address (`0000.1111.1111`):
SW1(config-if)#switchport port-security
SW1(config-if)#switchport port-security maximum 2
SW1(config-if)#switchport port-security mac-address 0000.1111.1111

yaml
Copy
Edit
> **Important:** Avoid sending traffic before adding PC1’s MAC address to prevent "Found duplicate mac-address" errors. If errors occur, shut down the interface, save configuration, reload switch, add MAC, then re-enable the interface.

---

## 3. Enable Default Port Security on FastEthernet0/2

- Set interface to access mode and enable port security with default settings:
SW1(config)#interface f0/2
SW1(config-if)#switchport mode access
SW1(config-if)#switchport port-security

yaml
Copy
Edit

---

## 4. Generate Traffic Between PCs

- From PC1 or PC2, ping the other to generate traffic.

---

## 5. Verify Learned MAC Address on SW1

- Verify PC2’s MAC address (`0000.2222.2222`) has been learned:
SW1#show port-security interface f0/2

yaml
Copy
Edit

---

## 6. Verify Port Security Configuration on Both Interfaces

- View port security details:
SW1#show port-security interface f0/1
SW1#show port-security interface f0/2

yaml
Copy
Edit

Expected output includes:

- Port Security: Enabled  
- Port Status: Secure-up  
- Violation Mode: Shutdown  
- Maximum MAC Addresses: 2 (f0/1), 1 (f0/2)  
- Total MAC Addresses learned  
- Configured MAC Addresses (manual)  
- Last Source MAC Address

---

**End of Lab 27-1**








You said:
no you are not understanding i need the the whole readme in one mardown box for copy paste purpose


ChatGPT said:
Got it! Here is the entire Lab 27-1 – Port Security Configuration README content in a single markdown block that you can copy and paste directly to your Git repo:

markdown
Copy
Edit
# Lab 27-1 – Port Security Configuration

In this lab you will configure Port Security on a small campus network to restrict unauthorized hosts from accessing the network through unused ports and control access on active ports.

---

## 1. Disable Unused Ports

- Identify unused ports on SW1 using the command:
SW1#show ip interface brief

diff
Copy
Edit
- Interfaces FastEthernet0/1 and FastEthernet0/2 are in use.
- Shutdown all other FastEthernet ports:
SW1(config)#interface range f0/3 - 24
SW1(config-if-range)#shutdown

css
Copy
Edit
- Shutdown all GigabitEthernet ports:
SW1(config-if-range)#interface range g0/1 - 2
SW1(config-if-range)#shutdown

yaml
Copy
Edit

---

## 2. Configure Port Security on FastEthernet0/1

- Set the interface to access mode:
SW1(config)#interface f0/1
SW1(config-if)#switchport mode access

pgsql
Copy
Edit
- Enable port security, set maximum allowed MAC addresses to 2, and manually add PC1’s MAC address (`0000.1111.1111`):
SW1(config-if)#switchport port-security
SW1(config-if)#switchport port-security maximum 2
SW1(config-if)#switchport port-security mac-address 0000.1111.1111

yaml
Copy
Edit
> **Important:** Do not send traffic (such as ping) before manually adding PC1’s MAC address. Otherwise, Packet Tracer may learn the MAC dynamically and cause “Found duplicate mac-address” errors. If this happens, shut down the interface, save config, reload, add MAC, then enable the interface again.

---

## 3. Enable Port Security on FastEthernet0/2 with Default Settings

- Set interface to access mode and enable port security with defaults:
SW1(config)#interface f0/2
SW1(config-if)#switchport mode access
SW1(config-if)#switchport port-security

yaml
Copy
Edit

---

## 4. Generate Traffic Between PCs

- From PC1 or PC2, generate traffic (e.g., ping PC1 from PC2) to verify connectivity.

---

## 5. Verify Port Security MAC Address Learning

- On SW1, verify that the MAC address of PC2 (`0000.2222.2222`) has been learned:
SW1#show port-security interface f0/2

yaml
Copy
Edit

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

yaml
Copy
Edit

---

**End of Lab 27-1**
