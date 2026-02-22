# ARP (Address Resolution Protocol)

ARP stands for Address Resolution Protocol. It is used to map an IP address to a MAC address within a local network.

ARP operates at the Data Link Layer (Layer 2) and is used when a device needs to find the MAC address associated with a known IP address.

In a LAN, data is delivered using MAC addresses. However, devices usually know the destination IP address first. ARP solves this by resolving (mapping) the IP address to its corresponding MAC address.

---

## Why ARP is Needed

IP addresses identify devices logically, but actual frame delivery inside a LAN happens using MAC addresses.

Since IP addresses can change (for example, when assigned dynamically via DHCP), ARP dynamically maps the current IP address to the correct MAC address.

Without ARP, devices would not know where to send frames within a local network.

---

## ARP Request

When a device wants to find the MAC address of an IP in the same LAN:

1. It checks its ARP table.
2. If no entry exists, it sends an ARP request.

The ARP request is broadcast to all devices in the LAN.

It basically asks:
"Who has this IP address? Tell me your MAC address"

Since the sender does not know the destination device yet, it uses broadcast.

---

## ARP Reply

The device that owns the requested IP address responds with its MAC address.

The ARP reply is unicast, meaning it is sent directly back to the requesting device.

It basically responds:
"This IP address is associated with this MAC address."

---

## ARP Table

Each device maintains an ARP table (also called ARP cache).

The ARP table contains mappings of:
- IP address
- Corresponding MAC address

This table is used to avoid sending repeated broadcast requests.

---

## ARP Spoofing

ARP can be spoofed because it does not verify the authenticity of reply.

An attacker can send a forged ARP reply that maps a legitimate IP address to the attackers MAC address.

Since ARP does not authenticate responses, the receiving device updates its ARP table and treats the forged reply as legitimate.

This can allow an attacker to perform a Man-in-the-Middle (MITM) attack inside a local network.
