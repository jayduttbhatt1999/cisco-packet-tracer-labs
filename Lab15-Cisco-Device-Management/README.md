# Lab 15 – Cisco Device Management

**Simulator:** Cisco Packet Tracer  
**Focus Areas:** Factory Reset, Password Recovery, Configuration Backup, IOS System Image Backup & Recovery, IOS Upgrade

---

## 🎯 Objective

In this lab, you will learn how to:

- Perform a factory reset and reload a Cisco router
- Recover from forgotten passwords using ROMMON mode
- Backup configurations to Flash and a TFTP server
- Backup and recover IOS system images
- Upgrade IOS on a Cisco switch

---

## 🧩 Topology

Devices involved:

- **R1** – Cisco Router
- **SW1** – Cisco Switch
- **TFTP Server** – IP: `10.10.10.10`

---

## ⚙️ Key Configuration Tasks

### 🔁 Factory Reset (R1)

- Erased NVRAM and reloaded R1
- Verified the Setup Wizard prompt and confirmed blank configuration
- Restored base configuration from the provided file

### 🔑 Password Recovery (R1)

- Set and then removed `enable secret` password
- Used `config-register 0x2120` to force boot to ROMMON
- Ignored startup config using `0x2142` and recovered original config via `copy start run`
- Fixed shutdown interfaces with `no shutdown`
- Restored standard boot behavior (`0x2102`)

### 💾 Configuration Backup

- Saved running config to Flash as `Backup-1`
- Backed up startup config to TFTP server as `Backup-2`

### 🧱 IOS System Image Backup & Recovery (R1)

- Backed up IOS to TFTP using `copy flash tftp`
- Deleted image from Flash and tested boot failure
- Recovered IOS via ROMMON using `tftpdnld` method

### ⬆️ IOS Upgrade (SW1)

- Verified current version: `12.2(25)FX`
- Copied new image `c2960-lanbasek9-mz.150-2.SE4.bin` from TFTP
- Set new boot image and saved config
- Verified version: `15.0(2)SE4` after reboot

---

## 📊 Verification & Output

Key command outputs:

```plaintext
Router#show run
hostname R1
interface GigabitEthernet0/0
ip address 10.10.10.1 255.255.255.0

Router#show ip int brief
GigabitEthernet0/0 10.10.10.1 YES NVRAM up up

SW1#show version
Cisco IOS Software, C2960-LANBASEK9-M, Version 15.0(2)SE4
