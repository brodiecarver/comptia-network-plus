# Wireless Security

## Overview

Wireless networks transmit data through the air, making them vulnerable to unauthorized access and eavesdropping.

Wireless security provides:

- Authentication (who can connect)
- Encryption (protecting data)
- Access control (restricting access)

---

# Wireless Security Standards

## WEP (Wired Equivalent Privacy)

### Characteristics

- Original wireless security standard
- Uses RC4 encryption
- Considered insecure
- Can be cracked quickly

### Exam Note

WEP should never be used.

---

## WPA (Wi-Fi Protected Access)

### Characteristics

- Replacement for WEP
- Uses TKIP
- More secure than WEP
- Still considered outdated

### Exam Note

WPA is better than WEP but has largely been replaced.

---

## WPA2

### Characteristics

- Uses AES encryption
- Much stronger than WPA
- Long-time industry standard
- Still widely used today

### Exam Note

WPA2 remains secure for most environments.

---

## WPA3

### Characteristics

- Newest wireless security standard
- Strongest security currently available
- Improved authentication
- Improved protection against password attacks

### Exam Note

WPA3 is the most secure wireless standard.

---

# Encryption Technologies

## TKIP

### Stands For

Temporal Key Integrity Protocol

### Used With

- WPA

### Characteristics

- Improvement over WEP
- Older technology
- Largely obsolete

---

## AES

### Stands For

Advanced Encryption Standard

### Used With

- WPA2
- WPA3

### Characteristics

- Strong encryption
- Modern standard
- Preferred for secure networks

---

# Security Progression

```text
WEP  → RC4 → Broken
WPA  → TKIP → Old
WPA2 → AES  → Good
WPA3 → AES  → Best
```

---

# PSK (Pre-Shared Key)

## Definition

A shared wireless password used by all users.

### Example

SSID: HomeWiFi

Password:

MyPassword123

### Common Usage

- Home networks
- Small businesses

### Examples

- WPA2-PSK
- WPA3-PSK

---

# Enterprise Authentication

## Purpose

Provides individual user authentication instead of one shared password.

### Benefits

- Individual accounts
- Better security
- Easier user management
- Easy account removal

---

# RADIUS

## Definition

Remote Authentication Dial-In User Service

### Purpose

Authenticates users attempting to connect to a network.

### Authentication Process

```text
Laptop
   ↓
Access Point
   ↓
RADIUS Server
   ↓
Allow / Deny
```

### Exam Note

RADIUS verifies usernames and passwords.

---

# 802.1X

## Definition

Authentication framework used in enterprise wireless networks.

### Purpose

Requires users to authenticate before network access is granted.

### Common Pairing

```text
WPA2/WPA3 Enterprise
        ↓
      802.1X
        ↓
      RADIUS
        ↓
   Allow / Deny
```

### Exam Note

802.1X provides individual user authentication.

---

# Captive Portal

## Definition

A web page displayed before internet access is allowed.

### Common Locations

- Hotels
- Airports
- Cafes
- Shopping Centres

### Example Process

```text
Connect to Wi-Fi
        ↓
Open Browser
        ↓
Captive Portal Appears
        ↓
Accept Terms / Login
        ↓
Internet Access Granted
```

### Exam Note

Captive Portal = Web page before internet access.

---

# Guest Networks

## Purpose

Provide internet access while preventing access to internal resources.

### Users

- Visitors
- Contractors
- Customers

### Access

Allowed:

- Internet

Denied:

- Servers
- Printers
- Workstations
- Internal resources

### Exam Note

Guest Networks provide isolation.

---

# Key Exam Facts

## Home Wireless Security

```text
WPA2-PSK
or
WPA3-PSK
```

One shared password.

---

## Enterprise Wireless Security

```text
WPA2/WPA3 Enterprise
        ↓
      802.1X
        ↓
      RADIUS
```

Individual usernames and passwords.

---

## Public Wi-Fi

```text
Captive Portal
```

Web page appears before internet access.

---

## Guest Access

```text
Guest Network
```

Internet access without internal network access.

---

# Network+ Exam Shortcuts

## Security Ranking

```text
WPA3 > WPA2 > WPA > WEP
```

## Encryption Mapping

```text
WEP  → RC4
WPA  → TKIP
WPA2 → AES
WPA3 → AES
```

## Authentication Mapping

```text
PSK = Shared Password

802.1X + RADIUS = Individual User Authentication
```

## Access Control Mapping

```text
Captive Portal = Login / Terms Page

Guest Network = Isolation
```