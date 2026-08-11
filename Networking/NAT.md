# NAT (Network Address Translation)

## 1. What is NAT?

NAT stands for **Network Address Translation**.

NAT is a technique used by routers or firewalls to translate IP addresses between different networks.

The most common use is translating **private IP addresses into a public IP address** when devices access the Internet.

Example:

```text id="q3x0u4"
Private Network
192.168.1.10
      |
      ↓
    Router
      |
      ↓
Public IP
203.0.113.10
      |
      ↓
   Internet
```

---

## 2. Why is NAT Used?

NAT is mainly used to:

* Allow private IP addresses to access the Internet
* Conserve public IPv4 addresses
* Hide internal addressing from external networks
* Translate addresses between different networks

Example:

```text id="7g9a6u"
PC1 → 192.168.1.10
PC2 → 192.168.1.11
PC3 → 192.168.1.12

        ↓ NAT

Public IP → 203.0.113.10
```

Multiple devices can share one public IPv4 address when using port-based NAT.

---

## 3. Private IP Addresses

Private IPv4 addresses are used inside local networks.

The main private IPv4 ranges are:

| Range                         | CIDR           |
| ----------------------------- | -------------- |
| 10.0.0.0 – 10.255.255.255     | 10.0.0.0/8     |
| 172.16.0.0 – 172.31.255.255   | 172.16.0.0/12  |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

Private IP addresses are not directly routable across the public Internet.

---

# 4. Public IP Address

A public IP address is an address that can be routed on the public Internet.

Example:

```text id="1exkde"
Private IP:
192.168.1.10

Public IP:
203.0.113.10
```

The router can translate the private address to the public address when communicating with the Internet.

---

# 5. How NAT Works

Suppose your computer has:

```text id="6a0l8e"
Private IP: 192.168.1.10
```

It wants to access a website.

The packet travels:

```text id="2qg5i3"
PC
192.168.1.10
      ↓
NAT Router
      ↓
Public IP
      ↓
Internet
      ↓
Web Server
```

The router changes the source address from the private address to the public address.

When the response comes back, the router translates it back to the appropriate internal device.

---

# 6. Types of NAT

The main types you should learn are:

1. Static NAT
2. Dynamic NAT
3. PAT (Port Address Translation)

---

# 7. Static NAT

Static NAT creates a **one-to-one mapping** between a private IP and a public IP.

Example:

```text id="l6q1or"
Private IP          Public IP
192.168.1.10   ↔    203.0.113.10
```

The mapping remains fixed.

### Use Case

Static NAT can be useful when an internal server needs a consistent public address.

Example:

```text id="4krxop"
Internal Web Server
192.168.1.10
      ↕
Public Address
203.0.113.10
```

---

# 8. Dynamic NAT

Dynamic NAT maps private addresses to addresses from a **pool of public IP addresses**.

Example:

```text id="w6d3kh"
Private IPs:

192.168.1.10
192.168.1.11
192.168.1.12

        ↓

Public IP Pool:

203.0.113.10
203.0.113.11
203.0.113.12
```

The router dynamically selects an available public address.

---

# 9. PAT

PAT stands for **Port Address Translation**.

It is also commonly called **NAT Overload**.

PAT allows multiple internal devices to share one public IP address by using different port numbers.

Example:

```text id="qv8f1n"
PC1
192.168.1.10:5000
       \
        \
PC2      → NAT Router → 203.0.113.10
192.168.1.11:5001
        /
       /
PC3
192.168.1.12:5002
```

The router keeps track of the connections using port information.

---

# 10. PAT Example

Suppose three computers connect to the Internet.

```text id="a2p6zv"
PC1:
192.168.1.10:5000

PC2:
192.168.1.11:5001

PC3:
192.168.1.12:5002
```

The router could translate them to:

```text id="xw0w0d"
203.0.113.10:6000
203.0.113.10:6001
203.0.113.10:6002
```

The public IP is the same, but the port numbers allow the NAT device to distinguish the connections.

---

# 11. Static NAT vs Dynamic NAT vs PAT

| Feature             | Static NAT                         | Dynamic NAT                    | PAT                            |
| ------------------- | ---------------------------------- | ------------------------------ | ------------------------------ |
| Mapping             | One-to-one                         | One-to-one from a pool         | Many-to-one                    |
| Public IPs required | Usually one per mapping            | Multiple public IPs            | Usually one or a few           |
| Uses ports          | Not required for mapping           | Not required for mapping       | Yes                            |
| Common use          | Publicly reachable internal server | Controlled address translation | Internet access for many users |

---

# 12. NAT Translation Table

A NAT router maintains translation/state information.

Example:

```text id="q1ft2n"
Inside Local        Inside Global
192.168.1.10:5000   203.0.113.10:6000
192.168.1.11:5001   203.0.113.10:6001
192.168.1.12:5002   203.0.113.10:6002
```

This allows the router to determine which internal device should receive a returning packet.

---

# 13. Inside and Outside Addresses

NAT terminology commonly uses:

### Inside Local

The private address assigned to the internal device.

Example:

```text id="x8d3cz"
192.168.1.10
```

### Inside Global

The address representing that internal device to the outside network.

Example:

```text id="z6xw9b"
203.0.113.10
```

### Outside Global

The actual public address of the external destination.

Example:

```text id="44r4k0"
198.51.100.20
```

For basic NAT learning, focus first on **inside local** and **inside global**.

---

# 14. NAT and Ports

PAT uses port numbers to distinguish different connections.

Example:

```text id="0kq0jv"
192.168.1.10:5000
        ↓
203.0.113.10:6000
```

The IP address is translated, and the source port may also be translated.

This is why PAT is often described as **many-to-one address translation using ports**.

---

# 15. NAT and Port Forwarding

NAT can also be used to forward incoming connections to an internal device.

Example:

```text id="2q1h4p"
Internet
   |
   | TCP 443
   ↓
Router
   |
   ↓
192.168.1.10:443
Web Server
```

This is commonly called **port forwarding** or **destination NAT**, depending on the platform and configuration.

Example:

```text id="x07k6p"
Public:
203.0.113.10:443

        ↓

Internal:
192.168.1.10:443
```

---

# 16. NAT and Port Forwarding Example

Suppose you have a web server inside your network:

```text id="b0zq8k"
Web Server:
192.168.1.100

Public IP:
203.0.113.10
```

You can configure the router so that incoming traffic to:

```text id="p9t6eg"
203.0.113.10:443
```

is forwarded to:

```text id="y6q0tw"
192.168.1.100:443
```

This allows external clients to reach the internal service.

Only expose services that are properly secured and authorized.

---

# 17. NAT vs PAT

NAT is the general concept of translating IP addresses.

PAT is a form of NAT that uses **port numbers** to allow multiple devices to share a public IP address.

Simple comparison:

```text id="7l5t0p"
NAT:
Private IP → Public IP

PAT:
Private IP + Port → Public IP + Port
```

---

# 18. Advantages of NAT

NAT provides several benefits:

### IPv4 Address Conservation

Many private devices can share a smaller number of public IPv4 addresses.

### Internal Addressing

Organizations can use private IP address ranges internally.

### Network Flexibility

Internal addressing can often be changed without requiring a corresponding change to public addressing.

### Some Exposure Reduction

NAT can make unsolicited direct connections to internal private addresses more difficult, although **NAT should not be treated as a firewall or complete security control**.

---

# 19. Disadvantages of NAT

NAT also has disadvantages:

* Adds complexity
* Can complicate troubleshooting
* Can interfere with some protocols/applications
* Port forwarding may be required for incoming connections
* Can make end-to-end connectivity more complicated
* Can complicate some peer-to-peer applications

---

# 20. NAT vs Firewall

NAT and firewalls are different.

### NAT

Primarily translates addresses and, in PAT, ports.

### Firewall

Controls whether network traffic is allowed or blocked based on configured security rules.

Example:

```text id="wm7c2a"
Internet
   ↓
Firewall → Allow / Block
   ↓
NAT → Translate
   ↓
Internal Network
```

A device can perform both NAT and firewall functions, but they are conceptually different.

---

# 21. NAT Example

Suppose:

```text id="aq0q0k"
Laptop:
192.168.1.10

Router:
192.168.1.1
Public IP:
203.0.113.10
```

The laptop sends traffic to a website.

```text id="i4x9hj"
Laptop
192.168.1.10
      ↓
Router
      ↓
NAT/PAT
      ↓
203.0.113.10
      ↓
Internet
```

The router records the translation so that the returning traffic can be sent back to the correct laptop.

---

# 22. NAT in a Network Diagram

```text id="d0v4ai"
          Private Network
   ┌─────────────────────────┐
   │                         │
   │ PC1  192.168.1.10       │
   │ PC2  192.168.1.11       │
   │ PC3  192.168.1.12       │
   │                         │
   └────────────┬────────────┘
                │
                ↓
          NAT/PAT Router
                │
        Public IP:
        203.0.113.10
                │
                ↓
             Internet
```

All three computers can use the same public IP when PAT is used.

---

# 23. Important Points to Remember

* NAT = **Network Address Translation**.
* NAT translates IP addresses between networks.
* Private IP addresses are commonly translated to public IP addresses.
* Static NAT provides a fixed one-to-one mapping.
* Dynamic NAT uses a pool of public IP addresses.
* PAT allows many private devices to share one public IP using port numbers.
* PAT is also called NAT Overload.
* Port forwarding allows incoming traffic to be directed to an internal service.
* NAT and firewall are different concepts.
* NAT is widely used with IPv4 because public IPv4 addresses are limited.
* NAT is not a replacement for a firewall.
