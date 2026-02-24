# TCP Data Transfer and Flow Control

After the three-way handshake, both sides can start sending data. TCP provides reliable and ordered delivery using sequence numbers, acknowledgment numbers, and sliding window mechanism.

---

## Data Transfer in TCP

TCP is byte oriented, not packet-oriented.

Each byte in the data stream is assigned a sequence number.

If a sender transmits data starting from sequence number S and sends N bytes:

- Last byte = S + N - 1
- Receiver will acknowledge with ACK = S + N

The ACK number always represents the next byte expected

---

## Sliding Window Mechanism

TCP does not send one segment and wait for acknowledgment. Instead, it allows multiple bytes to be "in flight" before waiting.

The receiver advertises a window size which represents how many bytes it can currently accept.

### Formula:

Available send space = Advertised Window − Unacknowledged Bytes

The sender can continue transmitting data as long as:

Unacknowledged Bytes ≤ Window Size

When ACKs are received, the window "slides forward, allowing more data to be sent

---

## Flow Control

Flow control prevents the sender from overwhelming the receiver.

The receiver includes a Window Size field in every TCP segment

This value tells the sender how much buffer space is available.

If the window becomes zero:

- Sendr stops transmitting new data.
- Sender periodically sends a Zero Window Probe.
- When receiver frees buffer space, it sends a Window Update.
- Sender resumes transmission.

Flow control protects the receiver.
