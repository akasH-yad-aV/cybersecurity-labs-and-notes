# NTP (Network Time Protocol)

Network Time Protocol (NTP) is used to synchronize the system clock of computers across a network.

Accurate time synchronization is important for:

- system logs
- authentication systems
- distributed systems
- security monitoring

| Property | Value |
|---|---|
| Default Port | 123 |
| Transport Protocol | UDP |

NTP allows systems to maintain consistent time by synchronizing with trusted time servers.

---

# Why Time Synchronization Matters

Many systems depend on accurate timestamps.

Examples:

- log correlation in security investigations
- authentication systems (Kerberos)
- distributed applications
- network monitoring tools

If system clocks are incorrect, logs from different systems may not match.

---

# NTP Architecture

NTP servers are organized in **stratum levels**.

### Stratum 0

Highly accurate time sources such as:

- atomic clocks
- GPS clocks

These devices do not connect directly to the network.

---

### Stratum 1

Servers directly connected to Stratum 0 devices.

These act as primary time servers.

---

### Stratum 2

Servers that synchronize from Stratum 1 servers.

Most public NTP servers belong to this level.

---

### Stratum 3 and Higher

Lower-level servers that synchronize from other NTP servers.

Each level increases the distance from the original time source.

---

# NTP Packet-Level Flow

NTP typically uses **UDP port 123**.

### Step 1 — Client Request

Client sends a time request to the NTP server.

```
Client → Server
UDP packet
Port: 123
```

This packet contains the client's timestamp.

---

### Step 2 — Server Response

Server responds with a packet containing timing information.

```
Server → Client
UDP packet
Port: 123
```

The response includes several timestamps used to calculate clock offset and network delay.

---

# NTP Timestamps

NTP packets contain four important timestamps:

| Timestamp | Description |
|---|---|
| T1 | Time request sent by client |
| T2 | Time request received by server |
| T3 | Time response sent by server |
| T4 | Time response received by client |

These values allow the client to calculate:

- network delay
- clock offset

The system clock is then adjusted accordingly.

---

# Example NTP Query

Example command to check time synchronization:

```bash
ntpq -p
```

Example output:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
time.google.com  .GOOG.           1 u   12   64  377   25.123   -0.234   0.102
```

---

# Observing NTP in Network Traffic

In Wireshark you can filter NTP packets using:

```
udp.port == 123
```

Typical traffic pattern:

```
Client → NTP request
Server → NTP response
```

Since UDP is used, there is **no connection handshake**.

---

# Security Risks

NTP has been abused in **reflection and amplification attacks**.

Attackers send small spoofed requests to NTP servers, which respond with much larger packets.

This causes a **DDoS amplification attack**.

Example attack pattern:

```
Attacker → NTP Server (spoofed request)
NTP Server → Victim (large response)
```

This can overwhelm the victim with traffic.

---

# Security Best Practices

To secure NTP services:

- restrict public NTP access
- disable unnecessary NTP commands
- configure firewall rules
- use trusted time servers

---

# Summary

NTP synchronizes system clocks across a network.

It operates over **UDP port 123** and allows systems to maintain accurate timestamps, which are critical for logging, authentication, and network operations.
