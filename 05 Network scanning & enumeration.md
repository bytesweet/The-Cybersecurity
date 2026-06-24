# Network Scanning & Enumeration

Network Scanning & Enumeration: The process of discovering hosts, services, devices, and information within a network to understand its structure and identify potential attack surfaces.

Use: Used by security professionals to map networks, identify active systems, discover running services, and assess security posture.

How it works: Scanning tools send network requests and analyze responses to gather information about hosts, ports, operating systems, services, and network resources.

Example: A security tester identifies active hosts, open ports, and running services before conducting a security assessment.

---------------------------------------------------------
## Reconnaissance

Reconnaissance: The information-gathering phase of a security assessment where details about a target are collected before deeper testing begins.

Use: Used to understand the target environment and identify potential entry points.

How it works: Information is collected from public sources, network scans, service responses, and system enumeration.

Example: Discovering company domains, active servers, exposed services, and network infrastructure.
---------------------------------------------------------

## Network Scanning

Network Scanning: The process of identifying active devices and accessible services on a network.

Use: Used to find live hosts, open ports, and available services.

How it works: Scanning tools communicate with target systems and analyze responses to determine what is reachable.

Example: Finding web servers, mail servers, and database servers running on a network.

---------------------------------------------------------
## Enumeration

Enumeration: The process of extracting detailed information from discovered systems and services.

Use: Used to identify users, shares, software versions, network resources, and configuration details.

How it works: After discovering a service, additional queries are used to gather more specific information.

Example: Retrieving service versions, user accounts, shared resources, or domain information.

---------------------------------------------------------

## Information Commonly Discovered

Hosts: Active devices connected to the network.

Open Ports: Communication endpoints accepting connections.

Running Services: Applications listening on network ports.

Operating Systems:The platform running on a target system.

Users and Groups: Accounts and permissions available on a system.

Network Resources: Shared folders, printers, databases, and internal services.

---------------------------------------------------------

Common Reconnaissance Goals
- Identify live hosts
- Discover open ports
- Detect running services
- Determine operating systems
- Enumerate users and resources
- Map network infrastructure
- Identify potential attack surfaces

---------------------------------------------------------

## Defender's Perspective

What defenders see:
- Unusual connection attempts
- Large numbers of probes
- Repeated requests to multiple ports
- Service enumeration activity
- Network mapping behavior

Why it matters: Scanning and enumeration often generate logs, alerts, and network traffic patterns that security teams can detect and investigate.

#########################################################################################################

# Passive Reconnaissance: OSINT, Shodan, Censys, WHOIS

## Passive Reconnaissance

Passive Reconnaissance: The process of gathering information about a target without directly interacting with its systems or network.

Use: Used to collect publicly available information while remaining difficult to detect.

How it works: Information is gathered from search engines, public databases, social media, DNS records, and internet-wide scanning platforms.

Example: Finding company domains, employee information, exposed services, and public infrastructure without contacting the target.

---------------------------------------------------------

## OSINT (Open Source Intelligence)

OSINT: The collection and analysis of information from publicly available sources.

Use: Used to gather information about organizations, domains, employees, technologies, and infrastructure.

How it works: Data is collected from websites, social media, public records, search engines, and online databases.

Example: Discovering company email formats, employee names, and public-facing assets.

---------------------------------------------------------

## Shodan

Shodan: A search engine that indexes internet-connected devices and services.

Use: Used to identify exposed servers, IoT devices, webcams, routers, and public services.

How it works: Shodan continuously scans the internet and stores information about accessible devices and their services.

Example: Finding publicly exposed web servers or remote management interfaces.

---------------------------------------------------------

## Censys

Censys: An internet intelligence platform that collects and analyzes data about internet-facing hosts and services.

Use: Used to discover exposed assets, certificates, domains, and service configurations.

How it works: It continuously scans the internet and indexes service and certificate data.

Example: Identifying systems using a specific certificate or technology.

---------------------------------------------------------

## WHOIS

WHOIS: A protocol and database used to obtain domain registration information.

Use: Used to identify domain ownership, registration details, and administrative information.

How it works: Queries are made against domain registration databases.

Example: Finding a domain's registrar, registration date, and name servers.

---------------------------------------------------------

## DNS Records

DNS Records: Public records that provide information about domains and their infrastructure.

Use: Used to discover servers, mail systems, and domain configurations.

Common Records:
- A Record
- AAAA Record
- MX Record
- NS Record
- TXT Record

Example: Identifying mail servers associated with a domain.

---------------------------------------------------------

## Search Engines

Search Engine Reconnaissance: Using search engines to gather information about publicly accessible resources.

Use: Used to discover websites, documents, subdomains, and public information.

Example: Finding publicly accessible files or forgotten web pages.

---------------------------------------------------------

## Certificate Transparency Logs

Certificate Transparency Logs: Public logs of issued SSL/TLS certificates.

Use: Used to discover domains and subdomains associated with an organization.

How it works: Every publicly trusted certificate is recorded in transparency logs.

Example: Identifying newly created subdomains.

---------------------------------------------------------

## Social Media Intelligence

Social Media Intelligence: Collecting information from employee profiles and public posts.

Use: Used to identify technologies, locations, organizational structure, and potential targets.

Example: Discovering technologies used by a company through employee job descriptions.

#########################################################################################################

# Active Reconnaissance

Active Reconnaissance: The process of directly interacting with a target system or network to collect technical information such as hosts, ports, services, and configurations.

Use: Used to map network structure, discover open services, identify operating systems, and find potential vulnerabilities.

How it works: The tester sends direct requests (network probes) to the target system and analyzes the responses to extract information.

Example: Scanning a server to find open ports and detect running services like web servers or databases.

---------------------------------------------------------

Key Characteristics: 
- Direct interaction with target systems
- Generates network traffic
- Provides accurate and detailed results
- Easier to detect by defenders

---------------------------------------------------------

## Host Discovery

Host Discovery: Identifying live systems on a network.

Use: To find which devices are active before deeper scanning.

How it works: Network probes are sent and responses confirm live hosts.

Example: Detecting active servers in a network range.

---------------------------------------------------------

## Port Scanning

Port Scanning: Identifying open, closed, or filtered ports on a system.

Use: To find accessible entry points into a system.

How it works: Different ports are tested and responses are analyzed.

Example: Finding open ports like 80 (HTTP) or 443 (HTTPS).

---------------------------------------------------------

## Service Enumeration

Service Enumeration: Identifying services running on open ports.

Use: To understand applications and versions running on the system.

How it works: Service responses are analyzed for identification details.

Example: Detecting Apache, Nginx, or database services.

---------------------------------------------------------

## OS Fingerprinting

OS Fingerprinting: Identifying the operating system of a target system.

Use: To understand system environment for further testing.

How it works: Network response patterns are analyzed to estimate OS type.

Example: Identifying Linux or Windows systems.

---------------------------------------------------------

## Banner Grabbing

Banner Grabbing: Collecting information exposed by services.

Use: To identify software versions and configurations.

How it works: Services reveal information in response headers or banners.

Example: Web server revealing version details.

---------------------------------------------------------

## Vulnerability Scanning

Vulnerability Scanning: Probing systems to find known security weaknesses.

Use: To detect misconfigurations and outdated software.

How it works: Automated or manual requests test system behavior.

Example: Finding vulnerable service versions.

---------------------------------------------------------

## Defender Perspective

What defenders see:
- Multiple connection attempts
- Port scanning patterns
- Repeated service probes
- Unusual network behavior

Detection systems:
- Firewall logs
- IDS/IPS alerts
- SIEM monitoring

#########################################################################################################

# Nmap: Host Discovery, Port Scanning, Service & OS Detection

## Nmap (Network Mapper)

Nmap: A network scanning tool used to discover hosts, ports, services, and operating systems in a network.

Use: Used in security testing to understand network structure and exposed services.

How it works: It sends network requests to target systems and analyzes their responses to collect information.

Example: Identifying live systems and what services they are running.

---------------------------------------------------------

## Host Discovery

Host Discovery: Process of finding which devices are active in a network.

Use: Used to identify live machines before further analysis.

How it works: Systems that respond to network requests are marked as active.

Example: Finding which computers are currently online in a network range.

---------------------------------------------------------

## Port Scanning

Port Scanning: Process of checking which ports on a system are open, closed, or filtered.

Use: Used to identify possible entry points into a system.

How it works: Each port is tested and its response is analyzed.

Example: Discovering open ports used by web or remote services.

---------------------------------------------------------

## Service Detection

Service Detection: Identifying what software is running on open ports.

Use: Used to understand system applications and versions.

How it works: Responses from services are analyzed to determine their type.

Example: Detecting web server or SSH service running on a machine.

---------------------------------------------------------

## OS Detection

OS Detection: Identifying the operating system of a target system.

Use: Used to understand system environment for security assessment.

How it works: Network behavior and response patterns are analyzed.

Example: Determining whether a system is Windows or Linux.

---------------------------------------------------------

## Defender Perspective

What defenders see:
- Multiple port probes
- Repeated scanning patterns
- Unusual connection attempts
- Fast sequential requests

Detection tools:
- IDS/IPS systems
- Firewall logs
- SIEM alerts


#########################################################################################################

# Nmap Scripting Engine (NSE) for Targeted Enumeration

## Nmap Scripting Engine (NSE)

NSE: A powerful feature of Nmap that uses scripts to automate advanced network scanning, enumeration, and vulnerability detection.

Use: Used to perform targeted enumeration of services, discover hidden information, and detect security weaknesses.

How it works: Nmap runs Lua-based scripts against specific services or ports to extract detailed information beyond basic scanning.

---------------------------------------------------------

## Targeted Enumeration

Targeted Enumeration: The process of focusing on a specific service or protocol to extract detailed information.

Use: Used to gather deeper insights like users, shares, configurations, or vulnerabilities.

How it works: Selected scripts are run only against relevant services instead of scanning everything blindly.

Example: Enumerating SMB shares, DNS records, or HTTP directories from a target system.

---------------------------------------------------------

## NSE Script Categories

---------------------------------------------------------

## Discovery Scripts

Used to gather general information about the target.
- Network info
- Service details
- System metadata

## Safe Scripts

Non-intrusive scripts that do not modify or harm the system.
- Information gathering only
- Low risk enumeration

## Intrusive Scripts

More aggressive scripts that may affect services.
- Deeper probing
- Authentication or sensitive checks

## Vulnerability Scripts

Used to detect known security issues.
- Outdated services
- Misconfigurations
- Known CVEs

---------------------------------------------------------

Service-Based Enumeration Examples

---------------------------------------------------------

## HTTP Enumeration
- Discover directories
- Detect web technologies
- Extract headers and metadata

## SMB Enumeration
- List shared folders
- Identify users and permissions
- Detect domain information

## DNS Enumeration
- Extract DNS records
- Find subdomains
- Identify zone configuration

## SSH / FTP Enumeration
- Identify version details
- Check supported features
- Detect misconfigurations

---------------------------------------------------------

## Why NSE is Powerful
- Automates manual enumeration
- Reduces time in reconnaissance
- Provides deep service-level details
- Helps identify hidden attack surfaces

---------------------------------------------------------

## Defender Perspective

What defenders see:
- Script-based probing behavior
- Multiple service-specific queries
- Increased scanning noise
- Targeted service enumeration attempts

#########################################################################################################

# DNS Enumeration: Zone Transfer, Brute Force, Subdomain Discovery

## DNS Enumeration

DNS Enumeration: The process of gathering information about a domain’s DNS records, subdomains, and internal infrastructure.

Use: Used to discover hidden subdomains, servers, and network structure of a target domain.

How it works: DNS queries are used to extract records like A, MX, NS, TXT, and subdomain mappings.

Example: Finding subdomains like admin.target.com, api.target.com.

---------------------------------------------------------

## Zone Transfer (AXFR)

Zone Transfer: A DNS mechanism used to copy all DNS records from a primary DNS server to a secondary server.

Use: If misconfigured, it can expose the entire domain structure.

How it works: A DNS server is requested to transfer full zone data.

Security Risk: Can leak all subdomains, IPs, and internal services.

---------------------------------------------------------

## DNS Brute Force

DNS Brute Force: A method of discovering subdomains by trying a large list of possible names.

Use: Used to find hidden or unlisted subdomains.

How it works: Common subdomain words are tested against a domain to see which exist.

Example: Finding subdomains like dev, test, mail, vpn.

---------------------------------------------------------

## Subdomain Enumeration (Subfinder)

Subdomain Enumeration: The process of discovering all possible subdomains of a target domain.

Use: Used to map the full attack surface of a domain.

How it works: Tools collect data from public sources, DNS records, and brute-force methods.

Example: Discovering blog.example.com, shop.example.com, api.example.com.

---------------------------------------------------------

DNS Records (Important):
- A Record: Maps domain to IPv4 address
- AAAA Record: Maps domain to IPv6 address
- MX Record: Mail servers
- NS Record: Name servers
- TXT Record: Verification / configuration data

---------------------------------------------------------

## Defender Perspective

What defenders see:
- High number of DNS queries
- Repeated subdomain lookups
- Zone transfer attempts
- Unusual DNS traffic patterns

#########################################################################################################

# SMB & NFS Enumeration

## SMB Enumeration (Server Message Block)

SMB Enumeration: The process of gathering information from SMB file-sharing services to discover shares, users, permissions, and system details.

Use: Used to identify shared folders, sensitive files, user accounts, and misconfigurations in Windows networks.

How it works: SMB services are queried to list available resources and access permissions.

Example: Finding shared folders like Public, Admin, or Backup on a Windows server.

---------------------------------------------------------

What can be discovered in SMB: 
- Shared folders (Shares)
- User accounts
- Domain information
- File permissions
- Printer resources

SMB Security Risks: 
- Anonymous share access
- Weak permissions (everyone read/write)
- Exposed sensitive files
- Credential leakage
- Misconfigured admin shares

## Defender Perspective

Defenders may detect:
- Unauthorized share enumeration attempts
- Repeated login or access requests
- Access to restricted shares
- Network scanning behavior targeting SMB ports

---------------------------------------------------------

## NFS Enumeration (Network File System)

NFS Enumeration: The process of gathering information from NFS file-sharing services used mainly in Linux/Unix systems.

Use: Used to discover exported directories and check access permissions on shared file systems.

How it works: NFS servers expose shared directories that can be queried to see what is accessible.

Example: Finding exported directories like /home, /backup, or /var/www.

---------------------------------------------------------

What can be discovered in NFS:
- Exported directories
- File system structure
- Access permissions
- Shared system files

NFS Security Risks:
- World-readable exports
- No authentication in misconfigured setups
- Sensitive file exposure
- Writable shares leading to system compromise

## Defender Perspective

Defenders may detect:
- Export list requests
- Repeated mount attempts
- Access to sensitive directories
- Unusual file system probing

---------------------------------------------------------

## SMB vs NFS (Quick Difference)

| Feature        | SMB                     | NFS                    |
| -------------- | ----------------------- | ---------------------- |
| System         | Windows                 | Linux/Unix             |
| Purpose        | File + resource sharing | File system sharing    |
| Authentication | Yes (usually)           | Sometimes weak/missing |
| Risk           | Share leakage           | Export exposure        |


#########################################################################################################

# Web Directory & Endpoint Enumeration (feroxbuster, ffuf)

## Web Directory & Endpoint Enumeration

Web Directory & Endpoint Enumeration: The process of discovering hidden directories, files, and API endpoints on a web application.

Use: Used to find hidden admin panels, backup files, API routes, and sensitive resources not linked in the website UI.

How it works: The tool sends many HTTP requests using wordlists to guess valid paths and observes server responses.

Example: Finding hidden paths like /admin, /backup, /api/v1/users.

---------------------------------------------------------

Why It Matters
- Developers often leave hidden endpoints
- Sensitive files may not be linked publicly
- APIs may expose internal functionality
- Misconfigured directories can leak data

---------------------------------------------------------

## feroxbuster

feroxbuster: A fast web content discovery tool used to brute-force directories and files on web servers.

Use: Used for recursive directory enumeration and deep web structure discovery.

How it works: It sends large numbers of requests and automatically explores discovered directories.

Key Strength:
- Fast scanning
- Recursive discovery
- Handles large wordlists efficiently

Example: Discovering nested directories like /admin/panel/config.

---------------------------------------------------------

## ffuf (Fuzz Faster U Fool)

ffuf: A web fuzzing tool used to discover directories, files, parameters, and virtual hosts.

Use: Used for flexible and customizable web enumeration.

How it works: It replaces placeholders in requests with wordlist values and checks responses.

Key Strength:
- Very fast
- Highly customizable
- Supports fuzzing multiple parameters

Example: Finding hidden API endpoints or testing parameter behavior.

---------------------------------------------------------

## Other Similar Tools
Gobuster
- Directory and DNS brute-forcing tool
- Simple and fast enumeration

Dirsearch
- Python-based directory scanner
- Focused on web directory discovery

Wfuzz
- Flexible fuzzing tool for parameters and endpoints

---------------------------------------------------------

## Defender Perspective

Defenders may observe:
- High volume of HTTP requests
- Sequential URL probing
- 404-heavy traffic patterns
- Automated scanning behavior
- Endpoint fuzzing attempts

Detection tools:
- WAF (Web Application Firewall)
- SIEM logs
- Rate limiting systems


#########################################################################################################

# Documenting Reconnaissance Findings (Structured Format)

# Recon Documentation

Recon Documentation: The process of organizing all collected reconnaissance data into a structured, readable, and repeatable format for analysis and reporting.

Use: Used to track discovered assets, open services, vulnerabilities, and attack surface during a security assessment.

How it works: All findings from passive and active reconnaissance are categorized, cleaned, and written in a consistent format so they can be easily reviewed or shared.

Example: A report listing domains, subdomains, open ports, services, and potential risks.

---------------------------------------------------------

## Standard Recon Report Structure

---------------------------------------------------------

1. Target Information

Purpose: Identify the scope of the target.

- Organization name
- Primary domain
- IP ranges (if known)
- Environment type (web, internal, cloud)

2. Passive Recon Findings

Purpose: Data collected without direct interaction.

- Domains & subdomains
- WHOIS information
- DNS records
- Public assets
- OSINT data (emails, employees, tech stack)
- Shodan / Censys results

3. Active Recon Findings

Purpose: Data collected via direct scanning.

- Live hosts
- Open ports
- Running services
- OS fingerprint results
- Banner information

4. Service Enumeration Results

Purpose: Detailed service-level information.

- Web server type & version
- SSH / FTP / SMB services
- Database services
- API endpoints

5. Web Enumeration Results
- Hidden directories
- API endpoints
- Admin panels
- Backup files
- Virtual hosts

6. 🗂️ DNS Enumeration Results
- A / AAAA records
- MX records
- NS records
- TXT records
- Subdomain discovery results
- Zone transfer results (if any)

7. SMB / NFS / Internal Services
- Shared folders
- Exported directories
- Access permissions
- Sensitive file exposure

8. Identified Security Risks
- Exposed admin panels
- Open sensitive ports
- Weak authentication points
- Misconfigured services
- Outdated software versions

9. Attack Surface Summary

Purpose: High-level overview of exposure.

- Total number of hosts
- Total open ports
- Critical services exposed
- High-risk entry points

10. Key Observations
- Unusual findings
- Suspicious services
- Interesting endpoints
- Potential pivot points

11. Recommendations
- Close unnecessary ports
- Disable unused services
- Fix misconfigurations
- Apply patches
- Restrict internal services
- Enable monitoring

---------------------------------------------------------

## Simple Example Format

        Target: example.com

        Passive Recon:
        - Subdomains: api.example.com, admin.example.com
        - WHOIS: private registration

        Active Recon:
        - Host: 192.168.x.x (live)
        - Open ports: 80, 443

        Web Enum:
        - /admin (hidden panel)
        - /backup.zip (sensitive file)

        Risk:
        - Exposed admin panel
        - Sensitive file leakage




#########################################################################################################




