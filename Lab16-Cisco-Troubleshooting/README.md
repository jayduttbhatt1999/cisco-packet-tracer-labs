# Lab 16 – The Cisco Troubleshooting Methodology

## 🧠 Focus
This lab practices structured troubleshooting using Cisco’s six-step troubleshooting methodology. You will identify and fix DNS connectivity issues using Packet Tracer's built-in tools.

> 🔁 Simulator: Cisco Packet Tracer 8.x or later  
> 📄 File: `Lab16-Cisco-Troubleshooting.pkt`

---

## 🎯 Objective

- Apply Cisco's six-step troubleshooting methodology
- Identify and resolve network connectivity issues
- Troubleshoot DNS resolution problems using Packet Tracer
- Use simulation mode to inspect and analyze packet flow
- Understand how incorrect IP configurations, downed interfaces, and wrong DNS entries affect connectivity

---

## 🧰 Devices Used

| Device      | Quantity | Purpose                       |
|-------------|----------|-------------------------------|
| Routers     | 2        | DNS client routing, DHCP, routing |
| Switches    | 2        | Inter-device connectivity     |
| PCs         | 3        | Client devices (PC0-PC2)      |
| Server      | 1        | DNS Server                    |

---

## 🔧 Configuration Summary

### ➤ DNS Server (Server0)
- IP: `192.168.10.10`
- Configured with DNS record:
  - **www.cisco.com → 192.0.2.1**

### ➤ PC Clients
- Use DHCP to receive IP and DNS settings
- All PCs should be able to resolve and ping `www.cisco.com`

### ➤ Common Issues to Fix:
- Incorrect DNS settings on PCs
- Down interface between Router and Switch
- Misconfigured gateway IP or subnet
- DNS entry typo

---

## 🧪 Test & Verification

| Test                        | Expected Result        | Status       |
|----------------------------|------------------------|--------------|
| Ping from PC0 to `www.cisco.com` | Successful DNS + ICMP  | ✅ After Fix |
| DNS resolution on PC1      | Resolves correctly     | ✅ After Fix |
| Interface `G0/0` on Router | Up/Up                  | ✅            |
| IP settings on Server      | Static, correct config | ✅            |

---

## 🧯 Troubleshooting Steps Followed

1. **Define the Problem:** PC cannot access `www.cisco.com`
2. **Gather Information:** Used simulation mode and `ipconfig`, `ping`, `nslookup`
3. **Analyze Information:** Detected DNS misconfiguration on PC
4. **Eliminate Possibilities:** Ruled out cabling and DHCP issues
5. **Implement Solution:** Corrected DNS IP on PC0, enabled router interface
6. **Verify and Monitor:** Ping and DNS resolution confirmed working

---

## 📸 Screenshots

_Add screenshots of the simulation mode packet capture and before/after ping results here if desired._

---

## 📚 Key Takeaways

- DNS misconfiguration is a common cause of network access issues.
- Simulation mode helps visualize packet flow and ARP/DNS/ICMP operations.
- Always verify both DNS resolution and layer 3 connectivity when troubleshooting.
