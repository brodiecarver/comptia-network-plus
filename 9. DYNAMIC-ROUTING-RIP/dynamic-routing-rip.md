# Dynamic Routing - Network+ Notes

# What is Dynamic Routing?

Dynamic routing is when routers automatically learn routes from each other.

Instead of manually configuring routes, routers exchange routing information using routing protocols.

Example:
- Router1 advertises networks
- Router2 learns those networks automatically
- Routes are added to the routing table dynamically

---

# Static Routing vs Dynamic Routing

## Static Routing
- Human manually adds routes
- Uses `ip route`
- Good for small/simple networks
- Does not automatically adapt to failures

## Dynamic Routing
- Routers learn routes automatically
- Uses routing protocols
- Better for large/enterprise networks
- Automatically adapts to topology changes

---

# Important Dynamic Routing Logic

Dynamic routing does NOT replace routing tables.

Routers still:
1. Check routing table
2. Choose next hop/interface
3. THEN ARP if needed
4. Forward packet

Important:
- Dynamic routing only changes HOW routes get INTO the routing table

The forwarding process itself does NOT change.

---

# Routing Advertisements

Routers using dynamic routing send:
> routing advertisements

Example:
```plaintext
"I can reach 192.168.2.0/24"