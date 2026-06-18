
#  Linux File System Hierarchy and Permissions

## What is the Linux File System?
    The Linux File System is the way Linux organizes files and directories.

Unlike Windows, Linux does not use drives like: C:\; D:\; E:\

Everything starts from a single root directory: /
This root directory contains all files, folders, devices, and mounted drives.

## Linux File System Hierarchy

        /
        ├── bin
        ├── boot
        ├── dev
        ├── etc
        ├── home
        ├── lib
        ├── media
        ├── mnt
        ├── opt
        ├── proc
        ├── root
        ├── run
        ├── sbin
        ├── srv
        ├── sys
        ├── tmp
        ├── usr
        └── var

------------------------------------------------------------------------------

## Important Directories


/ : The root of the entire file system. Everything starts here.

/home : Stores user files and personal data.
    Example: /home/alice; /home/bob
        Think of it as: C:\Users\ [in Windows.]

/root : Home directory of the root user. Only for the administrator.

/etc : Stores system configuration files.
    Examples: /etc/passwd; /etc/hosts; /etc/ssh/

/bin : Contains essential user commands.
    Examples: ls, cp, mv, cat

/sbin : Contains system administration commands.
    Examples: fdisk, reboot, shutdown

/usr : Contains installed programs and libraries.
    Examples: /usr/bin, /usr/lib

/var : Stores frequently changing data.
    Examples: Logs, Mail, Databases
    Common location: /var/log

/tmp : Stores temporary files. Files may be deleted automatically.

/boot : Contains files needed to start Linux.
    Examples: Kernel, GRUB Bootloader

/dev : Contains device files.
    Examples: /dev/sda, /dev/sdb, /dev/null
        Linux treats hardware as files.

Real-World Example: 
    Suppose a user named John logs in.
        His files may be stored in: /home/john
        System logs may be stored in: /var/log
        SSH configuration may be stored in: /etc/ssh/

------------------------------------------------------------------------------

## Linux Permissions
What are Permissions?
    Permissions determine: Who can read a file, Who can modify a file, Who can execute a file.

## Permission Table

            | Permission  | Value |
            | ----------- | ----- |
            | Read (r)    | 4     |
            | Write (w)   | 2     |
            | Execute (x) | 1     |



Permission Structure : -rwxr-xr--

Breakdown:

            - rwx r-x r--
            |   |   |
            Owner Group Others



-------------------------------------------------------

## Numeric Permissions

777 : 
- rwx rwx rwx
- Everyone can do everything.
- ⚠️ Very insecure.

755 : 
- rwx r-x r-x
- Owner can modify.
- Others can only read and execute.
- Common for scripts and directories.

644 : 
- rw- r-- r--
- Owner can modify.
- Others can only read.
- Common for files.

600 : 
- rw-------
- Only the owner has access.
- Common for private keys.

----------------------------------------------------------------------

## Changing Permissions : chmod

Example: chmod 755 script.sh
Sets permissions to: rwxr-xr-x

        Changing Ownership : chown

Example: chown john file.txt
Change owner to: john

        Change Owner and Group

chown john:developers file.txt

---------------------------------------------------------------------------

## Security Perspective

Dangerous Permissions: chmod 777 file.txt
    Anyone can read, modify, or delete the file.
    Avoid unless absolutely necessary.

                            Secure Permissions

Private SSH key: chmod 600 id_rsa
SSH often refuses to use keys with weaker permissions

#########################################################################################################


# Linux Process Model: fork(), exec(), Signals, and /proc

## What is a Process?: 
    A process is a running instance of a program.

For example:
        Program: firefox
        Process: Running Firefox Browser

When you start an application, Linux creates a process for it.

Each process gets a unique PID (Process ID).
Example:
        Firefox  → PID 1234
        SSH      → PID 5678

--------------------------------------------------------------------------

## Fork
What is Fork?: 
    fork() is a system call used to create a new process.

The new process is called the child process, and the original process is called the parent process.

How It Works: 
        Parent Process
            |
            fork()
            |
            +------> Child Process

After fork(), both processes continue running independently.

Real-World Example: 
    When you open a terminal and run: firefox
    The shell creates a new process using fork().

            Bash Shell
                |
            fork()
                |
            Firefox Process

----------------------------------------------------------------------

## Exec
What is Exec?: 
    exec() replaces the current process with a new program. Unlike fork(), it does not create a new process. It simply changes what the process is running.

How It Works: 
            Process A
                |
            exec()
                |
                v
            Process A now runs Program B

The PID stays the same.

Real-World Example:

A shell often uses: fork() → exec()

## Flow:

            Bash
            |
            fork()
            |
            Child Process
            |
            exec()
            |
            Runs ls command

-------------------------------------------------------------------------------

##  Fork + Exec Together

This is how most Linux commands are launched.

                Shell
                |
                fork()
                |
                Child
                |
                exec()
                |
                Program Starts

Example : ls

The shell: Creates a child process using fork() -> Child runs exec() to load ls -> ls executes -> Process exits

------------------------------------------------------------------------------

##  Signals
What are Signals?: 
    Signals are messages sent to processes.

They tell a process to: Stop, Pause, Continue, Reload, Terminate

Think of signals as a way for the operating system or users to communicate with running processes.

## Common Signals: 

                | Signal  | Number | Purpose              |
                | ------- | ------ | -------------------- |
                | SIGTERM | 15     | Gracefully terminate |
                | SIGKILL | 9      | Force kill           |
                | SIGINT  | 2      | Interrupt (Ctrl+C)   |
                | SIGSTOP | 19     | Pause process        |
                | SIGCONT | 18     | Resume process       |
                | SIGHUP  | 1      | Reload configuration |

Real-World Examples : 

- Ctrl + C : SIGINT
- Stops the running program.

- kill Command: kill 1234
- Sends: SIGTERM

to PID 1234.

- Force Kill: kill -9 1234
- Sends: SIGKILL
The process is terminated immediately.

---------------------------------------------------------------------------

## /proc
What is /proc?: 
    /proc is a virtual filesystem that provides information about running processes and the Linux kernel. It does not store real files on disk.
The kernel creates the information dynamically.

## How It Looks: 
        /proc
        ├── 1
        ├── 100
        ├── 250
        ├── cpuinfo
        ├── meminfo
        └── uptime

Process directories are named after their PID.


Example : /proc/1234 

    Contains information about process 1234.

------------------------------------------------------------------------------

##  Useful Files

Process Status: cat /proc/1234/status
Shows: Process name, State, Memory usage, Parent PID

Command Line: cat /proc/1234/cmdline
Shows how the process was started.

CPU Information: cat /proc/cpuinfo
Displays CPU details.

Memory Information: cat /proc/meminfo
Displays RAM usage.

System Uptime: cat /proc/uptime
Shows how long the system has been running.

-------------------------------------------------------------------------------

##  Security Perspective

Attackers and defenders both use process information.

Attackers May: Identify running services, Discover sensitive processes, Gather system information

Defenders May: Monitor suspicious processes, Detect malware, Investigate incidents, Analyze system activity

-------------------------------------------------------------------------------

##  Useful Commands

View Running Processes: ps aux
Interactive Process Viewer : htop or top
Find Process ID: pidof nginx
Send Signal: kill -15 PID
View /proc: ls /proc

#########################################################################################################

## Linux Capabilities and Privilege Separation

What are Linux Capabilities?: 
    Linux Capabilities are a security feature that breaks root privileges into smaller, specific permissions.

In traditional Linux, a process either runs as: Root User   → Full Access; Normal User → Limited Access;

With capabilities, a program can receive only the permission it needs instead of full root access.

Why are Capabilities Important?: 
    Giving every privileged program full root access is risky.
    If the program is compromised, an attacker may gain complete control of the system.
    Capabilities reduce this risk by granting only the required permissions.


This follows the Principle of Least Privilege: A program should have only the permissions it needs to perform its task.

Real-World Example: 
The ping command needs a special network permission.
Linux gives it: CAP_NET_RAW
instead of full root access.

So ping works, but it does not get complete control over the system.

------------------------------------------------------------------------------

## Privilege Separation means: 
    Do not give the whole application high privileges if only a small part needs them.

Why is it Needed?: 
    Imagine a bank. Not every employee has the key to the vault. Security Guard → Vault Key Customer Service → No Vault Key Only the person who needs the key gets it. Privilege Separation works the same way.

Real-World Example: 
SSH Server:

        SSH
        |
        +-- Login Checking
        |
        +-- Data Transfer

The login-checking part gets higher privileges.
The data-transfer part runs with limited privileges.
So if an attacker breaks the data-transfer part, they still cannot easily control the whole system.

#########################################################################################################

# Namespaces and cgroups (Container Primitives)

## What are Namespaces and cgroups?: 
    Namespaces and cgroups are Linux features that make containers possible.
They are the core building blocks used by container technologies like Docker.

Why are They Needed?: Imagine multiple applications running on the same server.

Without protection: Applications can interfere with each other. One application may consume all CPU or memory. A problem in one application may affect others.

Linux solves this using Namespaces and cgroups.

------------------------------------------------------------------------------

## Namespaces

Namespaces provide isolation.

They make an application think it has its own: Processes, Network, Filesystem, Hostname

Even though it is sharing the same operating system.

Simple Analogy

Think of namespaces as walls between apartments.

Apartment A
Apartment B
Apartment C

People inside one apartment cannot see what is happening inside the others.

------------------------------------------------------------------------------

##  cgroups

cgroups provide resource control.

They limit how much: CPU, Memory, Disk I/O

an application can use.

Simple Analogy

Think of cgroups as a spending limit on a bank card.

Maximum CPU = 2 Cores
Maximum RAM = 2 GB

The application cannot exceed its limit.

------------------------------------------------------------------------------

## How Containers Use Them

Namespaces → Isolation

cgroups → Resource Limits

Together they make an application behave like it has its own small, separate system.

------------------------------------------------------------------------------

## Real-World Example: 

A server runs: Website, Database, Monitoring Tool

Namespaces keep them separated.

cgroups prevent one application from using all system resources.

------------------------------------------------------------------------------

## Security Perspective

Without Namespaces:

        Application A
            ↓
        Can see Application B

Without cgroups:

        Application A
            ↓
        Uses all CPU and RAM

With both:

        Applications stay isolated
            +
        Resources stay controlled

#########################################################################################################

# Kernel Syscalls and the Attack Surface They Create

## What is a System Call (Syscall)?: 
    A system call (syscall) is a request made by a program to the Linux kernel.

Applications cannot directly access hardware, memory, disks, or network devices. Instead, they ask the kernel to do these tasks for them through syscalls.

Simple Analogy

## Think of the kernel as a bank manager.

        Customer (Program)
                |
            Request
                |
            Manager
            (Kernel)

A customer cannot open the vault directly. They must ask the manager.

Similarly, programs use syscalls to ask the kernel for services.


Why are Syscalls Needed?: 

Programs need to: Read files, Write files, Create processes, Allocate memory, Send network traffic

All of these operations require kernel assistance.

Without syscalls, applications would not be able to interact with the operating system.

------------------------------------------------------------------------------

## Common Syscalls

File Operations: open(); read(); write(); close();
Used when reading or writing files.

Process Operations: fork(); execve(); exit();
Used to create and manage processes.

Memory Operations: mmap(); brk();
Used to allocate memory.

Network Operations: socket(); connect(); bind(); listen();
Used for network communication.

------------------------------------------------------------------------------

## Real-World Example: 

When you open a file: cat notes.txt

The program does not access the disk directly.

Instead, it performs syscalls such as: open(); read(); close();

The kernel handles the actual file access and returns the data.

-------------------------------------------------------------------------------

## What is an Attack Surface?: 
    An attack surface is every point where an attacker can interact with or try to exploit a system.

The more features a system exposes, the larger its attack surface becomes.

How Do Syscalls Create an Attack Surface?

Every syscall is an entry point into the kernel.

        Application
            |
        Syscall
            |
            Kernel

If a syscall contains a bug, an attacker may be able to exploit it.

Because the kernel has very high privileges, kernel vulnerabilities can be extremely dangerous.

------------------------------------------------------------------------------

## Example Attack Scenario
        Application
            |
        Malicious Input
            |
        Vulnerable Syscall
            |
            Kernel

If the syscall does not properly handle the input, an attacker might: Crash the system, Escape a container, Gain higher privileges, Execute malicious code

Why the Kernel Is a High-Value Target

The kernel controls: Memory, Processes, Filesystems, Networking, Hardware

Compromising the kernel can mean compromising the entire system.

-------------------------------------------------------------------------------

## Security Measures
Reduce Available Syscalls
Container technologies often restrict which syscalls applications can use.

Example:

            Application
                |
            Allowed Syscalls Only
                |
                Kernel

This reduces the attack surface.

Keep the Kernel Updated: 
Many kernel vulnerabilities are fixed through security updates.

Use Least Privilege: 
Applications should only have access to the syscalls and resources they actually need.

Security Perspective

Every syscall is a door into the kernel.

        More Doors
            =
        Larger Attack Surface

The goal of system security is not to remove syscalls, but to:

Minimize unnecessary access
Patch vulnerabilities
Restrict dangerous operations

#########################################################################################################

# Shell Scripting for Automation and Reconnaissance

## What is Shell Scripting?: 
    A shell script is a file that contains a series of Linux commands that are executed automatically.

Instead of typing the same commands again and again, you can place them in a script and run them with a single command.

Why is Shell Scripting Needed?: 

## Imagine you need to run:

        whoami
        hostname
        ip a
        netstat -tuln

every day.
Typing them manually is slow and repetitive.
A shell script can perform all these tasks automatically.

------------------------------------------------------------------------------

## Automation: 
Automation means making a computer perform tasks automatically without manual effort.

Example

Instead of:
        Run Command 1
        Run Command 2
        Run Command 3
        Run Command 4

Use:
        Run Script
            ↓
        Everything Happens Automatically


Simple Shell Script

            #!/bin/bash

            echo "Current User:"
            whoami

            echo "Hostname:"
            hostname

Save as: info.sh

Run: bash info.sh

-------------------------------------------------------------------------------

##  Reconnaissance (Recon)
What is Reconnaissance?: 
    Reconnaissance is the process of gathering information about a target system or network.

In cybersecurity, recon is usually the first phase of an assessment.

The goal is to learn as much as possible before further testing.

Information Commonly Collected: IP addresses, Open ports, Running services, Hostnames, Operating systems, Domain information

Why Use Shell Scripts for Recon?: Recon often requires multiple commands.Instead of running them one by one, a script can collect everything automatically.

## Example Recon Script: 

            #!/bin/bash

            echo "User:"
            whoami

            echo "Hostname:"
            hostname

            echo "IP Address:"
            ip a

            echo "Open Ports:"
            ss -tuln

Running one script gathers multiple pieces of information.

-------------------------------------------------------------------------------

## Real-World Example: 

A system administrator wants a quick overview of a server.

## Instead of executing several commands manually:

        whoami
        hostname
        ip a
        ss -tuln
        df -h

they run:

        bash recon.sh

and receive all the information at once.

------------------------------------------------------------------------------

## Security Perspective

Shell scripts are powerful because they can automate many tasks.

Defensive Uses: 
        System monitoring
        Log collection
        Health checks
        Security audits

Offensive Uses: 
        Information gathering
        Automated scanning
        Repetitive testing

Because scripts can execute many commands quickly, administrators should carefully review scripts before running them.

#########################################################################################################

# Log Analysis: /var/log, journald, and auditd

## What is Log Analysis?: 
    Log Analysis is the process of examining system logs to understand what happened on a system.

## Logs help administrators and security analysts:
- Troubleshoot problems
- Monitor system activity
- Detect attacks
- Investigate incidents

Think of logs as a system's diary.

            System Activity
                ↓
                Logs
                ↓
            Investigation

------------------------------------------------------------------------------

## Why Are Logs Important?: 
    Imagine a server suddenly crashes or gets hacked.

The first question is: "What happened?"

The answer is usually found in the logs.
Without logs, investigating problems becomes much harde

------------------------------------------------------------------------------

## /var/log
What is /var/log?: 
    /var/log is the main directory where Linux stores log files.

Most system and application logs can be found here.

Common Log Files:
- /var/log/syslog
- /var/log/auth.log
- /var/log/kern.log
- /var/log/dpkg.log

Real-World Example:

Authentication activity: /var/log/auth.log

## May show:
        User login
        SSH login
        Failed password attempts
        sudo usage

This is often the first place to check when investigating suspicious logins.

------------------------------------------------------------------------------

## journald
What is journald?:
    journald is the logging service used by systems running systemd.

Instead of storing everything in plain-text log files, journald collects and manages logs in a central database called the journal.

Why is journald Useful?

Instead of searching many log files:
            auth.log
            syslog
            kern.log

you can query logs from one place.


Command: journalctl

View all journal logs.

Recent Boot Logs: journalctl -b


------------------------------------------------------------------------------

## auditd
What is auditd?: 
    auditd (Linux Audit Daemon) is a security-focused logging system.

While normal logs show general system events, auditd records security-relevant actions.

## What Can auditd Track?: 
            File access
            File modifications
            Command execution
            User activity
            Permission changes

------------------------------------------------------------------------------

## Why is auditd Important?

Normal logs may tell you: A file was changed.

auditd can tell you:
        Who changed it?
        When was it changed?
        Which process changed it?


Example

Monitor: /etc/passwd

If someone modifies it, auditd can record:
            User
            Time
            Process
            Action

This is very useful during investigations.

------------------------------------------------------------------------------

## Real-World Scenario : 

Imagine someone gains access to a server.

/var/log Shows: SSH Login

journald Shows:
        Service Activity
        System Events
        Errors

auditd Shows:
        Files Modified
        Commands Executed
        User Actions

Together they provide a complete picture of what happened.

#########################################################################################################
















