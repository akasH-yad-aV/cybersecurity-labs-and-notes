# DNS (Domain Name System)

DNS stands for Domain Name System.

It is an application layer protocol that translates human-readable domain names (like google.com) into IP addresses.

DNS primarily uses UDP (port 53).
For large responses, it can use TCP.

---

## Why DNS Exists

Humans remember domain names.
Computers communicate using IP addresses.

DNS acts as a translator between domain names and IP addresses.

---

## Domain Name Hierarchy

DNS is hierarchical.

Example:
www.google.com

- Root (.)
- Top-Level Domain (TLD): .com
- Second-Level Domain: google
- Subdomain: www

The DNS system is structured in levels.

---

## DNS Resolution Process

When a user types a domain name:

1️ Browser checks its own cache.  
2️ OS checks local DNS cache.  
3️ System checks the hosts file.  
4️ Query is sent to configured Recursive Resolver.

The recursive resolver performs:

1. Query Root DNS Server  
2. Root responds with TLD server (.com)  
3. Resolver queries TLD server  
4. TLD responds with Authoritative Name Server  
5. Resolver queries Authoritative server  
6. Authoritative server responds with IP address  
7. Resolver returns IP to client and caches it

---

## Recursive vs Iterative Query

Recursive Query:
- Client asks resolver to get the final answer.
- Resolver performs full lookup process.

Iterative Query:
- DNS server responds with the best information it has.
- Client or resolver continues querying other servers.

---

## DNS Record Types

Common DNS record types:

- A → Maps domain to IPv4 address  
- AAAA → Maps domain to IPv6 address  
- CNAME → Alias to another domain  
- MX → Mail server record  
- NS → Name server record  
- TXT → Text information (often used for verification)

---

## DNS Caching

DNS responses include TTL (Time To Live).

TTL defines how long a record can be cached before it must be refreshed.

Caching reduces:
- Latency
- Load on DNS servers

---

## DNS over UDP vs TCP

DNS usually uses UDP because:
- Queries are small
- Fast response needed

DNS switches to TCP when:
- Response is too large
- Zone transfers occur

---

## DNS Tunneling (Basic Concept)

DNS tunneling is a technique where attackers encode data inside DNS queries or responses.

Because DNS traffic is usually allowed through firewalls, it can be abused for:

- Data exfiltration
- Command and control communication

---

## SOC Perspective

Indicators of suspicious DNS activity:

- Excessively long domain names
- High frequency of DNS queries
- Random-looking subdomains
- Large DNS payload sizes
- DNS traffic to unknown servers
