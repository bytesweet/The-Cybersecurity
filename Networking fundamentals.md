What is the OSI Model?
The OSI (Open Systems Interconnection) Model is a framework that describes how data moves across a network.

Instead of treating communication as one large process, the OSI Model divides it into 7 layers, each with a specific responsibility.

Think of it like sending a package:

You write the message.
You put it in a box.
A shipping company transports it.
The recipient receives and opens it.

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

Purpose:
Provides network services directly to applications used by users.

Examples:
HTTP, HTTPS, FTP, DNS, SMTP

Common Attacks:

SQL Injection (SQLi)
Cross-Site Scripting (XSS)
Phishing
Command Injection

Attack Goal:
Steal data, bypass authentication, or execute malicious code.

Real-World Scenario:
An attacker exploits a vulnerable website login form to gain access to sensitive user information.

--------------------------------------------

Layer 6 – Presentation

Purpose:
Handles data formatting, encryption, decryption, and compression.

Examples:
SSL/TLS, JPEG, PNG, MP4

Common Attacks:

SSL Stripping
Certificate Spoofing
Weak Encryption Exploitation

Attack Goal:
Bypass encryption and read protected data.

Real-World Scenario:
An attacker intercepts a secure connection and forces it to use an insecure protocol.

------------------------------------------

Layer 5 – Session

Purpose:
Establishes, manages, and terminates communication sessions.

Common Attacks:

Session Hijacking
Session Replay
Session Fixation

Attack Goal:
Take control of an authenticated user's session.

Real-World Scenario:
An attacker steals a session cookie and gains access to a user's account without knowing the password.
-------------------------------------

Layer 4 – Transport

Purpose:
Provides reliable end-to-end communication.

Protocols:
TCP, UDP

Common Attacks:

SYN Flood
UDP Flood
TCP Reset Attack

Attack Goal:
Disrupt services or exhaust server resources.

Real-World Scenario:
A server becomes unavailable after receiving a massive number of fake connection requests.

-----------------------------------

Layer 3 – Network

Purpose:
Handles logical addressing and packet routing.

Protocols:
IP, ICMP, IPSec

Common Attacks:

IP Spoofing
ICMP Flood
Smurf Attack
Routing Attacks

Attack Goal:
Hide the attacker's identity or manipulate network traffic.

Real-World Scenario:
An attacker uses a fake IP address to disguise the source of malicious traffic.

------------------------------------

Layer 2 – Data Link

Purpose:
Provides communication between devices on the same local network.

Protocols:
Ethernet, ARP, MAC

Common Attacks:

ARP Spoofing
MAC Flooding
VLAN Hopping

Attack Goal:
Intercept, redirect, or monitor local network traffic.

Real-World Scenario:
An attacker tricks devices into sending traffic through their machine, allowing them to monitor communications.

---------------------------------------

Layer 1 – Physical

Purpose:
Handles the physical transmission of data through hardware and media.

Examples:
Network Cables, Fiber Optics, Wireless Signals, Network Devices

Common Attacks:

  Cable Tapping
  Signal Jamming
  Hardware Theft
  Device Tampering

Attack Goal:
  Gain physical access to data or disrupt communications.

Real-World Scenario:
  An attacker connects a device to a network cable to capture transmitted traffic


###############################################################################################################################

TCP/IP Stack: IP Addressing, Subnetting, and CIDR

Definition

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
Purpose

An IP Address uniquely identifies a device on a network, similar to how a home address identifies a house.

Without IP addresses, devices would not know where to send or receive data.

----------------------------------------------------------------

IPv4 Address Structure

IPv4 consists of 32 bits divided into 4 octets.

Example 192.168.1.10
Each octet ranges from: 0 - 255

----------------------------------------------------------------

Public vs Private IP

Public IP
  Routable on the Internet
  Assigned by an ISP
  Globally unique

Example: 8.8.8.8

Private IP
  Used inside local networks.
Ranges: 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, 192.168.0.0 - 192.168.255.255

Real-World Scenario
  Your router may have: Public IP: 103.x.x.x
  While your laptop has: Private IP: 192.168.1.10
    
    The router translates between them using NAT.

------------------------------------------------------------------------------

Subnetting
Definition
  Subnetting is the process of dividing a large network into smaller networks called subnets.

Why Use Subnetting?
  Better network organization
  Reduced broadcast traffic
  Improved performance
  Increased security
  Efficient IP allocation
  
Example
  Suppose a company owns: 192.168.1.0/24
  Instead of one large network, it can create: 192.168.1.0/26, 192.168.1.64/26, 192.168.1.128/26, 192.168.1.192/26

    Now different departments can use different subnets.

Real-World Scenario

  A company separates:
    HR Department
    Finance Department
    IT Department

into different subnets to reduce unnecessary traffic and improve security.

-----------------------------------------------------------------------------

CIDR (Classless Inter-Domain Routing)
Definition

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

Example
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




