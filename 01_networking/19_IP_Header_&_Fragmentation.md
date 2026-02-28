# IP Header and Fragmentation

IP (Internet Protocol) operates at the Network Layer (Layer 3).

It is responsible for logical addressing and packet forwarding across networks.

---

## Basic IP Header Fields

Important fields in IPv4 header:

- Version → IP version (IPv4 or IPv6)
- IHL (Internet Header Length)
- Total Length → Entire packet size
- Identification → Used for fragmentation tracking
- Flags → Control fragmentation (DF, MF)
- Fragment Offset → Position of fragment in original packet
- TTL (Time To Live)
- Protocol → Indicates next layer (TCP = 6, UDP = 17, ICMP = 1)
- Header Checksum
- Source IP Address
- Destination IP Address

---

## TTL (Time To Live)

TTL prevents packets from looping infinitely.

Each router:
- Decrements TTL by 1
- If TTL becomes 0 → packet is dropped
- Router sends ICMP Time Exceeded (Type 11)

TTL is used by traceroute.

---

## What Is MTU?

MTU (Maximum Transmission Unit) is the maximum packet size that can be transmitted on a network interface.

Example:
Ethernet MTU = 1500 bytes.

If a packet is larger than MTU:
- It must be fragmented
- Or dropped if DF flag is set

---

## IP Fragmentation

Fragmentation happens when:

- Packet size > MTU
- DF (Don't Fragment) flag is NOT set

Routers can fragment packets.

Reassembly happens ONLY at the destination host.

---

## Fragmentation Fields

### Identification
Used to group fragments belonging to the same original packet.

### Flags
- DF (Don't Fragment)
- MF (More Fragments)

MF = 1 → More fragments coming  
MF = 0 → Last fragment

### Fragment Offset
Indicates the position of fragment data in original packet.

Offset is measured in 8-byte units.

---

## What Happens If a Fragment Is Lost?

If any fragment is lost:

- Reassembly fails.
- Entire original packet is discarded.
- No automatic ICMP is sent for fragment loss.
- Higher-layer protocol (like TCP) handles retransmission.

---

## Path MTU Discovery

If DF flag is set and packet exceeds MTU:

- Router drops packet.
- Sends ICMP Type 3 Code 4 (Fragmentation Needed).

Sender reduces packet size accordingly.

Modern networks prefer Path MTU Discovery over fragmentation.

---

## Why Fragmentation Is Inefficient

- Increases packet count
- Requires memory for reassembly
- If one fragment is lost → entire packet retransmitted
- Can be abused for security evasion
