# OSI Model

## Purpose
The OSI model is a 7-layer networking model used to standardize network communication and troubleshooting.

---

# The 7 Layers

| Layer | Name | Main Purpose |
|---|---|---|
| 7 | Application | User/network services |
| 6 | Presentation | Encryption, formatting, translation |
| 5 | Session | Starts and manages sessions |
| 4 | Transport | Reliable delivery, TCP/UDP |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | MAC addresses and switching |
| 1 | Physical | Cables, signals, bits |

---

# Memory Trick

All People Seem To Need Data Processing

| Word | Layer |
|---|---|
| All | Application |
| People | Presentation |
| Seem | Session |
| To | Transport |
| Need | Network |
| Data | Data Link |
| Processing | Physical |

---

# Layer Breakdown

## Layer 7 - Application
Provides network services to applications.

### Examples
- HTTP/HTTPS
- DNS
- FTP
- SMTP

---

## Layer 6 - Presentation
Handles:
- encryption
- decryption
- formatting
- compression

### Examples
- SSL/TLS
- JPEG
- MP3

---

## Layer 5 - Session
Creates, manages, and terminates communication sessions.

### Examples
- Logged into websites
- Remote desktop sessions
- Video calls

---

## Layer 4 - Transport
Handles:
- reliability
- sequencing
- retransmission
- flow control

### Protocols
- TCP
- UDP

### PDU
Segment

---

## Layer 3 - Network
Handles:
- IP addressing
- routing between networks

### Devices
- Routers

### Protocols
- IP
- ICMP

### PDU
Packet

---

## Layer 2 - Data Link
Handles:
- MAC addresses
- switching
- local communication

### Devices
- Switches

### PDU
Frame

---

## Layer 1 - Physical
Handles:
- cables
- radio waves
- electrical/light signals

### Devices
- Hubs
- Repeaters
- Cables

### PDU
Bits

---

# Important Address Types

| Address Type | Layer |
|---|---|
| MAC Address | Layer 2 |
| IP Address | Layer 3 |

---

# Device Layers

| Device | OSI Layer |
|---|---|
| Hub | Layer 1 |
| Switch | Layer 2 |
| Router | Layer 3 |

---

# TCP vs UDP

## TCP
- Reliable
- Connection-oriented
- Uses acknowledgements and retransmission

### Common Uses
- Web browsing
- Email
- File transfers

---

## UDP
- Faster
- Less reliable
- Lightweight

### Common Uses
- Gaming
- Streaming
- VoIP

---

# Encapsulation

As data moves DOWN the OSI model, headers are added.

| Layer | PDU |
|---|---|
| Layers 7-5 | Data |
| Layer 4 | Segment |
| Layer 3 | Packet |
| Layer 2 | Frame |
| Layer 1 | Bits |

---

# Default Gateway

The default gateway is:
- the router interface IP on the local network
- where traffic is sent when leaving the local network

Example:

| Device | Gateway |
|---|---|
| 192.168.1.10 | 192.168.1.1 |
| 192.168.2.10 | 192.168.2.1 |

---

# Packet Tracer Lab Summary

Built network:

PC → Switch → Router → Switch → PC

Learned:
- assigning IP addresses
- router interfaces
- default gateways
- ping testing
- packet flow
- Layer 2 switching
- Layer 3 routing

---

# Key Exam Clues

| Clue | Likely Layer |
|---|---|
| Cable/signal issue | Layer 1 |
| MAC address | Layer 2 |
| IP/routing | Layer 3 |
| TCP/UDP | Layer 4 |
| Sessions | Layer 5 |
| Encryption | Layer 6 |
| HTTP/DNS/email | Layer 7 |