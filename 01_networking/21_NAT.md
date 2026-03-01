# NAT (Network Address Translation)

NAT is a technique used by routers to translate private IP addresses into public IP addresses.

It was introduced to solve IPv4 address exhaustion.

Private IP ranges are not routable on the Internet:

- 10.0.0.0/8
- 172.16.0.0 – 172.31.255.255
- 192.168.0.0/16

NAT allows devices using private IP addresses to communicate with external networks.

---

## Why NAT Exists

IPv4 provides limited address space (32-bit).

NAT allows multiple private devices to share one public IP address.

It conserves public IP addresses.

---

## Basic NAT Process

1. Internal device sends packet:
   - Source IP: Private IP
   - Destination IP: Public server

2. Router modifies:
   - Source IP → Public IP
   - Source Port → New unique port (in case of PAT)

3. Router stores mapping in NAT table.

4. Return traffic arrives at router.

5. Router checks NAT table and forwards packet to correct internal device.

---

## Types of NAT

###  Static NAT
One private IP ↔ One public IP  
Permanent mapping.  
Used for servers.

### 2 Dynamic NAT
Private IPs mapped from a pool of public IPs.  
Temporary mapping.

### 3 PAT (Port Address Translation)
Also called NAT Overload.

Multiple private IPs share one public IP.  
Router differentiates connections using port numbers.

This is commonly used in home routers.

---

## NAT Table

Router maintains a translation table:

| Private IP | Private Port | Public IP | Public Port |

This table allows router to forward return traffic correctly.

---

## NAT and Checksums

When NAT modifies:
- Source IP
- Source Port

It must recalculate:
- IP header checksum
- TCP/UDP checksum

---

## NAT and Security

NAT is not a security mechanism.

It was designed for address conservation.

However, it provides basic isolation because:
- Unsolicited inbound traffic is dropped.
- Only return traffic for established connections is allowed.

Proper security still requires firewall rules and inspection.

---

## NAT and IPv6

IPv6 has 128-bit address space.

Because of abundant addresses, NAT is generally not required in IPv6.

However, firewalling remains essential.
