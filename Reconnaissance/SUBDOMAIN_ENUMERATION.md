# Subdomain Enumeration

Subdomain enumeration is the process of discovering subdomains associated with a target domain. It is an important part of reconnaissance because different subdomains may host different applications, APIs, development environments, or services.

For example, if the main domain is:

example.com

Possible subdomains could include:

www.example.com
mail.example.com
api.example.com
dev.example.com
blog.example.com

In authorized security testing, discovering these subdomains helps security professionals understand the organization's external attack surface.

## Why Subdomain Enumeration is Important

Organizations may have many services hosted under different subdomains.

Subdomain enumeration can help identify:

- Web applications
- APIs
- Mail servers
- Development environments
- Testing environments
- VPN portals
- Cloud services
- Internal-looking names that are publicly exposed
- Forgotten or unused infrastructure

Finding these assets allows security teams to check whether they are properly secured.

## Types of Subdomain Enumeration

There are two main approaches:

### 1. Passive Subdomain Enumeration

Passive enumeration collects subdomain information from publicly available sources without directly interacting with the target's infrastructure.

Sources may include:

- Search engines
- Certificate Transparency logs
- Public DNS databases
- Security datasets
- Public repositories
- Internet search engines

Common tools include:

- Subfinder
- Amass
- Certificate Transparency services

Passive enumeration is generally less intrusive.

### 2. Active Subdomain Enumeration

Active enumeration directly interacts with DNS infrastructure or the target environment to discover subdomains.

Common techniques include:

- DNS brute-forcing
- DNS queries
- Wordlist-based discovery
- DNS resolution testing

Active enumeration can generate noticeable traffic and should only be performed when it is within the authorized testing scope.

## Subdomain Enumeration Methodology

A basic workflow can be:

1. Identify the authorized target domain
2. Perform passive enumeration
3. Collect discovered subdomains
4. Remove duplicate results
5. Resolve discovered subdomains
6. Perform active enumeration if authorized
7. Verify live hosts
8. Organize the results
9. Document the findings

## Certificate Transparency

Certificate Transparency (CT) logs contain information about publicly issued TLS certificates.

When certificates are issued for domains and subdomains, their names may become visible through CT logs.

This can sometimes reveal subdomains such as:

```text
api.example.com
dev.example.com
mail.example.com
vpn.example.com
