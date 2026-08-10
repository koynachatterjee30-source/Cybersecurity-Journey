# MAC Address

## 1. What is a MAC Address?

A MAC (Media Access Control) address is a unique hardware address assigned to a network interface. It is used to identify a device on a local network.

Example:

`00:1A:2B:3C:4D:5E`

---

## 2. Why is a MAC Address used?

MAC addresses are used to identify devices and deliver Ethernet frames to the correct device within a local network.

A switch uses MAC addresses to decide where to forward Ethernet frames.

---

## 3. MAC Address Format

A MAC address is normally written as 6 groups of hexadecimal numbers.

Example:

`00:1A:2B:3C:4D:5E`

Each group contains 2 hexadecimal digits.

A MAC address is **48 bits (6 bytes)** long.

---

## 4. 48-bit MAC Address

A standard MAC address contains 48 bits.

`48 bits = 6 bytes`

Example:

`00:1A:2B:3C:4D:5E`

Each hexadecimal pair represents 1 byte.

---

## 5. OUI

OUI stands for **Organizationally Unique Identifier**.

The first 24 bits (3 bytes) of a MAC address identify the manufacturer/vendor.

Example:

`00:1A:2B : 3C:4D:5E`

* `00:1A:2B` → OUI / manufacturer part
* `3C:4D:5E` → device-specific part

---

## 6. NIC-specific Identifier

The remaining 24 bits are used to identify the network interface/device within the manufacturer's assigned range.

So a MAC address can be viewed as:

`Manufacturer part + Device-specific part`

---

## 7. Unicast MAC Address

A unicast MAC address identifies a single network interface.

Communication:

`Device A → Device B`

Only the intended device receives the frame.

---

## 8. Multicast MAC Address

A multicast MAC address is used to send an Ethernet frame to a specific group of devices.

Communication:

`One sender → Multiple selected devices`

---

## 9. Broadcast MAC Address

The broadcast MAC address is:

`FF:FF:FF:FF:FF:FF`

A frame sent to this address is intended for all devices in the local broadcast domain.

---

## 10. Source MAC & Destination MAC

An Ethernet frame contains both:

* **Source MAC** → MAC address of the sender
* **Destination MAC** → MAC address of the intended receiver

Example:

```text
Source MAC:      AA:AA:AA:AA:AA:AA
Destination MAC: BB:BB:BB:BB:BB:BB
```

---

## 11. MAC Address vs IP Address

| MAC Address                                 | IP Address                                         |
| ------------------------------------------- | -------------------------------------------------- |
| Works mainly at Layer 2                     | Works at Layer 3                                   |
| Identifies network interface                | Identifies device/interface logically on a network |
| Used by Ethernet                            | Used by IP                                         |
| Used by switches                            | Used by routers                                    |
| Usually associated with a network interface | Can change depending on the network                |

Example:

```text
MAC: AA:BB:CC:DD:EE:FF
IP:  192.168.1.10
```

---

## 12. How to Find MAC Address in Linux

Use:

```bash
ip link
```

or:

```bash
ip addr
```

Look for the `link/ether` field.

Example:

```text
link/ether 00:1a:2b:3c:4d:5e
```

This is the MAC address of the network interface.
