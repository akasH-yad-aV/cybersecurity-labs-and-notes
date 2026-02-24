# TCP Connection Termination

TCP uses a four-way handshake to close a connection gracefully.

---

## Graceful Termination (FIN)

When one side finishes sending data:

1️ It sends a segment with FIN flag set.
2️ The other side acknowledges it (ACK).
3️ When ready, the second side sends its own FIN.
4️ The first side acknowledges it.

FIN consumes one sequence number.

This process allows both sides to close independently (half-close supported).

---

## TIME_WAIT State

After sending the final ACK, one side enters TIME_WAIT.

This ensures:

- Delayed packets do not interfere with future connections.
- The final ACK is not lost.

---

## Abrupt Termination (RST)

If a connection must be terminated immediately:

- RST flag is used.
- No graceful shutdown.
- No TIME_WAIT.

RST is used when:
- Invalid segments are received.
- Application forcefully closes connection.
