# NAT (Network Address Translation)

## Purpose of NAT

NAT allows private IP addresses to communicate with devices on the Internet using public IP addresses.

Why NAT exists:

- IPv4 addresses are limited
- Millions of devices need Internet access
- NAT allows many private devices to share fewer public IP addresses

---

## Private IP Ranges

### Class A Private

10.0.0.0 - 10.255.255.255

### Class B Private

172.16.0.0 - 172.31.255.255

### Class C Private

192.168.0.0 - 192.168.255.255

Private IP addresses are not routable on the Internet.

---

## Public IP Addresses

Examples:

8.8.8.8

1.1.1.1

203.0.113.1

Public IP addresses are globally unique and routable on the Internet.

---

## How NAT Works

### Before NAT

Source IP: 192.168.1.10

Destination IP: 203.0.113.100

### After NAT

Source IP: 203.0.113.1

Destination IP: 203.0.113.100

NAT changes the IP address inside the packet.

NAT does NOT change:

- Device IP addresses
- Router interface IP addresses

---

## Outbound NAT

When traffic leaves the network:

Source IP changes.

Example:

192.168.1.10

↓

203.0.113.1

---

## Inbound NAT

When return traffic arrives:

Destination IP changes.

Example:

203.0.113.1

↓

192.168.1.10

---

## PAT (Port Address Translation)

Also called:

NAT Overload

PAT allows multiple devices to share a single public IP address.

Example:

192.168.1.10:5000

↓

203.0.113.1:10001

192.168.1.20:5000

↓

203.0.113.1:10002

PAT uses logical TCP/UDP port numbers to keep conversations separate.

PAT is the most common NAT type used in home networks.

---

## NAT Types

### Static NAT

One private IP maps to one public IP.

Example:

192.168.1.100

↔

203.0.113.100

Used for:

- Web servers
- Mail servers
- Public-facing services

---

### Dynamic NAT

Many private devices share a pool of public IP addresses.

Example Public Pool:

203.0.113.10

203.0.113.11

203.0.113.12

Addresses are assigned temporarily.

---

### PAT (NAT Overload)

Many private IP addresses share a single public IP address using port numbers.

Example:

192.168.1.10

192.168.1.20

192.168.1.30

↓

203.0.113.1

---

## NAT Table

Purpose:

Tracks which private device owns each Internet conversation.

Example:

192.168.1.10:5000

↔

203.0.113.1:10001

192.168.1.20:5000

↔

203.0.113.1:10002

Useful command:

```bash
show ip nat translations
```

Example output:

```text
Inside Local  = 192.168.1.10
Inside Global = 203.0.113.1
Outside Global = 203.0.113.100
```

---

## NAT Terminology

### Inside Local

Private address of the internal device.

Example:

192.168.1.10

### Inside Global

Public address seen on the Internet after NAT.

Example:

203.0.113.1

### Outside Global

Public address of the external device.

Example:

203.0.113.100

### Memory Trick

Inside Local = My Private IP

Inside Global = My Public IP

Outside Global = Their Public IP

---

## NAT Packet Tracer Lab

### Topology

```text
PC
|
Switch
|
Router
|
Server
```

### PC Configuration

```text
IP Address: 192.168.1.10

Subnet Mask: 255.255.255.0

Default Gateway: 192.168.1.1
```

### Server Configuration

```text
IP Address: 203.0.113.100

Subnet Mask: 255.255.255.0

Default Gateway: 203.0.113.1
```

### Router Interface Configuration

```bash
interface g0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside
 no shutdown

interface g0/1
 ip address 203.0.113.1 255.255.255.0
 ip nat outside
 no shutdown
```

### ACL for NAT

```bash
access-list 1 permit 192.168.1.0 0.0.0.255
```

### PAT Configuration

```bash
ip nat inside source list 1 interface g0/1 overload
```

### Verification Commands

```bash
show ip nat translations
```

```bash
show access-lists
```

```bash
show run | section nat
```

### Connectivity Test

```bash
ping 203.0.113.100
```

Successful NAT translation should appear in:

```bash
show ip nat translations
```

---

## Exam Tips

If many devices share one public IP:

Answer = PAT (NAT Overload)

If one internal server always maps to one public IP:

Answer = Static NAT

If a pool of public IPs is used:

Answer = Dynamic NAT

If a company wants to conserve public IPv4 addresses:

Answer = NAT/PAT

---

## Key Concepts To Remember

Routing decides WHERE the packet goes.

NAT decides WHICH ADDRESS is used.

ARP decides WHICH MAC address receives the frame.

NAT changes addresses inside packets.

PAT uses logical ports to allow many devices to share one public IP address.

The NAT table tracks translations between private and public addresses.