# TCP/IP Model Notes

## What is the TCP/IP Model?

The TCP/IP model is a simplified networking model used in the real world to explain how data moves across networks and the internet.

It has 4 layers.

The TCP/IP model is more practical than the OSI model.

---

# The 4 TCP/IP Layers

| Layer | Purpose |
|---|---|
| Application | User services and applications |
| Transport | End-to-end communication |
| Internet | IP addressing and routing |
| Network Access | Local network communication |

---

# 1. Application Layer

This layer contains network services and protocols used by applications.

## Common Protocols

- HTTP / HTTPS
- DNS
- DHCP
- FTP
- SMTP
- IMAP
- POP3

## Simple Explanation

This is the layer where the user interacts with the network.

Example:
- Opening a website
- Sending an email
- Using DNS to find a website IP

---

# 2. Transport Layer

This layer controls communication between devices.

It uses:
- TCP
- UDP

## TCP

TCP is reliable.

Features:
- Error checking
- Ordered delivery
- Retransmission of lost packets

Used for:
- Websites
- Email
- File downloads

## UDP

UDP is faster but less reliable.

Features:
- No error recovery
- Lower delay
- Faster transmission

Used for:
- Gaming
- Streaming
- Voice/video calls

---

# 3. Internet Layer

This layer handles:
- IP addresses
- Routing
- Moving packets between networks

## Main Protocol

- IP (Internet Protocol)

## Devices

- Routers mainly operate here

## Simple Explanation

The Internet layer decides where data should go.

Routers forward traffic using destination IP addresses.

---

# 4. Network Access Layer

This layer handles local network communication.

## Includes

- Ethernet
- Wi-Fi
- MAC addresses
- Switches
- Cables
- NICs (Network Interface Cards)

## Simple Explanation

This layer moves data around the local network.

Switches use MAC addresses to forward frames locally.

---

# TCP/IP vs OSI Model

| TCP/IP | OSI Equivalent |
|---|---|
| Application | Layers 5, 6, 7 |
| Transport | Layer 4 |
| Internet | Layer 3 |
| Network Access | Layers 1 and 2 |

---

# Key Concepts

## Switches

- Use MAC addresses
- Operate mainly at the Network Access layer
- Forward frames locally

## Routers

- Use IP addresses
- Operate mainly at the Internet layer
- Route traffic between networks

---

# TCP vs UDP

| TCP | UDP |
|---|---|
| Reliable | Faster |
| Error checking | Less overhead |
| Ordered delivery | No guaranteed delivery |
| Used for websites/files | Used for gaming/streaming |

---

# Important Exam Points

## Application Layer
Protocols like:
- HTTP
- HTTPS
- DNS
- DHCP

## Transport Layer
Protocols:
- TCP
- UDP

## Internet Layer
- IP addressing
- Routing
- Routers

## Network Access Layer
- Ethernet
- Wi-Fi
- MAC addresses
- Switches

---

# Easy Memory Tricks

## Router = IP Address = Internet Layer

## Switch = MAC Address = Network Access Layer

## TCP = Reliable

## UDP = Fast

---

# Real World Example

Opening a website:

1. Application Layer
- HTTPS request is created

2. Transport Layer
- TCP communication begins

3. Internet Layer
- IP addresses are used for routing

4. Network Access Layer
- Ethernet/Wi-Fi sends frames using MAC addresses

---

# Summary

The TCP/IP model is the practical networking model used on the internet.

It explains:
- how devices communicate
- how data is transported
- how routing works
- how local networks operate

The TCP/IP model simplifies the OSI model into 4 layers.