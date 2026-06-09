                                                       OSI Model and Where Attacks Happen at Each Layer

What is the OSI Model?
  The OSI (Open Systems Interconnection) Model is a framework that describes how data moves across a network.

Instead of treating communication as one large process, the OSI Model divides it into 7 layers, each with a specific responsibility.

Think of it like sending a package: You write the message. You put it in a box. A shipping company transports it. The recipient receives and opens it.

Network communication works similarly.

--------------------------------------------

   The 7 Layers of the OSI Model
    | Layer | Name         |
    | ----- | ------------ |
    | 7     | Application  |
    | 6     | Presentation |
    | 5     | Session      |
    | 4     | Transport    |
    | 3     | Network      |
    | 2     | Data Link    |
    | 1     | Physical     |

-------------------------------------

    Layer 7 – Application

Purpose: Provides network services directly to applications used by users.

Examples: HTTP, HTTPS, FTP, DNS, SMTP

Common Attacks: SQL Injection (SQLi), Cross-Site Scripting (XSS), Phishing, Command Injection,

Attack Goal: Steal data, bypass authentication, or execute malicious code.

Real-World Scenario: An attacker exploits a vulnerable website login form to gain access to sensitive user information.

--------------------------------------------

    Layer 6 – Presentation

Purpose: Handles data formatting, encryption, decryption, and compression.

Examples: SSL/TLS, JPEG, PNG, MP4

Common Attacks: SSL Stripping, Certificate Spoofing, Weak Encryption Exploitation,

Attack Goal: Bypass encryption and read protected data.

Real-World Scenario: An attacker intercepts a secure connection and forces it to use an insecure protocol.

------------------------------------------

    Layer 5 – Session

Purpose: Establishes, manages, and terminates communication sessions.

Common Attacks: Session Hijacking, Session Replay, Session Fixation,

Attack Goal: Take control of an authenticated user's session.

Real-World Scenario: An attacker steals a session cookie and gains access to a user's account without knowing the password.

-------------------------------------

    Layer 4 – Transport

Purpose: Provides reliable end-to-end communication.

Protocols: TCP, UDP

Common Attacks: SYN Flood, UDP Flood, TCP Reset Attack,

Attack Goal: Disrupt services or exhaust server resources.

Real-World Scenario: A server becomes unavailable after receiving a massive number of fake connection requests.

-----------------------------------

    Layer 3 – Network

Purpose: Handles logical addressing and packet routing.

Protocols: IP, ICMP, IPSec

Common Attacks: IP Spoofing, ICMP Flood, Smurf Attack, Routing Attacks,

Attack Goal: Hide the attacker's identity or manipulate network traffic.

Real-World Scenario: An attacker uses a fake IP address to disguise the source of malicious traffic.

------------------------------------

    Layer 2 – Data Link

Purpose: Provides communication between devices on the same local network.

Protocols: Ethernet, ARP, MAC

Common Attacks: ARP Spoofing, MAC Flooding, VLAN Hopping,

Attack Goal: Intercept, redirect, or monitor local network traffic.

Real-World Scenario: An attacker tricks devices into sending traffic through their machine, allowing them to monitor communications.

---------------------------------------

    Layer 1 – Physical

Purpose: Handles the physical transmission of data through hardware and media.

Examples: Network Cables, Fiber Optics, Wireless Signals, Network Devices

Common Attacks: Cable Tapping, Signal Jamming, Hardware Theft, Device Tampering,

Attack Goal: Gain physical access to data or disrupt communications.

Real-World Scenario: An attacker connects a device to a network cable to capture transmitted traffic


###############################################################################################################################

                                                        TCP/IP Stack: IP Addressing, Subnetting, and CIDR

Definition: 
The TCP/IP Stack is the networking model used by the Internet. It defines how devices communicate and exchange data.

TCP/IP Layers

    | Layer          | Function                           |
    | -------------- | ---------------------------------- |
    | Application    | User-facing network services       |
    | Transport      | End-to-end communication (TCP/UDP) |
    | Internet       | Routing and IP addressing          |
    | Network Access | Physical network communication     |

-------------------------------------------------------------

             IP Addressing
An IP Address uniquely identifies a device on a network, similar to how a home address identifies a house.

Without IP addresses, devices would not know where to send or receive data.

----------------------------------------------------------------

    IPv4 Address Structure

IPv4 consists of 32 bits divided into 4 octets.

Example 192.168.1.10
Each octet ranges from: 0 - 255

----------------------------------------------------------------

    Public vs Private IP

Public IP: Routable on the Internet, Assigned by an ISP, Globally unique

Example: 8.8.8.8

Private IP: Used inside local networks.
Ranges: 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, 192.168.0.0 - 192.168.255.255

Real-World Scenario: 
  Your router may have: Public IP: 103.x.x.x
  While your laptop has: Private IP: 192.168.1.10
    
    The router translates between them using NAT.

------------------------------------------------------------------------------

        Subnetting

Definition: Subnetting is the process of dividing a large network into smaller networks called subnets.

Why Use Subnetting?: Better network organization, Reduced broadcast traffic, Improved performance, Increased security, Efficient IP allocation
  
Example: 
  Suppose a company owns: 192.168.1.0/24
  Instead of one large network, it can create: 192.168.1.0/26, 192.168.1.64/26, 192.168.1.128/26, 192.168.1.192/26

    Now different departments can use different subnets.

Real-World Scenario: 

  A company separates: HR Department, Finance Department, IT Department

into different subnets to reduce unnecessary traffic and improve security.

-----------------------------------------------------------------------------

        CIDR (Classless Inter-Domain Routing)
Definition: 
  CIDR is a method of representing IP networks using a prefix length.

  Instead of using old class-based networking (Class A, B, C), CIDR provides flexible network allocation.

CIDR Notation
  Format: IP_Address/Prefix
  Example: 192.168.1.0/24
    The number after "/" indicates how many bits belong to the network portion.

Common CIDR Values

    | CIDR | Subnet Mask     | Usable Hosts |
    | ---- | --------------- | ------------ |
    | /8   | 255.0.0.0       | 16,777,214   |
    | /16  | 255.255.0.0     | 65,534       |
    | /24  | 255.255.255.0   | 254          |
    | /25  | 255.255.255.128 | 126          |
    | /26  | 255.255.255.192 | 62           |
    | /27  | 255.255.255.224 | 30           |
    | /28  | 255.255.255.240 | 14           |
    | /30  | 255.255.255.252 | 2            |

Example: 
  Network: 192.168.1.0/24
  Meaning : 24 bits = Network Portion, 8 bits = Host Portion
  Total Addresses : 256
  Usable Hosts : 254

    (Network Address and Broadcast Address cannot be assigned to devices.)


----------------------------------------------------------------------------------

    Relationship Between IP Addressing, Subnetting, and CIDR

IP Addressing : Identifies devices.
Example: 192.168.1.10

Subnetting : Divides networks into smaller sections.
Example: 192.168.1.0/26

CIDR : Defines network size using prefix notation.
Example: /24, /26, /28,


Security Perspective : Subnetting improves security by separating systems.
Example: 
  HR Network : 192.168.10.0/24
  Finance Network : 192.168.20.0/24
  IT Network : 192.168.30.0/24
  
      If one subnet is compromised, attackers may have more difficulty reaching other departments.


##############################################################################################################

                                                            TCP Handshake, TCP Connection States, and RST Attacks

What is TCP?
  TCP (Transmission Control Protocol) is a protocol that helps two devices communicate reliably over a network.
Before sending data, TCP creates a connection between the devices and makes sure the data arrives correctly and in the right order.

Examples: Opening a website (HTTP/HTTPS), Using SSH, Sending emails, Transferring files

------------------------------------------------------------------------------------

TCP Handshake
What is TCP Handshake?
  Before a client and a server can exchange data, they must first establish a connection. This process is called the TCP Handshake.
It allows both devices to confirm that they are ready to communicate.

How It Works

    Client                         Server
    
    SYN -------------------------->
    
          <---------------- SYN-ACK
    
    ACK -------------------------->
  
  Connection Established
  
-----------------------------------------

Step 1: SYN
  The client sends a SYN packet to request a connection.
Think: "Can we communicate?"

Step 2: SYN-ACK
  The server responds with SYN-ACK.
Think: "Yes, I'm ready."

Step 3: ACK
  The client sends an ACK packet.
Think: "Great, let's start."

Real-World Example: When you visit a website, your browser performs a TCP handshake with the web server before loading the page.

-----------------------------------------------------------------------------------------

Connection States
What are Connection States?
  Connection states show the current stage of a TCP connection, from creation to termination.

Main States
LISTEN : The server is waiting for connection requests.

SYN-SENT : The client has sent a SYN packet.

SYN-RECEIVED : The server received the SYN and replied with SYN-ACK.

ESTABLISHED : The connection is active and data can be exchanged.

FIN-WAIT : One side wants to close the connection.

TIME-WAIT : TCP waits for a short period to ensure all packets have arrived.

CLOSED : The connection is fully terminated.

Simplified Lifecycle

    LISTEN
       ↓
    SYN-SENT
       ↓
    SYN-RECEIVED
       ↓
    ESTABLISHED
       ↓
    FIN-WAIT
       ↓
    TIME-WAIT
       ↓
    CLOSED

-------------------------------------------------------------------------------

    RST (Reset)
What is an RST Packet?
  RST (Reset) is a TCP flag used to immediately close a connection.
Unlike a normal close, an RST does not follow the usual shutdown process.

It simply says: "End this connection right now."

Normal Connection Close

    Client                    Server
    
    FIN --------------------->
    
         <---------------- ACK
    
         <---------------- FIN
    
    ACK --------------------->

The connection closes gracefully.



RST Close
  
    Client                    Server
    
    RST --------------------->

The connection closes immediately.

--------------------------------------------------------------------------

    RST Attack
What is an RST Attack?
  An RST Attack happens when an attacker sends a fake RST packet to an active TCP connection.
The devices believe the reset packet is legitimate and immediately close the connection.

How It Works

    Client <===========> Server
               ↑
               |
           Fake RST

Result : Connection Closed

------------------------------------------------------------------------

Attack Goal : Disconnect users, Interrupt SSH sessions, Break VPN connections, Disrupt communication, Cause service interruptions
  
Real-World Example : 
You are connected to a remote Linux server using SSH. An attacker sends a fake RST packet. Your SSH session suddenly disconnects even though neither you nor the server chose to end the connection.

Why is it Dangerous?
RST attacks can: Interrupt important communications, Disconnect administrators from servers, Disrupt business services, Help attackers cause denial-of-service situations

##############################################################################################################

                                                        DNS Resolution, DNS Zones, and DNS-Based Attacks

What is DNS?
  DNS (Domain Name System) is like the Internet's phonebook.

Humans use domain names such as: google.com, facebook.com, openai.com
But computers communicate using IP addresses such as: 142.250.190.14, 157.240.22.35

DNS converts a domain name into an IP address so your device can find the correct server.

---------------------------------------------------------------------------------------------

    DNS Resolution
What is DNS Resolution?
  DNS Resolution is the process of converting a domain name into an IP address.

How It Works

    User
      |
      v
    google.com
      |
      v
    DNS Resolver
      |
      v
    Root Server
      |
      v
    TLD Server (.com)
      |
      v
    Authoritative DNS Server
      |
      v
    IP Address Returned

  --------------------------------------------------------------------------------------

            Step-by-Step
Step 1: User Requests a Website

  You enter: google.com
  in your browser.

Step 2: DNS Resolver Checks Cache

  Your device first checks whether it already knows the IP address.
  If not, it asks a DNS resolver.

Step 3: Root Server

  The resolver asks a Root DNS Server: "Where can I find information about .com domains?"

Step 4: TLD Server

  The Root Server points to the .com TLD Server.
  The resolver then asks: "Where can I find google.com?"

Step 5: Authoritative DNS Server

  The TLD Server points to Google's Authoritative DNS Server.
  This server contains the official DNS records.

Step 6: IP Address Returned

  The Authoritative Server returns the IP address.
  Example: google.com → 142.250.x.x
  The browser can now connect to the website.


Real-World Example
  When you type: youtube.com
  DNS helps your computer find the correct IP address before the website loads.

  
-------------------------------------------------------------------------------

          DNS Zones
What is a DNS Zone?
  A DNS Zone is a portion of the DNS namespace managed by a specific DNS server.
  Think of it as a database that stores DNS records for a domain.

Example
Domain: example.com

Zone contains records such as: www.example.com, mail.example.com, api.example.com
  
Common DNS Records
  A Record
  Maps a domain name to an IPv4 address.

example.com → 192.168.1.10

AAAA Record
  Maps a domain name to an IPv6 address.

MX Record
  Specifies mail servers.
    mail.example.com

CNAME Record
  Creates an alias for another domain.
    www.example.com → example.com
    
NS Record
  Specifies the authoritative DNS servers for a domain.


Why Are Zones Important?
  Zones allow organizations to: Manage domains efficiently, Delegate administration, Store DNS records, Control domain resolution

-------------------------------------------------------------------

                  DNS-Based Attacks
1. DNS Spoofing
  What is it?
    An attacker provides a fake DNS response and redirects users to a malicious website.
  
  Attack Goal
    Redirect users to fake websites.
  
  Real-World Example
    	A user types: bank.com
        But DNS returns the attacker's fake banking website.

2. DNS Cache Poisoning
  What is it?
    An attacker inserts false DNS information into a DNS resolver's cache.
  
  Attack Goal
    Cause many users to receive incorrect IP addresses.
  
  Real-World Example
    Everyone using a compromised DNS server gets redirected to a malicious website.

3. DNS Amplification Attack
  What is it?
    A DDoS attack that abuses DNS servers to generate huge amounts of traffic.
  
  Attack Goal
    Overwhelm a target with traffic.
  
  Real-World Example
    A small request generates a much larger response, flooding the victim.

4. DNS Tunneling
  What is it?
    Attackers hide data inside DNS requests and responses.
  
  Attack Goal
    Steal data or bypass security controls.
  
  Real-World Example
    Malware secretly sends stolen information through DNS traffic.

5. Subdomain Takeover
  What is it?
    An attacker gains control of an unused subdomain.
  
  Attack Goal
    Host malicious content under a trusted domain.
  
  Real-World Example
    old.example.com
      points to a cloud service that no longer exists, allowing an attacker to claim it.

-----------------------------------------------------------------------------

    How to Protect DNS
Use DNSSEC
  Helps verify that DNS responses are authentic.

Monitor DNS Traffic
  Look for unusual requests or suspicious domains.

Use Trusted DNS Servers
  Examples include: Google Public DNS, Cloudflare DNS
    
Keep DNS Servers Updated
  Apply security patches regularly.

##############################################################################################################

                                                   HTTP, HTTPS, and TLS Handshake Internals
What is HTTP?
  HTTP (HyperText Transfer Protocol) is the protocol used to transfer data between a web browser and a web server.
When you visit a website, your browser uses HTTP to request web pages, images, videos, and other content.

Example
  Browser  ---- HTTP Request ---->  Server
  Browser  <--- HTTP Response ----  Server

Problem with HTTP
  HTTP sends data in plain text. 

Anyone who intercepts the traffic can read: Usernames, Passwords,Messages, Credit card information

Example : User → Password123

An attacker monitoring the network can see the password.

-----------------------------------------------------------------------------------------------

What is HTTPS?
  HTTPS (HyperText Transfer Protocol Secure) is HTTP protected by TLS (Transport Layer Security).
HTTPS encrypts communication between the browser and server.

Example
  Browser  <-- Encrypted Data -->  Server

Even if someone intercepts the traffic, they cannot easily read it.

What is TLS?
  TLS (Transport Layer Security) is the protocol that provides: Encryption, Authentication, Data Integrity
    
TLS is what makes HTTPS secure.

How HTTPS Works

When you visit: https://example.com

Two things happen:
  Step 1
  A TLS Handshake creates a secure connection.
  
  Step 2
  HTTP traffic is sent through that encrypted connection.
  
-----------------------------------------------------------------------------------------------

    TLS Handshake
What is a TLS Handshake?
    A TLS Handshake is the process used by a browser and server to: Verify identities, Exchange cryptographic information, Create encryption keys
        
Before any secure data is exchanged.

Simplified TLS Handshake

    Browser                           Server
    
    Client Hello -------------------->
    
                         <------------ Server Hello
    
                         <------------ Certificate
    
    Key Exchange -------------------->
    
    Secure Connection Created
    
    Encrypted Data <===============> Encrypted Data

Step 1: Client Hello

    The browser says: 
        "I want a secure connection."

    It sends: Supported TLS versions, Supported encryption algorithms, Random value

Step 2: Server Hello

    The server replies with: Selected TLS version, Selected encryption algorithm, Another random value


Step 3: Certificate

    The server sends its digital certificate.
        The certificate proves:
            "I am the real owner of this website."

Step 4: Certificate Verification

The browser verifies:
    Is the certificate valid?
    Is it expired?
    Is it signed by a trusted Certificate Authority (CA)?

If verification fails:
    Warning:
        Your connection is not private

Step 5: Key Exchange

    The browser and server create a shared secret key. This key will be used for encryption.

Step 6: Secure Communication

    Now both sides have the same encryption key.

    All HTTP traffic becomes encrypted.

        HTTP + TLS = HTTPS

-------------------------------------------------------------------------------------------

What Happens After the Handshake?   
Normal HTTP requests continue:
    GET /index.html
    POST /login
    GET /profile

The difference is:
    Everything is encrypted.

TLS Certificate
What is a Certificate?
    A certificate is a digital identity card for a website.

Example Information: Domain Name, Public Key, Expiration Date, Certificate Authority

Real-World Example  
    When you visit: https://google.com
        Your browser checks Google's certificate before trusting the connection.

--------------------------------------------------------------------------------------------

                Common HTTPS/TLS Attacks
1. SSL Stripping
What is it? 
    An attacker downgrades: 
        HTTPS → HTTP

Attack Goal
    Read traffic that should have been encrypted.

2. Man-in-the-Middle (MITM)
What is it?
    An attacker secretly places themselves between the client and server.
        Client <--> Attacker <--> Server
Attack Goal
    Intercept or modify communication.

3. Fake Certificates
What is it?
    An attacker uses a forged or stolen certificate.

Attack Goal
    Pretend to be a legitimate website.

4. TLS Downgrade Attack
What is it?
    Forcing a connection to use an older, weaker TLS version.

Attack Goal
    Exploit known weaknesses in outdated protocols.

-----------------------------------------------------------------------------------------

            Why HTTPS is Important

Without HTTPS: Passwords can be stolen, Sessions can be hijacked, Data can be modified, Privacy is lost.

With HTTPS: Data is encrypted, Website identity is verified, Data integrity is protected.

##############################################################################################################

            Common Protocols: SSH, SMTP, FTP, and SNMP

What are Network Protocols?
    A network protocol is a set of rules that allows devices to communicate with each other over a network.

Different protocols are designed for different purposes, such as remote access, email delivery, file transfer, or network monitoring.

---------------------------------------------------------------

        SSH (Secure Shell)

What is SSH?
    SSH (Secure Shell) is a protocol used to securely access and manage remote systems over a network.

It encrypts all communication between the client and the server.

Default Port : 22

Common Uses : Remote server administration, Secure command execution, Secure file transfer (SCP/SFTP)

Real-World Example : A Linux administrator connects to a remote server: ssh user@server-ip

Security Benefits : Encrypted communication, Secure authentication, Protection against eavesdropping

Common Attacks : Brute Force Attacks, Credential Theft, SSH Key Theft

----------------------------------------------------------------------

        SMTP (Simple Mail Transfer Protocol)

What is SMTP?
    SMTP (Simple Mail Transfer Protocol) is used to send emails between mail servers and from email clients to mail servers.

Default Ports : 
        25   - SMTP, 587  - SMTP Submission, 465  - SMTPS (Encrypted)
    
Common Uses: Sending emails, Email server communication

Real-World Example: When you click Send in your email application, SMTP delivers the message to the recipient's mail server.

Security Risks:  Email Spoofing, Spam Abuse, Phishing Emails

Common Attacks: SMTP Spoofing, Open Relay Abuse, Phishing Campaigns

------------------------------------------------------------------------

            FTP (File Transfer Protocol)
What is FTP?
    FTP (File Transfer Protocol) is used to transfer files between a client and a server.

Default Ports: 21 - Control Connection, 20 - Data Connection

Common Uses:  Uploading website files, Downloading files from servers, File sharing

Real-World Example: A web developer uploads website files to a hosting server using FTP.

Major Problem: FTP sends data, usernames, and passwords in plain text.

Secure Alternatives: SFTP (SSH File Transfer Protocol), FTPS (FTP over TLS)

Common Attacks: Credential Sniffing, Brute Force Attacks, File Manipulation

--------------------------------------------------------------------------

        SNMP (Simple Network Management Protocol)
What is SNMP?
    SNMP (Simple Network Management Protocol) is used to monitor and manage network devices.

Default Ports: 161 - SNMP Queries, 162 - SNMP Traps

Common Uses: Monitoring routers, Monitoring switches, Monitoring servers, Performance tracking

Real-World Example: A network administrator checks CPU usage, bandwidth, and device health from a central monitoring system.

Information SNMP Can Provide: CPU Usage, Memory Usage, Network Traffic, Device Status, Interface Statistics

Common Attacks: Information Gathering, SNMP Enumeration, Community String Attacks

-------------------------------------------------------------------------

            Security Perspective

        | Protocol | Main Risk              |
        | -------- | ---------------------- |
        | SSH      | Brute Force Attacks    |
        | SMTP     | Spoofing and Phishing  |
        | FTP      | Plain-text Credentials |
        | SNMP     | Information Disclosure |


##############################################################################

                            Wireshark: Capturing and Analyzing Live Traffic
What is Wireshark?
    Wireshark is a network protocol analyzer that allows you to capture and inspect network traffic in real time.

It shows the packets traveling across a network and helps you understand what devices are communicating and what data is being exchanged.

Wireshark helps you: Troubleshoot network problems, Analyze network performance, Learn how protocols work, Investigate security incidents, Detect suspicious network activity.

How Packet Capturing Works

        Your Device
            |
            v
        Network Interface
            |
            v
        Wireshark
            |
            v
        Captured Packets

Wireshark listens to a network interface and records packets that pass through it.

-----------------------------------------------------------------------------

                    Capturing Live Traffic


    Step 1: Open Wireshark

When Wireshark starts, it displays available network interfaces.

Examples: Ethernet, Wi-Fi, VPN Interfac

        Step 2: Select an Interface

Choose the interface carrying traffic.

Example: Wi-Fi

if you are connected wirelessly.

        Step 3: Start Capture

Click the blue shark-fin icon.

Wireshark immediately begins collecting packets.

        Step 4: Generate Traffic

Examples: Open a website, Ping a host, Download a file, Connect through SSH

You will see new packets appearing in real time.

        Step 5: Stop Capture

Click the red stop button.

The captured packets remain available for analysis.

---------------------------------------------------------------------------

                        Understanding the Wireshark Interface
Packet List Pane: Shows all captured packets.
Example:

        No.   Source      Destination   Protocol
        1     10.0.0.5    8.8.8.8       DNS
        2     8.8.8.8     10.0.0.5      DNS
        3     10.0.0.5    142.x.x.x     TCP


Packet Details Pane: Displays protocol information for the selected packet.
Example: Ethernet, IP, TCP, HTTP

Packet Bytes Pane: Shows the raw packet data in hexadecimal and ASCII format.

-----------------------------------------------------------------------------

                    Common Filters

Filters help you focus on specific traffic.

HTTP Traffic: http
HTTPS Traffic: https or tcp.port == 443
DNS Traffic: dns
TCP Traffic: tcp
UDP Traffic: udp
Traffic from a Specific IP: ip.addr == 192.168.1.10
Traffic on Port 22 (SSH): tcp.port == 22

                Analyzing Common Protocols
  
    DNS

Example: Query: google.com, Response: 142.250.x.x
Useful for: DNS troubleshooting, Detecting DNS-based attacks

    TCP

Look for: SYN, SYN-ACK, ACK
to observe the TCP handshake.
Useful for: Connection troubleshooting, Detecting SYN flood attacks

    HTTP

Example: GET /index.html
Useful for: Understanding web requests, Learning HTTP communication

    HTTPS

Traffic is encrypted.
You can still see: Source IP, Destination IP, Ports, TLS Handshake information

                Security Use Cases

    Detecting Port Scans

Look for one host connecting to many ports rapidly.

Example:

        192.168.1.50
        → Port 21
        → Port 22
        → Port 23
        → Port 80
        → Port 443


    Detecting ARP Spoofing

Look for unusual ARP replies claiming to be the gateway.

    Detecting DNS Attacks

Watch for: Suspicious domains, Large numbers of DNS requests, Unexpected DNS responses

    Investigating Malware Traffic

Look for: Unknown IP addresses, Repeated outbound connections, Suspicious DNS requests

------------------------------------------------------------------------------

                                Common Challenges
Large Packet Captures: Busy networks can generate thousands of packets per second. Use filters to reduce noise.

Encrypted Traffic: HTTPS traffic is encrypted. You can see metadata but not the actual content.

Capturing the Wrong Interface: If no packets appear, verify that the correct network interface is selected.

#############################################################################



























