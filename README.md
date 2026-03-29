# Cisco Packet Tracer Network Design  


# 1. Project Overview
This project designs and implements a complete enterprise network using **Cisco Packet Tracer**.

The company consists of **two buildings**, each with **three departments**, connected to an ISP router using Serial WAN links.

The project includes:
- Router & switch configuration  
- DHCP server setup  
- RIP v2 dynamic routing  
- Spanning Tree Protocol (STP) verification  
- Subnet planning  
- End‑to‑end connectivity testing  
- Full documentation & Packet Tracer file  

---

# 2. Network Topology Description
The network contains:
- ISP Router (R‑ISP)  
- Building Router 1 (R‑B1)  
- Building Router 2 (R‑B2)  
- Switch SW‑B1 and SW‑B2  
- Three PCs per building (6 total)  
- Serial WAN connections  
- Ethernet LAN connections  

Routing between buildings is performed via **RIP v2** using the ISP.

---

# 3. Network Addressing Documentation

## WAN Subnet #1 — ISP ↔ Building 1
Network ID:       93.1.2.0
Mask:             255.255.255.252 (/30)
R‑ISP:            93.1.2.1
R‑B1:             93.1.2.2
Broadcast:        93.1.2.3
## WAN Subnet #2 — ISP ↔ Building 2
Network ID:       93.1.2.4
Mask:             255.255.255.252 (/30)
R‑ISP:            93.1.2.5
R‑B2:             93.1.2.6
Broadcast:        93.1.2.7
## Building 1 LAN — 10.0.1.0/24
Network ID:       10.0.1.0
Gateway:          10.0.1.1
Host Range:       10.0.1.2 – 10.0.1.254
Broadcast:        10.0.1.255
## Building 2 LAN — 10.0.2.0/24
Network ID:       10.0.2.0
Gateway:          10.0.2.1
Host Range:       10.0.2.2 – 10.0.2.254
Broadcast:        10.0.2.255

---

# 4. DHCP Configuration

## R‑B1 DHCP
ip dhcp pool BUILDING1
 network 10.0.1.0 255.255.255.0
 default-router 10.0.1.1
 dns-server 8.8.8.8
ip dhcp excluded-address 10.0.1.1

## R‑B2 DHCP
ip dhcp pool BUILDING2
 network 10.0.2.0 255.255.255.0
 default-router 10.0.2.1
 dns-server 8.8.8.8
ip dhcp excluded-address 10.0.2.1

---

## 5. RIP v2 Routing Configuration
RIP v2 enables dynamic routing between the buildings and ISP.
router rip
 version 2
 network 93.1.2.0
 network 10.0.0.0
 no auto-summary

---

## 6. How to Run This Project

Open the .pkt file in Cisco Packet Tracer
View routing tables using: show ip route
Test connectivity with ping
Verify DHCP, RIP, and STP outputs

---

## 7. Author
Farhan Rahman M. Farabi
Romanian-American University
Computer Science for Economics
