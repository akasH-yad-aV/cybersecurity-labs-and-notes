# SSH (Secure Shell)

SSH is a protocol used for **secure remote access and command execution** on another system over a network.

It allows users to securely log into remote machines, execute commands, and transfer files.

| Property | Value |
|---|---|
| Default Port | 22 |
| Transport Protocol | TCP |
| Encryption | Yes |

SSH replaces insecure protocols like **Telnet**.

---

# SSH Packet-Level Connection Flow

SSH communication begins with a **TCP connection** followed by encryption negotiation and authentication.

---

# Step 1 — TCP Handshake

Client initiates connection to SSH server.

```
Client → Server
SYN
```

Server acknowledges.

```
Server → Client
SYN-ACK
```

Client confirms.

```
Client → Server
ACK
```

TCP connection is now established on **port 22**.

---

# Step 2 — Protocol Version Exchange

Both sides exchange SSH version information.

Example packets:

Client:

```
SSH-2.0-OpenSSH_9.0
```

Server:

```
SSH-2.0-OpenSSH_8.4
```

This identifies the SSH implementation and version.

---

# Step 3 — Key Exchange

Client and server negotiate encryption algorithms.

Algorithms negotiated may include:

- Key exchange algorithm
- Encryption algorithm
- Message authentication algorithm

Example:

```
Key Exchange: diffie-hellman-group14-sha256
Encryption: aes256-ctr
MAC: hmac-sha2-256
```

Using Diffie-Hellman, both sides create a **shared session key**.

From this point onward, communication becomes encrypted.

---

# Step 4 — Server Authentication

The server sends its **public host key** to the client.

The client verifies it against known hosts.

Stored in:

```
~/.ssh/known_hosts
```

If the key matches, the connection continues.

If it does not match, SSH warns about a possible **man-in-the-middle attack**.

---

# Step 5 — User Authentication

Client authenticates using one of several methods.

### Password Authentication

User enters password.

```
username + password
```

Credentials are encrypted during transmission.

---

### Public Key Authentication

Client proves identity using an SSH key pair.

Files involved:

```
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

Server stores authorized keys in:

```
~/.ssh/authorized_keys
```

Public key authentication is more secure than passwords.

---

# Step 6 — Encrypted Session

Once authentication succeeds, an encrypted session begins.

User can now execute commands remotely.

Example command:

```bash
ssh user@192.168.1.10
```

Example session:

```
user@server:~$ ls
Documents
Downloads
scripts
```

All communication is encrypted.

---

# SSH File Transfer

SSH also supports secure file transfer.

### SCP

Secure copy.

Example:

```bash
scp file.txt user@192.168.1.10:/home/user/
```

---

### SFTP

Secure file transfer protocol over SSH.

Example:

```bash
sftp user@192.168.1.10
```

---

# Security Benefits of SSH

SSH provides several security protections.

- Encryption of all traffic
- Secure authentication
- Protection against credential sniffing
- Integrity checking of transmitted data

---

# Common Security Risks

Despite being secure, SSH can still be targeted.

Examples:

- SSH brute force attacks
- Weak passwords
- Exposed SSH services on the internet
- Misconfigured SSH keys

Example attack pattern:

Many failed login attempts in logs:

```
Failed password for root from 192.168.1.50
```

This may indicate a brute-force attack.

---

# Summary

SSH is a secure protocol used for remote administration and encrypted communication.

Unlike older protocols such as Telnet, SSH encrypts all transmitted data, protecting credentials and commands from interception.
