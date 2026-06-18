# Web Application Security (Overview)

## Web Application Security

Web Application Security: Protection of websites and web apps from attacks that target data, users, and application logic.

Use: Used to keep user data, login systems, and web services safe from hackers.

How it works: Security controls are added in applications (frontend + backend + server) to prevent unauthorized access and attacks.

Example: Online banking, social media platforms, e-commerce websites.

---------------------------------------------------------

# Common Web Attacks (Core Concepts)

## SQL Injection (SQLi)

SQL Injection: An attack where malicious SQL queries are inserted into input fields.

Use (Attacker side): Used to access, modify, or delete database data.

Example: Login bypass using ' OR 1=1 --

Impact: Can leak user data, passwords, and full database access.

---------------------------------------------------------

## Cross-Site Scripting (XSS)

XSS: An attack where malicious scripts are injected into web pages viewed by users.

Use: Used to steal cookies, sessions, or redirect users.

Example: Injecting JavaScript into comment boxes.

Impact: Session hijacking and user impersonation.

---------------------------------------------------------

## Cross-Site Request Forgery (CSRF)

CSRF: An attack that tricks a logged-in user into performing unwanted actions.

Use: Used to perform actions like changing password or transferring money.

Example: A hidden request sent when user clicks a malicious link.

Impact: Unauthorized actions using victim’s session.

---------------------------------------------------------

## Authentication Failures

Authentication Failure: Weak login systems that allow attackers to bypass or steal credentials.

Examples:
- Weak passwords
- No MFA
- Session hijacking

Impact: Account takeover.

---------------------------------------------------------

## Broken Access Control

Broken Access Control: Users can access data or functions they should not be allowed to access.

Example: A normal user accessing admin panel using URL manipulation.

Impact: Data leakage and privilege escalation.

---------------------------------------------------------

## Security Misconfiguration

Security Misconfiguration: Incorrect server or application settings that expose vulnerabilities.

Example:
- Default passwords
- Open admin panels
- Unpatched servers

Impact: Easy exploitation by attackers.

---------------------------------------------------------

#########################################################################################################

# SQL Injection (SQLi): Error-Based, Blind, Time-Based, Out-of-Band

## SQL Injection (SQLi)

SQL Injection: An attack where an attacker injects malicious SQL queries into a web application input to manipulate the database.

Use (Attacker side): Used to read, modify, or delete database data or bypass login systems.

Example: ' OR 1=1 -- [used to bypass login.]

Impact: Full database compromise, data theft, authentication bypass.

---------------------------------------------------------

## Error-Based SQL Injection

Error-Based SQLi: An attack that uses database error messages to extract information.

Use: Used when the application shows database errors.

How it works: Attacker forces SQL errors and reads error output to learn database structure.

Example: Triggering SQL errors that reveal table or column names.

Security Risk: Leads to information disclosure.

---------------------------------------------------------

## Blind SQL Injection

Blind SQLi: An attack where no direct error or output is shown, but attacker infers data indirectly.

Use: Used when applications do not show database errors.

How it works: Attacker sends true/false queries and observes application behavior.

Example: Page behaves differently for TRUE vs FALSE conditions.

Security Risk: Slow but can extract full database data.

---------------------------------------------------------

## Time-Based Blind SQL Injection

Time-Based SQLi: A type of blind SQL injection where database response time is used to extract data.

Use: Used when no visible output or errors are available.

How it works: Attacker forces database to delay response (e.g., sleep function) based on condition.

Example: If response is delayed → condition is TRUE.

Security Risk: Very slow but effective for data extraction.

---------------------------------------------------------

## Out-of-Band SQL Injection

Out-of-Band SQLi: An attack where data is extracted using a different channel (not direct web response).

Use: Used when direct response is not possible.

How it works: Database sends data to an external server controlled by attacker (DNS/HTTP requests).

Example: Database making DNS request to attacker-controlled domain.

Security Risk: Hard to detect and very dangerous in misconfigured systems.

#########################################################################################################

# XSS (Cross-Site Scripting): Reflected, Stored, DOM-based, CSP Bypass

## XSS (Cross-Site Scripting)

XSS: A web vulnerability where attackers inject malicious scripts into web pages viewed by users.

Use: Used to steal cookies, hijack sessions, redirect users, or perform actions on behalf of victims.

Impact: User account takeover, session theft, data leakage.

Example: Malicious script is injected into a website input and executed in the user’s browser.

---------------------------------------------------------

## Reflected XSS

Reflected XSS: An attack where malicious input is immediately returned by the server and executed in the browser.

How it works: User input is included in the response without proper filtering, causing execution in the browser.

Example: A user clicks a malicious link and the website reflects unsafe input in the response.

Security Risk: Requires user interaction, often used in phishing attacks.

---------------------------------------------------------

## Stored XSS

Stored XSS: An attack where malicious content is permanently stored on the server.

How it works: Input is saved in a database and shown to multiple users, causing automatic execution in their browsers.

Example: A comment or post contains malicious content that affects every user who views it.

Security Risk: Very dangerous because it affects many users.

---------------------------------------------------------

## DOM-based XSS

DOM XSS: An attack that happens entirely in the browser due to unsafe client-side JavaScript.

How it works: JavaScript reads untrusted input (like URL or page data) and updates the page without validation.

Example: A web page dynamically updates content using unsafe user input.

Security Risk: Hard to detect because it does not involve server response.

---------------------------------------------------------

## CSP Bypass (Content Security Policy Bypass)

CSP Bypass: An attack where browser security rules (Content Security Policy) are bypassed due to weak configuration.

How it works: Attackers exploit misconfigured or overly permissive CSP rules.

Example: A website allows unsafe external resources due to weak security policy.

Security Risk: Can reduce or fully bypass browser-level XSS protection.

#########################################################################################################

# CSRF and SameSite Cookie Nuances

## CSRF (Cross-Site Request Forgery)

CSRF: A web attack where a user is tricked into performing unwanted actions on a website where they are already authenticated.

Use (Attacker side): Used to make a victim perform actions like changing account settings or performing transactions without their knowledge.

How it works: If a user is logged into a site, an attacker can trigger hidden requests from another site using the user’s active session.

Impact: Unauthorized actions using the victim’s account (account change, money transfer, etc.).

Example: A logged-in user unknowingly triggers an unwanted action just by visiting a malicious page.

---------------------------------------------------------

## CSRF Token (Protection Concept)

CSRF Token: A random, unique value added to requests to verify that the request comes from the legitimate user session.

Use: Prevents unauthorized requests from external websites.

How it works: Server checks whether the request contains a valid token before processing it.

Security Note: Without a valid token, the request is rejected.

---------------------------------------------------------

## SameSite Cookies

SameSite Cookie: A browser security feature that controls when cookies are sent in cross-site requests.

---------------------------------------------------------

## SameSite=Strict

Strict Mode: Cookies are only sent in first-party requests.

Use: Maximum protection against CSRF.

Effect: Cross-site requests cannot use cookies at all.

---------------------------------------------------------

## SameSite=Lax

Lax Mode: Cookies are sent in some safe cross-site navigation (like links), but not in most cross-site requests.

Use: Balanced security and usability.

Effect: Helps reduce CSRF risk while keeping user experience smooth.

---------------------------------------------------------

## SameSite=None

None Mode: Cookies are sent in all cross-site requests, but must use Secure flag (HTTPS).

Use: Required for third-party integrations.

Risk: Can allow CSRF if not protected with additional mechanisms.

---------------------------------------------------------

## CSRF vs SameSite Cookies
- CSRF is an attack technique
- SameSite is a browser defense mechanism

They work together with other protections like CSRF tokens.

#########################################################################################################

# SSRF (Server-Side Request Forgery): Cloud Metadata & Internal Network Pivoting

## SSRF (Server-Side Request Forgery)

SSRF: A web vulnerability where an attacker forces a server to make requests to unintended internal or external resources.

Use (Attacker side): Used to access internal services, sensitive data, or restricted cloud resources through a vulnerable server.

Impact: Internal network exposure, cloud credential theft, service compromise.

Example: A web server is tricked into sending requests to internal-only services that are not accessible from the internet.

---------------------------------------------------------

## How SSRF Works

How it works: The attacker controls a URL or input that the server uses to fetch data. Instead of accessing a normal external resource, the server is tricked into accessing internal systems.

Security Risk: Server becomes a proxy to internal network resources.

---------------------------------------------------------

## Cloud Metadata Attacks

Cloud Metadata SSRF: An attack where SSRF is used to access cloud instance metadata services.

Use: Used to steal sensitive cloud configuration and credentials.

How it works: The server is tricked into querying internal cloud metadata endpoints that contain sensitive information.

Example: Retrieving cloud instance identity, API keys, or temporary credentials from internal metadata services.

Security Risk: Can lead to full cloud account compromise.

---------------------------------------------------------

## Internal Network Pivoting

Internal Pivoting: An SSRF technique where the attacker uses the vulnerable server to scan and access internal network systems.

Use: Used to discover internal services not exposed to the internet.

How it works: The server is used as a bridge to interact with internal IP ranges and services.

Example: Accessing internal admin panels, databases, or services behind a firewall.

Security Risk: Breaks network isolation and exposes internal infrastructure.

---------------------------------------------------------

## SSRF Attack Types (Common Targets)
- Internal services (localhost, private IP ranges)
- Cloud metadata endpoints
- Internal APIs and dashboards
- Database or admin panels

#########################################################################################################

# Authentication Flaws: JWT Confusion, Session Fixation, and Related Issues

## Authentication Flaws

Authentication Flaws: Security weaknesses in login systems that allow attackers to impersonate users or bypass identity verification.

Use (Attacker side): Used to gain unauthorized access to accounts and sensitive systems.

Impact: Account takeover, privilege escalation, identity spoofing.

Example: An attacker gains access to another user’s session without knowing the password.

---------------------------------------------------------

## JWT Confusion (JSON Web Token Issues)

JWT Confusion: A vulnerability caused by incorrect validation or misuse of JWT tokens.

How it happens: Applications trust JWTs without properly verifying signature, algorithm, or token integrity.

Use (Attacker side): Used to forge or modify tokens to impersonate other users.

Example: A system accepts a tampered token and treats attacker as an admin user.

Security Risk: Broken authentication and privilege escalation.

---------------------------------------------------------

## Session Fixation

Session Fixation: An attack where an attacker forces a user to use a known session ID.

How it works: Attacker sets or predicts a session ID, then tricks the victim into logging in with it.

Use (Attacker side): Once the victim logs in, the attacker reuses the same session to access the account.

Example: User logs into a system using a session already known by the attacker.

Security Risk: Session hijacking and account takeover.

---------------------------------------------------------

## Broken Session Management

Broken Session Management: Weak handling of user sessions that allows unauthorized access.

Examples:
- Sessions not expiring properly
- Session IDs exposed in URLs
- No regeneration after login

Security Risk: Session hijacking and replay attacks.

---------------------------------------------------------

## Weak Password Mechanisms

Weak Authentication: Poor password policies or insecure login systems.

Examples:
- Weak passwords allowed
- No multi-factor authentication
- Poor rate limiting

Security Risk: Brute-force attacks and credential stuffing.



#########################################################################################################

# IDOR and Broken Access Control

## Broken Access Control

Broken Access Control: A web vulnerability where users can access data or actions that they are not authorized to access.

Use (Attacker side): Used to view, modify, or delete other users’ data or access admin-level functions.

Impact: Data leakage, privilege escalation, full account or system compromise.

Example: A normal user is able to access admin-only pages or modify other users’ information.

---------------------------------------------------------

## How Broken Access Control Happens

How it works: The application fails to properly check whether the user is allowed to perform a specific action or access a resource.

Security Risk: Authorization logic is missing or incorrectly implemented.

---------------------------------------------------------

## IDOR (Insecure Direct Object Reference)

IDOR: A specific type of broken access control where a user can access objects (like files, records, or data) by manipulating identifiers.

Use (Attacker side): Used to access other users’ private data by changing object references.

How it works: The application directly uses user-supplied IDs without checking ownership.

Example: A user changes an account ID in a request and accesses another user’s profile or data.

Security Risk: Direct data exposure and unauthorized access.

---------------------------------------------------------

## IDOR vs Broken Access Control

Broken Access Control = broad category
IDOR = specific type of broken access control

---------------------------------------------------------

## Common Targets of IDOR
- User profiles
- Orders and invoices
- Files and documents
- API resources



#########################################################################################################

# Burp Suite Master Note (Beginner → Advanced)

---------------------------------------------------------

## Burp Suite Overview

Burp Suite: A web application security testing tool used to intercept, analyze, and attack HTTP/HTTPS traffic.

Use: Used by security testers to find vulnerabilities like SQLi, XSS, CSRF, IDOR, authentication flaws, etc.

How it works: It acts as a proxy between browser and server, capturing all web traffic for testing and manipulation.


---------------------------------------------------------

## Core Architecture

Burp Suite works in 3 main layers:
- Browser → Burp Proxy → Server
- Intercepts requests and responses
- Allows modification before forwarding

---------------------------------------------------------

## 1. Proxy (Core Feature)

Proxy: Intercepts and controls all HTTP/HTTPS traffic.

Use: Inspect and modify requests/responses in real time.

Key Features:
- Intercept requests
- Modify parameters
- View full traffic history

Example: Changing request data before it reaches server to test behavior.

---------------------------------------------------------

## 2. Intercept

Intercept: A feature inside Proxy that stops requests before sending.

Use: Used to manually edit requests.

How it works: Request is paused → modified → then forwarded.

Example: Editing login request before submission.

---------------------------------------------------------

## 3. Target / Site Map

Target (Site Map): Automatically maps the entire web application structure.

Use: Used to understand endpoints, APIs, and hidden paths.

Example: Viewing all API endpoints of a web application.

---------------------------------------------------------

## 4. Repeater

Repeater: Tool to manually modify and resend requests.

Use: Testing how server reacts to different inputs.

Example: Testing different API parameters repeatedly.

---------------------------------------------------------

## 5. Intruder

Intruder: Automated tool for sending multiple modified requests.

Use: Used for fuzzing, brute force, and parameter testing.

How it works: Changes selected input fields and sends many requests automatically.

Example: Testing multiple usernames or input variations.

---------------------------------------------------------

## 6. Scanner (Pro Feature)

Scanner: Automatically detects vulnerabilities in web applications.

Use: Finds SQLi, XSS, misconfigurations, etc.

How it works: Crawls and analyzes the application automatically.

Example: Automatically detecting insecure input fields.

---------------------------------------------------------

## 7. Sequencer

Sequencer: Analyzes randomness of tokens (session IDs, cookies).

Use: Checks if tokens are predictable.

Example: Testing session ID randomness for security weakness.

---------------------------------------------------------

## 8. Decoder / Encoder

Decoder: Encodes and decodes data formats.

Use: Used for Base64, URL encoding, hex conversion.

Example: Decoding encoded tokens during analysis.

---------------------------------------------------------

## 9. Comparer

Comparer: Compares two requests or responses.

Use: Used to detect differences in behavior.

Example: Comparing normal vs modified responses.

---------------------------------------------------------

## 10. Extender (BApp Store)

Extender: Allows adding plugins to Burp Suite.

Use: Extends functionality with custom tools.

Example: Installing extensions for advanced scanning.

---------------------------------------------------------

## 11. Scope Control

Scope: Defines which targets Burp should analyze.

Use: Focus testing on specific applications only.

Example: Restricting Burp to one domain.

---------------------------------------------------------

Burp Suite Attack Workflow:
- Set browser proxy → Burp
- Capture traffic using Proxy
- Map application using Site Map
- Test requests using Repeater
- Automate testing using Intruder
- Analyze results manually
- Use Scanner for automation (Pro)

---------------------------------------------------------

Common Use Cases:
- SQL Injection testing
- XSS detection
- CSRF testing
- IDOR testing
- Authentication bypass testing
- API security testing

---------------------------------------------------------

## Security Testing Logic

Burp Suite helps answer:
- What data is being sent?
- Can input be modified?
- Is access properly controlled?
- Are tokens secure?
- Can responses be manipulated?

#########################################################################################################










