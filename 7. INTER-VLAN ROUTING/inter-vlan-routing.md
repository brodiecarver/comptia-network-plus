# Inter-VLAN Routing

# Overview

Inter-VLAN Routing is the process of allowing devices in different VLANs to communicate with each other.

Normally:
- VLANs are separate Layer 2 broadcast domains
- devices in different VLANs cannot communicate directly

A Layer 3 device is required:
- router
- or Layer 3 switch

---

# Key Concepts

# VLANs

A VLAN (Virtual LAN):
> logically separates devices into different networks on the same switch.

Example:

```text
VLAN 10 = Sales
VLAN 20 = HR
```

Devices in different VLANs behave as if they are on completely separate switches/networks.

---

# Broadcast Domains

Each VLAN is its own:
> broadcast domain

Broadcast traffic:
- stays inside its VLAN
- does not automatically cross into other VLANs

Example:

```text
Broadcast in VLAN 10
-> only floods VLAN 10 ports
```

---

# Why Inter-VLAN Routing is Needed

Without routing:
- VLAN 10 devices cannot communicate with VLAN 20 devices

A router or Layer 3 switch must:
- route traffic between networks/VLANs

---

# Router-on-a-Stick

Router-on-a-stick is a method of:
> routing multiple VLANs using one physical router interface.

This is done using:
- subinterfaces
- trunk links
- VLAN tagging

Example:

```text
g0/0.10
g0/0.20
```

Each subinterface represents:
- one VLAN
- one default gateway

---

# Access Ports vs Trunk Ports

# Access Ports

Access ports:
- belong to one VLAN only
- connect to end devices
- send/receive untagged traffic

Example:

```text
PC -> Access Port
```

---

# Trunk Ports

Trunk ports:
- carry multiple VLANs
- use VLAN tags
- usually connect:
  - switch to router
  - switch to switch

Example:

```text
Switch <-> Router
```

---

# VLAN Tagging

Trunk links use:
> 802.1Q tagging (dot1Q)

The switch adds:
- a VLAN tag to the Ethernet frame

This identifies:
> which VLAN the frame belongs to.

Example:

```text
VLAN 10 frame
-> tagged with VLAN 10
```

Important:
- the FRAME is tagged
- not the physical port itself

---

# Router Subinterfaces

Router subinterfaces allow:
- one physical interface
- to handle multiple VLANs

Example:

```cisco
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
```

Breakdown:

```text
g0/0.10
```
= subinterface for VLAN 10

```text
encapsulation dot1Q 10
```
= handles frames tagged for VLAN 10

```text
192.168.10.1
```
= default gateway for VLAN 10 devices

---

# Default Gateways

Each VLAN requires:
> its own default gateway.

Example:

```text
VLAN 10 gateway = 192.168.10.1
VLAN 20 gateway = 192.168.20.1
```

Devices send remote traffic to:
- their VLAN gateway

---

# Packet Flow Example

## PC0 in VLAN 10 communicating with PC1 in VLAN 20

---

# Step 1

PC0 creates:
- Packet:
  - Source IP = PC0
  - Destination IP = PC1

PC0 determines:
> destination is remote (different network/VLAN)

---

# Step 2

PC0 sends frame to:
- default gateway MAC address

Important:
- Destination IP remains PC1
- Destination MAC becomes router MAC

---

# Step 3

The switch forwards traffic:
- within VLAN 10

---

# Step 4

The frame crosses the trunk link.

The switch adds:
- VLAN 10 tag

Example:

```text
802.1Q VLAN tag
```

---

# Step 5

The router receives the tagged frame.

The router:
- reads the VLAN tag
- sends traffic to correct subinterface
- removes Layer 2 frame
- examines destination IP
- routes packet toward VLAN 20

---

# Step 6

The router creates:
- a NEW Layer 2 frame for VLAN 20

Important:
- IP addresses stay the same
- MAC addresses change

---

# Step 7

The switch forwards traffic:
- within VLAN 20
- toward PC1

---

# Important Concepts Learned

## VLANs separate Layer 2 networks

## Routers connect different networks

## Trunks carry multiple VLANs

## Frames are tagged across trunks

## Default gateways allow devices to leave their VLAN

---

# Commands Used

# VLAN Creation

```cisco
vlan 10
name SALES

vlan 20
name HR
```

---

# Access Port Configuration

```cisco
interface fastethernet 0/1
switchport mode access
switchport access vlan 10
```

```cisco
interface fastethernet 0/2
switchport mode access
switchport access vlan 20
```

---

# Trunk Configuration

```cisco
interface gigabitEthernet 0/1
switchport mode trunk
```

---

# Router Subinterfaces

```cisco
interface gigabitEthernet 0/0
no shutdown
```

```cisco
interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
```

```cisco
interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
```

---

# Verification Commands

```cisco
show ip interface brief
```

```cisco
ping
```

---

# Packet Tracer Lab Summary

## Topology

```text
PC0 -> Switch -> Router -> Switch
```

Using:
- VLAN 10
- VLAN 20
- trunk link
- router-on-a-stick

---

# Tasks Completed

- Created VLANs
- Configured access ports
- Configured trunk port
- Configured router subinterfaces
- Configured default gateways
- Tested inter-VLAN connectivity
- Used Simulation Mode to observe packet flow

---

# Troubleshooting Notes

## Common Issues

- Wrong VLAN assignment
- Trunk not configured
- Missing encapsulation dot1Q
- Wrong default gateway
- Interface shutdown
- Incorrect IP addressing
- VLAN mismatch
- Simulation Mode paused traffic

---

# Key Takeaways

- VLANs improve segmentation and organisation
- Broadcast traffic stays inside VLANs
- Inter-VLAN communication requires routing
- Router-on-a-stick uses one physical interface for multiple VLANs
- Trunk links carry tagged VLAN traffic
- Switches forward frames
- Routers route packets
- MAC addresses change at each hop
- IP addresses remain end-to-end