# OSI Model

The Open Systems Interconnection (OSI) model is a conceptual framework used to understand how data travels from one device to another over a network. It divides the communication process into seven distinct layers.

## Purpose

- **Standardization:** Establishes a common language and set of rules for network communication.  
- **Modular Design:** Allows each layer to function independently, so changes or updates in one layer do not directly affect others.  
- **Troubleshooting:** Enables network professionals to isolate and diagnose issues by identifying which layer is failing.

---

## The 7 Layers

### 1. Physical Layer
**Main Function:**  
Responsible for transmitting raw bits over a wired or wireless medium. These bits are transmitted as electrical signals in wires or as electromagnetic waves in wireless communication.

---

### 2. Data Link Layer
**Main Function:**  
Ensures reliable transmission of data frames between two nodes within the same network. It performs framing, MAC addressing, and error detection (such as CRC).

Protocols are typically implemented in the Network Interface Card (NIC) or other hardware devices.

**Example:**  
MAC address, Ethernet

---

### 3. Network Layer
Responsible for delivering data from one host to another across different networks until it reaches the destination.

**Main Functions:**
- **Fragmentation:** Breaks large packets into smaller fragments according to the Maximum Transmission Unit (MTU).  
- **IP Addressing:** Provides logical addressing using unique IP addresses assigned to devices.  
- **Routing:** Determines the best path to deliver data to the destination network.

**Example:**  
IP, Routing protocols

---

### 4. Transport Layer
Responsible for end-to-end communication between applications running on different hosts.

**Main Functions:**
- **Segmentation:** Divides data into smaller units (segments in TCP or datagrams in UDP) and reassembles them at the destination.  
- **Error Control:** Detects errors using checksums and ensures reliable data transmission in connection-oriented protocols like TCP.  
- **Flow Control:** Prevents the sender from overwhelming the receiver by controlling the rate of data transmission.  
- **Multiplexing/Demultiplexing:** Uses source and destination port numbers to ensure that data is delivered to the correct application or service.

**Protocols:**
- **TCP:** Reliable and connection-oriented  
- **UDP:** Unreliable, connectionless, and faster  

---

### 5. Session Layer
**Main Function:**  
Responsible for establishing, maintaining, terminating, and recovering communication sessions between applications. It manages session checkpoints and synchronization during communication.

**Example:**  
NetBIOS session service

---

### 6. Presentation Layer
**Main Functions:**
- **Data Translation:** Converts data into a format or syntax that the receiving application can understand.  
- **Encryption/Decryption:** Encrypts data (using protocols such as SSL/TLS) to prevent unauthorized access and decrypts it at the receiving side.  
- **Compression:** Reduces the size of data before transmission. Compression can be lossy or lossless.

---

### 7. Application Layer
**Main Functions:**
1. Provides network services directly to end-user applications.  
2. Defines how client and server applications communicate using protocols such as HTTP, FTP, SMTP, and DNS.  
3. Handles the request and response structure between applications.

**Example:**  
HTTP, FTP, SMTP, DNS
