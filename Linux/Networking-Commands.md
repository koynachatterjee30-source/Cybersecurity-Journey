# Linux Networking Commands

Linux provides many commands to check, configure, troubleshoot, and analyze network connections.

## IP Address & Interfaces

ip a                         # Show IP addresses and interfaces
ip addr                      # Show IP addresses
ip link                      # Show network interfaces
ip link show                 # Show interface status
ip -br a                     # Show IP addresses in short format
hostname -I                  # Show system IP address
hostname                     # Show hostname

## Network Interface Control

sudo ip link set eth0 up     # Enable interface
sudo ip link set eth0 down   # Disable interface
sudo ip link set eth0 mtu 1500 # Change MTU

## Routing

ip route                    # Show routing table
ip route show               # Show routing table
ip route get 8.8.8.8        # Show route to destination
sudo ip route add default via 192.168.1.1
sudo ip route del default

## Test Connectivity

ping google.com              # Test connectivity
ping -c 4 google.com         # Send 4 ping packets
ping 192.168.1.1             # Test local gateway

## DNS

nslookup google.com          # DNS lookup
dig google.com               # Detailed DNS lookup
dig A google.com              # Find IPv4 address
dig MX google.com             # Find mail servers
host google.com               # DNS lookup

## Network Connections & Ports

ss                           # Show network connections
ss -tuln                     # Show listening TCP/UDP ports
ss -tulpn                    # Show ports and processes
ss -tn                      # Show TCP connections
ss -un                      # Show UDP connections

## Older Network Commands

netstat -tuln                # Show listening ports
netstat -an                  # Show all connections
netstat -rn                  # Show routing table

## ARP

arp -a                       # Show ARP table
ip neigh                     # Show ARP/neighbour table
sudo ip neigh flush all      # Clear neighbour table

## Traceroute

traceroute google.com        # Trace network path
tracepath google.com         # Trace network path

## Download & HTTP

curl https://example.com     # Send HTTP request
curl -I https://example.com  # Show HTTP headers
wget https://example.com/file # Download file

## Network Configuration

nmcli device status          # Show network devices
nmcli connection show        # Show network connections
nmcli device wifi list       # Show available Wi-Fi networks
nmcli networking             # Show networking status

## Network Manager

sudo systemctl status NetworkManager
sudo systemctl restart NetworkManager

## Hostname

hostname                     # Show hostname
hostname -I                  # Show IP address
hostnamectl                  # Show hostname/system information

## MAC Address

ip link show                 # Show MAC address
ip link show eth0            # Show MAC address of interface

## Firewall

sudo ufw status              # Check firewall status
sudo ufw enable              # Enable firewall
sudo ufw disable             # Disable firewall
sudo ufw status verbose      # Detailed firewall status

## Network Information

ip a                         # IP address information
ip route                     # Routing information
ip neigh                     # Neighbour/ARP information
ss -tulpn                    # Open/listening ports
nmcli device status          # Network devices
cat /etc/resolv.conf         # DNS configuration
cat /etc/hosts               # Local hostname mappings

## Useful Troubleshooting Commands

ping 8.8.8.8                 # Test Internet connectivity
ping google.com              # Test DNS + connectivity
ip a                         # Check IP address
ip route                     # Check default gateway
nslookup google.com          # Check DNS
dig google.com               # Detailed DNS check
traceroute google.com        # Find network path
ss -tulpn                    # Check listening ports
curl -I https://google.com   # Test HTTP/HTTPS

## Important Commands

ip
ping
ss
netstat
nslookup
dig
host
traceroute
tracepath
curl
wget
arp
ip neigh
route
nmcli
hostname
ufw

## Key Concepts

IP Address       → Identifies a device on a network
MAC Address      → Hardware/network interface address
Port             → Identifies a network service
DNS              → Converts domain names to IP addresses
Gateway          → Connects the local network to other networks
Routing Table    → Determines where network traffic is sent
ARP              → Maps IPv4 addresses to MAC addresses
TCP              → Connection-oriented transport protocol
UDP              → Connectionless transport protocol

## Quick Networking Workflow

ip a
ip route
ping 8.8.8.8
ping google.com
nslookup google.com
ss -tulpn
traceroute google.com

# Note

Some commands such as arp, netstat, and ifconfig may not be installed
by default on modern Linux systems. The ip and ss commands are
preferred on modern Linux distributions.
