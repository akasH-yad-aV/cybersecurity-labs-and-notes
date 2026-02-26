# DHCP (Dynamic Host Configuration Protocol)

DHCP stands for Dynamic Host Configuration Protocol.

It is an application layer protocol used to automatically assign IP configuration to devices in a network.

DHCP works over UDP.

- Server port: 67  
- Client port: 68  

---

## Why DHCP Exists

Without DHCP, every device would need to be manually configured with:

- IP address
- Subnet mask
- Default gateway
- DNS server

In large networks, manual configuration is inefficient and error-prone.

DHCP automates this process.

---

## Static vs Dynamic IP

Static IP:
- Manually assigned
- Does not change
- Used for servers or critical devices

Dynamic IP:
- Automatically assigned by DHCP server
- Temporary (leased)
- Used for most client devices

---

## DORA Process

DHCP uses a four-step process known as DORA:

### 1️ Discover
- Client sends DHCP Discover message.
- Source IP: 0.0.0.0
- Destination IP: 255.255.255.255 (broadcast)
- Client does not yet have an IP address.

### 2️ Offer
- DHCP server responds with DHCP Offer.
- Contains proposed IP address and configuration details.

### 3️ Request
- Client broadcasts DHCP Request.
- Indicates it accepts the offered IP address.

### 4️ Acknowledge (ACK)
- Server sends DHCP ACK.
- Lease is granted.
- Client can now use the assigned IP.

---

## Why Broadcast Is Used

At the beginning:

- Client has no IP address.
- It does not know the DHCP server’s IP.
- Therefore, it must broadcast.

This is why 255.255.255.255 is used.

---

## Lease Time

IP addresses are not permanent.

They are assigned for a specific lease duration.

After lease expires:
- Client must renew.
- If not renewed, IP becomes available again.

---

## Lease Renewal (T1 and T2)

T1 (50% of lease time):
- Client attempts to renew directly with server (unicast).

T2 (87.5% of lease time):
- If renewal fails, client broadcasts request to any DHCP server.

If no response:
- Lease expires.
- Client must restart DORA process.

---

## DHCP Relay

If client and DHCP server are on different networks:

- Router can act as DHCP relay.
- It forwards DHCP messages to server.
- Enables centralized DHCP management.

---

## Security Issues

### Rogue DHCP
Unauthorized DHCP server in network.
Can assign incorrect gateway or DNS server.
Can redirect traffic (man-in-the-middle risk).

### DHCP Starvation
Attacker floods DHCP server with fake requests.
Exhausts available IP pool.
Legitimate users cannot obtain IP.

---

## SOC Perspective

Indicators of DHCP abuse:
- Excessive DHCP requests
- Multiple IP allocations to single MAC
- Unknown DHCP server responses
- Rapid lease exhaustion
