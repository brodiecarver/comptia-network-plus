# CompTIA Network+ - VPNs

## What is a VPN?

VPN stands for Virtual Private Network.

A VPN creates an encrypted tunnel across an untrusted network.

Usually:

Internet

Purpose:

- Privacy
- Confidentiality
- Secure Remote Access

---

## Remote Access VPN

Connects:

User → Network

Example:

Home Laptop
↓
VPN
↓
Company Network

Used by:

- Remote workers
- Travelling employees

---

## Site-to-Site VPN

Connects:

Network → Network

Example:

Melbourne Office
↓
VPN Tunnel
↓
Sydney Office

No VPN client required on end devices.

---

## Full Tunnel

All traffic passes through the VPN.

Advantages:

- Most secure

Disadvantages:

- More bandwidth usage

---

## Split Tunnel

Only company traffic uses the VPN.

Internet traffic goes directly to the internet.

Advantages:

- Faster
- Less bandwidth

Disadvantages:

- Less secure

---

## IPSec

Internet Protocol Security

Provides:

- Encryption
- Authentication
- Integrity

Most common VPN security protocol.

### Transport Mode

Encrypts payload only.

Original IP header remains visible.

### Tunnel Mode

Encrypts entire original packet.

Most common for site-to-site VPNs.

---

## SSL/TLS VPN

Uses HTTPS encryption.

Often browser-based.

Common clues:

- Portal
- Web Access
- HTTPS

Advantages:

- Easy to use
- No dedicated VPN client required

---

## VPN Benefits

- Secure communication
- Encryption
- Remote access
- Privacy

---

## Key Exam Points

VPN = Encrypted Tunnel

Remote Access VPN = User to Network

Site-to-Site VPN = Network to Network

IPSec = Encryption, Authentication, Integrity

Transport Mode = Payload Only

Tunnel Mode = Entire Packet

SSL/TLS VPN = Browser-Based VPN

Full Tunnel = All Traffic

Split Tunnel = Company Traffic Only
