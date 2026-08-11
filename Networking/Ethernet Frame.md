# Ethernet Frame

## 1. What is an Ethernet Frame?

An Ethernet frame is a unit of data used to transmit information over an Ethernet network.

It is created at the **Data Link Layer (Layer 2)** of the OSI model.

An Ethernet frame contains information such as the source MAC address, destination MAC address, and the data being transmitted.

---

## 2. Ethernet Frame Structure

A basic Ethernet frame looks like this:

```text
+---------------------------+
| Preamble                  |
+---------------------------+
| SFD                       |
+---------------------------+
| Destination MAC Address   |
+---------------------------+
| Source MAC Address        |
+---------------------------+
| EtherType / Length        |
+---------------------------+
| Payload / Data            |
+---------------------------+
| FCS                       |
+---------------------------+
```

Each field has a specific purpose.

---

## 3. Preamble

The **Preamble** is used to synchronize the sender and receiver before the actual Ethernet frame begins.

* Size: **7 bytes**
* Helps the receiver synchronize with the incoming data.

It consists of a repeating pattern of bits.

---

## 4. SFD (Start Frame Delimiter)

SFD stands for **Start Frame Delimiter**.

* Size: **1 byte**
* It indicates that the actual Ethernet frame is about to begin.

The SFD comes immediately after the Preamble.

---

## 5. Destination MAC Address

The Destination MAC Address identifies the device that should receive the Ethernet frame.

* Size: **6 bytes**
* It is the MAC address of the intended receiver.

Example:

```text
Destination MAC:
AA:BB:CC:DD:EE:FF
```

A broadcast frame uses:

```text
FF:FF:FF:FF:FF:FF
```

---

## 6. Source MAC Address

The Source MAC Address identifies the device that sent the Ethernet frame.

* Size: **6 bytes**

Example:

```text
Source MAC:
11:22:33:44:55:66
```

Therefore:

```text
Source MAC      → Sender
Destination MAC → Receiver
```

---

## 7. EtherType / Length

The EtherType field tells the receiving device what type of protocol is contained inside the payload.

It is **2 bytes** long.

Common EtherType values:

```text
0x0800 → IPv4
0x0806 → ARP
0x86DD → IPv6
```

For example, if EtherType is `0x0800`, the payload contains an IPv4 packet.

---

## 8. Payload / Data

The Payload contains the actual data being transmitted.

For example:

```text
Ethernet Frame
      ↓
Payload
      ↓
IPv4 Packet
      ↓
TCP Segment
      ↓
Application Data
```

The normal Ethernet payload size is:

* Minimum: **46 bytes**
* Maximum: **1500 bytes**

If the actual data is smaller than 46 bytes, padding is added.

---

## 9. FCS (Frame Check Sequence)

FCS stands for **Frame Check Sequence**.

* Size: **4 bytes**
* Used to detect errors in the Ethernet frame.

The sender calculates a value using the frame data and places it in the FCS field.

The receiver performs a similar calculation.

If the values don't match, the frame is considered corrupted.

FCS is used for **error detection**, not error correction.

---

## 10. Minimum and Maximum Ethernet Frame Size

The standard Ethernet frame has:

**Minimum frame size:** 64 bytes

**Maximum frame size:** 1518 bytes

The 64-byte minimum includes:

```text
Destination MAC → 6 bytes
Source MAC      → 6 bytes
EtherType       → 2 bytes
Payload         → 46 bytes
FCS             → 4 bytes
```

Total:

```text
6 + 6 + 2 + 46 + 4 = 64 bytes
```

The Preamble and SFD are normally considered separately from the Ethernet frame size.

With an 802.1Q VLAN tag, the maximum becomes **1522 bytes**.

---

## 11. How an Ethernet Frame Travels

Suppose PC1 wants to send data to PC2.

```text
PC1 ───────> Switch ───────> PC2
```

### Step 1: PC1 creates an Ethernet frame

PC1 puts:

```text
Source MAC      → PC1's MAC
Destination MAC → PC2's MAC
```

into the frame.

### Step 2: Frame reaches the switch

The switch examines the **Source MAC** and learns which port PC1 is connected to.

It stores this information in its MAC address table.

### Step 3: Switch checks Destination MAC

The switch looks at the Destination MAC address.

If it knows where PC2 is connected, it forwards the frame only through that port.

### Step 4: PC2 receives the frame

PC2 checks the Destination MAC.

If the MAC address belongs to PC2, it accepts and processes the frame.

---

## 12. Ethernet Frame Example

Example:

```text
Destination MAC: AA:BB:CC:DD:EE:FF
Source MAC:      11:22:33:44:55:66
EtherType:       0x0800
Payload:         IPv4 Packet
FCS:             Error-checking value
```

This means:

```text
11:22:33:44:55:66
          ↓
       sends data
          ↓
AA:BB:CC:DD:EE:FF
```

The EtherType `0x0800` tells us that the payload contains an IPv4 packet.

---

## 13. Ethernet Frame vs IP Packet vs TCP Segment

These are different layers of networking.

```text
Ethernet Frame
      ↓
   IP Packet
      ↓
  TCP Segment
      ↓
 Application Data
```

### Ethernet Frame

Works mainly at **Layer 2**.

Contains:

* Source MAC
* Destination MAC
* EtherType
* Payload
* FCS

### IP Packet

Works at **Layer 3**.

Contains:

* Source IP
* Destination IP
* TTL
* Protocol
* Data

### TCP Segment

Works at **Layer 4**.

Contains:

* Source port
* Destination port
* Sequence number
* Acknowledgment number
* TCP flags
* Data

---

## 14. Important Points to Remember

* Ethernet frames operate mainly at **Layer 2**.
* MAC addresses identify devices/interfaces on the local Ethernet network.
* The Source MAC identifies the sender.
* The Destination MAC identifies the receiver.
* EtherType identifies the protocol carried in the payload.
* Payload contains the actual network-layer data.
* FCS detects transmission errors.
* Standard Ethernet frame size is **64–1518 bytes** excluding the Preamble and SFD.
* VLAN tagging can increase the maximum frame size to **1522 bytes**.
