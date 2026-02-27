# ICMP (Internet Control Message Protocol)

ICMP stands for Internet Control Message Protocol.

It operates at the Network Layer (Layer 3) and is carried inside IP packets.

ICMP is not a transport protocol like TCP or UDP.  
It is a support protocol used by IP for error reporting and diagnostics.

---

## Why ICMP Exists

IP is connectionless and unreliable.

If a packet cannot be delivered, IP itself does not provide feedback.

ICMP is used to report network-level problems back to the sender.

Without ICMP, devices would not know why packet delivery failed.

---

## ICMP Message Structure

An ICMP message contains:

- Type
- Code
- Checksum
- Additional data
- Portion of the original IP packet (for reference)

Type indicates the category of message.  
Code provides more specific details.

---

## Important ICMP Message Types

### 1️⃣ Echo Request (Type 8)

- Used by ping.
- Sent to check if a host is reachable.

### 2️⃣ Echo Reply (Type 0)

- Response to Echo Request.
- Confirms the host is reachable.

---

### 3️⃣ Destination Unreachable (Type 3)

Common codes:

- Code 0 → Network Unreachable  
- Code 1 → Host Unreachable  
- Code 3 → Port Unreachable  
- Code 4 → Fragmentation Needed (DF set)

Used when a packet cannot reach its destination.

---

### 4️⃣ Time Exceeded (Type 11)

- Code 0 → TTL expired in transit

Occurs when a router decrements TTL to zero and drops the packet.

This message is used by traceroute.

---

## How Ping Works

1. Host sends ICMP Echo Request.
2. Destination replies with ICMP Echo Reply.
3. Round Trip Time (RTT) is calculated.

Ping does not use TCP or UDP.

---

## How Traceroute Works

Traceroute manipulates TTL values.

1. Packet sent with TTL = 1.
2. First router decrements TTL to 0.
3. Router sends ICMP Time Exceeded.

TTL is incremented step-by-step to discover each hop.

When packet reaches final destination:
- If UDP is used, destination replies with ICMP Port Unreachable.
- This indicates the trace is complete.

---

## Path MTU Discovery

If a packet is larger than the outgoing interface MTU and the DF (Don't Fragment) flag is set:

- Router drops the packet.
- Sends ICMP Type 3 Code 4 (Fragmentation Needed).

This allows the sender to reduce packet size.

---

## Security Perspective

ICMP can be abused for:

- Network reconnaissance (ping sweep)
- ICMP flood attacks
- ICMP tunneling (data exfiltration)

However, completely blocking ICMP is not recommended because:

- It breaks diagnostics.
- It breaks Path MTU Discovery.
- It affects proper network behavior.

---

## SOC Perspective

Indicators of suspicious ICMP activity:

- High volume of Echo Requests (possible scanning)
- Large ICMP payload sizes
- Repeated Destination Unreachable messages
- ICMP traffic to unusual external servers
