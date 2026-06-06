# CompTIA Network+ - IDS & IPS

## IDS

Intrusion Detection System

Purpose:

- Detect threats
- Generate alerts

Does NOT block traffic.

Think:

Security Camera

---

## IPS

Intrusion Prevention System

Purpose:

- Detect threats
- Block threats

Think:

Security Guard

---

## IDS vs IPS

IDS

- Detect
- Alert

IPS

- Detect
- Block

---

## Passive vs Inline

IDS

Passive

Receives copies of traffic.

Does not sit directly in the traffic path.

IPS

Inline

Traffic passes through the IPS.

Can actively block attacks.

---

## NIDS

Network-based Intrusion Detection System

Monitors network traffic.

Examples:

- SPAN Port Monitoring
- Network Sensors

---

## NIPS

Network-based Intrusion Prevention System

Monitors and blocks network attacks.

Installed inline.

---

## HIDS

Host-based Intrusion Detection System

Installed on:

- Servers
- Workstations

Monitors the local device.

---

## HIPS

Host-based Intrusion Prevention System

Installed on:

- Servers
- Workstations

Can actively block malicious activity.

---

## Signature-Based Detection

Looks for known attack patterns.

Think:

Known Bad

Advantages:

- Accurate
- Low false positives

Disadvantages:

- Misses unknown threats

---

## Anomaly-Based Detection

Learns normal behaviour.

Detects unusual activity.

Think:

Strange Behaviour

Advantages:

- Detects unknown attacks

Disadvantages:

- Higher false positives

---

## False Positive

Alert generated.

No attack actually exists.

False alarm.

---

## False Negative

No alert generated.

Attack actually exists.

Most dangerous outcome.

---

## Key Exam Points

IDS = Detect

IPS = Prevent

HIDS = Host Detection

HIPS = Host Prevention

NIDS = Network Detection

NIPS = Network Prevention

Signature = Known Bad

Anomaly = Strange Behaviour

False Positive = False Alarm

False Negative = Missed Attack

IDS = Passive

IPS = Inline
