# COMMON NETWORK PROTOCOLS

## 1. What is a Network Protocol?

A network protocol is a set of rules that defines how devices communicate and exchange data over a network.

Protocols specify things such as:

* How data is formatted
* How data is transmitted
* How devices identify each other
* How errors are handled
* How communication is established

EXAMPLES:

* HTTP
* HTTPS
* DNS
* DHCP
* FTP
* SSH
* SMTP
* ICMP

---

# 2. DNS

DNS stands for **Domain Name System**.

DNS converts human-readable domain names into IP addresses.

Example:

```text
google.com
     ↓
DNS
     ↓
142.250.x.x
```

Without DNS, users would need to remember IP addresses instead of domain names.

### COMMON DNS PORTS

```text
UDP 53
TCP 53
```

UDP is commonly used for normal DNS queries. TCP can be used for larger responses, zone transfers, and other cases.

### Example

```bash
nslookup example.com
```

or:

```bash
dig example.com
```

---

# 3. DHCP

DHCP stands for **Dynamic Host Configuration Protocol**.

DHCP automatically provides network configuration to devices.

It can provide:

* IP address
* Subnet mask
* Default gateway
* DNS server

### DHCP Process

The basic DHCP process is called **DORA**:

```text
D → Discover
O → Offer
R → Request
A → Acknowledgment
```

### Process

```text
Client                     DHCP Server
  |                            |
  | ---- DHCP Discover ------> |
  | <----- DHCP Offer -------- |
  | ---- DHCP Request -------> |
  | <--- DHCP ACK ------------ |
```

### Common Ports

```text
UDP 67 → DHCP Server
UDP 68 → DHCP Client
```

---

# 4. HTTP

HTTP stands for **Hypertext Transfer Protocol**.

HTTP is used to transfer web resources between clients and servers.

Example:

```text
Browser
   ↓
HTTP Request
   ↓
Web Server
   ↓
HTTP Response
   ↓
Browser
```

### Common Port

```text
TCP 80
```

HTTP does not provide encryption by itself.

---

# 5. HTTPS

HTTPS stands for **Hypertext Transfer Protocol Secure**.

HTTPS is HTTP protected using **TLS (Transport Layer Security)**.

It provides:

* Encryption
* Authentication
* Integrity

Example:

```text
https://example.com
```

### Common Port

```text
TCP 443
```

Modern HTTPS can also use HTTP/3 over QUIC, which uses UDP.

### HTTP vs HTTPS

| HTTP                           | HTTPS                            |
| ------------------------------ | -------------------------------- |
| Not encrypted by HTTP itself   | Protected using TLS              |
| Usually port 80                | Usually port 443                 |
| Less secure for sensitive data | Provides encrypted communication |
| `http://`                      | `https://`                       |

---

# 6. FTP

FTP stands for **File Transfer Protocol**.

FTP is used to transfer files between a client and a server.

It can be used for:

* Uploading files
* Downloading files
* Managing files on a remote server

### Common Ports

```text
TCP 21 → Control connection
TCP 20 → Traditional FTP data connection
```

FTP does not encrypt data by default.

---

# 7. SFTP

SFTP stands for **SSH File Transfer Protocol**.

It provides secure file transfer through SSH.

It supports:

* File upload
* File download
* File management
* Encrypted communication

### Common Port

```text
TCP 22
```

### FTP vs SFTP

| FTP                      | SFTP          |
| ------------------------ | ------------- |
| Not encrypted by default | Encrypted     |
| Ports 20/21              | Port 22       |
| Separate FTP protocol    | Runs over SSH |
| Less secure              | More secure   |

---

# 8. SSH

SSH stands for **Secure Shell**.

SSH is used for secure remote access to computers and servers.

It provides encrypted communication.

Common uses:

* Remote server administration
* Secure command-line access
* Secure file transfer using SFTP
* Tunneling

### Common Port

```text
TCP 22
```

Example:

```bash
ssh username@192.168.1.10
```

---

# 9. ICMP

ICMP stands for **Internet Control Message Protocol**.

ICMP is used for network diagnostics, error reporting, and control messages.

It is not a transport protocol like TCP or UDP.

### Common Uses

* Ping
* Traceroute
* Error reporting
* Network troubleshooting

Example:

```bash
ping 8.8.8.8
```

A typical ping uses:

```text
ICMP Echo Request
        ↓
ICMP Echo Reply
```

ICMP does not use TCP or UDP port numbers.

---

# 10. SMTP

SMTP stands for **Simple Mail Transfer Protocol**.

SMTP is used to send email between mail clients and mail servers and between mail servers.

### Common Ports

```text
TCP 25  → Server-to-server SMTP
TCP 587 → Message submission
TCP 465 → SMTP over TLS commonly used for secure submission
```

SMTP is primarily used for **sending** email.

---

# 11. POP3

POP3 stands for **Post Office Protocol version 3**.

POP3 is used to retrieve email from a mail server.

### Common Ports

```text
TCP 110  → POP3
TCP 995  → POP3 over TLS
```

POP3 is generally designed around downloading messages from the server.

---

# 12. IMAP

IMAP stands for **Internet Message Access Protocol**.

IMAP is used to access and manage email stored on a mail server.

### Common Ports

```text
TCP 143  → IMAP
TCP 993  → IMAP over TLS
```

IMAP is useful when accessing the same mailbox from multiple devices because messages and mailbox state can remain on the server.

---

# 13. NTP

NTP stands for **Network Time Protocol**.

NTP synchronizes the clocks of computers and network devices.

Accurate time is important for:

* Logs
* Authentication
* Security monitoring
* Troubleshooting
* Certificates

### Common Port

```text
UDP 123
```

---

# 14. SNMP

SNMP stands for **Simple Network Management Protocol**.

SNMP is used to monitor and manage network devices.

It can be used to monitor:

* Routers
* Switches
* Servers
* Printers
* Network interfaces

### Common Ports

```text
UDP 161 → SNMP queries
UDP 162 → SNMP traps/notifications
```

---

# 15. Telnet

Telnet is a protocol used for remote command-line access.

### Common Port

```text
TCP 23
```

Telnet sends data, including credentials, without encryption.

Therefore, **SSH is preferred for secure remote access**.

---

# 16. LDAP

LDAP stands for **Lightweight Directory Access Protocol**.

LDAP is used to access and manage directory information.

It can be used for:

* User accounts
* Groups
* Authentication
* Organizational information

### Common Ports

```text
TCP 389  → LDAP
TCP 636  → LDAP over TLS (LDAPS)
```

---

# 17. Common Network Protocols Table

| Protocol | Purpose                      | Common Port    |
| -------- | ---------------------------- | -------------- |
| DNS      | Domain name resolution       | UDP/TCP 53     |
| DHCP     | Automatic IP configuration   | UDP 67/68      |
| HTTP     | Web communication            | TCP 80         |
| HTTPS    | Secure web communication     | TCP 443        |
| FTP      | File transfer                | TCP 20/21      |
| SFTP     | Secure file transfer         | TCP 22         |
| SSH      | Secure remote access         | TCP 22         |
| Telnet   | Remote access                | TCP 23         |
| SMTP     | Sending email                | TCP 25/587/465 |
| POP3     | Receiving email              | TCP 110/995    |
| IMAP     | Email access                 | TCP 143/993    |
| ICMP     | Diagnostics/control messages | No ports       |
| NTP      | Time synchronization         | UDP 123        |
| SNMP     | Network management           | UDP 161/162    |
| LDAP     | Directory services           | TCP 389/636    |

---

# 18. TCP vs UDP Protocol Examples

Some protocols commonly use TCP:

```text
HTTP
HTTPS
FTP
SSH
SMTP
IMAP
POP3
```

Some commonly use UDP:

```text
DNS
DHCP
NTP
SNMP
```

However, protocol behavior can vary by version, configuration, and application.

---

# 19. How Protocols Work Together

When you open a website, multiple protocols can work together.

For example:

```text
You type:
https://example.com
        ↓
DNS
        ↓
Find the server's IP address
        ↓
TCP / QUIC connection
        ↓
TLS
        ↓
HTTPS
        ↓
Web server sends data
        ↓
Browser displays website
```

At lower layers, the data is encapsulated:

```text
Application Data
       ↓
TCP Segment / QUIC
       ↓
IP Packet
       ↓
Ethernet Frame
       ↓
Physical Network
```

---

# 20. Practical Linux Commands

### DNS

```bash
nslookup example.com
```

```bash
dig example.com
```

### DHCP / Network Configuration

```bash
ip addr
```

```bash
ip route
```

### HTTP/HTTPS

```bash
curl https://example.com
```

### SSH

```bash
ssh username@192.168.1.10
```

### ICMP

```bash
ping 8.8.8.8
```

### NTP

```bash
timedatectl
```

---

# 21. Network Protocols and Cybersecurity

Understanding network protocols is very important in cybersecurity.

Security professionals analyze protocols to identify:

* Misconfigurations
* Open services
* Unencrypted communication
* Weak authentication
* Suspicious traffic
* Network attacks

For example:

```text
Nmap
  ↓
Find open ports
  ↓
Identify services
  ↓
Identify protocols
  ↓
Analyze security
```

Wireshark can also be used to inspect network traffic and identify protocols such as:

* ARP
* DNS
* DHCP
* HTTP
* TCP
* UDP
* ICMP

Only scan and analyze systems that you own or have permission to test.

---

# 22. Important Points to Remember

* A network protocol defines rules for communication.
* DNS converts domain names into IP addresses.
* DHCP provides network configuration automatically.
* HTTP is used for web communication.
* HTTPS provides HTTP communication protected by TLS.
* FTP is used for file transfer.
* SFTP provides secure file transfer over SSH.
* SSH provides secure remote access.
* ICMP is used for diagnostics and control messages.
* SMTP is mainly used for sending email.
* POP3 and IMAP are used for retrieving/accessing email.
* NTP synchronizes system clocks.
* SNMP is used for network monitoring and management.
* Telnet is insecure because it does not encrypt traffic by default.
* Protocols often use specific port numbers.
