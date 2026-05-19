````markdown
# Encapsulation

## What is Encapsulation?

Encapsulation is the process of adding information to data as it moves down the networking layers before transmission.

Each layer adds its own:
- Header
- Sometimes a trailer

This added information helps devices know:
- where data is going
- how to process it
- what protocol is being used

---

# Encapsulation Flow

Data moves DOWN the networking stack during encapsulation.

```text
Data
→ Segment
→ Packet
→ Frame
→ Bits
```

| Layer | Data Name |
|---|---|
| Application | Data |
| Transport | Segment |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

---

# De-encapsulation

De-encapsulation is the reverse process.

As data moves UP the stack:
- headers are removed
- trailers are removed
- original application data is recovered

---

# Headers vs Trailers

## Headers
Headers are added to the FRONT of data.

Examples:
- IP addresses
- MAC addresses
- Port numbers

## Trailers
Trailers are added to the END of data.

Usually used for:
- error checking
- frame verification

---

# Transport Layer

The Transport layer adds:
- source port
- destination port
- sequencing information

The data becomes a:
# Segment

Protocols:
- TCP
- UDP

---

# Network Layer

The Network layer adds:
- source IP address
- destination IP address

The segment becomes a:
# Packet

Routers primarily operate here.

---

# Data Link Layer

The Data Link layer adds:
- source MAC address
- destination MAC address

The packet becomes a:
# Frame

Switches primarily operate here.

---

# Physical Layer

Frames are converted into:
# Bits

Example:

```text
101010101010
```

Bits travel as:
- electrical signals
- light
- radio waves

---

# Switches vs Routers

## Switches
Switches:
- operate mainly at Layer 2
- forward frames
- use MAC addresses

### Key Concept

```text
Switches forward FRAMES using MAC addresses
```

---

## Routers
Routers:
- operate mainly at Layer 3
- route packets
- use IP addresses

### Key Concept

```text
Routers route PACKETS using IP addresses
```

---

# MAC Addresses vs IP Addresses

| MAC Address | IP Address |
|---|---|
| Local delivery | Network-to-network delivery |
| Layer 2 | Layer 3 |
| Changes at router hops | Usually stays the same end-to-end |

---

# ARP (Address Resolution Protocol)

ARP resolves:
# IP address → MAC address

ARP only works on the:
# local network (LAN/broadcast domain)

---

# Local vs Remote Traffic

## Local Destination
If the destination is on the same subnet:
- the PC ARPs for the destination device MAC address

Example:

```text
192.168.1.10 → 192.168.1.50
```

---

## Remote Destination
If the destination is on another network:
- the PC ARPs for the default gateway/router MAC address

Example:

```text
192.168.1.10 → 8.8.8.8
```

The PC sends the frame to:
# the router

---

# Switch Flooding

A switch floods traffic when:
- destination MAC is unknown
- traffic is broadcast

Example:
- ARP requests

Flooding occurs only inside the local LAN/VLAN.

Routers do NOT forward broadcasts.

---

# Re-encapsulation

When a router receives a frame:

1. Removes old Layer 2 frame
2. Checks IP packet
3. Chooses next network
4. Creates NEW Layer 2 frame
5. Forwards traffic onward

This is:
# Re-encapsulation

---

# Example Packet Journey

## Before Router

```text
Source MAC = PC MAC
Destination MAC = Router MAC
```

## After Router

```text
Source MAC = Router MAC
Destination MAC = Next Device MAC
```

## IP Addresses

Usually remain:

```text
Source IP → Destination IP
```

through the entire trip.

---

# MTU (Maximum Transmission Unit)

MTU is:
# the maximum packet/frame size allowed on a network link

If data is too large:
- it may be split into smaller pieces

This is called:
# Fragmentation

---

# Fragmentation

Fragmentation means:
# splitting large packets into smaller pieces

Usually due to MTU limitations.

---

# TCP Flags (Basic Intro)

TCP uses small markers called:
# Flags

These help manage TCP communication.

| Flag | Meaning |
|---|---|
| SYN | Start connection |
| ACK | Acknowledge receipt |
| FIN | Finish/close connection |
| RST | Reset connection |

---

# TCP Three-Way Handshake

Basic TCP connection setup:

```text
SYN
→
SYN-ACK
→
ACK
```

This establishes a reliable TCP connection.

---

# Important Concepts to Remember

```text
Data
→ Segment
→ Packet
→ Frame
→ Bits
```

```text
Switches use MAC addresses
```

```text
Routers use IP addresses
```

```text
ARP only works locally
```

```text
Routers re-encapsulate frames
```

---

# Packet Tracer Reinforcement Lab

## Lab Topology

```text
PC → Switch → Router → Switch → PC
```

## Practice Observing
- ARP requests
- ICMP traffic
- MAC address changes
- IP address persistence
- router re-encapsulation
- switch forwarding behavior

## Use
# Simulation Mode

Inspect:
- OSI Model tab
- Inbound PDU Details
- Outbound PDU Details

---

# Summary

Encapsulation is the process of wrapping data with headers/trailers as it moves down the networking layers.

Each layer has a specific role:
- Transport = ports/segments
- Network = IP packets
- Data Link = MAC frames

Switches forward locally using MAC addresses.

Routers move traffic between networks using IP addresses.

Understanding encapsulation is foundational for:
- switching
- routing
- Wireshark
- packet analysis
- Security+
- SOC analysis
````
