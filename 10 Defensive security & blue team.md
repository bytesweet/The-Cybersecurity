
# Defensive Security & Blue Team

Defensive Security & Blue Team: The practice of protecting systems, networks, and data from cyber attacks. The Blue Team is responsible for defending an organization's IT environment.

Use (Defender Side): Used by SOC analysts, incident responders, security engineers, and Blue Team members to detect, investigate, and stop cyber threats.

Security Goal: Prevent attacks, detect threats quickly, and protect business systems and data.

Example: A Blue Team detects malware on a computer, removes it, and blocks the attacker from accessing the network.

---------------------------------------

## 🔵 Blue Team

Blue Team: The team responsible for defending an organization's systems and responding to security incidents.

How it works: Monitors systems, investigates alerts, and responds to cyber attacks.

Use: Protect networks, endpoints, and cloud environments.

Example: Investigating a suspicious login alert.

Security Benefit: Reduces the impact of cyber attacks.

---------------------------------------

## 🔴 Red Team vs 🔵 Blue Team

Red Team vs Blue Team: Red Team simulates attacks, while Blue Team detects and defends against them.

How it works: Red Team tests security, and Blue Team responds to the simulated attack.

Use: Find and fix security weaknesses.

Example: Red Team launches a phishing test, and Blue Team detects and blocks it.

Security Benefit: Improves an organization's security.

---------------------------------------

## 🟣 Purple Team

Purple Team: Red Team and Blue Team working together to improve security.

How it works: Both teams share knowledge to improve detection and defense.

Use: Build better security and faster incident response.

Example: Red Team demonstrates an attack, and Blue Team creates a new detection rule.

Security Benefit: Stronger security through teamwork.


#########################################################################################################

# SIEM Fundamentals

SIEM (Security Information and Event Management): A security platform that collects, analyzes, and correlates logs from different systems to detect suspicious activities and security threats.

Use (Defender Side): Used by SOC analysts, Blue Teams, and security engineers to monitor security events, investigate incidents, and respond to attacks.

Security Goal: Centralize log management, detect threats quickly, and improve incident response.

Example: A SIEM detects multiple failed login attempts followed by a successful login and generates a security alert.

---------------------------------------

## Log Ingestion

Log Ingestion: The process of collecting logs from different sources such as servers, endpoints, firewalls, cloud services, and applications.

How it works: Devices and applications send logs to the SIEM for storage and analysis.

Use: Gather security data from across the environment.

Example: Windows Event Logs and firewall logs are sent to the SIEM.

Security Benefit: Provides centralized visibility into security events.

---------------------------------------

## Log Correlation

Log Correlation: The process of connecting related events from multiple log sources to identify suspicious activity.

How it works: The SIEM analyzes logs and links events that match predefined rules or patterns.

Use: Detect attacks that may not be visible in a single log source.

Example: The SIEM correlates VPN login logs with endpoint logs to identify suspicious user activity.

Security Benefit: Improves threat detection and reduces false positives.

---------------------------------------

## Alerting

Alerting: The process of automatically notifying security teams when suspicious activity or security rules are triggered.

How it works: The SIEM generates alerts based on correlation rules, threat intelligence, or abnormal behavior.

Use: Notify analysts about potential security incidents.

Example: An alert is generated after multiple failed login attempts from the same IP address.

Security Benefit: Enables faster detection and response to threats.

---------------------------------------

## Dashboards

Dashboards: Visual panels that display security events, alerts, system health, and key metrics.

How it works: The SIEM presents collected data using charts, graphs, and summaries.

Use: Monitor the organization's security status in real time.

Example: A dashboard shows the number of critical alerts detected today.

Security Benefit: Improves visibility and situational awareness.

---------------------------------------

## Threat Hunting

Threat Hunting: The proactive search for hidden threats using SIEM data and security logs.

How it works: Analysts investigate logs and events to find suspicious behavior that automated alerts may miss.

Use: Discover advanced or stealthy attacks.

Example: Searching SIEM logs for unusual PowerShell activity across multiple endpoints.

Security Benefit: Detects threats before they cause significant damage.


#########################################################################################################

# Elastic Security & Splunk

Elastic Security & Splunk: SIEM platforms used to collect, search, analyze, and visualize security logs from different systems.

Use (Defender Side): Used by SOC analysts, Blue Teams, and security engineers to investigate incidents, monitor security events, and detect cyber threats.

Security Goal: Centralize log management, improve threat detection, and support incident response.

Example: A SOC analyst searches Windows Event Logs for suspicious login activity and monitors alerts through a security dashboard.

---------------------------------------

## Query Language

Query Language: A search language used to find and filter security events stored in the SIEM.

How it works: Analysts write queries to search logs based on users, IP addresses, event IDs, timestamps, or keywords.

Use: Investigate incidents, perform threat hunting, and analyze security events.

Example: Searching for all failed login attempts from a specific IP address.

Security Benefit: Speeds up investigations and helps identify malicious activity.

---------------------------------------

## Dashboards

Dashboards: Visual interfaces that display logs, alerts, charts, and security metrics in real time.

How it works: SIEM platforms organize collected data into customizable charts, graphs, and tables.

Use: Monitor security events and track the organization's security posture.

Example: A dashboard showing authentication failures, malware detections, and critical alerts.

Security Benefit: Improves visibility and enables faster incident detection.

---------------------------------------

## Alerting

Alerting: Automatically generates notifications when suspicious activity matches predefined rules.

How it works: The SIEM continuously analyzes incoming logs and triggers alerts when detection conditions are met.

Use: Notify analysts about potential security incidents.

Example: Alert when multiple failed login attempts are detected within a short period.

Security Benefit: Enables rapid detection and response.

---------------------------------------

## Visualizations

Visualizations: Charts, graphs, and tables used to present security data in an easy-to-understand format.

How it works: SIEM platforms convert raw logs into visual reports.

Use: Identify trends, anomalies, and attack patterns.

Example: A graph showing the number of failed logins during the last 24 hours.

Security Benefit: Simplifies analysis and improves situational awareness.

---------------------------------------

## Saved Searches

Saved Searches: Frequently used queries stored for quick access.

How it works: Analysts save search queries and reuse them during investigations.

Use: Speed up repetitive investigations.

Example: A saved query that searches for PowerShell execution events.

Security Benefit: Improves investigation efficiency and consistency.

---------------------------------------

## Platform Features

Elastic Security: Uses KQL (Kibana Query Language) and ES|QL to search logs, build dashboards, detect threats, and investigate incidents.

Splunk: Uses SPL (Search Processing Language) to search machine data, create dashboards, generate alerts, and perform security investigations.

Security Benefit: Both platforms provide powerful capabilities for log analysis, threat detection, and security monitoring.

#########################################################################################################

# Detection Engineering & Sigma Rules

Detection Engineering: The process of creating, testing, and improving detection rules to identify malicious activity in an organization's environment.

Use (Defender Side): Used by SOC analysts, Blue Teams, detection engineers, and threat hunters to detect cyber attacks and improve security monitoring.

Security Goal: Detect malicious behavior quickly while reducing false positives.

Example: A detection engineer creates a rule to alert whenever PowerShell is used to download files from the internet.

---------------------------------------

## Detection Rules

Detection Rules: Rules that define suspicious behaviors or attack patterns to monitor.

How it works: The SIEM or EDR compares incoming events against predefined conditions and generates an alert when a match is found.

Use: Detect known attack techniques and suspicious activities.

Example: Alert when a user logs in from two different countries within a short time.

Security Benefit: Improves threat detection and incident response.

---------------------------------------

## Sigma Rules

Sigma Rules: A vendor-neutral rule format used to describe security detections that can be converted to different SIEM platforms.

How it works: A Sigma rule defines the log source, detection logic, and conditions. It can then be converted into queries for platforms such as Splunk, Elastic Security, Microsoft Sentinel, and QRadar.

Use: Write detection rules once and use them across multiple SIEM solutions.

Example: A Sigma rule detects suspicious PowerShell execution regardless of the SIEM platform.

Security Benefit: Makes detection rules portable and easier to maintain.

---------------------------------------

## Log Sources

Log Sources: The systems that generate logs used by detection rules.

How it works: SIEM platforms collect logs from endpoints, servers, firewalls, cloud services, and applications.

Use: Provide the data needed for threat detection.

Example: Windows Event Logs, Sysmon logs, Linux logs, and firewall logs.

Security Benefit: Better log coverage leads to better threat detection.

---------------------------------------

## False Positives

False Positives: Benign activities that incorrectly trigger a security alert.

How it works: Detection rules may match normal behavior that appears suspicious.

Use: Analysts review and tune rules to reduce unnecessary alerts.

Example: An administrator legitimately uses PowerShell, triggering a detection rule.

Security Benefit: Reduces alert fatigue and improves SOC efficiency.

---------------------------------------

Rule Tuning

Rule Tuning: The process of improving detection rules to increase accuracy.

How it works: Analysts adjust conditions, exclusions, or thresholds based on investigation results.

Use: Improve detection quality and reduce false positives.

Example: Excluding approved administrator accounts from a PowerShell detection rule.

Security Benefit: Produces more reliable and actionable alerts.


#########################################################################################################

# EDR Telemetry

EDR Telemetry: The security data collected by an Endpoint Detection and Response (EDR) solution to monitor endpoint activity and detect suspicious behavior.

Use (Defender Side): Used by SOC analysts, Blue Teams, threat hunters, and incident responders to investigate attacks and monitor endpoint activity.

Security Goal: Provide visibility into endpoint behavior and detect malicious activities in real time.

Example: An EDR detects that a process launched PowerShell, connected to a suspicious IP address, and created an executable file.

---------------------------------------

## Process Creation

Process Creation: Records information whenever a new process starts on an endpoint.

How it works: The EDR logs the process name, parent process, command line, user, and execution time.

Use: Detect malicious programs and suspicious process execution.

Example: Microsoft Word starts powershell.exe with an unusual command.

Security Benefit: Helps identify malware execution and attacker activity.

---------------------------------------

## Network Connections

Network Connections: Records outbound and inbound network connections made by processes.

How it works: The EDR logs source and destination IP addresses, ports, protocols, and the responsible process.

Use: Detect communication with malicious servers or unusual network behavior.

Example: A process connects to a known command-and-control (C2) server.

Security Benefit: Helps detect malware communication and data exfiltration.

---------------------------------------

## File Events

File Events: Records file creation, modification, deletion, and renaming activities.

How it works: The EDR monitors changes made to files by running processes.

Use: Detect ransomware, malware, and unauthorized file changes.

Example: A process encrypts hundreds of files within a few minutes.

Security Benefit: Helps identify malicious file activity.

---------------------------------------

## Registry Events

Registry Events: Records changes made to the Windows Registry.

How it works: The EDR monitors registry keys and values that are created, modified, or deleted.

Use: Detect persistence mechanisms and unauthorized system changes.

Example: Malware creates a Run registry key to start automatically after reboot.

Security Benefit: Helps identify persistence techniques.

---------------------------------------

## User Activity

User Activity: Records authentication events and actions performed by users.

How it works: The EDR tracks logins, logouts, and user-related activities.

Use: Detect compromised accounts and unusual user behavior.

Example: A user logs in from an unexpected location and immediately launches administrative tools.

Security Benefit: Helps detect account compromise and insider threats.


#########################################################################################################

# Threat Intelligence

Threat Intelligence: Information about cyber threats, attackers, and attack techniques that helps organizations detect, prevent, and respond to security incidents.

Use (Defender Side): Used by SOC analysts, Blue Teams, threat hunters, and incident responders to improve threat detection and security decisions.

Security Goal: Identify threats early, understand attacker behavior, and strengthen security defenses.

Example: A security team blocks a malicious IP address after receiving threat intelligence that it is being used in ransomware attacks.

---------------------------------------

## Indicators of Compromise (IOCs)

Indicators of Compromise (IOCs): Artifacts that indicate a system may have been compromised.

How it works: Analysts search for known malicious indicators in logs, endpoints, and network traffic.

Use: Detect known threats and support incident investigations.

Example: Malicious IP addresses, file hashes, domains, registry keys, and filenames.

Security Benefit: Enables fast detection of known attacks.

---------------------------------------

## Tactics, Techniques, and Procedures (TTPs)

Tactics, Techniques, and Procedures (TTPs): The methods and behaviors attackers use to achieve their objectives.

How it works: Security teams study attacker behavior instead of relying only on known IOCs.

Use: Detect advanced threats and improve threat hunting.

Example: Using PowerShell for lateral movement or creating scheduled tasks for persistence.

Security Benefit: Helps detect attacks even when IOCs change.

---------------------------------------

## STIX (Structured Threat Information eXpression)

STIX: A standardized format for describing and sharing cyber threat intelligence.

How it works: Threat information is organized into a structured format that different security tools can understand.

Use: Share threat intelligence between organizations and security platforms.

Example: Sharing malware indicators and attacker techniques using the STIX format.

Security Benefit: Improves threat intelligence sharing and interoperability.

---------------------------------------

## TAXII (Trusted Automated eXchange of Intelligence Information)

TAXII: A protocol used to automatically exchange threat intelligence between organizations and security tools.

How it works: TAXII transfers STIX data securely between threat intelligence servers and clients.

Use: Automate threat intelligence sharing and updates.

Example: A SIEM automatically downloads the latest threat intelligence from a TAXII server.

Security Benefit: Keeps security tools updated with current threat information.

---------------------------------------

## Threat Feeds

Threat Feeds: Continuously updated sources of threat intelligence containing IOCs and other security information.

How it works: Security tools import threat feeds and compare them against collected logs and events.

Use: Detect known malicious IP addresses, domains, and file hashes.

Example: A firewall blocks traffic to an IP address listed in a threat intelligence feed.

Security Benefit: Improves detection of known threats.


#########################################################################################################

# MITRE ATT&CK for Detection Mapping

MITRE ATT&CK for Detection Mapping: The process of mapping security detections to the MITRE ATT&CK framework to identify which attacker techniques can be detected and where detection gaps exist.

Use (Defender Side): Used by SOC analysts, Blue Teams, detection engineers, and threat hunters to build better detection rules and improve security coverage.

Security Goal: Improve threat detection by aligning security monitoring with known attacker behaviors.

Example: A Sigma rule that detects PowerShell execution is mapped to the corresponding MITRE ATT&CK technique.

---------------------------------------

## MITRE ATT&CK Framework

MITRE ATT&CK Framework: A knowledge base that documents real-world attacker tactics, techniques, and procedures (TTPs).

How it works: It organizes attacker behavior into tactics and techniques based on real cyber attacks.

Use: Understand attacker behavior and improve security defenses.

Example: Mapping malware behavior to the Credential Access tactic.

Security Benefit: Provides a common framework for detection and threat analysis.

---------------------------------------

## Tactics

Tactics: The high-level goals an attacker is trying to achieve during an attack.

How it works: Each tactic represents a stage of the attack lifecycle.

Use: Categorize attacker objectives.

Example: Initial Access, Execution, Persistence, Privilege Escalation, Defense Evasion, Credential Access, Lateral Movement, Exfiltration.

Security Benefit: Helps defenders understand each stage of an attack.

---------------------------------------

## Techniques

Techniques: The methods attackers use to achieve a specific tactic.

How it works: Each technique describes a common attack method observed in real-world incidents.

Use: Build detections for specific attacker behaviors.

Example: PowerShell, Command and Scripting Interpreter, Scheduled Tasks, Remote Services.

Security Benefit: Improves the accuracy of detection rules.

---------------------------------------

## Detection Mapping

Detection Mapping: Linking detection rules, alerts, or security controls to MITRE ATT&CK techniques.

How it works: Each detection is associated with the ATT&CK technique it identifies.

Use: Measure detection coverage and identify missing detections.

Example: Mapping a PowerShell detection rule to the PowerShell technique in MITRE ATT&CK.

Security Benefit: Helps organizations understand which attack techniques are covered and which require new detections.

---------------------------------------

## Coverage Analysis

Coverage Analysis: Reviewing which ATT&CK techniques are currently detected and which are not.

How it works: Security teams compare existing detection rules against the MITRE ATT&CK framework.

Use: Improve security monitoring and prioritize detection development.

Example: Discovering that there are detections for Initial Access but none for Credential Dumping.

Security Benefit: Reduces detection gaps and strengthens defensive capabilities.

#########################################################################################################

# Security Operations Center (SOC) Workflows

Security Operations Center (SOC) Workflows: The step-by-step process a SOC follows to monitor, detect, investigate, respond to, and recover from security incidents.

Use (Defender Side): Used by SOC analysts, Blue Teams, incident responders, and security engineers to handle security events efficiently.

Security Goal: Detect threats quickly, reduce response time, and minimize the impact of cyber attacks.

Example: A SOC receives a malware alert, investigates the affected endpoint, isolates the device, removes the malware, and documents the incident.

---------------------------------------

## Monitoring

Monitoring: Continuously watching systems, networks, and security logs for suspicious activity.

How it works: SIEM, EDR, and other security tools collect and analyze events in real time.

Use: Identify potential security threats.

Example: Monitoring failed login attempts across the network.

Security Benefit: Detects attacks at an early stage.

---------------------------------------

## Alert Triage

Alert Triage: Reviewing and prioritizing security alerts to determine which require investigation.

How it works: Analysts classify alerts based on severity and likelihood of being a real threat.

Use: Focus on the most important security incidents.

Example: A high-severity ransomware alert is investigated before a low-risk policy violation.

Security Benefit: Improves response efficiency and reduces alert fatigue.

---------------------------------------

## Investigation

Investigation: Analyzing alerts and collecting evidence to determine whether malicious activity occurred.

How it works: Analysts review logs, EDR telemetry, network traffic, and user activity.

Use: Confirm security incidents and understand their impact.

Example: Investigating suspicious PowerShell execution on an employee's computer.

Security Benefit: Helps identify the root cause of an incident.

---------------------------------------

## Incident Response

Incident Response: Taking action to contain, remove, and recover from a security incident.

How it works: The SOC isolates affected systems, removes threats, and restores normal operations.

Use: Minimize damage and prevent further compromise.

Example: Isolating an infected endpoint to stop malware from spreading.

Security Benefit: Limits the impact of cyber attacks.

---------------------------------------

## Reporting & Documentation

Reporting & Documentation: Recording the details of security incidents, investigations, and response actions.

How it works: Analysts document findings, evidence, timelines, and recommendations.

Use: Support future investigations, audits, and security improvements.

Example: Writing an incident report after responding to a phishing attack.

Security Benefit: Improves future response and compliance.


#########################################################################################################
