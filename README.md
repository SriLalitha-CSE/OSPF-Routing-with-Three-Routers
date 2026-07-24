# OSPF Routing with Three Routers using Cisco Packet Tracer

##  Overview

This project demonstrates the implementation of **Open Shortest Path First (OSPF)** in a network consisting of three interconnected routers. OSPF is a link-state dynamic routing protocol that automatically discovers routes, exchanges routing information, and calculates the shortest path between networks using Dijkstra's algorithm.

This lab showcases how routers communicate within the same OSPF Area (Area 0) to enable efficient routing between multiple LANs.

---

##  Objectives

- Design a network with three interconnected routers.
- Configure IP addresses for routers and end devices.
- Configure serial interfaces between routers.
- Implement OSPF (Process ID 1).
- Advertise LAN and serial networks in Area 0.
- Verify routing information and end-to-end connectivity.

---

##  Software Used

- Cisco Packet Tracer

---

##  Network Topology

### Devices Used

- 3 Cisco Routers
- 3 Switches
- Multiple PCs
- Serial (DCE/DTE) Connections
- Copper Straight-Through Cables

Each router connects to:

- One Local Area Network (LAN)
- Two neighboring routers through serial links

---

##  Network Addressing

### LAN Networks

| Network | Connected Router |
|---------|------------------|
| 192.168.1.0/24 | Router 3 |
| 192.168.2.0/24 | Router 6 |
| 192.168.3.0/24 | Router 5 |

### Serial Networks

| Network | Connected Routers |
|---------|-------------------|
| 11.0.0.0/8 | Router 3 ↔ Router 6 |
| 12.0.0.0/8 | Router 6 ↔ Router 5 |
| 13.0.0.0/8 | Router 5 ↔ Router 3 |

---

##  Configuration Performed

- Configured FastEthernet interfaces.
- Assigned IP addresses to all PCs.
- Configured serial interfaces between routers.
- Enabled interfaces using `no shutdown`.
- Configured clock rate on DCE serial interfaces.
- Enabled OSPF Process ID 1.
- Advertised LAN and serial networks in Area 0.
- Verified neighbor relationships and routing tables.

---

## 📖 Key Commands Used

### Configure Router Interface

```bash
interface fastEthernet 0/0
ip address <IP_Address> <Subnet_Mask>
no shutdown
```

### Configure Serial Interface

```bash
interface serial 0/0/0
ip address <IP_Address> <Subnet_Mask>
clock rate 64000
no shutdown
```

### Configure OSPF

```bash
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 11.0.0.0 0.255.255.255 area 0
network 13.0.0.0 0.255.255.255 area 0
```

> Similar OSPF configuration was performed on the remaining routers using their respective LAN and serial networks.

### Verify Routing Table

```bash
show ip route
```

### Verify OSPF Configuration

```bash
show running-config
```

### Verify OSPF Neighbors

```bash
show ip ospf neighbor
```

---

##  Verification

After configuring OSPF:

- OSPF neighbor relationships were successfully established.
- Routers dynamically learned all remote networks.
- Routing tables were automatically updated with OSPF routes.
- PCs on different LANs successfully communicated using **ping**.
- End-to-end connectivity across all networks was verified.

---

##  Concepts Learned

- Open Shortest Path First (OSPF)
- Link-State Routing Protocol
- OSPF Process ID
- OSPF Area 0
- Wildcard Masks
- Dynamic Routing
- Router Configuration
- Serial Communication
- Routing Tables
- Network Troubleshooting

---

##  Repository Contents

- `OSPF-3-Routers.pkt` – Cisco Packet Tracer simulation
- `README.md` – Project documentation

---

##  Future Improvements

- Implement Multi-Area OSPF.
- Compare OSPF with RIP and Static Routing.
- Configure OSPF authentication.
- Explore OSPF route summarization and load balancing.

---
