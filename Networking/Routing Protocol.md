# Routing Protocols

## 1. What is a Routing Protocol?

A routing protocol is a set of rules used by routers to **exchange information about networks and learn routes automatically**.

Instead of manually configuring every route, routers can use routing protocols to discover and maintain routes.

Example:

```text id="z7h3s8"
Network A
   |
 Router 1
   |
 Router 2
   |
Network B
```

Router 1 can learn how to reach Network B from Router 2 using a routing protocol.

---

## 2. Why are Routing Protocols Used?

Routing protocols are used to:

* Discover available networks
* Exchange routing information
* Select the best path
* Adapt to network changes
* Maintain routing tables
* Provide redundancy

For example, if one link fails:

```text id="2m4h6g"
        Router 2
       /        \
Router 1        Router 3
       \        /
        Router 4
```

A routing protocol may find another available path.

---

# 3. Static Routing vs Dynamic Routing

There are two major ways routers can learn routes.

### Static Routing

Routes are manually configured by an administrator.

Example:

```text id="c8h5kx"
Network: 192.168.20.0/24
Next Hop: 192.168.1.2
```

Advantages:

* Simple for small networks
* No routing protocol overhead
* Predictable

Disadvantages:

* Manual configuration
* Difficult to maintain in large networks
* Does not automatically adapt to failures

---

### Dynamic Routing

Routes are learned automatically using routing protocols.

Examples:

* RIP
* OSPF
* EIGRP
* IS-IS
* BGP

Advantages:

* Automatic route learning
* Can adapt to network changes
* Suitable for larger networks

Disadvantages:

* More complex
* Uses CPU, memory, and bandwidth
* Requires proper configuration

---

# 4. Types of Routing Protocols

Routing protocols can be classified in different ways.

The major categories to know are:

### IGP

IGP stands for **Interior Gateway Protocol**.

Used for routing **within an organization or autonomous system**.

Examples:

* RIP
* OSPF
* EIGRP
* IS-IS

### EGP

EGP refers to routing between different autonomous systems.

The main modern protocol is:

* BGP

---

# 5. Autonomous System (AS)

An **Autonomous System (AS)** is a group of IP networks and routers under a common administrative control and routing policy.

Each AS is identified using an **ASN (Autonomous System Number)**.

Example:

```text id="t5sp1p"
AS 65001
     |
     | BGP
     |
AS 65002
```

BGP is commonly used to exchange routing information between autonomous systems.

---

# 6. Distance Vector Routing

Distance-vector protocols determine routes based on information received from neighboring routers.

Routers generally share routing information with their neighbors.

The router considers factors such as:

* Distance
* Metric
* Next hop

Example:

```text id="tgjl4k"
Router A → Router B → Router C
```

Router A can learn about Network C through Router B.

Examples:

* RIP
* EIGRP is often described as an advanced distance-vector/hybrid protocol

---

# 7. Link-State Routing

Link-state protocols build a more complete view of the network topology.

Routers exchange information about their links and use that information to calculate paths.

Example:

```text id="f0n7pw"
Router A ─ Router B
   |          |
   |          |
Router C ─ Router D
```

Each router can build a topology database and calculate the best path.

Examples:

* OSPF
* IS-IS

---

# 8. Path-Vector Routing

Path-vector routing uses information about the path through autonomous systems.

The main example is:

**BGP (Border Gateway Protocol)**

BGP uses attributes and AS-path information to select routes.

Example:

```text id="k2m9gc"
AS 100
   |
AS 200
   |
AS 300
```

BGP can learn that a route is reachable through:

```text id="8z2v0k"
AS 100 → AS 200 → AS 300
```

---

# 9. RIP

RIP stands for **Routing Information Protocol**.

RIP is a simple distance-vector routing protocol.

It uses **hop count** as its routing metric.

### Maximum Hop Count

RIP supports a maximum of **15 hops**.

A metric of:

```text id="f9c3v6"
16 = Unreachable
```

### RIP Versions

* RIPv1
* RIPv2
* RIPng for IPv6

RIPv2 supports features such as classless routing and authentication.

---

# 10. OSPF

OSPF stands for **Open Shortest Path First**.

OSPF is a **link-state IGP**.

It is widely used in enterprise networks.

OSPF uses the **Shortest Path First (SPF)** algorithm, commonly associated with Dijkstra's algorithm, to calculate paths.

### OSPF Metric

OSPF uses **cost** as its primary routing metric.

The cost is commonly related to interface bandwidth.

Example:

```text id="qjz1a4"
Router A
   |
   | Cost 10
   |
Router B
   |
   | Cost 20
   |
Router C
```

Total path cost:

```text id="c1m5f0"
10 + 20 = 30
```

OSPF selects paths based on the lowest total cost.

---

# 11. OSPF Areas

OSPF can divide a large network into **areas**.

The backbone area is:

```text id="g4b5yf"
Area 0
```

Other areas can connect to the backbone.

Example:

```text id="3v1w5j"
       Area 1
          |
          |
       Area 0
       /    \
   Area 2   Area 3
```

Area 0 is called the **backbone area**.

---

# 12. EIGRP

EIGRP stands for **Enhanced Interior Gateway Routing Protocol**.

It was developed by Cisco.

EIGRP is often classified as an **advanced distance-vector** or hybrid routing protocol.

It uses the **DUAL (Diffusing Update Algorithm)** to calculate loop-free routes and can converge quickly.

EIGRP considers multiple factors, including:

* Bandwidth
* Delay

Other factors such as reliability and load can be configured as part of the metric calculation, but they are not included by default.

---

# 13. IS-IS

IS-IS stands for **Intermediate System to Intermediate System**.

It is a **link-state routing protocol**.

It is commonly used in:

* Service provider networks
* Large enterprise networks

It is similar in overall concept to OSPF but has its own protocol design and terminology.

---

# 14. BGP

BGP stands for **Border Gateway Protocol**.

BGP is the main routing protocol used to exchange routes between autonomous systems on the Internet.

It is a **path-vector routing protocol**.

Example:

```text id="ppw3ml"
AS 100
   |
   | BGP
   |
AS 200
   |
   | BGP
   |
AS 300
```

BGP considers routing attributes and policies when selecting routes.

---

# 15. BGP Path Attributes

Some important BGP attributes include:

* AS Path
* Local Preference
* MED
* Origin
* Next Hop

These attributes help determine which route should be preferred.

---

# 16. Administrative Distance

**Administrative Distance (AD)** is a Cisco concept used to indicate how trustworthy a route source is when routes to the same destination are learned from different sources.

Common Cisco defaults include:

| Route Source | Administrative Distance |
| ------------ | ----------------------: |
| Connected    |                       0 |
| Static       |                       1 |
| EIGRP        |                      90 |
| OSPF         |                     110 |
| RIP          |                     120 |

Lower administrative distance is preferred.

Note: Administrative distance is **not the same thing as a routing protocol metric**.

---

# 17. Routing Metric

A **metric** is a value used by a routing protocol to compare routes learned through that protocol.

Different protocols use different metrics.

| Protocol | Main Metric            |
| -------- | ---------------------- |
| RIP      | Hop count              |
| OSPF     | Cost                   |
| EIGRP    | Composite metric       |
| BGP      | Path attributes/policy |

Example:

```text id="d9v6n0"
Path A → Metric 10
Path B → Metric 20
```

The protocol generally prefers the path with the better metric according to its rules.

---

# 18. Convergence

**Convergence** is the process by which routers update their routing information after a network change and reach a consistent view of the network.

Example:

```text id="d6i7e2"
Before:

R1 ─── R2 ─── R3


Link R2-R3 fails:

R1 ─── R2     R3
```

A routing protocol can detect the change and calculate an alternative route if one exists.

Faster convergence generally means the network can recover more quickly from failures.

---

# 19. Routing Table

A router stores learned and configured routes in a **routing table**.

Example:

```text id="l1l2jd"
Destination        Next Hop
192.168.10.0/24    Directly Connected
192.168.20.0/24    192.168.1.2
10.0.0.0/8         192.168.1.3
```

The router uses the routing table to determine where to forward packets.

---

# 20. How Dynamic Routing Works

Basic process:

```text id="2cx0mg"
Router 1
   |
   | Exchange routing information
   ↓
Router 2
   |
   ↓
Build routing information
   |
   ↓
Calculate best path
   |
   ↓
Install route in routing table
```

If the network changes, routers exchange updated information and may select a different route.

---

# 21. Routing Protocol Comparison

| Protocol | Type                     | Main Use                        | Metric/Selection      |
| -------- | ------------------------ | ------------------------------- | --------------------- |
| RIP      | Distance Vector          | Small/legacy networks           | Hop count             |
| OSPF     | Link State               | Enterprise networks             | Cost                  |
| EIGRP    | Advanced Distance Vector | Mainly Cisco environments       | Composite metric      |
| IS-IS    | Link State               | Large/service provider networks | Cost                  |
| BGP      | Path Vector              | Inter-AS/Internet routing       | Attributes and policy |

---

# 22. Practical Cisco Commands

### Show routing table

```text id="m3v4gz"
show ip route
```

### Show OSPF neighbors

```text id="2uy5eu"
show ip ospf neighbor
```

### Show OSPF information

```text id="f6u5be"
show ip ospf
```

### Show BGP summary

```text id="y7e9t1"
show ip bgp summary
```

### Show running configuration

```text id="v6z4qf"
show running-config
```

These commands are commonly used on Cisco devices.

---

# 23. Routing Protocols and Cybersecurity

Understanding routing protocols is important in cybersecurity because routing determines how traffic moves through a network.

Security professionals should understand:

* Routing tables
* Route manipulation
* Network segmentation
* Routing protocol authentication
* Unauthorized routing changes
* Traffic redirection
* Network monitoring

Incorrect or malicious routing changes can potentially redirect network traffic.

Routing protocol security should therefore be properly configured and monitored.

Only test routing security on networks where you have permission.

---

# 24. Important Points to Remember

* Routing protocols allow routers to learn routes dynamically.
* Static routing is manually configured.
* Dynamic routing uses routing protocols.
* IGPs operate within an autonomous system.
* BGP is used primarily between autonomous systems.
* RIP uses hop count.
* OSPF is a link-state protocol and uses cost.
* EIGRP is an advanced distance-vector protocol.
* IS-IS is a link-state protocol.
* BGP is a path-vector protocol.
* Administrative Distance and routing metrics are different concepts.
* Convergence is the process of routers adapting to network changes.
* Routing tables contain routes used for packet forwarding.
