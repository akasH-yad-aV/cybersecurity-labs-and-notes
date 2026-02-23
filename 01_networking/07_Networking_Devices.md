# Networking Devices

## Hub

**Layer:**  
Physical Layer (Layer 1)

**Main Function:**  
A hub is a basic networking device that connects multiple devices in a local network. It operates only at the physical level and does not understand frames or MAC addresses.

**How It Forwards Traffic:**  
When a hub receives electrical signals from one port, it simply repeats (broadcasts) those signals to all other ports. It does not inspect or filter traffic.

**Security Relevance:**  
- All traffic is broadcast to every connected device.
- Increases network congestion.
- Makes packet sniffing easier.
- Mostly obsolete and replaced by switches.

---

## Switch

**Layer:**  
Data Link Layer (Layer 2)

**Main Function:**  
A switch connects multiple devices within a local network and forwards frames based on MAC addresses.

**How It Forwards Traffic:**  
When a switch receives a frame, it checks the destination MAC address and forwards the frame only to the port associated with that MAC address.

If the MAC address is unknown, the switch floods the frame to all ports except the source port.

**MAC Table (CAM Table):**  
A switch maintains a MAC address table (also called CAM table) which stores:
- MAC address  
- Associated switch port  

The switch learns MAC addresses dynamically by observing incoming frames.

**Security Relevance:**  
- More secure and efficient than a hub.
- Limits unnecessary traffic.
- Supports port mirroring (SPAN) for monitoring.
- Can be targeted by MAC flooding attacks.

---

## Router

**Layer:**  
Network Layer (Layer 3)

**Main Function:**  
A router connects different networks and forwards packets based on destination IP addresses.

**How It Forwards Traffic:**  
When a router receives a frame, it removes the Layer 2 header and examines the IP packet inside. It checks the destination IP address and consults its routing table to determine the next hop.

If the destination IP belongs to the router itself, the packet is processed locally. Otherwise, the router forwards the packet toward the correct network.

After making the routing decision, the router creates a new frame with new source and destination MAC addresses for the next hop.

**Routing Table:**  
A router maintains a routing table which contains:
- Destination network  
- Subnet mask  
- Next hop IP address  
- Outgoing interface  

The routing table is used to determine the best path for packet forwarding.

**Security Relevance:**  
- Connects internal network to external networks.
- Can implement Access Control Lists (ACLs).
- Performs NAT (Network Address Translation).
- Acts as a boundary between internal and external networks.

---

## Firewall

**Layer:**  
Basic firewalls operate at Layer 3 (Network Layer) and Layer 4 (Transport Layer).  
Advanced firewalls (such as Web Application Firewalls) operate at Layer 7.

**Main Function:**  
A firewall is a network security system that acts as a barrier between a trusted internal network and an untrusted external network (such as the Internet).

It allows or blocks traffic based on predefined security rules.

**How It Filters Traffic:**  
A firewall inspects:
- Source IP address  
- Destination IP address  
- Protocol (TCP, UDP, ICMP)  
- Source and destination port numbers  

Based on configured rules, it can:
- Allow traffic  
- Block traffic  
- Log traffic  

Some firewalls also monitor outgoing traffic and block connections to malicious destinations.

**Types:**  
- Packet-filtering firewall  
- Stateful firewall  
- Application-layer firewall (WAF)

**Security Relevance:**  
- Protects internal network from external threats.
- Controls inbound and outbound traffic.
- Logs suspicious activity.
- Enforces security policies.

---

## Access Point (AP)

**Layer:**  
Primarily operates at Layer 2 (Data Link Layer).

**Main Function:**  
An Access Point connects wireless devices to a wired network. It acts as a bridge between wireless clients and the Ethernet network.

**How It Works:**  
- Receives wireless signals from devices.
- Converts them into Ethernet frames.
- Forwards them into the wired network.
- Does not perform routing between different networks.

**Clarification:**  
In many home networks, a single device commonly referred to as a "router" actually combines:
- Router  
- Switch  
- Access Point  
- Sometimes modem  

However, an Access Point alone does not perform routing.

**Security Relevance:**  
- Weak Wi-Fi encryption can allow unauthorized access.
- Misconfigured AP can expose the internal network.
- Can be entry point for attacks.

---

## Modem

**Layer:**  
Primarily operates at the Physical Layer (Layer 1).

**Main Function:**  
A modem (Modulator-Demodulator) connects a local network to the Internet through the Internet Service Provider (ISP).

It converts signals between the ISP transmission format and the local network format.

**How It Works:**  
- Converts incoming ISP signals into digital data usable by the router.
- Converts outgoing digital data into a format suitable for ISP transmission.

**Clarification:**  
A modem does not perform routing.  
In many home setups, the modem is combined with a router into one device.

**Security Relevance:**  
- Entry point to the Internet.
- Misconfiguration can expose the network.

---

## Network Interface Card (NIC)

**Layer:**  
Operates at Layer 1 (Physical Layer) and Layer 2 (Data Link Layer).

**Main Function:**  
A Network Interface Card (NIC) allows a device to connect to a network.

It is responsible for:
- Converting digital data into electrical or wireless signals.
- Receiving signals and converting them back into digital data.

**MAC Address:**  
Each NIC contains a unique MAC address assigned by the manufacturer. This MAC address is used for frame delivery within a local network.

**Types:**  
- Wired NIC (Ethernet)
- Wireless NIC (Wi-Fi)

**Security Relevance:**  
- MAC address spoofing is possible.
- Network access control may use MAC filtering.

---

## Default Gateway

A default gateway is the device (usually a router) that forwards traffic from a local network to other networks.

When a device wants to send data:
- It checks the destination IP address.
- Using the subnet mask, it determines whether the destination is inside the same network.
- If the destination is in the same subnet, the device sends the packet directly.
- If the destination is outside the subnet, the device sends the packet to the default gateway.

The default gateway then forwards the packet toward the correct external network.
