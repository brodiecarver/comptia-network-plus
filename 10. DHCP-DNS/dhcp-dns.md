# DHCP + DNS Fundamentals

## Overview

DHCP and DNS are two of the most important network services.

DHCP allows devices to automatically obtain network settings.

DNS allows devices to translate hostnames into IP addresses.

Together they make modern networking possible.

---

# DHCP (Dynamic Host Configuration Protocol)

## Purpose

DHCP automatically provides network configuration to devices.

Without DHCP, every device would need to be manually configured.

DHCP typically provides:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server

Example:

| Setting | Value |
|----------|----------|
| IP Address | 192.168.1.2 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.1.1 |
| DNS Server | 8.8.8.8 |

---

## DHCP Scope

A DHCP Scope is the pool of addresses available for assignment.

Example:

```text
192.168.1.100 - 192.168.1.200
```

The DHCP server can assign addresses from this range.

---

## DORA Process

Devices obtain an address using DORA.

### D - Discover

Client broadcasts:

```text
"Is there a DHCP server available?"
```

---

### O - Offer

Server replies:

```text
"I can offer you this IP address."
```

---

### R - Request

Client responds:

```text
"I would like to use that address."
```

---

### A - Acknowledge

Server confirms:

```text
"The address is yours."
```

---

### DORA Summary

```text
Discover
Offer
Request
Acknowledge
```

---

## DHCP Lease

A lease is the temporary ownership of an IP address.

Examples:

- 8 hours
- 24 hours
- 7 days

When the lease expires, the client attempts to renew it.

---

## DHCP Reservation

A reservation ensures a specific device always receives the same IP address.

Usually configured using the device MAC address.

Example:

| Device | Reserved IP |
|----------|----------|
| Printer | 192.168.1.50 |

Common uses:

- Printers
- Servers
- CCTV Systems
- Network Devices

---

## APIPA

APIPA stands for:

```text
Automatic Private IP Addressing
```

Used when DHCP fails.

Windows typically self-assigns:

```text
169.254.x.x
```

Example:

```text
169.254.22.5
```

### Exam Tip

If you see:

```text
169.254.x.x
```

Think:

```text
DHCP Failure
```

---

## Common DHCP Troubleshooting

### DHCP Working

```text
IP Address = Assigned
Gateway = Assigned
DNS = Assigned
```

---

### DHCP Failure

```text
No DHCP Offer
No IP Address
No Gateway
No DNS
```

In real Windows environments:

```text
169.254.x.x
```

may be assigned automatically.

---

# DNS (Domain Name System)

## Purpose

DNS translates hostnames into IP addresses.

Example:

```text
www.google.com
```

becomes:

```text
142.250.x.x
```

Humans prefer names.

Computers communicate using IP addresses.

---

## DNS Process

User enters:

```text
www.google.com
```

DNS lookup occurs.

DNS server responds with:

```text
IP Address
```

The client can then communicate with the destination.

---

## Common DNS Records

### A Record

Maps a hostname to an IPv4 address.

Example:

```text
www.company.com
→ 192.168.1.10
```

---

### AAAA Record

Maps a hostname to an IPv6 address.

---

### MX Record

Used for email services.

Example:

```text
company.com
→ mail.company.com
```

---

### CNAME Record

Alias record.

Example:

```text
help.company.com
→ support.company.com
```

---

## DNS Record Summary

```text
A = IPv4 Address

AAAA = IPv6 Address

MX = Mail Server

CNAME = Alias
```

---

## DNS Cache

DNS results are often temporarily stored.

Purpose:

- Reduce repeated lookups
- Improve performance
- Reduce DNS traffic

Example:

```text
Visit google.com
↓
DNS Lookup
↓
Answer Cached
↓
Future visits are faster
```

---

# DHCP vs DNS

## DHCP

Answers:

```text
Who am I?
```

Provides:

- IP Address
- Subnet Mask
- Gateway
- DNS

---

## DNS

Answers:

```text
Where is Google?
```

Provides:

- Name Resolution
- Hostname to IP Translation

---

# Troubleshooting Clues

## DHCP Problem

Symptoms:

```text
169.254.x.x
```

or

```text
No IP Address
```

Think:

```text
DHCP Failure
```

---

## DNS Problem

Symptoms:

```text
Can ping IP addresses
Cannot browse websites by name
```

Example:

```text
Ping 8.8.8.8 = Works

Ping www.google.com = Fails
```

Think:

```text
DNS Failure
```

---

# Packet Tracer Lab Summary

## Topology

```text
PC0
 |
Switch
 |
Router (DHCP Server)
```

---

## Router Configuration

```cisco
interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
```

### DHCP Pool

```cisco
ip dhcp excluded-address 192.168.1.1

ip dhcp pool LAN
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8
```

---

## Verification

PC obtained:

```text
IP Address: 192.168.1.2
Gateway: 192.168.1.1
DNS: 8.8.8.8
```

Ping to:

```text
192.168.1.1
```

Successful.

---

## DHCP Failure Test

Removed DHCP pool:

```cisco
no ip dhcp pool LAN
```

Result:

```text
No IP Address
Gateway = 0.0.0.0
DNS = 0.0.0.0
```

Demonstrated DHCP failure troubleshooting.

---

# Key Exam Facts

- DHCP assigns IP configuration automatically.
- DNS translates names into IP addresses.
- DORA = Discover, Offer, Request, Acknowledge.
- APIPA = 169.254.x.x.
- A Record = IPv4.
- AAAA Record = IPv6.
- MX Record = Mail.
- CNAME = Alias.
- If names fail but IPs work → DNS issue.
- If APIPA appears → DHCP issue.