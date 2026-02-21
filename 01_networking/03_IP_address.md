# IP Addressing

An IP address is a unique logical address assigned to every device connected to a network. Its main purpose is to identify a device and provide its logical location so data can be delivered correctly across networks.

An IP address performs two main functions:
- Identifying a device on a network
- Providing its logical location for routing over the Internet

---

## IPv4

IPv4 addresses are 32 bits long and are written as four decimal numbers separated by dot. Each of these numbers is called an octet.

Example:
192.168.1.1

Each octet ranges from 0 to 255.

---

## IPv6

IPv6 addresses are 128 bits long and are written as eight groups of four hexadecimal digits separated by colons.

Example:
2001:0db8:85a3:0000:0000:8a2e:0370:7334

IPv6 was introduced to overcome the address limitation problem of IPv4 and to support the growing number of internet-connected devices.

---

## Public IP Address

A public IP address is a globally unique address assigned by an Internet Service Provider (ISP). It allows devices or networks to communicate over the Internet.

Public IP addresses:
- Are globally unique
- Are routable on the Internet
- Allow access to websites and online service

Usually, the router in a home network is assigned the public IP address by the ISP.

---

## Private IP Address

A private IP address is used within a local network and is not visible or directly accessible on the Internet.

Private IP addresses:
- Are assigned manually (static) or automatically using DHCP
- Are not routable on the public Internet
- Can be reused across different networks without conflict
- Are assigned to devices such as computers, printers, smartphones, CCTV cameras, etc

Most devices inside a home or office network are assigned private IP addresses.

---

## NAT (Network Address Translation)

When a device with a private IP address wants to access a resource on the Internet, the router replaces (substitutes) the private IP address with its own public IP address.

This process is called Network Address Translation (NAT).

In simple terms NAT converts private IP addresses into a public IP address so that devices inside a local network can communicate with external networks or the Internet.
