# Network Security

## 1. What is Network Security?

Network security is the practice of protecting networks, devices, systems, and data from:

* Unauthorized access
* Attacks
* Data theft
* Malware
* Network disruption
* Unauthorized changes

The main goal is to keep network resources **confidential, available, and trustworthy**.

---

# 2. CIA Triad

The CIA Triad is one of the basic concepts of cybersecurity.

CIA stands for:

```text id="x6s3pg"
C → Confidentiality
I → Integrity
A → Availability
```

### Confidentiality

Only authorized people should be able to access information.

Example:

```text
User → Login → Access allowed
Attacker → Access denied
```

### Integrity

Data should not be modified without authorization.

Example:

```text
Original:
Salary = ₹50,000

Attacker changes:
Salary = ₹5,00,000
```

This is an integrity violation.

### Availability

Systems and services should be available when needed.

Example:

```text
Website
   ↓
Users can access it
```

A DDoS attack can attempt to make a service unavailable.

---

# 3. Common Network Threats

Common network security threats include:

* Malware
* Phishing
* Man-in-the-Middle attacks
* ARP spoofing
* DNS attacks
* DoS/DDoS attacks
* Packet sniffing
* Password attacks
* Rogue devices
* VLAN hopping
* Routing attacks

---

# 4. Malware

Malware means **malicious software**.

Examples include:

* Virus
* Worm
* Trojan
* Ransomware
* Spyware
* Botnet malware

Malware can:

* Steal information
* Damage systems
* Encrypt files
* Install unauthorized software
* Create backdoors

---

# 5. Man-in-the-Middle Attack

A **Man-in-the-Middle (MITM)** attack occurs when an attacker positions themselves between two communicating parties and attempts to intercept or manipulate communication.

Example:

```text id="8x0g6v"
User
  |
  ↓
Attacker
  |
  ↓
Server
```

The attacker may attempt to:

* Read traffic
* Modify traffic
* Steal credentials
* Redirect communication

Encryption such as TLS helps protect communication from interception and modification.

---

# 6. ARP Spoofing

ARP spoofing occurs when an attacker sends forged ARP information on a local network.

Example:

```text id="j5d4x0"
Real:

192.168.1.1 → Router MAC


Attacker:

192.168.1.1 → Attacker MAC
```

This can allow the attacker to intercept traffic.

Possible defenses include:

* Dynamic ARP Inspection
* Static ARP entries in specific cases
* Network segmentation
* Encryption
* Monitoring

---

# 7. DNS Attacks

DNS is responsible for translating domain names into IP addresses.

Attackers may attempt attacks such as:

* DNS spoofing
* DNS cache poisoning
* DNS hijacking

Example:

```text id="h8v1s5"
User:
example.com

       ↓

Fake DNS response

       ↓

Malicious IP
```

Security mechanisms such as DNSSEC can help authenticate DNS data.

---

# 8. DoS Attack

DoS stands for **Denial of Service**.

The goal is to make a service unavailable or difficult to access.

Example:

```text id="n0g9p6"
Attacker
  ↓↓↓↓↓
Server
  ↓
Overloaded
  ↓
Service unavailable
```

---

# 9. DDoS Attack

DDoS stands for **Distributed Denial of Service**.

Instead of one system attacking the target, many compromised systems may generate traffic.

```text id="3e7w2f"
Bot 1 ──┐
Bot 2 ──┤
Bot 3 ──┤
Bot 4 ──┤──→ Target Server
Bot 5 ──┤
Bot 6 ──┘
```

Defenses can include:

* Rate limiting
* Traffic filtering
* Load balancing
* DDoS protection services
* CDN-based protection

---

# 10. Packet Sniffing

Packet sniffing means capturing and analyzing network traffic.

Tools such as **Wireshark** can capture packets for troubleshooting and security analysis.

Example:

```text id="i4s5j7"
Network Traffic
      ↓
Packet Capture
      ↓
Wireshark
      ↓
Analyze packets
```

Unencrypted protocols can expose sensitive information.

For example, plain HTTP traffic can be inspected more easily than HTTPS traffic.

Only capture traffic on networks where you have permission.

---

# 11. Encryption

Encryption converts readable information into protected data.

Example:

```text id="7j2m5p"
Plaintext
   ↓
Encryption
   ↓
Ciphertext
```

The intended recipient can decrypt the data using the appropriate cryptographic key.

Encryption helps protect **confidentiality**.

---

# 12. TLS

TLS stands for **Transport Layer Security**.

TLS protects network communication by providing:

* Encryption
* Authentication
* Integrity

HTTPS uses TLS.

Example:

```text id="6m2x9f"
Browser
   |
   | TLS
   ↓
Web Server
```

TLS helps prevent attackers from easily reading or modifying protected traffic in transit.

---

# 13. Firewall

A firewall controls network traffic according to security rules.

Example:

```text id="q6k8m2"
Internet
    |
    ↓
Firewall
  /   \
Allow  Block
```

A firewall can filter traffic based on factors such as:

* Source IP
* Destination IP
* Port
* Protocol
* Connection state
* Application, depending on firewall type

Example rule:

```text id="s4h8p1"
Allow TCP 443
Block unauthorized traffic
```

---

# 14. Network Segmentation

Network segmentation divides a network into separate logical or physical sections.

Example:

```text id="v9s7d1"
              Network
                 |
      ┌──────────┼──────────┐
      ↓          ↓          ↓
   Users       Servers     Guests
```

Technologies such as VLANs can be used for segmentation.

Segmentation can limit the spread of attacks and restrict access between systems.

---

# 15. VLAN Security

VLANs can separate different groups of devices.

Example:

```text id="a5p2q7"
VLAN 10 → Employees
VLAN 20 → Servers
VLAN 30 → Guests
```

Traffic between VLANs can be controlled using routing and access-control rules.

Important security practices include:

* Disable unused ports
* Configure access ports explicitly
* Restrict trunk VLANs
* Use appropriate native VLAN configuration
* Monitor unusual VLAN activity

---

# 16. ACL

ACL stands for **Access Control List**.

An ACL contains rules that determine whether traffic should be allowed or denied.

Example:

```text id="u2c8y5"
Source: 192.168.10.0/24
Destination: 192.168.20.0/24
Service: TCP 443
Action: ALLOW
```

Another example:

```text id="z1v6k4"
Source: Guest VLAN
Destination: Internal Server VLAN
Action: DENY
```

ACLs are commonly used on:

* Routers
* Layer 3 switches
* Firewalls

---

# 17. IDS

IDS stands for **Intrusion Detection System**.

An IDS monitors network or system activity and generates alerts when suspicious activity is detected.

Example:

```text id="j4v8m3"
Network Traffic
      ↓
     IDS
      ↓
Suspicious activity
      ↓
    Alert
```

An IDS generally detects and alerts rather than automatically blocking the traffic.

---

# 18. IPS

IPS stands for **Intrusion Prevention System**.

An IPS can detect suspicious traffic and take action to block or prevent it.

Example:

```text id="n8c4r2"
Network Traffic
      ↓
     IPS
      ↓
Detect Attack
      ↓
Block Traffic
```

### IDS vs IPS

| IDS                            | IPS                        |
| ------------------------------ | -------------------------- |
| Detects suspicious activity    | Detects and can block      |
| Generates alerts               | Can actively prevent       |
| Usually monitoring-focused     | Usually placed inline      |
| Does not normally stop traffic | Can stop malicious traffic |

---

# 19. VPN

VPN stands for **Virtual Private Network**.

A VPN creates an encrypted tunnel over an untrusted network.

Example:

```text id="w5m8t2"
Laptop
   |
   | Encrypted Tunnel
   |
Internet
   |
   |
VPN Server
   |
Internal Network
```

VPNs can be used for:

* Secure remote access
* Connecting branch offices
* Protecting traffic over untrusted networks

Common VPN technologies include:

* IPsec
* SSL/TLS-based VPNs
* WireGuard
* OpenVPN

---

# 20. Authentication

Authentication verifies **who a user or device is**.

Examples:

* Username + password
* Multi-factor authentication (MFA)
* Certificates
* Security keys

Example:

```text id="g7p2m9"
Username
   +
Password
   +
MFA
   ↓
Authentication
```

---

# 21. Authorization

Authorization determines **what an authenticated user is allowed to do**.

Example:

```text id="b2x6q8"
User authenticated
        ↓
Authorization
        ↓
Can access:
- Website
- Files

Cannot access:
- Admin panel
```

Authentication and authorization are different:

```text id="m4n8r1"
Authentication → Who are you?

Authorization → What can you access?
```

---

# 22. Network Access Control

Network access control ensures that only authorized devices/users can connect to network resources.

Examples include:

* 802.1X
* NAC systems
* Device authentication
* Network segmentation

Example:

```text id="q3k7m1"
Device
   ↓
Authentication
   ↓
Authorized?
  /   \
Yes    No
 ↓      ↓
Access  Denied
```

---

# 23. Zero Trust

Zero Trust is a security approach based on the idea that access should not automatically be trusted just because a user or device is inside the network.

A simple principle is:

```text id="h7d2s4"
Never automatically trust
        ↓
Verify
        ↓
Authorize
        ↓
Monitor
```

Important concepts include:

* Continuous verification
* Least privilege
* Strong authentication
* Device security
* Network segmentation
* Monitoring

---

# 24. Least Privilege

Least privilege means giving users and systems **only the access they need**.

Example:

```text id="n4q6p8"
Employee
   ↓
Needs HR application
   ↓
Give HR application access

Do not give:
- Server administrator access
- Network administrator access
- Database administrator access
```

This reduces the potential impact of compromised accounts.

---

# 25. Network Monitoring

Network monitoring helps identify abnormal or suspicious activity.

Useful information includes:

* Source IP
* Destination IP
* Ports
* Protocols
* Connection times
* Packet counts
* Authentication events

Tools commonly used include:

* Wireshark
* tcpdump
* Zeek
* Suricata
* SIEM platforms

---

# 26. Common Network Security Tools

| Tool      | Purpose                                |
| --------- | -------------------------------------- |
| Wireshark | Packet analysis                        |
| tcpdump   | Command-line packet capture            |
| Nmap      | Network/service discovery              |
| Zeek      | Network security monitoring            |
| Suricata  | IDS/IPS and network threat detection   |
| Firewall  | Traffic filtering                      |
| VPN       | Secure network communication           |
| SIEM      | Security event collection and analysis |

Use security tools only on systems and networks you own or have explicit permission to test.

---

# 27. Basic Network Security Architecture

A simple secure network might look like:

```text id="x9f3k6"
                  Internet
                     |
                     ↓
                 Firewall
                     |
              ┌──────┴──────┐
              ↓             ↓
            DMZ          Internal
             |             Network
             |                |
          Web Server       VLANs
                              |
                    ┌─────────┼─────────┐
                    ↓         ↓         ↓
                  Users     Servers    Guests
```

The firewall controls traffic between network zones.

VLANs can provide additional segmentation inside the internal network.

---

# 28. Defense in Depth

Defense in depth means using multiple layers of security instead of relying on one security control.

Example:

```text id="c7m4p2"
Authentication
      ↓
Firewall
      ↓
Network Segmentation
      ↓
IDS/IPS
      ↓
Endpoint Security
      ↓
Logging & Monitoring
```

If one security control fails, other controls can still provide protection.

---

# 29. Important Security Concepts

Remember these concepts:

### Confidentiality

Protect information from unauthorized access.

### Integrity

Protect information from unauthorized modification.

### Availability

Keep systems and services available.

### Authentication

Verify identity.

### Authorization

Control permissions.

### Encryption

Protect data from unauthorized reading.

### Segmentation

Separate networks and systems.

### Monitoring

Detect suspicious activity.

### Least Privilege

Give only necessary permissions.

---

# 30. Important Points to Remember

* Network security protects networks, devices, services, and data.
* CIA stands for Confidentiality, Integrity, and Availability.
* Firewalls filter network traffic.
* IDS detects suspicious activity.
* IPS can detect and block suspicious traffic.
* VPNs can provide encrypted tunnels over untrusted networks.
* VLANs can provide network segmentation.
* ACLs control allowed and denied traffic.
* TLS protects many network communications.
* Authentication verifies identity.
* Authorization controls access.
* Least privilege limits unnecessary access.
* Zero Trust requires verification rather than assuming trust.
* Network monitoring helps detect attacks and anomalies.
* Defense in depth uses multiple security controls.
