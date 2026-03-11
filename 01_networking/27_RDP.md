# RDP (Remote Desktop Protocol)

Remote Desktop Protocol (RDP) is used to remotely access and control another computer's graphical interface over a network.

It is commonly used in Windows environments for remote administration.

| Property | Value |
|---|---|
| Default Port | 3389 |
| Transport | TCP (and sometimes UDP) |
| Encryption | Yes |

RDP allows a user to interact with a remote system as if they were physically present.

---

# What RDP Is Used For

RDP allows users to:

- remotely control a system
- run applications on a remote computer
- manage servers
- access files and programs remotely

Example scenario:

```
Client → Remote Windows Server
```

The client sees the remote desktop environment.

---

# RDP Packet-Level Flow

### Step 1 — TCP Connection

Client initiates connection to the server.

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

Connection established on **TCP port 3389**.

---

# Step 2 — Security Negotiation

Client and server negotiate encryption and security protocols.

Possible security layers:

- TLS
- CredSSP
- Network Level Authentication (NLA)

This stage ensures secure communication before authentication.

---

# Step 3 — Authentication

User credentials are verified.

User provides:

```
username
password
```

Authentication is commonly handled by Windows authentication systems such as:

```
NTLM
Kerberos
```

---

# Step 4 — Session Establishment

Once authentication succeeds, a remote session is created.

The server sends graphical desktop data to the client.

Client sends input events:

- keyboard input
- mouse movements

This creates an interactive remote desktop environment.

---

# RDP Traffic Characteristics

In network traffic analysis:

- Traffic occurs on **port 3389**
- Data is encrypted
- Packet sizes are often larger due to graphical data transmission

Wireshark filter:

```
tcp.port == 3389
```

---

# RDP Security Risks

RDP is frequently targeted by attackers.

Common attacks include:

### Brute Force Attacks

Attackers repeatedly attempt login with different passwords.

Example log entries:

```
Failed login attempt from 192.168.1.50
```

---

### Exposed RDP Services

Systems exposed directly to the internet may be scanned and attacked.

Example scanning behavior:

```
Multiple connection attempts to port 3389
```

---

### RDP Exploits

Certain vulnerabilities have allowed attackers to gain remote access.

Example:

```
BlueKeep vulnerability
```

---

# Security Best Practices

To secure RDP:

- Enable Network Level Authentication (NLA)
- Use strong passwords
- Restrict RDP access using firewall rules
- Use VPN for remote access
- Monitor login attempts

---

# Summary

RDP allows users to remotely access and control a system's graphical interface.

While it is useful for remote administration, it must be secured properly to prevent unauthorized access and brute-force attacks.
