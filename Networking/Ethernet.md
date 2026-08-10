# Ethernet

## 1. What is Ethernet?

Ethernet is a networking technology used to connect devices in a Local Area Network (LAN) and exchange data between them.

Ethernet mainly operates at **Layer 2 (Data Link Layer)** of the OSI model and uses **MAC addresses** to identify devices.

---

## 2. Where is Ethernet used?

Ethernet is commonly used in:

* Computers
* Servers
* Network switches
* Routers
* Printers
* Other network devices

Example:

```text
PC 1 ────── Switch ────── PC 2
```

The devices communicate using Ethernet frames.

---

## 3. Ethernet and MAC Address

Ethernet uses MAC addresses to identify the sender and receiver of data.

Example:

```text
Source MAC:      AA:AA:AA:AA:AA:AA
Destination MAC: BB:BB:BB:BB:BB:BB
```

The switch reads these MAC addresses to forward the frame to the correct device.

---

## 4. Ethernet Frame

Data is transmitted over Ethernet in the form of an **Ethernet frame**.

Basic structure:

```text
+---------------------+
| Destination MAC     |
+---------------------+
| Source MAC          |
+---------------------+
| EtherType           |
+---------------------+
| Data / Payload      |
+---------------------+
| FCS                 |
+---------------------+
```

The Ethernet frame contains the MAC addresses and the actual data being transmitted.

---

## 5. Ethernet Cable

Traditional wired Ethernet commonly uses twisted-pair cables.

Common cable categories include:

* Cat5e
* Cat6
* Cat6a

Ethernet cables use an **RJ-45 connector** for common copper Ethernet connections.

---

## 6. Ethernet Speed

Common Ethernet speeds include:

* 10 Mbps
* 100 Mbps (Fast Ethernet)
* 1 Gbps (Gigabit Ethernet)
* 10 Gbps

Modern networks commonly use Gigabit Ethernet or faster.

---

## 7. Full-Duplex and Half-Duplex

### Full-Duplex

Devices can send and receive data at the same time.

```text
PC A  <───────>  Switch
```

### Half-Duplex

A device can either send or receive at a given time, but not both simultaneously.

Half-duplex is mostly associated with older shared Ethernet networks.

---

## 8. Ethernet Switch

A switch connects multiple devices in a LAN.

It learns the MAC addresses of connected devices and stores them in a **MAC address table**.

Example:

```text
PC1 ──┐
PC2 ──┼── Switch
PC3 ──┘
```

The switch uses the destination MAC address to decide which port should receive the frame.

---

## 9. Ethernet Standards

Some common Ethernet standards are:

| Standard            |    Speed |
| ------------------- | -------: |
| Ethernet            |  10 Mbps |
| Fast Ethernet       | 100 Mbps |
| Gigabit Ethernet    |   1 Gbps |
| 10 Gigabit Ethernet |  10 Gbps |

---

## 10. Ethernet vs Wi-Fi

| Ethernet              | Wi-Fi                         |
| --------------------- | ----------------------------- |
| Wired connection      | Wireless connection           |
| Uses cables           | Uses radio signals            |
| Generally more stable | More affected by interference |
| Usually lower latency | Usually higher latency        |
| Common in LANs        | Common for wireless LANs      |

Both can be used to connect devices to a network.

---

## 11. Important Terms

* Ethernet
* Ethernet frame
* MAC address
* Switch
* LAN
* RJ-45
* Full-duplex
* Half-duplex
* Fast Ethernet
* Gigabit Ethernet
* 10 Gigabit Ethernet
* MAC address table
