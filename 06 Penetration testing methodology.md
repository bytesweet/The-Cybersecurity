# Penetration Testing Methodology

Penetration Testing Methodology: A structured process used to simulate cyberattacks on systems, networks, or applications to identify security weaknesses in a controlled and systematic way.

Use: Used by security professionals to find vulnerabilities, assess risk, and improve system security before real attackers exploit them.

How it works: A penetration test follows defined phases—from planning and information gathering to exploitation and reporting—to ensure complete and safe security assessment.

Example: Testing a web application to find SQL injection, XSS, or broken access control before deployment.

---------------------------------------

# Core Phases of Penetration Testing

---------------------------------------

1. Planning & Scope Definition

Purpose: Define what will be tested and what is allowed.

Use: Ensures legal and controlled testing environment.

How it works: Tester and client agree on scope, rules, and targets.

Example: Only testing example.com, not other systems.

---------------------------------------

2. Reconnaissance (Information Gathering)

Purpose: Collect information about the target.

Use: Helps understand attack surface.

Types: 
- Passive Recon (OSINT, WHOIS, Shodan)
- Active Recon (Nmap, scanning)

Example: Finding subdomains and open ports.

---------------------------------------

3. Scanning & Enumeration

Purpose: Identify live systems, services, and vulnerabilities.

Use: Builds detailed map of target infrastructure.

How it works: Port scanning, service detection, and enumeration of resources.

Example: Discovering web server, database, and SMB shares.

---------------------------------------

4. Vulnerability Analysis

Purpose: Identify security weaknesses in systems.

Use: Find exploitable flaws.

How it works: Analyze scan results and compare with known vulnerabilities.

Example: Outdated software with known CVEs.

---------------------------------------

5. Exploitation

Purpose: Verify vulnerabilities by actively exploiting them.

Use: Confirms real impact of security flaws.

How it works: Attacker attempts to gain access or execute actions.

Example: Exploiting SQL injection to access database data.

---------------------------------------

6. Post-Exploitation

Purpose: Understand the impact after gaining access.

Use: Assess privilege level and system control.

How it works: Explore system, escalate privileges, or move laterally.

Example: Accessing sensitive files after system compromise.

---------------------------------------

7. Persistence (Optional)

Purpose: Maintain access to compromised system.

Use: Simulates long-term attacker behavior.

How it works: Creating backdoors or maintaining access methods.

Note: Usually avoided in ethical testing unless permitted.

---------------------------------------

8. Reporting

Purpose: Document all findings and recommendations.

Use: Helps organizations fix vulnerabilities.

How it works: Includes vulnerabilities, impact, evidence, and fixes.

Example: Report showing SQLi, XSS, and IDOR with risk level.

#########################################################################################################

# Pentest Phases (Penetration Testing Lifecycle)

## Penetration Testing Phases

Penetration Testing Phases: A structured sequence of steps used to simulate real-world cyberattacks in order to identify, exploit, and report security vulnerabilities in a system.

Use: Used by security professionals to systematically test applications, networks, and systems for weaknesses.

How it works: The process follows a lifecycle starting from information gathering to final reporting, ensuring complete coverage of the target environment.

Example: Testing a web application by discovering endpoints, finding vulnerabilities, exploiting them, and reporting the risks.

---------------------------------------

1. Reconnaissance

Reconnaissance: The process of collecting information about the target system.

Use: Used to understand the target’s structure, technologies, and exposed assets.

How it works: Information is gathered using passive sources (OSINT) and active methods (scanning).

Example: Finding subdomains, IP addresses, and exposed services.

---------------------------------------

2. Scanning & Enumeration

Scanning & Enumeration: The process of identifying live hosts, open ports, services, and system details.

Use: Used to map the target environment and find entry points.

How it works: Network probes are used to discover running services and configurations.

Example: Detecting a web server, SSH service, or database service.

---------------------------------------

3. Exploitation

Exploitation: The process of using discovered vulnerabilities to gain access or execute actions.

Use: Used to confirm whether vulnerabilities are real and impactful.

How it works: Attacker simulates malicious actions against the system.

Example: Exploiting SQL injection to access database data.

---------------------------------------

4. Post-Exploitation

Post-Exploitation: The process of analyzing the system after successful access.

Use: Used to determine the extent of compromise.

How it works: Attacker explores system privileges, data, and internal networks.

Example: Accessing sensitive files or escalating privileges.

---------------------------------------

5. Reporting

Reporting: The process of documenting all findings from the test.

Use: Used to help organizations fix security issues.

How it works: All vulnerabilities, evidence, and recommendations are organized into a structured report.

Example: A report listing SQL injection, XSS, and broken access control issues.


#########################################################################################################

# Rules of Engagement (RoE) & Legal Considerations in Pentesting

## Rules of Engagement (RoE)

Rules of Engagement (RoE): A formal agreement that defines how a penetration test will be conducted, what is allowed, and what is strictly prohibited.

Use: Used to ensure testing is controlled, safe, and aligned with the client’s expectations.

How it works: Before testing starts, both tester and client agree on scope, methods, timing, and limitations.

Example: Permission is given to test only example.com, not other subdomains or internal systems.

---------------------------------------

## Key Components of RoE

Scope Definition:
- Target systems (domains, IPs, apps)
- In-scope vs out-of-scope assets

Allowed & Forbidden Actions: 
- What types of attacks are allowed
- What is strictly prohibited (e.g., DoS, data destruction)

Time Window:
- When testing is allowed
- Avoid production downtime periods

Data Handling Rules: 
- How sensitive data should be treated
- Whether data can be stored or must be deleted

Communication Plan: 
- Who to contact in case of issues
- Emergency shutdown procedures

Impact Limitations: 
- Maximum allowed stress on systems
- Restrictions on aggressive testing

---------------------------------------

## Legal Considerations

Legal Considerations: The laws and permissions that govern whether penetration testing is allowed and under what conditions.

Authorization: 
- Written permission is mandatory
- Without authorization = illegal activity
- Must be signed agreement or contract

Laws & Regulations:
- Cybersecurity laws vary by country
- Unauthorized access is a criminal offense
- Data protection laws must be followed

Data Privacy
- Sensitive data must be protected
- Personal data should not be misused
- Compliance with privacy laws (e.g., GDPR concepts)

Unauthorized Testing
- Testing without permission is illegal hacking
- Even scanning can be considered illegal in some jurisdictions
- Always ensure scope approval

Risk of Misuse
- Legal consequences (fines, jail)
- Damage to organization systems
- Loss of trust and reputation

Ethical Responsibility
- Test only what is allowed
- Do not cause unnecessary damage
- Report findings responsibly



#########################################################################################################

# Metasploit Framework: Modules, Payloads, Sessions

Metasploit Framework: A penetration testing platform used to discover, validate, and demonstrate security vulnerabilities in systems and applications.

Use: Used by security professionals for exploitation, vulnerability assessment, post-exploitation, and security research.

How it works: Metasploit combines exploits, payloads, scanners, and post-exploitation tools into a single framework to simulate real-world attacks in a controlled environment.

Example: Using a known vulnerability to gain access to a vulnerable test system and assess its security impact.

---------------------------------------

## Modules

Modules: The core components of Metasploit that perform specific tasks.

Use: Used to scan, exploit, enumerate, or perform post-exploitation activities.

How it works: Each module is designed for a specific purpose and can be executed against a target system.

Example: Running a vulnerability scanner or exploiting a known software flaw.

Types:
- Exploit Modules
- Payload Modules
- Auxiliary Modules
- Post Modules
- Encoder Modules
- NOP Modules

---------------------------------------

## Exploit Modules

Exploit Modules: Modules designed to take advantage of known vulnerabilities.

Use: Used to gain access to vulnerable systems.

How it works: The module targets a specific weakness and attempts to trigger it.

Example: Testing a vulnerable web server or network service.

---------------------------------------

## Auxiliary Modules

Auxiliary Modules: Modules used for scanning, enumeration, fuzzing, and information gathering.

Use: Used to collect information without exploiting the target.

How it works: The module interacts with services and systems to gather useful data.

Example: Scanning for open services or enumerating network resources.

---------------------------------------

Post Modules

Post Modules: Modules used after successful access has been obtained.

Use: Used to gather information and assess the impact of a compromise.

How it works: The module runs through an active session and collects system data.

Example: Enumerating users, processes, or network configurations.

---------------------------------------

## Encoder Modules

Encoder Modules: Modules that transform payload data into different formats.

Use: Used to modify payload structure for compatibility and delivery purposes.

How it works: The payload is encoded before being delivered to the target.

Example: Preparing a payload for a specific target environment.

---------------------------------------

## NOP Modules

NOP (No Operation) Modules: Modules that generate no-operation instructions.

Use: Used to improve payload reliability and execution flow.

How it works: Additional instructions are inserted without changing payload behavior.

Example: Supporting exploit stability during execution.

---------------------------------------

## Payloads

Payloads: Code that executes after a successful exploit.

Use: Used to perform actions on a compromised system.

How it works: The exploit creates access, and the payload performs the intended task.

Example: Opening a remote shell on the target system.

Payload Types: 
- Singles Payload
- Stagers Payload
- Stages Payload

---------------------------------------

## Single Payloads

Single Payloads: Standalone payloads containing all required functionality.

Use: Used when a simple and self-contained payload is needed.

How it works: The entire payload is delivered and executed at once.

Example: A payload that immediately opens a command shell.

---------------------------------------

## Stagers Payloads

Stagers: Small payloads that establish communication with the attacker.

Use: Used to prepare the target for a larger payload.

How it works: The stager creates a connection and downloads additional components.

Example: Creating a connection before loading advanced functionality.

---------------------------------------

## Stages Payloads

Stages: Additional payload components delivered after a stager succeeds.

Use: Used to provide advanced features and capabilities.

How it works: The stage is loaded through the established connection.

Example: Loading an advanced remote administration environment.

---------------------------------------

## Sessions

Sessions: Active connections established after successful exploitation.

Use: Used to interact with compromised systems.

How it works: Metasploit manages active access through sessions.

Example: An active connection to a target machine.

Session Types: 
- Shell Session
- Meterpreter Session

---------------------------------------

## Shell Session

Shell Session: A basic command-line interface on the target system.

Use: Used for executing commands and basic interaction.

How it works: Commands entered by the tester are executed on the target.

Example: Viewing files and system information.

---------------------------------------

## Meterpreter Session

Meterpreter Session: An advanced in-memory payload that provides enhanced system interaction.

Use: Used for post-exploitation activities and system management.

How it works: Runs in memory and provides advanced features without writing files to disk.

Example: Gathering system information, managing processes, and interacting with files.

---------------------------------------

## Workspace

Workspace: A project management feature used to organize penetration testing data.

Use: Used to separate hosts, findings, services, and sessions between assessments.

How it works: Information is stored and managed within dedicated workspaces.

Example: Creating separate environments for different client engagements.

---------------------------------------

## Defender Perspective

What defenders may observe:
- Exploitation attempts
- Unusual network connections
- Active sessions
- Post-exploitation activity
- Security monitoring alerts

Detection methods:
- IDS/IPS systems
- EDR solutions
- SIEM platforms
- Network monitoring tools

#########################################################################################################

# Manual Exploitation vs Automated Tools

## Exploitation Methods

Exploitation Methods: The techniques used to verify and exploit vulnerabilities in a target system. Exploitation can be performed manually by a tester or automatically using security tools.

Use: Used to validate vulnerabilities and assess their real-world impact.

How it works: The tester either manually analyzes and exploits the vulnerability or uses automated tools to perform the process.

Example: Testing a vulnerable web application manually or with an exploitation framework.

---------------------------------------

## Manual Exploitation

Manual Exploitation: The process of identifying, analyzing, and exploiting vulnerabilities without relying heavily on automated attack tools.

Use: Used when deeper understanding, precision, and custom testing are required.

How it works: The tester manually examines the target, crafts requests, analyzes responses, and verifies vulnerabilities.

Example: Manually testing a web application's input fields to verify SQL Injection or IDOR vulnerabilities.

---------------------------------------

Advantages of Manual Exploitation:
- Greater accuracy
- Better understanding of vulnerabilities
- Finds complex business logic flaws
- Lower false positives
- More flexible and customizable

Disadvantages of Manual Exploitation: 
- Time-consuming
- Requires higher skill level
- Difficult to scale on large environments

---------------------------------------

## Automated Tools

Automated Tools: Software that automatically scans, identifies, and sometimes exploits vulnerabilities.

Use: Used to quickly assess large environments and identify common security issues.

How it works: The tool follows predefined checks, signatures, or attack patterns against the target.

Example: Using vulnerability scanners or exploitation frameworks to identify security weaknesses.

---------------------------------------

## Common Automated Tools

Metasploit: Used for exploitation and post-exploitation activities.

Nessus: Used for vulnerability assessment.

OpenVAS: Used for automated vulnerability scanning.

Burp Suite Scanner: Used for automated web application testing.

Nuclei: Used for fast template-based vulnerability detection.

---------------------------------------

Advantages of Automated Tools: 
- Fast assessment
- Scalable for large environments
- Consistent results
- Efficient vulnerability discovery
- Saves time

Disadvantages of Automated Tools:
- May miss complex vulnerabilities
- Can generate false positives
- Limited by built-in signatures
- Less effective against custom applications

---------------------------------------

## Real-World Pentesting Approach

Most professional penetration tests use both methods together:
- Automated tools identify potential vulnerabilities.
- Manual testing verifies findings.
- Manual exploitation confirms real-world impact.
- Results are documented and reported.

This combination provides both speed and accuracy.

#########################################################################################################

# Privilege Escalation on Linux & Windows

## Privilege Escalation

Privilege Escalation: The process of gaining higher permissions or access rights on a system after obtaining an initial foothold.

Use: Used by attackers and penetration testers to determine the potential impact of a system compromise.

How it works: An attacker identifies misconfigurations, weak permissions, software vulnerabilities, or credential exposure that allow movement from a low-privileged account to a more privileged one.

Example: A standard user account gaining administrative or root-level access.

---------------------------------------

## Linux Privilege Escalation

Linux Privilege Escalation: The process of gaining elevated privileges, typically root access, on a Linux system.

Use: Used to assess whether a compromised Linux account can gain full control of the system.

How it works: The attacker analyzes system configurations, permissions, services, and installed software to identify escalation paths.

Example: A low-privileged user obtaining root access through a misconfiguration.

---------------------------------------

## Common Linux Privilege Escalation Vectors

---------------------------------------

## Sudo Misconfigurations

Sudo Misconfigurations: Improper sudo permissions that allow users to execute commands with elevated privileges.

Use: Can provide unintended administrative access.

## Weak File & Directory Permissions

Weak Permissions: Sensitive files or directories accessible by unauthorized users.

Use: May expose credentials or allow modification of critical files.

## SUID / SGID Binaries

SUID & SGID: Special permissions that allow programs to run with the privileges of the file owner or group.

Use: Misconfigured binaries may allow privilege escalation.

## Scheduled Tasks (Cron Jobs)

Cron Jobs: Automated tasks executed at scheduled intervals.

Use: Misconfigured jobs may allow unauthorized code execution.

## Kernel Vulnerabilities

Kernel Vulnerabilities: Security flaws within the Linux kernel.

Use: Can potentially allow users to gain elevated privileges.

## Credential Exposure

Credential Exposure: Passwords, SSH keys, or secrets stored insecurely.

Use: Can provide access to privileged accounts.

---------------------------------------

## Windows Privilege Escalation

Windows Privilege Escalation: The process of obtaining higher privileges, typically Administrator or SYSTEM access, on a Windows system.

Use: Used to assess whether a compromised account can gain full control of a Windows environment.

How it works: The attacker identifies weak permissions, insecure services, credential exposure, or software vulnerabilities.

Example: A standard user gaining Administrator-level access.

---------------------------------------

## Common Windows Privilege Escalation Vectors

---------------------------------------

## Service Misconfigurations

Service Misconfigurations: Windows services configured with insecure permissions or paths.

Use: May allow attackers to gain elevated privileges.

## Weak File Permissions

Weak Permissions: Sensitive files or executables writable by low-privileged users.

Use: Can enable unauthorized modifications.

## Scheduled Tasks

Scheduled Tasks: Automated jobs running with elevated privileges.

Use: Misconfigurations may provide escalation opportunities.

## Credential Exposure

Credential Exposure: Passwords, hashes, or tokens stored insecurely.

Use: Can provide access to privileged accounts.

## Unpatched Software & OS Vulnerabilities

Software Vulnerabilities: Known security flaws in Windows components or installed applications.

Use: May allow privilege escalation when exploited.

## Token & Permission Abuse

Token & Permission Abuse: Misuse of Windows security tokens or excessive user rights.

Use: Can result in elevated access levels.

---------------------------------------

## Defender Perspective

What defenders should monitor:
- Unusual privilege changes
- Access to sensitive files
- Unauthorized service modifications
- Suspicious scheduled task activity
- Unexpected administrative actions

Prevention methods:
- Principle of Least Privilege (PoLP)
- Regular patching
- Secure permission management
- Credential protection
- Continuous monitoring

#########################################################################################################

# Lateral Movement Techniques

## Lateral Movement

Lateral Movement: The process of moving from one compromised system to other systems within the same network after gaining initial access.

Use: Used to expand access, reach high-value targets, and assess the potential impact of a security breach.

How it works: After compromising a system, an attacker uses credentials, trust relationships, shared resources, or administrative access to move through the environment.

Example: Compromising a workstation and then accessing a file server or domain controller.

---------------------------------------

Purpose of Lateral Movement: 
- Expand access within a network
- Reach critical systems
- Access sensitive data
- Increase privileges
- Demonstrate breach impact

---------------------------------------

## Credential-Based Movement

Credential-Based Movement: Using stolen or discovered credentials to access other systems.

Use: Used when valid usernames, passwords, keys, or tokens are available.

How it works: Authentication mechanisms are used to access additional hosts.

Example: Using an administrator account to access multiple systems.

---------------------------------------

## Remote Management Services

Remote Management Services: Administrative services that allow remote system access.

Use: Used to manage systems across a network.

How it works: Attackers may abuse legitimate administration channels after obtaining valid credentials.

Example: Moving from one system to another using remote administration capabilities.

---------------------------------------

## Shared Resources & Network Shares

Network Shares: Shared folders and resources accessible by multiple systems or users.

Use: Used to exchange files and data across a network.

How it works: Access to shared resources may reveal sensitive information or additional credentials.

Example: Accessing a departmental file share containing sensitive documents.

---------------------------------------

## Trust Relationship Abuse

Trust Relationships: Connections between systems, domains, or services that allow authenticated access.

Use: Designed to simplify administration and resource sharing.

How it works: Attackers may leverage existing trust relationships to move between systems.

Example: Accessing systems that trust an already compromised account.

---------------------------------------

## Account & Permission Abuse

Account Abuse: Using excessive permissions assigned to users or service accounts.

Use: Can provide broader access than intended.

How it works: Attackers identify accounts with elevated privileges and use them to access additional systems.

Example: A service account with permissions across multiple servers.

---------------------------------------

## Internal Service Enumeration

Internal Service Enumeration: Discovering systems, services, and resources available inside a network.

Use: Used to identify additional targets for movement.

How it works: Information gathered from one system helps identify others.

Example: Finding database servers, file servers, or management systems.

---------------------------------------

## Cloud & Hybrid Environments

Cloud Lateral Movement: Movement between cloud resources, accounts, or services.

Use: Used to assess risks in cloud and hybrid infrastructures.

How it works: Attackers leverage permissions, identities, and trust relationships within cloud environments.

Example: Moving between cloud-hosted workloads using compromised credentials.

---------------------------------------

Risks of Successful Lateral Movement: 
- Access to sensitive data
- Broader network compromise
- Increased attack impact
- Exposure of critical systems
- Potential full-environment takeover

---------------------------------------

## Defender Perspective

What defenders should monitor:
- Unusual authentication activity
- Access to multiple systems from one account
- Unexpected use of administrative tools
- New connections between internal systems
- Suspicious account behavior

Prevention methods:
- Principle of Least Privilege (PoLP)
- Network segmentation
- Multi-Factor Authentication (MFA)
- Credential protection
- Continuous monitoring

#########################################################################################################

# Writing Professional Pentest Reports

## Professional Pentest Report

Professional Pentest Report: A formal document that summarizes the findings, risks, evidence, and recommendations discovered during a penetration test.

Use: Used to communicate security weaknesses and remediation steps to clients, management, and technical teams.

How it works: All findings from reconnaissance, scanning, exploitation, and post-exploitation are organized into a structured and easy-to-understand format.

Example: A report describing a SQL Injection vulnerability, its impact, proof of concept, and recommended fix.

---------------------------------------

## Executive Summary

Executive Summary: A high-level overview of the assessment written for managers and non-technical stakeholders.

Use: Used to quickly communicate overall security posture and business risk.

How it works: Provides a concise summary of major findings, risk levels, and recommendations.

Example: "The assessment identified three high-risk vulnerabilities that could allow unauthorized access to sensitive data."

---------------------------------------

## Engagement Overview

Engagement Overview: Describes the scope, objectives, and methodology of the assessment.

Use: Used to document what was tested and under what conditions.

How it works: Lists targets, testing dates, scope boundaries, and Rules of Engagement.

Example: Testing a web application and external infrastructure within a defined scope.

---------------------------------------

## Scope & Targets

Scope & Targets: Defines the systems, applications, domains, and IP ranges included in the assessment.

Use: Used to clearly identify what was tested.

How it works: Lists all in-scope assets and exclusions.

Example:
- example.com
- api.example.com
- 192.168.x.x range

---------------------------------------

## Methodology

Methodology: The approach used during testing.

Use: Used to explain how the assessment was performed.

How it works: Documents each testing phase.

Example Phases:
- Reconnaissance
- Scanning & Enumeration
- Vulnerability Analysis
- Exploitation
- Post-Exploitation
- Reporting

---------------------------------------

## Vulnerability Findings

Vulnerability Findings: Detailed descriptions of each discovered security issue.

Use: Used to explain vulnerabilities and their risks.

How it works: Each finding should include technical details and supporting evidence.

Example: SQL Injection in login functionality.

---------------------------------------

## Finding Structure

Title: Clear vulnerability name.
Example: SQL Injection in Login Form


Severity: Risk rating assigned to the finding.
Common Levels:
- Critical
- High
- Medium
- Low
- Informational


Description: Explain the vulnerability.
Example: User input is not properly validated, allowing unauthorized database queries.


Impact: Describe what an attacker could achieve.
Example: Unauthorized access to sensitive customer data.


Evidence: Provide proof that the vulnerability exists.
Examples:
- Screenshots
- Request/Response samples
- Logs
- Output snippets


Reproduction Steps: Explain how the issue can be reproduced.
Use: Allows developers and security teams to verify findings.
Example:Step-by-step testing process.


Remediation: Provide recommendations for fixing the issue.
Example: Use parameterized queries and input validation.


References: Relevant standards and documentation.
Examples:
- OWASP
- CVE References
- Vendor Documentation


Risk Matrix: A table used to prioritize findings.

| Severity      | Business Impact           |
| ------------- | ------------------------- |
| Critical      | Immediate action required |
| High          | Significant risk          |
| Medium        | Moderate risk             |
| Low           | Limited risk              |
| Informational | Best practice issue       |


---------------------------------------

## Recommendations

Recommendations: Security improvements based on assessment findings.

Examples:
- Apply security patches
- Remove unnecessary services
- Strengthen authentication
- Implement least privilege
- Improve monitoring

---------------------------------------

## Appendices

Appendices: Additional supporting information.

May Include:
- Tool lists
- Network diagrams
- Scan results
- Asset inventory
- Raw evidence

---------------------------------------

## Professional Report Writing Best Practices
- Be clear and concise
- Avoid unnecessary jargon
- Focus on business impact
- Include reproducible evidence
- Prioritize findings by risk
- Provide actionable recommendations
- Maintain professional language
- Separate facts from assumptions

#########################################################################################################
