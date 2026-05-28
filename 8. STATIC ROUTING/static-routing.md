# Static Routing - Network+ Notes

# What is Static Routing?

Static routing is when a human manually configures routes on a router.

Instead of routers learning routes automatically, the administrator tells the router:

> "To reach this network, send traffic to this next-hop router."

---

# Important Routing Logic

Routers DO NOT guess where packets should go.

A router MUST have:
- a directly connected route
OR
- a static/dynamic route

Otherwise:
- the packet is dropped.

---

# Routing Process Order

Very important:

1. Router checks routing table
2. Router finds matching route
3. Router determines next hop/interface
4. THEN ARP happens if needed
5. Frame forwarded

Important:
- Routing table lookup happens BEFORE ARP

---

# Directly Connected Networks

Routers automatically know networks attached to their own interfaces.

Example:

Router interface:
```plaintext
192.168.1.1/24