# FTP, FTPS, and SFTP

File transfer protocols are used to transfer files between a client and a server over a network.

FTP is the traditional protocol used for file transfers, while FTPS and SFTP provide secure alternatives.

---

# FTP (File Transfer Protocol)

FTP is a standard protocol used to transfer files between systems over a network.

- **Port:** 21
- **Transport Protocol:** TCP
- **Encryption:** None (plaintext)

FTP follows a **client-server architecture** where a client connects to an FTP server to upload or download files.

Example FTP connection:

```bash
ftp 192.168.1.10
```

---

# How FTP Works

FTP uses **two separate TCP connections**.

## Control Connection

Used to send commands from client to server.

```
Client → Server
TCP Port 21
```

Commands such as authentication and file operations are sent through this channel.

Common commands:

```
USER
PASS
LIST
RETR
STOR
QUIT
```

---

## Data Connection

Used for transferring files or directory listings.

FTP supports two modes:

### Active Mode

Server initiates the data connection back to the client.

```
Server → Client
```

This can cause problems with firewalls.

---

### Passive Mode

Client initiates the data connection.

```
Client → Server
```

Passive mode is commonly used because it works better with NAT and firewalls.

---

# FTP Security Issues

FTP is considered insecure because:

- Credentials are transmitted in plaintext
- File contents are not encrypted
- Attackers can capture usernames and passwords using packet sniffing

Example captured credentials in Wireshark:

```
USER admin
PASS password123
```

This is why FTP should not be used on untrusted networks.

---

# FTPS (FTP Secure)

FTPS is FTP with **TLS/SSL encryption**.

It adds encryption to protect authentication and data transfers.

- **Port:** 21 (explicit FTPS) or 990 (implicit FTPS)
- **Transport Protocol:** TCP
- **Encryption:** TLS/SSL

FTPS maintains the same architecture as FTP but encrypts communication.

This prevents attackers from reading credentials and transferred files.

---

# SFTP (SSH File Transfer Protocol)

SFTP is a completely different protocol from FTP.

It runs over **SSH** and provides secure file transfer functionality.

- **Port:** 22
- **Transport Protocol:** TCP
- **Encryption:** SSH encryption

SFTP uses a **single secure connection** for both commands and file transfer.

Example connection:

```bash
sftp user@192.168.1.10
```

---

# Differences Between FTP, FTPS, and SFTP

| Protocol | Port | Encryption | Connections |
|--------|------|------------|------------|
| FTP | 21 | None | Separate control and data connections |
| FTPS | 21 / 990 | TLS/SSL | Separate control and data connections |
| SFTP | 22 | SSH | Single encrypted connection |

---

# Security Considerations

FTP should be avoided in modern networks because credentials and data are transmitted in plaintext.

Secure alternatives such as **FTPS** and **SFTP** provide encryption and better protection against interception attacks.

SFTP is widely used because it integrates with SSH and is easier to configure securely.
