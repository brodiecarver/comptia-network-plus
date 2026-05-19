# Ethernet & Switching - Network+ Notes

## Ethernet Basics

Ethernet is the main wired LAN technology used for local network communication.

Ethernet mainly operates at:
- Layer 2 (Data Link Layer)

Ethernet uses:
- Frames
- MAC Addresses

---

# Ethernet Frames

An Ethernet frame contains:
- Source MAC Address
- Destination MAC Address
- Payload/Data
- FCS (error checking)

Ethernet delivers frames locally using MAC addresses.

---

# MAC Addresses

MAC addresses are:
- Layer 2 addresses
- Physical addresses assigned to network interfaces

Example:

```md
00:1A:2B:3C:4D:5E
```

Important:
- MAC addresses belong to interfaces, not entire devices
- A device can have multiple MAC addresses if it has multiple interfaces

Examples:
- Ethernet NIC
- Wi-Fi adapter
- Bluetooth adapter

---

# Broadcast MAC Address

Ethernet broadcast address:

```md
FF:FF:FF:FF:FF:FF
```

Meaning:
- Send to all devices on the local LAN

Broadcasts are local only.
Routers do not forward Layer 2 broadcasts.

---

# Switches

Switches are mainly Layer 2 devices.

Main job:
- Forward Ethernet frames using MAC addresses

Switches use a MAC/CAM table to map:

```md
MAC Address -> Port
```

---

# MAC Address Learning

Switches learn MAC addresses from:
- Source MAC addresses

Example:
- Frame arrives on Port 1
- Source MAC = AA

Switch learns:

```md
AA = Port 1
```

The switch learns from where the frame physically came from.

---

# Normal Forwarding

If the switch already knows the destination MAC location:

Example:

```md
BB = Port 2
```

The switch forwards the frame only to Port 2.

This is called:
- Forwarding

---

# Unicast

Unicast means:
- One sender to one receiver

Example:

```md
Destination MAC = BB
```

Only the device with MAC BB should process the frame.

---

# Broadcast

Broadcast means:
- One sender to all devices on the local LAN

Broadcast uses:

```md
FF:FF:FF:FF:FF:FF
```

Switches flood broadcast traffic out all ports except the incoming port.

Broadcasts are commonly used by:
- ARP Requests
- DHCP Discover messages

---

# ARP (Address Resolution Protocol)

ARP translates:

```md
IP Address -> MAC Address
```

ARP asks:

```md
"Who has this IP?"
```

ARP requests are broadcast traffic.

Example:

```md
Who has 192.168.1.20?
```

ARP is performed by:
- The sending device

NOT:
- The switch

---

# Same LAN vs Remote Network

## Same LAN

If the destination is local:
- ARP for the destination device MAC

Example:

```md
192.168.1.20 -> MAC BB
```

---

# Remote Network

If the destination is remote:
- ARP for the default gateway/router MAC

Example:

```md
Who has 192.168.1.1?
```

The Ethernet frame destination becomes:
- Router MAC

The IP packet destination remains:
- Remote server IP

---

# Unknown Unicast Flooding

Unknown unicast flooding occurs when:
- The switch knows the destination MAC
- But does not know which port contains that MAC

Example:

```md
Destination MAC = BB
```

But:

```md
BB not found in MAC table
```

The switch temporarily floods all ports except the incoming port.

This is different from broadcast flooding.

---

# Broadcast Flooding vs Unknown Unicast Flooding

## Broadcast Flooding
- Frame is intentionally for everyone
- Uses:

```md
FF:FF:FF:FF:FF:FF
```

## Unknown Unicast Flooding
- Frame is intended for one device
- Switch temporarily does not know which port contains the MAC

---

# Collision Domains

Collision domains relate to:
- Signal interference

Old hubs created:
- One large collision domain

Switches separate collision domains.

Usually:

```md
1 switch port = 1 collision domain
```

Modern switched Ethernet mostly eliminates collisions.

---

# Broadcast Domains

Broadcast domains control:
- How far broadcasts can spread

Routers separate broadcast domains.

Important rule:
- Switches forward broadcasts
- Routers stop broadcasts

---

# Key Differences

| Device/Protocol | Main Job |
|---|---|
| ARP | IP -> MAC |
| Switch | MAC -> Port |
| Router | IP -> Network |

---

# Important Exam Concepts

## Switches use:
- MAC addresses

## Routers use:
- IP addresses

## Broadcasts are:
- Local only

## ARP:
- Finds MAC addresses from IP addresses

## Unknown unicast flooding:
- Happens when switch does not know destination port yet

---

# Easy Memory Tricks

## ARP

```md
IP -> MAC
```

## Switch

```md
MAC -> Port
```

## Router

```md
IP -> Network
```

## Broadcast

```md
Everyone local
```

## Unicast

```md
One specific device
```