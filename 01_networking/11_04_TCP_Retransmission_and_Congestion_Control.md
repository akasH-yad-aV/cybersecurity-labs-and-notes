# TCP Retransmission and Congestion Control

TCP uses retransmission techniques to provide reliability.

---

## Loss Detection Mechanisms

### 1️ Timeout (Retransmission Timeout - RTO)

The sender will retransmit a segment if it doesnt receive an acknowledgment for a certain amount of time.

This approach is slower because it relies on the timer expiring

---

### 2️ Fast Retransmit

The receiver will detect gaps in sequence numbers if data is missing.

The sender will retransmit a segment if it receives three duplicate ACKs.

Fast retransmit is faster because it relies on ACK patterns rather than the timer expiring.

---

## Congestion Control (High-Level)

Congestion control ensures the sender doesnt flood the network.

It is not the same as flow control.

- Flow control is for protecting the receiver.
- Congestion control is for protecting the network

TCP uses network conditions to control its transmission rate with the following techniques:

- Slow Start
- Congestion Avoidance

This provides network stability in a large network such as the Internet
