# Routing Basics

## Overview

Routing is the process of moving packets between different networks.

A router operates at:
- Layer 3 (Network Layer) of the OSI model

Routers make forwarding decisions using:
- IP addresses
- Routing tables

---

# Key Concepts

## What a Router Does

A router:
- connects different networks together
- examines destination IP addresses
- forwards packets toward their destination

Example:

```text
192.168.1.0/24 <--> Router <--> 192.168.2.0/24
```

Without a router:
- devices on different networks cannot communicate

---

# Default Gateway

The default gateway is:
> the router interface a device sends traffic to when the destination is on another network.

Example:

```text
PC IP: 192.168.1.10
Gateway: 192.168.1.1
```

If the destination device is outside the local network:
- the PC sends the frame to the gateway MAC address

---

# Switching vs Routing

## Switches
Switches:
- operate mainly at Layer 2
- forward frames using MAC addresses
- keep traffic inside the local network/VLAN

## Routers
Routers:
- operate at Layer 3
- forward packets between networks
- use IP addresses and routing tables

---

# Local vs Remote Communication

## Local Network Communication

If the destination is on the same network:
- the PC uses ARP to learn the destination MAC address
- the switch forwards the frame directly

Example:

```text
192.168.1.10 -> 192.168.1.20
```

No router is needed.

---

## Remote Network Communication

If the destination is on another network:
- the PC sends the frame to the default gateway MAC
- the router routes the packet toward the remote network

Example:

```text
192.168.1.10 -> 192.168.2.10
```

A router is required.

---

# ARP (Address Resolution Protocol)

ARP is used to:
> find a MAC address from a known IP address.

Example:

```text
Who has 192.168.1.1?
```

The router replies with its MAC address.

Important:
- ARP only works on the local network
- ARP broadcasts do not cross routers

---

# Packet Flow Example

## PC0 communicating with PC1 on another network

### Step 1
PC0 creates:
- Packet:
  - Source IP = PC0
  - Destination IP = PC1

### Step 2
PC0 checks:
> Is the destination local or remote?

The destination is remote.

### Step 3
PC0 sends the frame to:
- Default gateway MAC address

Important:
- Destination IP remains PC1
- Destination MAC becomes the router MAC

### Step 4
The switch forwards the frame to the router.

### Step 5
The router:
- removes the Layer 2 frame
- reads the destination IP
- checks the routing table
- forwards the packet to the correct network

### Step 6
The router creates a NEW Layer 2 frame for the next network.

Important:
- IP addresses stay the same end-to-end
- MAC addresses change at every hop

---

# Encapsulation and De-encapsulation

## Encapsulation
As data moves down the OSI model:
- headers are added

Example:

```text
Data
-> Segment
-> Packet
-> Frame
-> Bits
```

## De-encapsulation
The receiving device removes headers as the data moves up the OSI model.

---

# Routing Table

Routers use routing tables to determine:
- where packets should go next

The routing table contains:
- destination networks
- next-hop information
- directly connected networks

---

# Packet Tracer Lab Summary

## Topology

```text
PC0 -> Switch -> Router -> Switch -> PC1
```

## Tasks Completed

- Configured router interfaces
- Assigned IP addresses to PCs
- Configured default gateways
- Tested connectivity using ping
- Used Simulation Mode to observe packet flow

---

# Important Things Learned

## Switches move frames locally
## Routers move packets between networks

---

# Key Takeaways

- Routers connect different networks
- Default gateways allow devices to leave their local network
- ARP finds MAC addresses locally
- Switches use MAC addresses
- Routers use IP addresses
- MAC addresses change at each hop
- IP addresses stay the same end-to-end
- Routing decisions happen at Layer 3

---

# Commands Used

## Router Interface Configuration

```cisco
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
```

```cisco
interface gigabitEthernet 0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
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

# Troubleshooting Notes

## Common Issues

- Incorrect IP address
- Incorrect subnet mask
- Wrong default gateway
- Interface shutdown
- Incorrect cabling
- ARP not learned yet
- Simulation Mode paused traffic

---

# Simulation Mode Notes

Packet Tracer Simulation Mode:
- pauses packet movement
- allows step-by-step packet analysis

Useful for observing:
- ARP
- switching
- routing
- encapsulation
- MAC/IP changes
- packet flow