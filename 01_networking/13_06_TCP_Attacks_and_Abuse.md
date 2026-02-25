# TCP Attacks and Abuse

Understanding TCP mechanisms helps in understanding certain attacks.

---

## SYN Flood Attack

SYN flood exploits the three-way handshake

Attacker sends multiple SYN packets but does not complete the handshake.

Server responds with SYN-ACK and allocates resources for each half-open connection.

If many half-open connections accumulate:

- Server backlog queue fills.
- Legitimate users cannot connect.

This attack abuses TCP’s connection-oriented nature.

---

## RST Injection

An attacker can send forged RST packets to terminate a connection abruptly.

If sequence numbers are guessed correctly, the connection can be disrupted.

---

## Detection Perspective

Indicators of SYN flood:

- High number of SYN packets
- Many half-open connection
- Repeated SYN-ACK retransmissions
- No corresponding ACKs

Understanding TCP behavior helps in detecting abnormal traffic patterns.
