# CompTIA Network+ - Firewalls

## What is a Firewall?

A firewall is a security device that monitors and controls network traffic based on security rules.

Purpose:

- Allow legitimate traffic
- Block unwanted traffic

Think of a firewall as a security guard at the entrance to a network.

---

## How Firewalls Work

Traffic arrives at the firewall.

The firewall compares the traffic against configured rules.

The firewall then:

- Allows the traffic
- Blocks the traffic

---

## Stateless Firewall

Makes decisions using individual packets only.

Checks:

- Source IP
- Destination IP
- Port Number

Does not remember previous traffic.

### Advantages

- Fast
- Simple

### Disadvantages

- Less secure

---

## Stateful Firewall

Tracks active connections.

Remembers:

- Established sessions
- Previous traffic

### Advantages

- More secure
- Better decision making

### Disadvantages

- Uses more resources

---

## Next Generation Firewall (NGFW)

Modern firewall with advanced security features.

Can inspect:

- Applications
- Users
- Content

Often includes:

- IDS
- IPS
- Malware protection

---

## Packet Filtering

Examines packet headers and makes decisions based on:

- Source IP
- Destination IP
- Port Number
- Protocol

---

## Application Filtering

Controls traffic based on applications.

Examples:

- Allow Microsoft Teams
- Block BitTorrent

---

## URL Filtering

Controls access to websites.

Examples:

- Allow business websites
- Block gambling websites
- Block social media

---

## DMZ

Demilitarized Zone

A separate network used to host public-facing services.

Examples:

- Web Servers
- Email Servers
- DNS Servers

Purpose:

If a public server is compromised, the internal network remains protected.

---

## Firewall Placement

Internet
↓
Firewall
↓
Internal Network

Common design:

Internet
↓
Firewall
├── Internal Network
└── DMZ

---

## Key Exam Points

Firewall = Permit or Block Traffic

Stateless = No Memory

Stateful = Tracks Connections

NGFW = Advanced Security Features

DMZ = Public-Facing Servers
