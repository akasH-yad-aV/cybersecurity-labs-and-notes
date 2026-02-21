# TCP/IP Model

The TCP/IP (Transmission Control Protocol / Internet Protocol) model is a practical networking model used to describe how data is transmitted across the internet. It is the foundation of modern network communication.

Unlike the OSI model, which is mainly conceptual, the TCP/IP model was developed around real working protocols and is actually implemented in networks.

---

## Layers of the TCP/IP Model

The original TCP/IP model consists of 4 layers.

### 1. Application Layer

This layer provides network services directly to user applications. It combines the functions of the OSI Application, Presentation, and Session layers.

**Responsibilities:**
- Defines communication protocols
- Handles request and response structure
- Provides services to end-user applications

**Examples:**
HTTP, HTTPS, FTP, SMTP, DNS

---

### 2. Transport Layer

This layer provides end-to-end communication between devices.

**Responsibilities:**
- Segmentation and reassembly of data
- Error detection and reliability (in TCP)
- Flow control
- Port addressing (multiplexing and demultiplexing)

**Protocols:**
- TCP (Reliable and connection-oriented)
- UDP (Unreliable, connectionless and faster)

---

### 3. Internet Layer

This layer is responsible for logical addressing and routing packets across different networks.

**Responsibilities:**
- IP addressing
- Routing of packets
- Fragmentation of data

**Protocols:**
IP, ICMP, ARP

---

### 4. Network Access Layer

This layer handles how data is physically transmitted over the network. It combines the responsibilities of the OSI Data Link and Physical layers.

**Responsibilities:**
- Frame transmission
- MAC addressing
- Physical signaling

**Examples:**
Ethernet, Wi-Fi

---

## OSI vs TCP/IP Mapping

 OSI Model Layer  TCP/IP Layer 
 Application    -->  Application 
 Presentation   -->  Application
 Session        -->  Application 
 Transport       --> Transport   
 Network         --> Internet    
 Data Link       --> Network Access 
 Physical        --> Network Access 

---

## Why TCP/IP is More Practical

- It has a simpler structure with 4 layers
- It was designed for real-world implementation
- It forms the backbone of the modern Internet
- It is actually used in real communication between systems
