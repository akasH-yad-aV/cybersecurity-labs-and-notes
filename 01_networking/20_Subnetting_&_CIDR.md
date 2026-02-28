# Subnetting and CIDR

Subnetting is the process of dividing a larger IP network into smaller logical networks by borrowing bits from the host portion of the address.

It is used for efficient IP allocation, segmentation, and reducing broadcast domains.

---

## IP Address Structure

An IPv4 address consists of 32 bits.

It is divided into:

- Network portion
- Host portion

The subnet mask (or prefix length) determines how many bits belong to the network and how many belong to hosts.

---

## Subnet Mask and Prefix

Prefix notation example:

192.168.1.0/24

/24 means:
- 24 bits are network bits
- 8 bits are host bits

Since total bits = 32:

Host bits = 32 - 24 = 8

Total addresses = 2^8 = 256  
Usable hosts = 256 - 2 = 254  

The "-2" accounts for:
- Network address
- Broadcast address

---

## Network and Broadcast Address

For every subnet:

- First address = Network address
- Last address = Broadcast address
- Usable range = Between them

Example:

192.168.1.0/26

/26 → 6 host bits  
2^6 = 64 addresses  

Subnets increment by 64:

- 192.168.1.0 – 63
- 192.168.1.64 – 127
- 192.168.1.128 – 191
- 192.168.1.192 – 255

For 192.168.1.0/26:

Network address: 192.168.1.0  
Broadcast address: 192.168.1.63  
Usable range: 192.168.1.1 – 192.168.1.62  

---

## Borrowing Bits (Creating Subnets)

If a network is:

192.168.1.0/24

Host bits = 8

If we change to /26:

Network bits increase to 26  
Host bits decrease to 6  

Borrowed bits = 2  

Number of subnets created = 2^2 = 4  

More network bits → More subnets → Fewer hosts per subnet  

---

## CIDR (Classless Inter-Domain Routing)

CIDR allows flexible prefix lengths instead of fixed classful boundaries (Class A, B, C).

Instead of assigning large blocks like /16 unnecessarily, CIDR allows:

- /23
- /26
- /27
- etc.

Example:

If organization needs 300 hosts:

Minimum required addresses = 300 + 2 = 302  
2^9 = 512  

Host bits = 9  
Prefix = 32 - 9 = /23  

CIDR allows efficient allocation without wasting large address blocks.

---

## How Devices Decide Local vs Remote

A device checks if destination IP is in same subnet using subnet mask.

If destination network = local network:
- Device sends ARP for destination
- Communication happens directly

If destination network ≠ local network:
- Device sends packet to default gateway
- Device ARPs for gateway’s MAC address

Default gateway must always be in same subnet as host.

---

## Why Subnetting Is Important

- Reduces broadcast domain size
- Improves performance
- Enables network segmentation
- Enhances security
- Efficient IP allocation
