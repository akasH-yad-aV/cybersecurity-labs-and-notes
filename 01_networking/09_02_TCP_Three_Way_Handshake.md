# TCP Three-Way Handshake

TCP is a connection-oriented protocol. This means a connection must be established between two devices before data transmission begins.

The connection is established using the Three-Way Handshake mechanism

## Why Handshake Is Needed

- To synchronize sequence numbers.
- To confirm both sides are ready to communicate.
- To establish initial parameters for reliable communication.

## The Three Steps

### 1 SYN (Client → Server)

The client sends a TCP segment with:
- SYN flag set
- Sequence number = X

This indicates the client wants to initiate a connection.

SYN consumes one sequence number.

---

### 2 SYN-ACK (Server → Client)

The server responds with:
- SYN flag set
- ACK flag set
- Sequence number = Y
- Acknowledgment number = X + 1

This means:
- The server acknowledges the client's SYN.
- The server also sends its own initial sequence number

SYN also consumes one sequence number on the server side.

---

### 3 ACK (Client → Server)

The client sends:
- ACK flag set
- Sequence number = X + 1
- Acknowledgment number = Y + 1

This acknowledges the server’s SYN.

After this step, the connection is established and data transfer can begin.
### Wireshark Capture – TCP Three-Way Handshake

The capture below shows the TCP connection establishment process.

<img width="797" height="40" alt="image" src="https://github.com/user-attachments/assets/71fa0523-6fd6-4c70-85c7-cf2fd9dd7b77" />
Observed sequence:

1. Client sends a segment with SYN flag set (Seq = X).
2. Server responds with SYN-ACK (Seq = Y, Ack = X + 1).
3. Client sends final ACK (Seq = X + 1, Ack = Y + 1).

This confirms:
- SYN consumes one sequence number.
- Both sides synchronize their initial sequence numbers.
- Connection is successfully established before data transmission begins


