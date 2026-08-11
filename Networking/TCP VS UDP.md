# TCP vs UDP

## 1. What is TCP?

TCP stands for **Transmission Control Protocol**.

TCP is a **connection-oriented** transport-layer protocol used to provide reliable communication between devices.

TCP operates at **Layer 4 (Transport Layer)** of the OSI model.

TCP ensures that data is:

* Delivered reliably
* Delivered in the correct order
* Checked for errors
* Retransmitted if necessary

Examples of applications that use TCP include:

* HTTPS
* HTTP
* SSH
* FTP
* SMTP

---

## 2. What is UDP?

UDP stands for **User Datagram Protocol**.

UDP is a **connectionless** transport-layer protocol.

It sends data without establishing a connection and does not guarantee that packets will arrive or arrive in the correct order.

UDP is generally faster and has less overhead than TCP.

Examples of applications that commonly use UDP include:

* DNS
* DHCP
* VoIP
* Online gaming
* Live streaming

---

## 3. TCP vs UDP

| Feature            | TCP                           | UDP                              |
| ------------------ | ----------------------------- | -------------------------------- |
| Full name          | Transmission Control Protocol | User Datagram Protocol           |
| Layer              | Transport Layer (Layer 4)     | Transport Layer (Layer 4)        |
| Connection         | Connection-oriented           | Connectionless                   |
| Reliability        | Reliable                      | No delivery guarantee            |
| Ordering           | Maintains order               | No ordering guarantee            |
| Error recovery     | Yes                           | No retransmission mechanism      |
| Flow control       | Yes                           | No                               |
| Congestion control | Yes                           | No                               |
| Speed              | Generally slower              | Generally faster                 |
| Overhead           | Higher                        | Lower                            |
| Handshake          | Yes                           | No                               |
| Use case           | Reliable data transfer        | Fast, low-overhead communication |

---

## 4. TCP Connection

TCP establishes a connection before transferring data.

It uses the **Three-Way Handshake**.

```text
Client                         Server
  |                              |
  | -------- SYN --------------> |
  |                              |
  | <------ SYN + ACK ----------- |
  |                              |
  | -------- ACK --------------> |
  |                              |
  |       Connection Ready       |
```

### Step 1: SYN

The client sends a **SYN** packet to the server.

It is requesting to establish a TCP connection.

### Step 2: SYN-ACK

The server responds with **SYN + ACK**.

This means the server received the request and is also ready to establish the connection.

### Step 3: ACK

The client sends an **ACK**.

The TCP connection is now established.

---

## 5. TCP Reliability

TCP provides reliable communication using several mechanisms.

### Acknowledgment

The receiver sends an **ACK** to confirm that data was received.

### Sequence Numbers

TCP assigns sequence numbers to data so that the receiver can:

* Put data in the correct order
* Detect missing data
* Identify duplicate data

### Retransmission

If TCP detects that data was lost, it can retransmit the missing data.

Example:

```text
Sender → Packet 1 → Receiver
Sender → Packet 2 → Receiver
Sender → Packet 3 → X Lost
Sender → Packet 4 → Receiver

Receiver requests/reports missing data
              ↓
Sender → Packet 3 → Receiver
```

---

## 6. TCP Flow Control

TCP uses **flow control** to prevent a sender from overwhelming the receiver.

TCP uses a **receive window** to indicate how much data the receiver can accept.

The sender adjusts how much data it sends based on the receiver's available capacity.

---

## 7. TCP Congestion Control

TCP also uses **congestion control** to reduce network congestion.

It adjusts the sending rate based on network conditions.

Some TCP congestion-control concepts include:

* Slow Start
* Congestion Avoidance
* Fast Retransmit
* Fast Recovery

---

## 8. TCP Flags

TCP headers contain flags that control the connection.

Important TCP flags include:

| Flag | Purpose                        |
| ---- | ------------------------------ |
| SYN  | Establish a connection         |
| ACK  | Acknowledge received data      |
| FIN  | Gracefully close a connection  |
| RST  | Immediately reset a connection |
| PSH  | Push data to the application   |
| URG  | Indicates urgent data          |

The most important ones to remember initially are:

**SYN, ACK, FIN, RST**

---

## 9. TCP Connection Termination

TCP normally uses a process involving **FIN** and **ACK** messages to close a connection.

Simplified example:

```text
Client                         Server
  |                              |
  | -------- FIN --------------> |
  | <-------- ACK -------------- |
  | <-------- FIN -------------- |
  | -------- ACK --------------> |
  |                              |
  |       Connection Closed      |
```

This is commonly referred to as the **TCP four-way termination**.

---

## 10. What is a Port Number?

A port number identifies a specific application or service on a device.

Port numbers range from:

```text
0 – 65535
```

Example:

```text
IP Address: 192.168.1.10
Port:       443
```

Together, the IP address and port identify a network endpoint.

---

## 11. Common TCP Ports

|  Port | Protocol / Service |
| ----: | ------------------ |
| 20/21 | FTP                |
|    22 | SSH                |
|    25 | SMTP               |
|    80 | HTTP               |
|   443 | HTTPS              |

---

## 12. Common UDP Ports

|  Port | Protocol / Service |
| ----: | ------------------ |
|    53 | DNS                |
| 67/68 | DHCP               |
|   123 | NTP                |
|   161 | SNMP               |

Some protocols can use both TCP and UDP depending on the application or version.

---

## 13. UDP Communication

UDP does not perform a three-way handshake.

The sender simply creates a UDP datagram and sends it.

```text
Client                         Server
  |                              |
  | -------- UDP Data ---------> |
  | -------- UDP Data ---------> |
  | -------- UDP Data ---------> |
  |                              |
```

There is no built-in guarantee that:

* The data will arrive
* The data will arrive only once
* The data will arrive in order

---

## 14. Why Use UDP?

UDP is useful when **speed and low overhead** are more important than guaranteed delivery.

Examples:

### DNS

DNS commonly uses UDP because queries and responses are usually small and fast.

### Online Gaming

Games often need fast updates. Waiting for retransmission of old information can be less useful than receiving newer information quickly.

### VoIP

For voice communication, a small amount of packet loss may be preferable to delays caused by retransmission.

### Streaming

Real-time applications may prioritize continuous delivery and low latency.

---

## 15. TCP vs UDP Example

### TCP

Imagine sending an important document.

You want to make sure:

```text
Packet 1 ✓
Packet 2 ✓
Packet 3 ✓
Packet 4 ✓
```

If Packet 3 is lost, TCP can retransmit it.

### UDP

Imagine a live game or voice call.

If one packet is lost:

```text
Packet 1 ✓
Packet 2 ✓
Packet 3 ✗
Packet 4 ✓
```

The application may continue rather than waiting for Packet 3 to be retransmitted.

---

## 16. TCP Header

A TCP segment contains fields such as:

* Source Port
* Destination Port
* Sequence Number
* Acknowledgment Number
* Header Length
* Flags
* Window Size
* Checksum
* Urgent Pointer
* Options
* Data

Simplified:

```text
+-------------------+-------------------+
| Source Port       | Destination Port  |
+-------------------+-------------------+
| Sequence Number                       |
+---------------------------------------+
| Acknowledgment Number                  |
+---------------------------------------+
| Header | Flags | Window Size          |
+---------------------------------------+
| Checksum          | Urgent Pointer    |
+---------------------------------------+
| Options                               |
+---------------------------------------+
| Data                                  |
+---------------------------------------+
```

---

## 17. UDP Header

The UDP header is much simpler.

It contains only:

* Source Port
* Destination Port
* Length
* Checksum

```text
+-------------------+-------------------+
| Source Port       | Destination Port  |
+-------------------+-------------------+
| Length            | Checksum          |
+-------------------+-------------------+
| Data                                  |
+---------------------------------------+
```

The UDP header is only **8 bytes**.

---

## 18. TCP Segment vs UDP Datagram

TCP data is commonly called a **TCP segment**.

UDP data is commonly called a **UDP datagram**.

```text
TCP:
Application Data
      ↓
TCP Segment
      ↓
IP Packet
      ↓
Ethernet Frame
```

```text
UDP:
Application Data
      ↓
UDP Datagram
      ↓
IP Packet
      ↓
Ethernet Frame
```

---

## 19. TCP vs UDP in Simple Words

### TCP

**Reliable but more overhead**

```text
Connection
    ↓
Send data
    ↓
ACK
    ↓
Retransmit if needed
    ↓
Correct order
```

### UDP

**Fast and lightweight but no delivery guarantee**

```text
Create datagram
      ↓
Send
      ↓
Continue
```

---

## 20. Important Points to Remember

* TCP and UDP operate at **Layer 4 (Transport Layer)**.
* TCP is **connection-oriented**.
* UDP is **connectionless**.
* TCP provides reliable, ordered delivery.
* UDP does not guarantee delivery or ordering.
* TCP uses acknowledgments and retransmission.
* TCP uses a **three-way handshake**.
* UDP does not use a TCP-style handshake.
* TCP has more overhead than UDP.
* UDP is useful for low-latency applications.
* Port numbers identify applications/services.
* TCP header minimum size is **20 bytes**.
* UDP header size is **8 bytes**.
