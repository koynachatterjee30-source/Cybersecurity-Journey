# DNS Reconnaissance

DNS Reconnaissance is the process of collecting information about a domain and its DNS infrastructure. DNS stands for Domain Name System. It translates domain names into IP addresses and helps identify services such as web servers and mail servers.

DNS reconnaissance is an important part of cybersecurity reconnaissance because DNS records can reveal information about an organization's infrastructure.

## What is DNS?

DNS (Domain Name System) is a system that converts human-readable domain names into IP addresses.

For example:

example.com → IP address

Instead of remembering an IP address, users can access a website using its domain name.

DNS can also provide information about different services associated with a domain.

## Why DNS Reconnaissance is Important

DNS reconnaissance can help security professionals identify:

- Domain names
- Subdomains
- IP addresses
- Name servers
- Mail servers
- DNS servers
- DNS records
- Related infrastructure
- External services

This information can help map an organization's external attack surface.

## Common DNS Record Types

### A Record

An A record maps a domain name to an IPv4 address.

Example:

example.com → 192.0.2.10

### AAAA Record

An AAAA record maps a domain name to an IPv6 address.

### CNAME Record

A CNAME record creates an alias from one domain name to another.

Example:

www.example.com → example.com

### MX Record

MX stands for Mail Exchange.

MX records identify the mail servers responsible for receiving email for a domain.

### NS Record

NS stands for Name Server.

NS records identify the authoritative DNS servers for a domain.

### TXT Record

TXT records can contain text-based information.

They are commonly used for:

- SPF
- Domain verification
- Email security
- Other configuration information

### SOA Record

SOA stands for Start of Authority.

It contains important information about the DNS zone, including the primary name server and zone-related parameters.

## Common DNS Reconnaissance Tools

### nslookup

`nslookup` is a command-line tool used to query DNS information.

Example:

```bash
nslookup example.com
