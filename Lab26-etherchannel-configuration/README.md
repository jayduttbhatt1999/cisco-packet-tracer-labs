# Lab 26-1 – EtherChannel Configuration

In this lab you will configure EtherChannel links in a campus LAN to increase bandwidth and provide redundancy. The lab covers LACP, PAgP, and static EtherChannel configuration at Layer 2, as well as Layer 3 EtherChannel with IP addressing and OSPF routing.

---

## LACP EtherChannel Configuration

1. The access layer switches Acc3 and Acc4 both have two FastEthernet uplinks. However, spanning tree protocol shuts down all but one uplink, so total bandwidth between PCs attached to Acc3 and Acc4 is 100 Mbps.

2. Convert the uplinks from Acc3 to CD1 and CD2 to LACP EtherChannel. Configure descriptions on port channel interfaces:

   - On Acc3 to CD1:

     ```
     interface range f0/23 - 24
     channel-group 1 mode active
     exit
     interface port-channel 1
     description Link to CD1
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On CD1 with matching settings:

     ```
     interface range f0/23 - 24
     channel-group 1 mode active
     exit
     interface port-channel 1
     description Link to Acc3
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On Acc3 to CD2 (port-channel 2):

     ```
     interface range f0/21 - 22
     channel-group 2 mode active
     exit
     interface port-channel 2
     description Link to CD2
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On CD2 with matching settings:

     ```
     interface range f0/21 - 22
     channel-group 2 mode active
     exit
     interface port-channel 2
     description Link to Acc3
     switchport mode trunk
     switchport trunk native vlan 199
     ```

3. Verify EtherChannels come up on both sides with flags like (SU) and member ports marked (P).

---

## PAgP EtherChannel Configuration

4. Convert uplinks from Acc4 to CD1 and CD2 to PAgP EtherChannel. Use port channel 1 and 2 respectively but opposite from Acc3 configuration:

   - On Acc4 to CD2 (port-channel 1):

     ```
     interface range f0/23 - 24
     channel-group 1 mode desirable
     exit
     interface port-channel 1
     description Link to CD2
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On CD2 matching:

     ```
     interface range f0/23 - 24
     channel-group 1 mode desirable
     exit
     interface port-channel 1
     description Link to Acc4
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On Acc4 to CD1 (port-channel 2):

     ```
     interface range f0/21 - 22
     channel-group 2 mode desirable
     exit
     interface port-channel 2
     description Link to CD1
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On CD1 matching:

     ```
     interface range f0/21 - 22
     channel-group 2 mode desirable
     exit
     interface port-channel 2
     description Link to Acc4
     switchport mode trunk
     switchport trunk native vlan 199
     ```

5. Verify EtherChannels are up on Acc4, CD1, and CD2.

---

## Static EtherChannel Configuration

6. Convert uplinks between CD1 and CD2 to static EtherChannel (port-channel 3):

   - On CD1:

     ```
     interface range g0/1 - 2
     channel-group 3 mode on
     exit
     interface port-channel 3
     description Link to CD2
     switchport mode trunk
     switchport trunk native vlan 199
     ```

   - On CD2 matching:

     ```
     interface range g0/1 - 2
     channel-group 3 mode on
     exit
     interface port-channel 3
     description Link to CD1
     switchport mode trunk
     switchport trunk native vlan 199
     ```

7. Verify the EtherChannel is up on both CD1 and CD2.

8. The total bandwidth between PCs attached to Acc3 and Acc4 is now 200 Mbps because two FastEthernet links are aggregated and active towards the root bridge CD1.

---

## Layer 3 EtherChannel Configuration

9. Configure Layer 3 EtherChannel with LACP between Switch1 and Switch2 using GigabitEthernet1/0/1 and 1/0/2:

interface range GigabitEthernet1/0/1 - 2
no switchport
channel-group 1 mode active
exit
interface port-channel 1
ip address 192.168.0.1 255.255.255.252
no shutdown

- Switch2 configuration with IP 192.168.0.2/30 on port-channel 1 similarly.

10. Configure Layer 3 EtherChannel between Switch1 and Switch3 on interfaces 1/0/3 - 4 with IP 192.168.0.5/30 and 192.168.0.6/30 respectively.

11. Configure Layer 3 EtherChannel between Switch2 and Switch3 on interfaces 1/0/5 - 6 with IP 192.168.0.9/30 and 192.168.0.10/30 respectively.

12. Verify all Layer 3 EtherChannels are up.

---

## OSPF Integration

13. Enable IP routing and configure OSPF Area 0 on Switch1, Switch2, and Switch3 for the 192.168.0.0/24 subnet:

ip routing
router ospf 1
network 192.168.0.0 0.0.0.255 area 0

14. Verify OSPF adjacencies form between switches.

15. Verify routing tables include all configured networks.

16. Spanning Tree Protocol does not disable any Layer 3 EtherChannel interfaces as STP only runs on Layer 2 ports.

---

## Verification Commands Summary

- `show etherchannel summary` — Verify EtherChannel status  
- `show interfaces port-channel` — Check port channel interfaces  
- `show spanning-tree` — Confirm spanning tree behavior  
- `show ip ospf neighbor` — Verify OSPF adjacency  
- `show ip route` — Check routing table entries  

---

This lab demonstrates how to increase bandwidth, provide redundancy using EtherChannel technologies, and integrate Layer 3 EtherChannel links with dynamic routing protocols like OSPF.

---

⭐️ **Star this repository if you find it useful!**  
🎯 [Follow me on GitHub](https://github.com/jayduttbhatt1999) for more networking labs and projects.
