# UDP (User Datagram Protocol) – Overview

UDP stands for User Datagram Protocol. It operates at Layer 4 (Transport Layer) of the OSI model.

UDP is a connectionless protocol, meaning it does not establish a connection before sending data.

---

## Key Characteristics

- Connectionless communication
- No handshake
- No reliability guarantee
- No retransmission mechanism
- No flow control
- No congestion control
- Faster than TCP (less overhead)

UDP simply sends data without ensuring delivery, order, or duplication protection.

---

## Why UDP Exists

In some applications, speed is more important than reliability.

For example:
- Real-time streaming
- Online gaming
- VoIP
- DNS queries

If a packet is lost, it is not retransmitted. The application must handle loss if needed.

---

## UDP Header Fields

UDP header is very small (8 bytes only).

It contains:

- Source Port
- Destination Port
- Length
- Checksum

Unlike TCP, UDP does not include:
- Sequence number
- Acknowledgment number
- Window size
- Flags

UDP is simple and lightweight.
