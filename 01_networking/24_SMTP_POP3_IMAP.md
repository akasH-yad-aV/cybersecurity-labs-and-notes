# SMTP, POP3, and IMAP (Email Protocols)

Email communication on the internet relies on different protocols for **sending** and **retrieving** messages.

- **SMTP** → Sending email
- **POP3** → Downloading email from server
- **IMAP** → Synchronizing email with server

All three operate over **TCP**.

---

# SMTP (Simple Mail Transfer Protocol)

SMTP is responsible for **sending emails from client to mail server and between mail servers**.

| Property | Value |
|---|---|
| Default Port | 25 |
| Submission Port | 587 |
| Secure Port | 465 |
| Transport | TCP |

SMTP is **text-based**, meaning commands are sent as readable text inside TCP packets.

---

# SMTP Packet-Level Flow

Example when a client sends an email.

### Step 1 — TCP Connection

Client initiates TCP connection to SMTP server.

```
Client → Server
SYN
Server → Client
SYN-ACK
Client → Server
ACK
```

Connection established on **TCP port 25 or 587**.

---

### Step 2 — Server Greeting

Server sends greeting banner.

```
220 mail.example.com ESMTP Postfix
```

Seen in Wireshark as **SMTP response packet**.

---

### Step 3 — Client Identification

Client identifies itself.

```
EHLO client.example.com
```

Server responds with supported features.

```
250-mail.example.com
250-AUTH LOGIN
250 STARTTLS
```

---

### Step 4 — Sender Declaration

Client specifies sender email.

```
MAIL FROM:<user@example.com>
```

Server responds:

```
250 OK
```

---

### Step 5 — Recipient Declaration

Client specifies recipient.

```
RCPT TO:<admin@example.com>
```

Server responds:

```
250 OK
```

---

### Step 6 — Message Transfer

Client begins message body.

```
DATA
```

Server replies:

```
354 End data with <CR><LF>.<CR><LF>
```

Client sends email content:

```
Subject: Test

Hello this is a test email.
.
```

The period (`.`) indicates the end of the message.

Server response:

```
250 Message accepted for delivery
```

---

### Step 7 — Connection Close

```
QUIT
```

Server responds:

```
221 Bye
```

TCP connection closes.

---

# POP3 (Post Office Protocol Version 3)

POP3 is used by clients to **retrieve emails from a mail server**.

| Property | Value |
|---|---|
| Default Port | 110 |
| Secure Port | 995 |
| Transport | TCP |

POP3 usually **downloads emails and removes them from the server**.

---

# POP3 Packet-Level Flow

### Step 1 — TCP Connection

Client connects to mail server.

```
Client → Server
TCP SYN
Server → Client
SYN-ACK
Client → Server
ACK
```

---

### Step 2 — Server Greeting

Server responds:

```
+OK POP3 server ready
```

---

### Step 3 — Authentication

Client sends username.

```
USER akash
```

Server replies:

```
+OK
```

Client sends password.

```
PASS password123
```

Server response:

```
+OK mailbox locked
```

Note: In plaintext POP3 this **password is visible in packet captures**.

---

### Step 4 — Retrieve Messages

Client lists messages.

```
LIST
```

Server replies with message list.

Client retrieves message.

```
RETR 1
```

Server sends email content.

---

### Step 5 — End Session

```
QUIT
```

Connection closes.

---

# IMAP (Internet Message Access Protocol)

IMAP allows clients to **access and manage emails stored on the server**.

Unlike POP3, emails remain on the server and are synchronized across devices.

| Property | Value |
|---|---|
| Default Port | 143 |
| Secure Port | 993 |
| Transport | TCP |

---

# IMAP Packet-Level Flow

### Step 1 — TCP Connection

Client initiates connection to server on port **143**.

Standard TCP handshake occurs.

---

### Step 2 — Server Greeting

Server responds:

```
* OK IMAP4 ready
```

---

### Step 3 — Authentication

Client sends login request.

```
A001 LOGIN akash password123
```

Server response:

```
A001 OK LOGIN completed
```

---

### Step 4 — Mailbox Selection

Client selects mailbox.

```
A002 SELECT INBOX
```

Server returns message metadata.

---

### Step 5 — Fetch Email

Client retrieves message.

```
A003 FETCH 1 BODY[]
```

Server sends email contents.

---

### Step 6 — Connection Close

```
A004 LOGOUT
```

Server terminates session.

---

# POP3 vs IMAP

| Feature | POP3 | IMAP |
|---|---|---|
| Email Storage | Local client | Server |
| Multi-device sync | No | Yes |
| Folder support | Limited | Full |
| Typical usage | Older clients | Modern email apps |

---

# Security Considerations

Unencrypted email protocols expose credentials and message content.

Packet capture example (plaintext):

```
USER akash
PASS password123
```

Secure variants protect traffic using TLS:

| Protocol | Secure Version | Port |
|---|---|---|
| SMTP | SMTPS / STARTTLS | 465 / 587 |
| POP3 | POP3S | 995 |
| IMAP | IMAPS | 993 |

Encryption prevents attackers from intercepting credentials or email content.
