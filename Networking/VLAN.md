# VLAN (Virtual Local Area Network)

## 1. What is a VLAN?

VLAN stands for **Virtual Local Area Network**.

A VLAN is a logical way of dividing one physical network into multiple separate networks.

Instead of requiring separate physical switches for every network, VLANs allow multiple logical networks to exist on the same physical switch.

Example:

```text
                Switch
             /    |    \
           PC1   PC2   PC3
           VLAN10 VLAN10 VLAN20
```

PC1 and PC2 are in the same VLAN, while PC3 is in a different VLAN.

---

## 2. Why are VLANs Used?

VLANs are used to:

* Divide a network into smaller logical networks
* Improve network organization
* Reduce broadcast traffic
* Improve security through segmentation
* Separate different departments or groups
* Make network management easier

Example:

```text
VLAN 10 → Employees
VLAN 20 → Students
VLAN 30 → Guests
```

Even though all devices may be connected to the same physical switch, they can be logically separated.

---

## 3. VLAN and Broadcast Domain

A VLAN creates a separate **broadcast domain**.

Without VLANs:

```text
All devices
     ↓
One Broadcast Domain
```

With VLANs:

```text
VLAN 10 → Broadcast Domain 1
VLAN 20 → Broadcast Domain 2
VLAN 30 → Broadcast Domain 3
```

A broadcast sent in VLAN 10 normally does not reach devices in VLAN 20.

---

## 4. VLAN ID

Each VLAN is identified by a **VLAN ID**.

The VLAN ID ranges from:

```text
1 – 4094
```

with some IDs reserved or otherwise treated specially depending on the standard and device.

Common examples:

```text
VLAN 10
VLAN 20
VLAN 30
```

VLAN 1 is the default VLAN on many switches.

---

## 5. Access Port

An **access port** is a switch port that normally carries traffic for a single VLAN.

Example:

```text
PC1
 |
 | Access Port
 |
Switch
 |
VLAN 10
```

If a PC is connected to an access port assigned to VLAN 10, its traffic belongs to VLAN 10.

Access ports are commonly used for:

* PCs
* Printers
* Servers
* Other end devices

---

## 6. Trunk Port

A **trunk port** carries traffic for multiple VLANs over a single physical link.

Example:

```text
Switch 1                     Switch 2
   |                            |
   |-------- Trunk ------------|
       VLAN 10, 20, 30
```

Trunk links are commonly used:

* Between switches
* Between a switch and router
* Between a switch and some virtualization/network devices

---

## 7. Access Port vs Trunk Port

| Access Port                                             | Trunk Port                                |
| ------------------------------------------------------- | ----------------------------------------- |
| Usually carries one VLAN                                | Carries multiple VLANs                    |
| Used for end devices                                    | Commonly used between network devices     |
| Frames are normally sent untagged toward the end device | VLAN information is carried using tagging |
| Example: PC connection                                  | Example: Switch-to-switch connection      |

---

## 8. VLAN Tagging

When multiple VLANs travel over a trunk link, the Ethernet frame needs VLAN information.

The common standard is **IEEE 802.1Q**.

A VLAN tag is inserted into the Ethernet frame.

Simplified:

```text
+---------------------+
| Destination MAC     |
+---------------------+
| Source MAC          |
+---------------------+
| 802.1Q VLAN Tag     |
+---------------------+
| EtherType           |
+---------------------+
| Data                |
+---------------------+
| FCS                 |
+---------------------+
```

The VLAN tag contains information including the VLAN ID.

---

## 9. Native VLAN

On an 802.1Q trunk, the **native VLAN** is the VLAN whose traffic is sent untagged by default.

Example:

```text
Native VLAN → VLAN 99
```

The native VLAN should be configured consistently on both ends of a trunk.

For security, network administrators often avoid using the default VLAN as the native VLAN.

---

## 10. VLAN Example

Suppose a company has three departments:

```text
VLAN 10 → HR
VLAN 20 → IT
VLAN 30 → Finance
```

Network:

```text
                  Switch
             /      |       \
           HR       IT      Finance
         VLAN 10   VLAN 20   VLAN 30
```

Each department is placed into a separate broadcast domain.

---

## 11. Communication Between VLANs

Devices in different VLANs cannot normally communicate directly through a Layer 2 switch.

For example:

```text
PC1 → VLAN 10
PC2 → VLAN 20
```

To communicate between them, a **Layer 3 device** is required.

This is called **Inter-VLAN Routing**.

A router or Layer 3 switch can perform this routing.

```text
VLAN 10
   |
   ↓
Router / Layer 3 Switch
   |
   ↓
VLAN 20
```

---

## 12. Router-on-a-Stick

**Router-on-a-Stick** is a method of performing inter-VLAN routing using one physical router interface with multiple logical subinterfaces.

Example:

```text
              Router
                |
             Trunk
                |
              Switch
             /     \
        VLAN 10   VLAN 20
```

The router has separate subinterfaces for different VLANs.

Example:

```text
G0/0.10 → VLAN 10
G0/0.20 → VLAN 20
```

Each subinterface can have its own IP address and act as the gateway for that VLAN.

---

## 13. Layer 3 Switch

A Layer 3 switch can perform routing between VLANs.

Example:

```text
VLAN 10 ──┐
          │
          ↓
     Layer 3 Switch
          ↑
          │
VLAN 20 ──┘
```

This is commonly used in larger networks.

---

## 14. VLAN and IP Subnets

VLANs are often mapped to separate IP subnets.

Example:

```text
VLAN 10
192.168.10.0/24

VLAN 20
192.168.20.0/24

VLAN 30
192.168.30.0/24
```

This makes network segmentation easier to manage.

A common design is:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
```

---

## 15. VLAN Configuration Example

A basic Cisco switch configuration might look like:

```text
enable
configure terminal

vlan 10
name HR

vlan 20
name IT

interface fastethernet 0/1
switchport mode access
switchport access vlan 10

interface fastethernet 0/2
switchport mode access
switchport access vlan 20
```

This assigns:

```text
Port Fa0/1 → VLAN 10
Port Fa0/2 → VLAN 20
```

---

## 16. Trunk Configuration Example

Example Cisco configuration:

```text
interface gigabitethernet 0/1
switchport mode trunk
```

The interface can then carry multiple VLANs, subject to the switch's trunk configuration.

In some Cisco environments, allowed VLANs can also be specified:

```text
switchport trunk allowed vlan 10,20,30
```

---

## 17. Useful VLAN Commands

### Show VLANs

```text
show vlan brief
```

### Show trunk interfaces

```text
show interfaces trunk
```

### Show running configuration

```text
show running-config
```

These commands are commonly used on Cisco switches.

---

## 18. VLAN Security

VLANs provide **segmentation**, but VLANs alone are not a complete security solution.

Security practices include:

* Use separate VLANs for different groups
* Restrict unnecessary VLAN access
* Configure trunks carefully
* Disable unused switch ports
* Avoid unnecessary native VLAN exposure
* Use appropriate ACLs between VLANs
* Use secure management protocols such as SSH

Example:

```text
Employees VLAN
      ↓
     ACL
      ↓
Servers VLAN
```

An ACL can control which traffic is allowed between networks.

---

## 19. VLAN Hopping

**VLAN hopping** is an attack where an attacker attempts to access traffic belonging to another VLAN.

Two commonly discussed techniques are:

* Switch spoofing
* Double-tagging

Defensive measures include:

* Do not use dynamic trunk negotiation unnecessarily
* Configure user ports explicitly as access ports
* Restrict allowed VLANs on trunks
* Use a dedicated/unused native VLAN where appropriate
* Disable unused ports

Only test VLAN security on networks where you have permission.

---

## 20. VLAN Advantages

### Security

VLANs can separate users and systems into different logical networks.

### Performance

Separating broadcast domains can reduce unnecessary broadcast traffic.

### Organization

Different departments can have different VLANs.

### Flexibility

Devices can be logically grouped without requiring separate physical switches for every group.

---

## 21. VLAN Disadvantages

* Configuration can become complex in large networks.
* Inter-VLAN communication requires routing.
* Misconfiguration can cause connectivity problems.
* VLANs alone do not provide complete security.
* Troubleshooting may become more difficult as the network grows.

---

## 22. VLAN Example in a Company

Suppose a company has:

```text
VLAN 10 → HR
VLAN 20 → IT
VLAN 30 → Finance
VLAN 40 → Guest
```

IP addressing:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
VLAN 40 → 192.168.40.0/24
```

A Layer 3 switch can route between these VLANs while ACLs can control which VLANs are allowed to communicate.

---

## 23. Important Points to Remember

* VLAN = **Virtual Local Area Network**.
* VLANs logically divide a physical network.
* Each VLAN is a separate broadcast domain.
* VLANs are identified using VLAN IDs.
* Access ports normally carry one VLAN.
* Trunk ports carry multiple VLANs.
* **802.1Q** is the common VLAN tagging standard.
* Inter-VLAN communication requires Layer 3 routing.
* Router-on-a-Stick is one method of inter-VLAN routing.
* Layer 3 switches can also route between VLANs.
* VLANs are often associated with separate IP subnets.
* VLANs improve segmentation and organization.
* VLANs alone are not a complete security mechanism.
* VLAN hopping is a VLAN-related security concern.
