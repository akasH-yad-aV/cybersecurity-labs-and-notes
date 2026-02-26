# TCP vs UDP

Both TCP and UDP operate at the Transport Layer (Layer 4), but they serve different purposes.

---

## Key Differences

| Feature | TCP | UDP |
|----------|------|------|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Reliable (ACK, retransmission) | No reliability guarantee |
| Ordering | Ensures ordered delivery | No ordering guarantee |
| Flow Control | Yes (Window Size) | No |
| Congestion Control | Yes | No |
| Speed | Slower (more overhead) | Faster (minimal overhead) |
| Header Size | 20+ bytes | 8 bytes |

---

## When to Use TCP

TCP is preferred when complete and accurate data delivery is required.

Examples:
- Web browsing (HTTP/HTTPS)
- Email (SMTP)
- File transfer (FTP)
- Secure communication (TLS over TCP)

TCP ensures:
- No data loss
- Ordered delivery
- Error correction

---

## When to Use UDP

UDP is preferred when speed is more important than reliability.

Examples:
- Voice calls (VoIP)
- Video calls
- Live streaming
- Online gaming
- DNS queries

In these cases:
- Small packet loss is acceptable.
- Real-time performance is more important than perfect delivery.

---

## Important Concept

TCP handles reliability at the transport layer.

UDP leaves reliability (if needed) to the application layer.

This makes UDP lightweight and fast, while TCP is heavier but reliable.
