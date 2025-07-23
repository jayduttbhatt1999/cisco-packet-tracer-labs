# Lab 24-1 – HSRP Configuration 🛡️

In this lab, you will configure and test **Hot Standby Router Protocol (HSRP)** for a small campus network to provide gateway redundancy and failover.

---

## Lab Objectives

- Configure basic HSRP on two routers for the 10.10.10.0/24 subnet
- Assign physical and virtual IP addresses for HSRP interfaces
- Verify active and standby router roles
- Test connectivity through the virtual IP gateway
- Configure priority and preemption to control active router selection
- Simulate router failure and observe HSRP failover behavior

---

## Lab Steps

1. Configure physical IP addresses on GigabitEthernet0/1 on R1 and R2.
2. Assign the same virtual IP address (10.10.10.1) to HSRP group 1 on both routers.
3. Verify which router is active using `show standby` commands.
4. Test PC connectivity to the virtual IP and external gateway.
5. Check the MAC addresses on physical interfaces and HSRP virtual interface.
6. Configure R1 with a higher priority (110) and enable preemption.
7. Verify that R1 becomes the active router.
8. From PC1, run continuous ping to the virtual IP.
9. Save R1 configuration and reload it.
10. Observe failover to R2 during R1 reboot.
11. After R1 boots, verify it regains active status due to preemption.
12. Stop the ping on PC1 and review any dropped packets during failover.

---

## Verification Commands

- `show standby GigabitEthernet0/1`
- `show interface GigabitEthernet0/1`
- Ping virtual IP (10.10.10.1) and external IP (203.0.113.1)
- PC ARP table and ping results

---

## Key Concepts

- HSRP allows two routers to share a virtual IP for gateway redundancy.
- The active router owns the virtual IP and MAC; the standby router monitors and takes over if needed.
- Priority and preemption control which router becomes active.
- Failover happens smoothly with minimal packet loss.

---

> ⚠️ Note: MAC addresses and IPs may vary depending on your environment and Packet Tracer version.

---
