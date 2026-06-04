# Switching

## What is Switching?

Switching is the process of forwarding data frames between devices within the same network using a switch.

## What is a Switch?

A switch is a network device that connects multiple devices in a Local Area Network (LAN) and sends data only to the intended destination device.

## How Switching Works

- A switch learns the MAC addresses of connected devices.
- It stores these addresses in a MAC address table.
- When a frame arrives, the switch forwards it to the correct port.

## Types of Switching

### Store-and-Forward Switching
- Receives the entire frame before forwarding.
- Checks for errors before transmission.

### Cut-Through Switching
- Starts forwarding as soon as the destination address is read.
- Faster but performs less error checking.

## Advantages of Switching

- Reduces network congestion
- Improves network performance
- Provides dedicated bandwidth to devices
- Supports communication within a LAN

## MAC Address Table

A switch maintains a MAC address table that maps device MAC addresses to switch ports.

## Practical Learning

- Connected PCs using a switch in Cisco Packet Tracer
- Observed MAC address learning
- Tested communication between devices
- Configured basic network topologies
