NMAP (NETWORK MAPPER) - COMPLETE CYBERSECURITY NOTES

Nmap stands for Network Mapper. It is an open-source network scanning and security auditing tool used to discover hosts, scan ports, identify running services and their versions, detect operating systems, map networks, and perform security assessment. Nmap is widely used by cybersecurity professionals, penetration testers, network administrators, and security resercher.

LEGAL NOTICE:
Only scan systems, networks, IP addresses, or websites that you own or have explicit permission to test. For practice, use your own computer, virtual machines, CTF , platforms, or authorized labs.

1. INSTALLATION

Kali Linux / Debian / Ubuntu:
sudo apt update
sudo apt install nmap

Check installation:
nmap --version

2. BASIC SYNTAX

nmap [options] [target]

Example:
nmap 192.168.1.1

3. SINGLE IP SCAN

nmap 192.168.1.1

Performs a basic scan against the target.

4. DOMAIN SCAN

nmap example.com

Nmap resolves the domain to an IP address and scans the target. Only scan authorized domains.

5. MULTIPLE TARGETS

nmap 192.168.1.1 192.168.1.2

6. IP RANGE SCAN

nmap 192.168.1.1-20

Scans IP addresses from 192.168.1.1 to 192.168.1.20.

7. SUBNET SCAN

nmap 192.168.1.0/24

Scans hosts in the 192.168.1.0/24 network.

8. HOST DISCOVERY

nmap -sn 192.168.1.0/24

-sn performs host discovery without a normal port scan.

9. BASIC PORT SCAN

nmap 192.168.1.10

Example result:
PORT     STATE     SERVICE
22/tcp   open      ssh
80/tcp   open      http
443/tcp  open      https

10. SPECIFIC PORT

nmap -p 80 192.168.1.10

11. MULTIPLE PORTS

nmap -p 22,80,443 192.168.1.10

12. PORT RANGE

nmap -p 1-1000 192.168.1.10

13. ALL TCP PORTS

nmap -p- 192.168.1.10

14. TCP SYN SCAN

sudo nmap -sS 192.168.1.10

-sS performs a TCP SYN scan and is commonly used for efficient TCP port discovery.

15. TCP CONNECT SCAN

nmap -sT 192.168.1.10

-sT performs a TCP connect scan using the operating system's normal TCP connection mechanism.

16. UDP SCAN

sudo nmap -sU 192.168.1.10

-sU scans UDP ports.

Common UDP services:
53 - DNS
67/68 - DHCP
123 - NTP
161 - SNMP

17. TCP + UDP SCAN

sudo nmap -sS -sU 192.168.1.10

18. SERVICE AND VERSION DETECTION

nmap -sV 192.168.1.10

-sV attempts to identify the service and version running on an open port.

Example:
22/tcp open ssh OpenSSH
80/tcp open http Apache

19. OPERATING SYSTEM DETECTION

sudo nmap -O 192.168.1.10

-O attempts to identify the target operating system.

20. AGGRESSIVE SCAN

sudo nmap -A 192.168.1.10

-A enables OS detection, version detection, NSE scripts, and traceroute.

Use aggressive scans only on authorized systems.

21. DEFAULT NSE SCRIPTS

nmap -sC 192.168.1.10

-sC runs Nmap's default NSE scripts.

Common combination:
nmap -sC -sV 192.168.1.10

22. NMAP SCRIPTING ENGINE (NSE)

NSE stands for Nmap Scripting Engine. It allows Nmap to perform additional automated tasks such as service enumeration, information gathering, configuration checks, and vulnerability checks.

Basic syntax:
nmap --script <script> <target>

Example:
nmap --script http-title 192.168.1.10

23. NSE SCRIPT LOCATION

NSE scripts are commonly stored in:
/usr/share/nmap/scripts/

List scripts:
ls /usr/share/nmap/scripts/

Search scripts:
ls /usr/share/nmap/scripts/ | grep http

24. COMMON NSE CATEGORIES

auth
broadcast
brute
default
discovery
dos
exploit
external
fuzzer
intrusive
malware
safe
version
vuln

Some categories can generate intrusive traffic. Use them only in authorized environments.

25. FIREWALL DETECTION

sudo nmap -sA 192.168.1.10

-sA performs an ACK scan and can help analyze firewall filtering behavior.

26. TIMING OPTIONS

-T0
-T1
-T2
-T3
-T4
-T5

Example:
nmap -T4 192.168.1.10

Higher timing values generally make scans faster but may generate more traffic.

27. VERBOSE MODE

nmap -v 192.168.1.10

More verbose:
nmap -vv 192.168.1.10

28. SAVE NORMAL OUTPUT

nmap -oN scan.txt 192.168.1.10

29. SAVE XML OUTPUT

nmap -oX scan.xml 192.168.1.10

30. SAVE GREPABLE OUTPUT

nmap -oG scan.txt 192.168.1.10

31. SAVE ALL FORMATS

nmap -oA scan 192.168.1.10

Creates:
scan.nmap
scan.xml
scan.gnmap

32. UNDERSTANDING PORT STATES

OPEN:
A service is listening on the port.

CLOSED:
The host is reachable, but no service is listening on that port.

FILTERED:
A firewall or filtering mechanism is preventing Nmap from determining whether the port is open.

OPEN|FILTERED:
Nmap cannot determine whether the port is open or filtered.

CLOSED|FILTERED:
Nmap cannot determine whether the port is closed or filtered.

33. COMMON PORTS

20 - FTP Data
21 - FTP
22 - SSH
23 - Telnet
25 - SMTP
53 - DNS
67/68 - DHCP
80 - HTTP
110 - POP3
123 - NTP
143 - IMAP
161 - SNMP
389 - LDAP
443 - HTTPS
445 - SMB
3306 - MySQL
3389 - RDP
5432 - PostgreSQL
8080 - HTTP Alternate

34. IMPORTANT NMAP COMMANDS

nmap 192.168.1.10
nmap -sn 192.168.1.0/24
nmap -p 80 192.168.1.10
nmap -p 22,80,443 192.168.1.10
nmap -p 1-1000 192.168.1.10
nmap -p- 192.168.1.10
sudo nmap -sS 192.168.1.10
nmap -sT 192.168.1.10
sudo nmap -sU 192.168.1.10
nmap -sV 192.168.1.10
sudo nmap -O 192.168.1.10
nmap -sC 192.168.1.10
nmap -sC -sV 192.168.1.10
sudo nmap -A 192.168.1.10
sudo nmap -sA 192.168.1.10
nmap -v 192.168.1.10
nmap -vv 192.168.1.10
nmap -oN scan.txt 192.168.1.10
nmap -oX scan.xml 192.168.1.10
nmap -oG scan.txt 192.168.1.10
nmap -oA scan 192.168.1.10

35. NMAP IN CYBERSECURITY

Nmap is mainly used during reconnaissance and enumeration.

Typical workflow:

Target → Host Discovery → Port Scanning → Service Detection → Version Detection → OS Detection → NSE Enumeration → Security Assessment

Example:

nmap -sn 192.168.1.0/24

This helps identify active hosts.

Then:

nmap -p- 192.168.1.10

This scans TCP ports.

Then:

nmap -sV -sC 192.168.1.10

This identifies services, versions, and performs default script enumeration.

36. NMAP AND VAPT

Nmap is commonly used during the information-gathering and enumeration phases of VAPT.

It can help identify:

IP Addresses → Active Hosts → Open Ports → Running Services → Service Versions → Potential Attack Surface

Nmap is not a complete VAPT tool. It is mainly a network discovery, scanning, and enumeration tool.

37. NMAP VS NETCAT

Nmap:
Network discovery
Port scanning
Service detection
OS detection
NSE scripting

Netcat:
TCP/UDP connections
Connectivity testing
Simple client/server communication
Banner grabbing

38. ADVANTAGES OF NMAP

Free and open source
Works on Linux, Windows, and macOS
Powerful scanning capabilities
Supports multiple scanning techniques
Supports NSE scripts
Useful for network administrators
Useful for penetration testing
Highly customizable
Large community
Useful for network mapping

39. LIMITATIONS OF NMAP

Nmap cannot identify every vulnerability.
Nmap may not correctly identify every operating system.
Nmap may not correctly identify every service version.
Nmap cannot bypass every firewall.
Nmap cannot replace manual security testing.
Nmap is not a complete vulnerability assessment platform.

Nmap results should always be verified before making security conclusions.

40. SAFE NMAP PRACTICE

Use Nmap on:
Your own computer
Your own network
Your own virtual machines
Cybersecurity labs
CTF platforms
Authorized test environments
Intentionally vulnerable machines

41. NMAP LEARNING ORDER

Nmap Basics
↓
IP Addresses
↓
Host Discovery
↓
Port Scanning
↓
TCP Scanning
↓
UDP Scanning
↓
Service Detection
↓
Version Detection
↓
OS Detection
↓
NSE
↓
Firewall Detection
↓
Output and Reporting
↓
Practice Labs

42. IMPORTANT CONCEPTS TO UNDERSTAND

IP Address
MAC Address
TCP
UDP
Ports
Services
Protocols
Firewalls
Subnetting
DNS
HTTP
HTTPS
SSH
SMB
RDP
Network Segmentation

Understanding networking makes Nmap much easier to learn.

43. EXAMPLE AUTHORIZED LAB WORKFLOW

Step 1:
nmap -sn 192.168.1.10

Step 2:
nmap 192.168.1.10

Step 3:
nmap -p- 192.168.1.10

Step 4:
nmap -sV 192.168.1.10

Step 5:
nmap -sC 192.168.1.10

Step 6:
nmap -sC -sV 192.168.1.10

Step 7:
sudo nmap -O 192.168.1.10

Step 8:
nmap -oA lab-scan 192.168.1.10

44. FINAL SUMMARY

Nmap is one of the most important tools for learning cybersecurity and networking. It helps security professionals discover hosts, identify open ports, identify services and versions, detect operating systems, perform enumeration, and understand the network attack surface.

The main concepts to remember are:

Host Discovery
Port Scanning
TCP Scanning
UDP Scanning
Service Detection
Version Detection
OS Detection
NSE
Firewall Detection
Enumeration
Output and Reporting

IMPORTANT COMMANDS TO REMEMBER:

nmap <target>
nmap -sn <network>
nmap -p <port> <target>
nmap -p- <target>
sudo nmap -sS <target>
sudo nmap -sU <target>
nmap -sV <target>
sudo nmap -O <target>
nmap -sC <target>
nmap -sC -sV <target>
sudo nmap -A <target>
nmap -oA <filename> <target>

NEXT TOPIC IN CYBERSECURITY ROADMAP:

Networking
↓
Linux
↓
Nmap
↓
Reconnaissance
↓
VAPT
↓
Burp Suite
↓
Web Security
↓
OWASP Top 10
↓
CTF Practice
↓
Cybersecurity Projects


