# Ports and Sockets

## Port

A port is a numerical value assigned to a process or application running on a device.

We need port numbers because multiple applications and services run on the same device. The port number helps the operating system identify which application the incoming data is meant for.

In simple terms:
- IP address identifies the device.
- Port number identifies the specific application or service on that device.

---

## Port Range

Ports are 16-bit numbers, ranging from 0 to 65535.

They are divided into three categories:

- **0–1023 (Well-known ports):**  
  Reserved for well-known services like HTTP, HTTPS, SMTP, SSH, FTP, etc.

- **1024–49151 (Registered ports):**  
  Assigned to specific services or applications but can also be used by user processes.

- **49152–65535 (Dynamic or Ephemeral ports):**  
  Used temporarily by client applications when initiating connections.

---

## Socket

A socket is a combination of an IP address and a port number.

It is usually written in the format:

<IP address>:<Port number>

Example:
192.168.1.195:80

This means the device with IP 192.168.1.195 is running a service on port 80 (HTTP).

A socket helps uniquely identify a communication endpoint.

In real communication, a full TCP connection is identified by:
- Source IP
- Source Port
- Destination IP
- Destination Port
- Protocol (TCP or UDP)

This combination uniquely identifies a session.

---

## Practical Example

When we type a domain like amazon.com in a browser:

- The destination port is usually 443 (HTTPS).
- The browser uses a random ephemeral port as the source port.
- The operating system keeps track of the session using the combination of source IP, source port, destination IP, and destination port.

This allows multiple connections to the same website at the same time without confusion.
