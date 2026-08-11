# ARP (Address Resolution Protocol)

## 1. What is ARP?

ARP stands for **Address Resolution Protocol**.

ARP is used to find the **MAC address of a device when its IPv4 address is known**.

In simple words:

```text
IP Address → MAC Address
```

ARP is used on a local network.

---

## 2. Why is ARP Needed?

IP addresses are used at **Layer 3 (Network Layer)**, while MAC addresses are used at **Layer 2 (Data Link Layer)**.

When a device wants to send data to another device on the same local network, it needs the destination MAC address to create an Ethernet frame.

For example:

```text
IP Address:
192.168.1.20

       ↓ ARP

MAC Address:
AA:BB:CC:DD:EE:FF
```

ARP helps find the MAC address associated with an IPv4 address.

---

## 3. Where Does ARP Work?

ARP works between:

* **Network Layer (Layer 3)**
* **Data Link Layer (Layer 2)**

ARP is mainly associated with **IPv4**.

IPv6 does not use ARP. IPv6 uses **Neighbor Discovery Protocol (NDP)** instead.

---

## 4. How ARP Works

Suppose PC1 wants to communicate with PC2.

```text
PC1                         PC2
IP: 192.168.1.10            IP: 192.168.1.20
MAC: AA:AA:AA:AA:AA:AA      MAC: BB:BB:BB:BB:BB:BB
```

PC1 knows PC2's IP address:

```text
192.168.1.20
```

But PC1 does not know PC2's MAC address.

So PC1 sends an **ARP Request**.

---

## 5. ARP Request

PC1 broadcasts an ARP request to the local network:

```text
"Who has 192.168.1.20?"
```

The destination MAC address is:

```text
FF:FF:FF:FF:FF:FF
```

This is the broadcast MAC address.

All devices on the local network receive the request.

---

## 6. ARP Reply

The device that owns `192.168.1.20` responds.

PC2 sends an ARP Reply to PC1:

```text
"192.168.1.20 is at
BB:BB:BB:BB:BB:BB"
```

The reply is normally sent as a **unicast** Ethernet frame to PC1.

PC1 can now communicate with PC2 using its MAC address.

---

## 7. ARP Process

The complete process is:

```text
PC1
 |
 | ARP Request (Broadcast)
 | "Who has 192.168.1.20?"
 ↓
Switch
 |
 ↓
PC2
 |
 | ARP Reply (Unicast)
 | "192.168.1.20 is at BB:BB:BB:BB:BB:BB"
 ↓
PC1
```

Then PC1 can send normal Ethernet frames to PC2.

---

## 8. ARP Cache / ARP Table

Devices store recently learned IP-to-MAC mappings in an **ARP cache/table**.

Example:

```text
IP Address       MAC Address
192.168.1.20     BB:BB:BB:BB:BB:BB
192.168.1.30     CC:CC:CC:CC:CC:CC
```

This prevents the device from sending an ARP request every time it needs to communicate.

ARP entries can expire and be learned again.

---

## 9. How to View ARP Information in Linux

Use:

```bash
ip neigh
```

Example output:

```text
192.168.1.1 dev eth0 lladdr AA:BB:CC:DD:EE:FF REACHABLE
```

Here:

```text
192.168.1.1
    ↓
IP Address

AA:BB:CC:DD:EE:FF
    ↓
MAC Address
```

You can also use:

```bash
arp -a
```

if the `arp` utility is installed.

---

## 10. ARP Request vs ARP Reply

| ARP Request                        | ARP Reply                           |
| ---------------------------------- | ----------------------------------- |
| Usually broadcast                  | Usually unicast                     |
| Asks for a MAC address             | Provides the MAC address            |
| Sent when MAC is unknown           | Sent by the device that owns the IP |
| Destination MAC: FF:FF:FF:FF:FF:FF | Destination MAC: Requester's MAC    |

---

## 11. ARP Packet Fields

An ARP message contains information such as:

* Hardware Type
* Protocol Type
* Hardware Address Length
* Protocol Address Length
* Operation
* Sender MAC Address
* Sender IP Address
* Target MAC Address
* Target IP Address

For Ethernet + IPv4, common values include:

```text
Hardware Type: Ethernet
Protocol Type: IPv4
Operation: Request or Reply
```

---

## 12. ARP and the Default Gateway

ARP is also used when communicating with a device outside the local network.

Suppose:

```text
PC IP:       192.168.1.10
Destination: 8.8.8.8
Gateway:     192.168.1.1
```

PC1 does **not** need the MAC address of `8.8.8.8`.

Instead, it needs the MAC address of its **default gateway**:

```text
192.168.1.1 → Gateway MAC Address
```

PC1 uses ARP to find the gateway's MAC address.

Then the Ethernet frame is sent to the router.

---

## 13. ARP Spoofing

ARP does not provide strong authentication.

An attacker on the same local network can send false ARP messages to associate their MAC address with another device's IP address.

Example:

```text
Real:

192.168.1.1 → Router MAC


Attacker tries:

192.168.1.1 → Attacker MAC
```

This technique is called **ARP spoofing** or **ARP poisoning**.

It can potentially be used for:

* Man-in-the-middle attacks
* Traffic interception
* Network disruption

ARP spoofing should only be studied or tested on networks where you have permission.

---

## 14. ARP vs DNS

ARP and DNS are different.

| ARP                                    | DNS                               |
| -------------------------------------- | --------------------------------- |
| Finds MAC address from IPv4 address    | Finds IP address from domain name |
| Used on local network                  | Used for domain-name resolution   |
| Example: IP → MAC                      | Example: google.com → IP          |
| Works with Ethernet/IPv4 communication | Application-layer service         |

Example:

```text
ARP:
192.168.1.20 → MAC Address

DNS:
example.com → IP Address
```

---

## 15. ARP vs DHCP

ARP and DHCP also have different purposes.

**DHCP** gives a device network configuration such as:

* IP address
* Subnet mask
* Default gateway
* DNS server

**ARP** finds the MAC address associated with an IPv4 address on the local network.

---

## 16. Practical Lab

### Step 1: Check your network interface

```bash
ip addr
```

### Step 2: Check your ARP/neighbor table

```bash
ip neigh
```

### Step 3: Ping a device on your local network

```bash
ping 192.168.1.1
```

Replace the IP address with your actual gateway or another device on your network.

### Step 4: Check the neighbor table again

```bash
ip neigh
```

You may see a new IP-to-MAC mapping.

---

## 17. ARP in One Diagram

```text
        PC1
IP: 192.168.1.10
MAC: AA:AA:AA:AA:AA:AA
        |
        | ARP Request (Broadcast)
        | "Who has 192.168.1.20?"
        ↓
      Switch
        |
        ↓
        PC2
IP: 192.168.1.20
MAC: BB:BB:BB:BB:BB:BB
        |
        | ARP Reply
        | "192.168.1.20 is at
        |  BB:BB:BB:BB:BB:BB"
        ↓
       PC1
```

## 18. Important Points to Remember

* ARP = **Address Resolution Protocol**.
* ARP maps an **IPv4 address to a MAC address**.
* ARP is used on the local network.
* ARP Request is normally **broadcast**.
* ARP Reply is normally **unicast**.
* Broadcast MAC address is `FF:FF:FF:FF:FF:FF`.
* ARP information is stored in an ARP/neighbor cache.
* Linux command: `ip neigh`.
* IPv6 uses **NDP instead of ARP**.
* ARP spoofing can be used in attacks such as **Man-in-the-Middle**.
