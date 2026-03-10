# SMB (Server Message Block)

SMB is a network protocol used for **file sharing, printer sharing, and resource access** between systems on a network.

It is widely used in **Windows environments** but is also supported on Linux using **Samba**.

| Property | Value |
|---|---|
| Default Port | 445 |
| Transport | TCP |

---

# What SMB Is Used For

SMB allows users to:

- access shared folders
- transfer files
- share printers
- communicate with remote systems

Example Windows shared folder:

```
\\server\shared_folder
```

---

# SMB Packet-Level Flow

### Step 1 — TCP Connection

Client connects to SMB server.

```
Client → Server
SYN
```

Server responds:

```
Server → Client
SYN-ACK
```

Client confirms:

```
Client → Server
ACK
```

Connection established on **TCP port 445**.

---

# Step 2 — SMB Negotiation

Client sends negotiation request to determine supported SMB version.

Example versions:

- SMB1
- SMB2
- SMB3

Server responds with supported protocol version.

---

# Step 3 — Authentication

Client authenticates using credentials.

Common authentication method:

```
NTLM authentication
```

Client sends username and authentication information.

Server verifies credentials.

---

# Step 4 — Session Setup

After authentication, an SMB session is established.

Client can now access shared resources.

Example operations:

- read files
- write files
- list directories

---

# SMB Example in Network Traffic

Wireshark filter:

```
smb
```

Example operations observed:

```
SMB2 CREATE Request
SMB2 READ Request
SMB2 WRITE Request
```

These represent file access operations.

---

# Security Risks

SMB has been targeted in many attacks.

Examples:

- SMB brute force
- SMB relay attacks
- Worm propagation

Example vulnerability:

```
EternalBlue (WannaCry ransomware)
```

This vulnerability exploited SMB to spread across networks.

---

# SMB in Linux

Linux systems can interact with SMB using **Samba**.

Example command to list shares:

```bash
smbclient -L //192.168.1.10
```

Access shared folder:

```bash
smbclient //192.168.1.10/share
```

---

# Summary

SMB is a protocol used for network file sharing and resource access.

It is commonly used in enterprise environments and is an important protocol to understand for network analysis and security investigations.
