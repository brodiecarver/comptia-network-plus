# VLANs & Trunking Notes

## What is a VLAN?

VLAN stands for:

Virtual Local Area Network

A VLAN is a way to logically separate networks inside a switch.

Instead of:
- using separate physical switches

You can:
- create multiple logical networks on the same switch.

---

# Logical vs Physical Separation

## Physical Separation
Separate:
- switches
- cables
- hardware

Example:
- one switch for office PCs
- one switch for security cameras

---

## Logical Separation
Same physical switch hardware, but the switch internally separates traffic using software/rules.

Traffic from one VLAN is not forwarded into another VLAN unless routing is used.

---

# VLANs Create Broadcast Domains

Each VLAN is its own broadcast domain.

Broadcast traffic stays inside its VLAN.

Example:

- VLAN 10 broadcasts stay in VLAN 10
- VLAN 20 broadcasts stay in VLAN 20

---

# Access Ports

An access port:
- carries ONE VLAN
- is usually used for end devices

Examples:
- PCs
- printers
- cameras

Example:

Fa0/1 = VLAN 10

The connected device belongs to VLAN 10.

---

# Trunk Ports

A trunk port:
- carries MULTIPLE VLANs
- usually connects networking devices together

Examples:
- switch to switch
- switch to router
- switch to enterprise wireless AP

---

# VLAN Tagging

Trunk ports use VLAN tagging.

The VLAN tag tells the switch:
- which VLAN the frame belongs to

This allows:
- multiple VLANs to travel over one Ethernet cable

---

# Important VLAN Concept

Trunks DO NOT merge VLANs together.

Trunks only:
- transport VLAN traffic between switches

The VLANs remain separated.

---

# Same VLAN Across Multiple Switches

Devices in the SAME VLAN can communicate across switches through a trunk link.

Example:

PC0 = VLAN 10
PC2 = VLAN 10

Even though they are on different switches:
- they can communicate

because:
- the trunk carries VLAN 10 traffic between switches

---

# Different VLANs

Devices in DIFFERENT VLANs cannot directly communicate.

Example:

PC0 = VLAN 10
PC1 = VLAN 20

Communication fails because:
- VLANs are separate logical networks

---

# Inter-VLAN Routing

Different VLANs require:
- a router
OR
- a Layer 3 switch

to communicate.

This is called:

Inter-VLAN Routing

---

# Access Port vs Trunk Port

| Access Port | Trunk Port |
|---|---|
| One VLAN | Multiple VLANs |
| End devices | Networking devices |
| Untagged traffic | Tagged traffic |
| PC/printer/camera | Switch/router/AP |

---

# Packet Tracer Lab Summary

## Topology

- 2 switches
- 4 PCs
- 1 trunk link between switches

---

## VLAN Assignments

### VLAN 10
- PC0
- PC2

### VLAN 20
- PC1
- PC3

---

# IP Addressing

## VLAN 10
PC0 = 192.168.10.10
PC2 = 192.168.10.20

## VLAN 20
PC1 = 192.168.20.10
PC3 = 192.168.20.20

Subnet Mask:
255.255.255.0

---

# Lab Results

## Successful Pings

PC0 -> PC2
PC1 -> PC3

Reason:
- same VLAN
- trunk carried VLAN traffic between switches

---

## Failed Ping

PC0 -> PC1

Reason:
- different VLANs
- no inter-VLAN routing configured

---

# Simulation Mode Observations

Observed:
- ARP traffic
- ICMP traffic
- STP packets
- CDP packets
- DTP packets

---

# ARP Understanding

ARP happens BEFORE ICMP when the sender does not know the destination MAC address.

Once learned:
- the MAC is cached
- later pings may skip ARP

---

# Key Takeaways

- VLANs separate networks logically
- Access ports carry one VLAN
- Trunk ports carry multiple VLANs
- Trunks transport VLANs but do not merge them
- Same VLANs can communicate across switches
- Different VLANs require routing to communicate
- Switches use VLAN membership when forwarding traffic