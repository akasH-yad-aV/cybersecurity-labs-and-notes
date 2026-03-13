# TLS and SSL

Transport Layer Security (TLS) and Secure Sockets Layer (SSL) are cryptographic protocols used to secure communication over a network.

They provide:

- Encryption
- Data integrity
- Authentication

TLS is the modern replacement for SSL.

| Property | Value |
|---|---|
| Common Usage | HTTPS, FTPS, SMTPS |
| Transport | TCP |
| Example Port | 443 (HTTPS) |

Most secure web communication today uses **TLS**.

---

# SSL vs TLS

SSL is the older protocol and is now deprecated.

| Protocol | Status |
|---|---|
| SSL 2.0 | Deprecated |
| SSL 3.0 | Deprecated |
| TLS 1.0 | Deprecated |
| TLS 1.1 | Deprecated |
| TLS 1.2 | Widely used |
| TLS 1.3 | Modern standard |

Modern systems use **TLS 1.2 or TLS 1.3**.

---

# Why TLS Is Needed

Without encryption, attackers could intercept traffic.

Example insecure communication:

```
Client → Server
GET /login
username=admin
password=123
```

Anyone monitoring the network could read these credentials.

TLS encrypts the communication channel to prevent this.

---

# TLS Packet-Level Flow (Handshake)

Before encrypted communication begins, TLS performs a **handshake process**.

---

# Step 1 — TCP Connection

TLS runs on top of TCP.

Client initiates connection.

```
Client → Server
SYN
```

Server responds.

```
Server → Client
SYN-ACK
```

Client confirms.

```
Client → Server
ACK
```

TCP connection established.

---

# Step 2 — Client Hello

Client sends a **ClientHello** message.

This packet contains:

- supported TLS versions
- supported cipher suites
- random number
- supported compression methods

Example:

```
ClientHello
TLS Version: TLS 1.3
Cipher Suites: TLS_AES_128_GCM_SHA256
```

---

# Step 3 — Server Hello

Server selects the encryption parameters.

Server responds with:

```
ServerHello
```

Includes:

- chosen cipher suite
- server random value
- TLS version

---

# Step 4 — Certificate Exchange

Server sends its **digital certificate**.

The certificate contains:

- server public key
- domain name
- certificate authority signature

Example:

```
Certificate: www.example.com
Issued by: DigiCert
```

Client verifies the certificate using trusted Certificate Authorities (CA).

---

# Step 5 — Key Exchange

Client and server generate a **shared session key**.

Common key exchange methods:

- Diffie-Hellman
- Elliptic Curve Diffie-Hellman (ECDHE)

This session key will encrypt the communication.

---

# Step 6 — Finished Messages

Both sides send a **Finished message** confirming handshake success.

After this step:

```
Encrypted communication begins
```

---

# Encrypted Data Transmission

Once the handshake completes, all application data becomes encrypted.

Example:

```
Client → Server
Encrypted HTTP Request
```

Example HTTPS request:

```
GET /index.html HTTP/1.1
Host: example.com
```

But the content appears encrypted in packet captures.

---

# Observing TLS in Network Traffic

In Wireshark you may see packets such as:

```
Client Hello
Server Hello
Certificate
Change Cipher Spec
Encrypted Application Data
```

Wireshark filter:

```
tls
```

Common TLS traffic appears on **port 443**.

---

# Security Benefits

TLS protects communication by providing:

- Confidentiality (encryption)
- Integrity (data cannot be altered)
- Authentication (server identity verification)

---

# TLS in Real Protocols

Many protocols use TLS for secure communication.

Examples:

| Protocol | Secure Version |
|---|---|
| HTTP | HTTPS |
| FTP | FTPS |
| SMTP | SMTPS |
| IMAP | IMAPS |
| POP3 | POP3S |

---

# Security Risks

Improper TLS configuration can lead to vulnerabilities.

Examples:

- weak cipher suites
- expired certificates
- outdated TLS versions

Attack example:

```
Man-in-the-middle attack
```

If certificate validation fails, attackers may intercept traffic.

---

# Summary

TLS is the modern protocol used to secure communication across networks.

It establishes encryption through a handshake process and protects data from interception or tampering.
