# Python for Reconnaissance

Python is a powerful programming language that can be used in cybersecurity to automate reconnaissance tasks, process collected information, interact with network services, and build custom security tools.

Python is especially useful because it provides built-in modules for networking, DNS, file handling, HTTP requests, regular expressions, and system interaction.

## Why Python is Useful for Reconnaissance

Python can help automate repetitive reconnaissance tasks such as:

- DNS lookups
- IP address resolution
- Port checking
- HTTP status checking
- Subdomain verification
- URL processing
- Data collection
- Log and result processing
- Report generation

Automation can make reconnaissance faster and more consistent.

## Python Modules Useful for Reconnaissance

Some useful Python modules include:

- `socket` - Network communication and DNS resolution
- `ipaddress` - IP address and network calculations
- `requests` - HTTP requests
- `subprocess` - Running system commands
- `os` - Operating system interaction
- `re` - Regular expressions
- `json` - JSON data processing
- `csv` - CSV file processing
- `argparse` - Command-line arguments
- `ssl` - TLS/SSL connections
- `urllib` - Working with URLs

## 1. DNS Resolution with Python

The `socket` module can be used to resolve a domain name to an IP address.

Example:

```python
import socket

domain = "example.com"

ip = socket.gethostbyname(domain)

print("Domain:", domain)
print("IP Address:", ip)
