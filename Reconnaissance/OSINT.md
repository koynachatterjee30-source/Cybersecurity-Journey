# OSINT - Open Source Intelligence

OSINT stands for Open Source Intelligence. It is the process of collecting, analyzing, and using information that is publicly available from open and legal sources.

In cybersecurity, OSINT is commonly used during reconnaissance to understand a target's publicly exposed information, digital footprint, infrastructure, technologies, and potential attack surface.

## Why OSINT is Important

OSINT helps cybersecurity professionals collect information before performing security testing.

It can help identify:

- Domains and subdomains
- IP addresses
- DNS information
- Email addresses
- Usernames
- Publicly exposed files
- Technologies and services
- Social media presence
- Public repositories
- Company information
- Metadata
- Potentially exposed credentials or secrets

## Common Sources of OSINT

Information can be collected from many publicly available sources.

### Search Engines

Search engines can be used to discover publicly indexed information.

Examples:

- Google
- Bing
- DuckDuckGo

Search operators can help narrow search results.

Examples:

- `site:example.com`
- `site:example.com filetype:pdf`
- `site:example.com login`
- `"example.com"`

These techniques should only be used for authorized security research.

## Domain Information

Domain information can provide useful details about an organization's online infrastructure.

Information may include:

- Domain name
- Subdomains
- DNS records
- Name servers
- Mail servers
- IP addresses
- Domain registration information

Common tools:

- WHOIS
- dig
- nslookup
- Amass
- Subfinder

## Email Reconnaissance

Publicly available email addresses can sometimes be discovered through:

- Company websites
- Public documents
- Search engines
- Public repositories
- Professional profiles

Email reconnaissance can help security teams identify what information is publicly exposed.

It can also help organizations understand their potential phishing and social-engineering exposure.

## Username Reconnaissance

A username may be reused across multiple platforms.

Security researchers can investigate publicly available usernames to understand an individual's or organization's digital footprint.

Tools such as Sherlock can be used for authorized username research.

## Social Media Intelligence

Public social media profiles can contain useful information such as:

- Organization names
- Job roles
- Technologies used
- Public announcements
- Employee information
- Publicly shared documents
- Project information

Social media information should be collected and used responsibly.

## Metadata Analysis

Metadata is information stored inside files such as:

- Images
- PDFs
- Microsoft Office documents
- Videos

Metadata may contain information such as:

- Author
- Software used
- Creation date
- Modification date
- Device information
- Location information, when present

Security professionals can analyze metadata to understand what information an organization may unintentionally expose.

## GitHub and Public Repositories

Public code repositories can contain valuable information about an organization's technology stack.

Researchers may look for:

- Programming languages
- Frameworks
- API endpoints
- Configuration files
- Documentation
- Public infrastructure information
- Accidentally exposed secrets

Security researchers must not use discovered credentials or secrets to access systems without explicit authorization.

## Shodan

Shodan is a search engine that indexes information about internet-connected devices and services.

It can provide information such as:

- Open ports
- Services
- Server information
- Device types
- Software versions
- Network information

Shodan can be useful for understanding an organization's externally visible attack surface.

## Common OSINT Tools

Some commonly used OSINT tools include:

### WHOIS

Used to retrieve publicly available domain registration information.

### theHarvester

Used to gather publicly available information such as domains, subdomains, email addresses, and host information.

### Recon-ng

A reconnaissance framework that provides modules for collecting and organizing information.

### Maltego

A visual investigation and link-analysis tool used to discover relationships between entities.

### Sherlock

Used to search for usernames across multiple publicly available platforms.

### Shodan

Used to search information about internet-connected devices and services.

### Amass

Used for attack-surface mapping and subdomain discovery.

### Subfinder

Used primarily for passive subdomain enumeration.

## OSINT Workflow

A basic OSINT workflow can be:

1. Define the authorized target
2. Identify the scope
3. Collect publicly available information
4. Gather domain and DNS information
5. Search for subdomains
6. Investigate public technologies and infrastructure
7. Check publicly available documents
8. Analyze metadata where appropriate
9. Organize the collected information
10. Verify important findings
11. Document the results

## Information Verification

Not every piece of information found online is accurate.

Before considering information as a reliable finding:

- Verify it using multiple sources
- Check whether the information is current
- Confirm that the source is trustworthy
- Avoid making assumptions
- Record the source and date of discovery

## OSINT in VAPT

OSINT is commonly performed during the reconnaissance stage of VAPT.

Example workflow:

OSINT → DNS Recon → Subdomain Enumeration → Network Recon → Technology Identification → Vulnerability Assessment

OSINT helps security professionals understand what information is already publicly exposed before performing technical security testing.

## Defensive Use of OSINT

OSINT is not only useful for attackers or penetration testers.

Security teams can use OSINT to discover their own organization's exposed information.

For example, an organization can search for:

- Exposed company information
- Publicly accessible documents
- Unnecessary subdomains
- Publicly exposed services
- Accidentally published credentials
- Sensitive metadata
- Employee information

This helps organizations reduce their external attack surface.

## Legal and Ethical Considerations

OSINT should be performed responsibly.

Only collect and analyze information that you are legally permitted to access and use.

Do not:

- Access private accounts
- Bypass authentication
- Use stolen credentials
- Exploit discovered vulnerabilities without permission
- Attempt unauthorized access
- Harass or target individuals

For practice, use your own accounts and infrastructure, CTFs, authorized bug-bounty programs, and intentionally vulnerable environments.

## Learning Objective

The goal of this section is to understand how publicly available information can be collected, verified, analyzed, and used during cybersecurity reconnaissance.

OSINT provides valuable information about an organization's digital footprint and helps security professionals identify publicly exposed assets before conducting authorized security testing.
