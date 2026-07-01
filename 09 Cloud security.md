
# Cloud Security

Cloud Security: Security practices, technologies, and policies designed to protect cloud infrastructure, applications, data, and services from cyber threats and unauthorized access.

Use (Defender Side): Used by organizations and security teams to secure cloud resources, protect sensitive data, enforce access control, and maintain compliance.

Security Goals: Prevent data breaches, unauthorized access, misconfigurations, service disruptions, and cloud-based attacks.

Example: A company stores customer data on AWS and uses encryption, IAM policies, and continuous monitoring to protect its cloud environment.

---------------------------------------

## Cloud Service Models

Infrastructure as a Service (IaaS): Provides virtual machines, storage, networking, and other infrastructure resources that customers manage.

Use: Gives organizations full control over operating systems, applications, and network configurations.

Example: Launching virtual servers on AWS EC2 or Azure Virtual Machines.

Security Focus: Securing operating systems, applications, network configurations, and access controls.

---------------------------------------

## Platform as a Service (PaaS)

Platform as a Service (PaaS): Provides a managed platform for developing, deploying, and running applications without managing the underlying infrastructure.

Use: Allows developers to focus on application development instead of server management.

Example: Deploying a web application using Google App Engine or Azure App Service.

Security Focus: Securing application code, identities, data, and configurations.

---------------------------------------

## Software as a Service (SaaS)

Software as a Service (SaaS): Delivers fully managed software applications over the internet.

Use: Enables users to access applications through a web browser without installing or maintaining software.

Example: Using Microsoft 365, Google Workspace, or Salesforce.

Security Focus: Managing user accounts, permissions, authentication, and protecting stored data.

---------------------------------------

## Shared Responsibility Model

Shared Responsibility Model: A cloud security model that defines which security responsibilities belong to the cloud provider and which belong to the customer.

How it works: The cloud provider secures the underlying infrastructure, while customers are responsible for securing their data, identities, applications, and configurations.

Example: AWS secures its data centers, while the customer secures EC2 instances, IAM policies, and stored data.

Security Benefit: Clearly defines security responsibilities and reduces misunderstandings.

---------------------------------------

## Cloud Attack Surface

Cloud Attack Surface: The collection of cloud resources, services, APIs, and configurations that could potentially be targeted by attackers.

Examples:
- Publicly exposed services
- Misconfigured storage buckets
- Weak IAM permissions
- Exposed APIs
- Unsecured virtual machines

Security Risk: Increased opportunities for unauthorized access and data exposure.

#########################################################################################################

# Cloud Shared Responsibility Model

Cloud Shared Responsibility Model: A security model that defines how security responsibilities are divided between the cloud service provider and the customer.

Use (Defender Side): Used by organizations, cloud administrators, and security teams to understand which security tasks are managed by the cloud provider and which remain the customer's responsibility.

Security Goal: Ensure that both the cloud provider and the customer properly secure their respective parts of the cloud environment.

Example: AWS secures the physical data centers and cloud infrastructure, while the customer is responsible for securing virtual machines, applications, IAM permissions, and stored data.

---------------------------------------

## Cloud Provider Responsibility

Cloud Provider Responsibility: The cloud provider is responsible for securing the infrastructure that runs cloud services.

Examples:
- Physical data centers
- Networking infrastructure
- Storage infrastructure
- Servers and hardware
- Virtualization layer
- Managed cloud services

Security Benefit: Customers do not need to manage or protect the underlying physical infrastructure.

---------------------------------------

## Customer Responsibility

Customer Responsibility: Customers are responsible for securing everything they deploy and manage in the cloud.

Examples:
- IAM users, roles, and permissions
- Virtual machines
- Applications
- Operating systems
- Databases
- Stored data
- Network configurations
- Encryption settings

Security Benefit: Gives customers full control over the security of their workloads and data.

---------------------------------------

## Responsibility by Service Model

Infrastructure as a Service (IaaS): Customers manage most security responsibilities, including operating systems, applications, and data.

Platform as a Service (PaaS): The cloud provider manages the underlying platform, while customers secure their applications, identities, and data.

Software as a Service (SaaS): The cloud provider manages nearly the entire service, while customers primarily manage user accounts, permissions, and data.

Security Impact: Customer responsibility decreases as the level of managed cloud service increases.

---------------------------------------

## Common Misunderstandings

Common Misunderstandings: Many cloud security incidents occur because customers assume the cloud provider automatically secures everything.

Examples:
- Publicly exposed storage buckets
- Overly permissive IAM policies
- Unencrypted sensitive data
- Weak authentication settings

Security Risk: Misconfigurations can lead to data breaches, unauthorized access, and compliance violations.


#########################################################################################################

# AWS IAM (Identity and Access Management)

AWS IAM: A cloud security service that manages authentication and authorization for AWS resources by controlling who can access what and what actions they are allowed to perform.

Use (Defender Side): Used by cloud administrators and security teams to securely manage users, roles, permissions, and access to AWS resources.

Security Goal: Enforce the principle of least privilege, protect cloud resources from unauthorized access, and securely manage identities.

Example: An organization grants developers access to Amazon EC2 but prevents them from deleting S3 buckets or modifying IAM policies.

---------------------------------------

## IAM Users

IAM User: An identity created for an individual person or application that needs to access AWS resources.

Use: Provides unique credentials and permissions for each user.

Example: Creating separate IAM users for developers, administrators, and automation tools.

Security Benefit: Improves accountability and access control.

---------------------------------------

## IAM Groups

IAM Group: A collection of IAM users that share the same permissions.

Use: Simplifies permission management by assigning policies to a group instead of individual users.

Example: Placing all developers into a "Developers" group with identical access permissions.

Security Benefit: Makes permission management easier and more consistent.

---------------------------------------

## IAM Roles

IAM Role: A temporary identity that provides permissions without requiring long-term credentials.

How it works: A user, AWS service, or application assumes a role and receives temporary security credentials with the permissions defined by that role.

Use: Securely grant temporary access to AWS resources.

Example: An EC2 instance assumes a role to access an S3 bucket without storing AWS access keys.

Security Benefit: Reduces the risk associated with long-term credentials.

---------------------------------------

## IAM Policies

IAM Policy: A JSON document that defines which actions are allowed or denied on specific AWS resources.

How it works: Policies are attached to users, groups, or roles to control access based on defined permissions.

Use: Enforce fine-grained access control across AWS services.

Example: Allowing read-only access to an S3 bucket while denying deletion permissions.

Security Benefit: Implements least privilege and reduces unauthorized access.

---------------------------------------

## IAM Privilege Escalation

IAM Privilege Escalation: A security issue where a user gains higher AWS permissions than originally intended because of overly permissive IAM configurations.

How it happens: Misconfigured IAM policies, excessive permissions, or incorrect role assignments allow a user to obtain additional privileges.

Use (Attacker Side): Used to gain broader access to AWS resources and administrative capabilities.

Example: A user with excessive IAM permissions is able to assign themselves a more privileged role.

Security Risk: Unauthorized administrative access, account compromise, and complete cloud environment takeover.

---------------------------------------

## Least Privilege Principle

Least Privilege: A security principle that grants users only the permissions required to perform their tasks.

Use: Minimizes unnecessary access and reduces the impact of compromised accounts.

Example: Granting a developer access only to the services required for application development.

Security Benefit: Reduces the attack surface and limits privilege escalation opportunities.

#########################################################################################################

# Amazon S3 Misconfiguration

Amazon S3 Misconfiguration: Security weaknesses caused by incorrect configuration of Amazon S3 buckets, permissions, or access controls that expose data or allow unauthorized access.

Use (Defender Side): Studied by cloud administrators, security engineers, and penetration testers to identify insecure S3 configurations and secure cloud storage.

Security Impact: Data leakage, unauthorized access, accidental data modification, data deletion, and compliance violations.

Example: A company accidentally makes an S3 bucket containing customer backups publicly accessible.

---------------------------------------

## Public Buckets

Public Bucket: An S3 bucket that allows anonymous users to access some or all of its contents.

How it happens: Public access is enabled through bucket policies, ACLs, or disabled Block Public Access settings.

Use (Attacker Side): Used to discover exposed files, backups, source code, or sensitive information.

Example: A publicly accessible bucket exposes confidential company documents.

Security Risk: Information disclosure and data breaches.

---------------------------------------

## Bucket Policies

Bucket Policy: A resource-based JSON policy that controls who can access an S3 bucket and what actions they can perform.

How it works: Policies grant or deny permissions to IAM users, roles, AWS accounts, or anonymous users.

Use: Control access to buckets and objects.

Example: Allowing only a specific IAM role to upload files to a bucket.

Security Risk: Overly permissive policies may unintentionally expose sensitive data.

---------------------------------------

## Access Control Lists (ACLs)

ACL (Access Control List): A legacy permission system used to grant read or write access to buckets and individual objects.

How it works: ACLs assign permissions to AWS accounts or predefined groups.

Use: Manage object-level or bucket-level permissions when required.

Example: Granting another AWS account read access to selected objects.

Security Risk: Incorrect ACL settings can expose private data.

---------------------------------------

## Pre-Signed URLs

Pre-Signed URL: A temporary URL that provides time-limited access to a private S3 object without requiring AWS credentials.

How it works: AWS generates a signed URL that remains valid until its expiration time.

Use: Securely share private files with users for a limited period.

Example: Sending a customer a temporary download link for a private invoice.

Security Risk: Anyone who obtains the URL before it expires can access the associated object.

---------------------------------------

## Block Public Access

Block Public Access: An S3 security feature that prevents buckets and objects from becoming publicly accessible.

How it works: It overrides public bucket policies and ACLs that would otherwise expose data.

Use: Prevent accidental public exposure of S3 resources.

Example: Enabling Block Public Access for all buckets within an AWS account.

Security Benefit: Significantly reduces the risk of data leaks caused by configuration mistakes.

---------------------------------------

## Bucket Versioning

Bucket Versioning: A feature that keeps multiple versions of an object within the same bucket.

How it works: When an object is modified or deleted, previous versions are retained instead of being permanently removed.

Use: Recover deleted or overwritten files and protect against accidental changes.

Example: Restoring a previous version of a document after it was accidentally deleted.

Security Benefit: Improves data recovery and resilience against accidental deletion or ransomware.

---------------------------------------

## Server-Side Encryption

Server-Side Encryption (SSE): A feature that automatically encrypts data when it is stored in an S3 bucket.

How it works: AWS encrypts objects during upload and decrypts them when accessed by authorized users.

Use: Protect sensitive information stored in S3.

Example: Encrypting customer records before they are written to a storage bucket.

Security Benefit: Protects data at rest from unauthorized access.

---------------------------------------

## S3 Logging & Monitoring

S3 Logging & Monitoring: Features that record bucket activity and monitor access to S3 resources.

How it works: Services such as CloudTrail and S3 server access logs record API calls and object access events.

Use: Detect suspicious activity, investigate incidents, and support compliance.

Example: Reviewing logs to identify unexpected access to sensitive files.

Security Benefit: Improves visibility, auditing, and incident response.


#########################################################################################################

# SSRF to Cloud Metadata Endpoint Attacks

SSRF to Cloud Metadata Endpoint Attacks: A cloud security issue where a Server-Side Request Forgery (SSRF) vulnerability is abused to make a server send requests to its own cloud metadata service, potentially exposing sensitive information such as temporary credentials and instance metadata.

Use (Attacker Side): Used to access cloud instance metadata, obtain temporary credentials, gather environment information, and potentially expand access within a cloud environment.

Security Impact: Credential exposure, unauthorized cloud resource access, privilege escalation, data compromise, and potential cloud account takeover.

Example: A vulnerable web application running on an AWS EC2 instance is tricked into requesting the instance metadata service, exposing temporary IAM role credentials.

---------------------------------------

## Server-Side Request Forgery (SSRF)

SSRF: A vulnerability that allows an attacker to make a server send unintended requests to internal or external resources.

How it happens: An application accepts a user-supplied URL or resource without proper validation and fetches it on behalf of the user.

Use (Attacker Side): Used to access internal services, cloud metadata endpoints, or resources that are not directly accessible from the internet.

Example: A web application fetches an attacker-controlled URL that redirects the request to an internal service.

Security Risk: Internal network access, sensitive information disclosure, and cloud credential theft.

---------------------------------------

## Cloud Metadata Service

Cloud Metadata Service: A special service provided by cloud platforms that supplies information about a running virtual machine or instance.

How it works: The cloud instance can query the metadata service to retrieve information such as instance ID, region, networking details, and temporary credentials.

Use: Enables applications and cloud services to obtain instance-specific configuration and credentials.

Example: An EC2 instance retrieves temporary IAM credentials from the metadata service.

Security Risk: Unauthorized access to the metadata service may expose sensitive cloud information.

---------------------------------------

## Temporary IAM Credentials

Temporary IAM Credentials: Short-lived access credentials automatically provided to cloud instances through attached IAM roles.

How it works: Applications use these credentials instead of storing permanent AWS access keys.

Use: Secure access to AWS services without embedding long-term credentials.

Example: An EC2 instance accesses an S3 bucket using temporary credentials assigned through an IAM role.

Security Risk: If exposed, these credentials may allow unauthorized access to cloud resources.

---------------------------------------

## Instance Metadata Service Version 2 (IMDSv2)

IMDSv2: An enhanced version of the AWS Instance Metadata Service that adds session-based authentication to protect against unauthorized metadata access.

How it works: Clients must first obtain a temporary session token before requesting metadata.

Use: Reduces the risk of SSRF-based metadata access.

Example: An EC2 instance requires a valid IMDSv2 session token before returning IAM role credentials.

Security Benefit: Provides stronger protection against metadata endpoint attacks.

---------------------------------------

## SSRF Mitigation

SSRF Mitigation: Security measures designed to prevent attackers from abusing SSRF vulnerabilities.

Examples:
- Validate and sanitize user-supplied URLs.
- Restrict outbound requests to trusted destinations.
- Block access to internal IP ranges and metadata endpoints.
- Enable IMDSv2 instead of IMDSv1.
- Apply least privilege to IAM roles.
- Monitor unusual outbound network requests.

Security Benefit: Reduces the likelihood of cloud credential theft and unauthorized access.

#########################################################################################################

# AWS Security Services

AWS Security Services: Native AWS services designed to help organizations monitor, detect, investigate, and respond to security threats while improving the overall security posture of their cloud environment.

Use (Defender Side): Used by cloud administrators, security engineers, SOC analysts, and incident responders to detect threats, monitor AWS activity, audit cloud environments, and maintain security compliance.

Security Goal: Detect malicious activity, improve visibility, support incident response, and strengthen cloud security.

Example: An organization uses AWS CloudTrail to audit API activity, GuardDuty to detect suspicious behavior, and Security Hub to manage security findings from multiple AWS services.

---------------------------------------

## Amazon GuardDuty

Amazon GuardDuty: A threat detection service that continuously monitors AWS accounts and workloads for suspicious or malicious activity.

How it works: GuardDuty analyzes AWS logs, network activity, DNS requests, and account behavior to identify potential threats using threat intelligence and machine learning.

Use: Detect compromised accounts, malicious network activity, cryptocurrency mining, and other cloud threats.

Example: GuardDuty alerts when an EC2 instance communicates with a known malicious IP address.

Security Benefit: Continuous threat detection with minimal manual configuration.

---------------------------------------

## AWS Security Hub

AWS Security Hub: A centralized security management service that collects, organizes, and prioritizes security findings from AWS services and supported third-party security tools.

How it works: Security Hub aggregates findings, performs security checks against best practices, and provides a unified security dashboard.

Use: Monitor security posture, prioritize vulnerabilities, and simplify compliance management.

Example: Security Hub reports an S3 bucket with public access and recommends remediation.

Security Benefit: Centralized visibility into security findings across AWS resources.

---------------------------------------

## AWS CloudTrail

AWS CloudTrail: A logging and auditing service that records AWS API calls and account activity.

How it works: CloudTrail captures events generated by users, applications, and AWS services, creating an audit trail for security investigations.

Use: Audit AWS activity, investigate incidents, monitor administrative actions, and support compliance.

Example: Reviewing CloudTrail logs to determine who modified an IAM policy.

Security Benefit: Provides detailed visibility and accountability for AWS account activity.

---------------------------------------

## Amazon CloudWatch

Amazon CloudWatch: A monitoring service that collects metrics, logs, and events from AWS resources and applications.

How it works: CloudWatch monitors resource performance, collects logs, and generates alerts when predefined conditions are met.

Use: Monitor system health, detect operational issues, and automate responses to security events.

Example: Sending an alert when an EC2 instance experiences unusually high CPU usage.

Security Benefit: Improves visibility and enables proactive monitoring.

---------------------------------------

## AWS Inspector

AWS Inspector: A vulnerability management service that continuously scans AWS workloads for security weaknesses and software vulnerabilities.

How it works: Inspector analyzes EC2 instances, container images, and other supported resources to identify known vulnerabilities and configuration issues.

Use: Detect vulnerabilities and prioritize remediation.

Example: Inspector identifies a critical software vulnerability on an EC2 instance.

Security Benefit: Continuous vulnerability assessment across AWS workloads.

#########################################################################################################

# Infrastructure Security Scanning with Checkov & tfsec

Infrastructure Security Scanning with Checkov & tfsec: The process of automatically analyzing Infrastructure as Code (IaC) files to identify security misconfigurations before cloud resources are deployed.

Use (Defender Side): Used by DevSecOps engineers, cloud security engineers, and developers to detect security issues early in the development lifecycle and enforce secure cloud configurations.

Security Goal: Prevent insecure cloud deployments, reduce misconfigurations, and improve compliance by identifying security issues before infrastructure is provisioned.

Example: A Terraform project is scanned before deployment, revealing that an S3 bucket is publicly accessible and an EC2 security group allows unrestricted SSH access.

---------------------------------------

## Infrastructure as Code (IaC)

Infrastructure as Code (IaC): The practice of defining and managing cloud infrastructure using configuration files instead of manual setup.

How it works: Infrastructure resources are described in code and automatically created using IaC tools.

Use: Automate cloud deployments and maintain consistent infrastructure.

Example: Using Terraform to provision AWS infrastructure.

Security Benefit: Improves consistency, automation, and version control.

---------------------------------------

## Checkov

Checkov: An open-source Infrastructure as Code security scanner that analyzes cloud configuration files for security and compliance issues.

How it works: Checkov scans IaC templates and compares them against built-in security policies and best practices.

Use: Identify insecure cloud configurations before deployment.

Example: Detecting an unencrypted S3 bucket or an overly permissive security group.

Security Benefit: Prevents cloud misconfigurations during development.

---------------------------------------

## tfsec

tfsec: An open-source security scanner designed specifically for Terraform configurations.

How it works: tfsec analyzes Terraform files and reports security weaknesses based on cloud security best practices.

Use: Detect Terraform security issues before infrastructure is deployed.

Example: Reporting an AWS security group that allows unrestricted inbound access.

Security Benefit: Reduces the risk of insecure Terraform deployments.

---------------------------------------

## Security Policies

Security Policies: Predefined security rules used to evaluate cloud infrastructure configurations.

How it works: Scanning tools compare IaC files against security policies and report violations.

Use: Enforce security standards and organizational requirements.

Example: Requiring encryption for all storage resources.

Security Benefit: Ensures consistent security across cloud environments.

---------------------------------------

## CI/CD Integration

CI/CD Integration: Running security scans automatically as part of the software development and deployment pipeline.

How it works: Infrastructure code is scanned whenever changes are committed or before deployment.

Use: Detect security issues early and prevent insecure infrastructure from reaching production.

Example: Automatically scanning every Terraform pull request before it is merged.

Security Benefit: Supports continuous security and DevSecOps practices.


#########################################################################################################

# Cloud Penetration Testing with Pacu (AWS)

Cloud Penetration Testing with Pacu: The process of assessing the security of AWS environments using Pacu, an open-source AWS exploitation framework designed for authorized cloud security testing.

Use (Defender Side): Used by penetration testers, red teamers, cloud security engineers, and security researchers to identify misconfigurations, excessive IAM permissions, and other security weaknesses in AWS environments.

Security Goal: Identify and remediate AWS security weaknesses before they can be exploited by attackers.

Example: A penetration tester uses Pacu during an authorized assessment to identify overly permissive IAM roles and publicly exposed AWS resources.

---------------------------------------

## Pacu

Pacu: An open-source AWS exploitation and security assessment framework used for authorized penetration testing.

How it works: Pacu uses AWS credentials to interact with AWS services, enumerate resources, identify security weaknesses, and perform authorized security assessments through modular plugins.

Use (Defender Side): Assess AWS environments and validate cloud security controls.

Example: Using Pacu to enumerate IAM users, roles, and S3 buckets during an authorized penetration test.

Security Benefit: Helps identify cloud security misconfigurations before attackers do.

---------------------------------------

## AWS Enumeration

AWS Enumeration: The process of discovering AWS resources, identities, permissions, and configurations.

How it works: Security assessment tools collect information about AWS services and resources accessible with the provided permissions.

Use: Identify the attack surface and security posture of an AWS environment.

Example: Enumerating IAM users, EC2 instances, Lambda functions, and S3 buckets.

Security Benefit: Improves visibility into cloud assets and configurations.

---------------------------------------

## IAM Assessment

IAM Assessment: Evaluating IAM users, roles, groups, and policies to identify excessive permissions and insecure access controls.

How it works: Permissions are reviewed to determine whether they violate the principle of least privilege.

Use: Detect privilege escalation opportunities and overly permissive IAM configurations.

Example: Identifying an IAM role with unnecessary administrative permissions.

Security Benefit: Reduces the risk of unauthorized access and privilege escalation.

---------------------------------------

## S3 Security Assessment

S3 Security Assessment: Reviewing S3 bucket configurations to identify insecure storage settings.

How it works: Bucket permissions, policies, encryption, and public access settings are evaluated.

Use: Detect publicly accessible buckets and insecure storage configurations.

Example: Identifying an S3 bucket that unintentionally allows public read access.

Security Benefit: Prevents data exposure and storage-related security incidents.

---------------------------------------

## Security Findings

Security Findings: Documented security issues discovered during a cloud penetration test.

How it works: Findings are analyzed, assigned a risk level, and accompanied by remediation recommendations.

Use: Help organizations understand and fix cloud security weaknesses.

Example: Reporting an overprivileged IAM role with recommendations to apply least privilege.

Security Benefit: Supports risk reduction and continuous cloud security improvement.


#########################################################################################################
