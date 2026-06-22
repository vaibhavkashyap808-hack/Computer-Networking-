# Networking Protocols - Quick Revision Notes

## OSI Model (7 Layers)

| Layer | Name | Function | Examples |
|-------|------|----------|----------|
| 7 | **Application** | User applications, services | HTTP, HTTPS, FTP, SSH, DNS, SMTP |
| 6 | **Presentation** | Data encryption, compression | SSL/TLS, JPEG, ASCII |
| 5 | **Session** | Connection management | Session tokens, cookies |
| 4 | **Transport** | End-to-end communication | TCP, UDP |
| 3 | **Network** | Routing, IP addressing | IP (IPv4, IPv6), ICMP, ARP |
| 2 | **Data Link** | MAC addressing, switches | Ethernet, MAC, Switch |
| 1 | **Physical** | Cables, signals | Copper, Fiber, WiFi |

---

## TCP/IP Model (4 Layers)

| Layer | OSI Match | Protocols |
|-------|-----------|-----------|
| **Application** | 7, 6, 5 | HTTP, HTTPS, SSH, FTP, DNS, SMTP, POP3, IMAP |
| **Transport** | 4 | TCP, UDP, SCTP |
| **Internet** | 3 | IP, ICMP, IGMP, ARP |
| **Link** | 2, 1 | Ethernet, PPP, WiFi |

---

## Key Protocols Explained

### **TCP (Transmission Control Protocol)**
- **Port:** 6 (protocol number)
- **Connection:** Connection-oriented (3-way handshake: SYN, SYN-ACK, ACK)
- **Reliability:** Guaranteed delivery, ordered
- **Speed:** Slower (reliable)
- **Use:** Email, Web (HTTP/HTTPS), FTP, SSH, Telnet
- **When to use:** When data accuracy matters (bank transactions, emails)

### **UDP (User Datagram Protocol)**
- **Port:** 17 (protocol number)
- **Connection:** Connectionless (no handshake)
- **Reliability:** No guarantee (fast but unreliable)
- **Speed:** Faster (no confirmation needed)
- **Use:** DNS queries, Online gaming, Video streaming, VoIP
- **When to use:** When speed matters more than perfection (live streaming)

### **HTTP (HyperText Transfer Protocol)**
- **Port:** 80
- **Security:** None (plaintext)
- **Method:** Stateless, request-response
- **Use:** Web browsing (insecure)
- **Status Codes:** 200 (OK), 404 (Not Found), 500 (Server Error)

### **HTTPS (HTTP Secure)**
- **Port:** 443
- **Security:** Encrypted with SSL/TLS
- **Use:** Secure web browsing, e-commerce, online banking
- **Certificate:** Uses digital certificates for authentication

### **DNS (Domain Name System)**
- **Port:** 53 (TCP/UDP)
- **Function:** Converts domain names → IP addresses
- **Example:** example.com → 93.184.216.34
- **Record Types:** A (IPv4), AAAA (IPv6), MX (Mail), NS (Nameserver), CNAME (Alias), TXT
- **Quick:** Fast lookup with caching

### **SSH (Secure Shell)**
- **Port:** 22
- **Use:** Remote server access, secure login, tunneling
- **Security:** Encrypted communication, public-key cryptography
- **Alternative to:** Telnet (insecure)

### **FTP (File Transfer Protocol)**
- **Port:** 21 (control), 20 (data)
- **Use:** File upload/download
- **Security:** Plaintext (use SFTP for secure version)
- **SFTP Port:** 22 (runs over SSH)

### **SMTP (Simple Mail Transfer Protocol)**
- **Port:** 25, 587, 465
- **Function:** Sending emails from client to server
- **Port 25:** Between mail servers
- **Port 587:** TLS encryption
- **Port 465:** SSL encryption

### **POP3 (Post Office Protocol 3)**
- **Port:** 110 (109 with SSL)
- **Function:** Downloading emails from server to client
- **Limitation:** Deletes mail from server (unless configured)

### **IMAP (Internet Message Access Protocol)**
- **Port:** 143 (993 with SSL)
- **Function:** Accessing emails on server, keeping copy
- **Better than POP3:** Sync across devices, keeps mail on server

### **ICMP (Internet Control Message Protocol)**
- **Port:** N/A (network layer)
- **Use:** Ping, Traceroute, Error messages
- **Example:** `ping google.com` (checks if host is reachable)

### **ARP (Address Resolution Protocol)**
- **Function:** Maps IP addresses → MAC addresses
- **Use:** Local network communication
- **Example:** Finding MAC of 192.168.1.5 on local network

### **TLS/SSL (Transport Layer Security)**
- **Port:** Runs on top of other protocols (443 for HTTPS)
- **Function:** Encryption and authentication
- **Handshake:** Client and server exchange certificates
- **Use:** HTTPS, SMTP over TLS, POP3 over SSL, IMAP over SSL

---

## Common Ports Reference

| Port | Protocol | Service |
|------|----------|---------|
| 20 | TCP | FTP (Data) |
| 21 | TCP | FTP (Control) |
| 22 | TCP | SSH, SFTP |
| 23 | TCP | Telnet (insecure) |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS |
| 465 | TCP | SMTP over SSL |
| 587 | TCP | SMTP over TLS |
| 3306 | TCP | MySQL |
| 5432 | TCP | PostgreSQL |
| 3389 | TCP | RDP (Remote Desktop) |

---

## IP Addressing Basics

### **IPv4**
- **Format:** XXX.XXX.XXX.XXX (4 octets, 0-255 each)
- **Example:** 192.168.1.1
- **Total Addresses:** 2^32 = 4.3 billion

### **IPv6**
- **Format:** XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX (hex)
- **Example:** 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- **Total Addresses:** 2^128 (basically unlimited)

### **Private IP Ranges**
```
10.0.0.0 - 10.255.255.255       (Class A)
172.16.0.0 - 172.31.255.255     (Class B)
192.168.0.0 - 192.168.255.255   (Class C)
```

---

## Quick Concept Review

### **Connection-Oriented vs Connectionless**
- **Connection-Oriented (TCP):** Establish connection first → Send data → Close connection (reliable but slower)
- **Connectionless (UDP):** Send data directly → No connection needed (fast but unreliable)

### **Stateful vs Stateless**
- **Stateful (TCP):** Remembers previous interactions
- **Stateless (HTTP):** Each request independent (uses cookies/sessions for memory)

### **Packet Structure**
```
[Header] [Payload] [Trailer]
- Header: Source/Dest IP, Port, Protocol info
- Payload: Actual data
- Trailer: Error checking (CRC)
```

### **Firewall Concepts**
- **Stateful:** Tracks connections, smart filtering
- **Stateless:** Checks each packet independently


---

## Quick Memory Aid

**"Please Do Not Throw Sausage Pizza Away"**
- **P**hysical (1)
- **D**ata Link (2)
- **N**etwork (3)
- **T**ransport (4)
- **S**ession (5)
- **P**resentation (6)
- **A**pplication (7)

---

## Common Scenarios in SOC

| Scenario | Key Protocol | Port | Action |
|----------|--------------|------|--------|
| Email phishing | SMTP/POP3/IMAP | 25/110/143 | Check email headers |
| Website defacement | HTTP/HTTPS | 80/443 | Check web logs |
| Unauthorized SSH login | SSH | 22 | Review SSH logs |
| DNS exfiltration | DNS | 53 | Monitor DNS queries |
| Data exfil via FTP | FTP/SFTP | 21/22 | Check file transfer logs |
| Web attack | HTTP/HTTPS | 80/443 | Analyze HTTP requests |

