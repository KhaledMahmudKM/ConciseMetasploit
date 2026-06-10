# Chapter 3: Core Concepts of Metasploit Framework

## 3.1 Overview

To use Metasploit effectively, you must understand its internal building blocks. The framework is not a single tool, but a collection of modular components that work together to simulate real-world attacks.

This chapter explains the **core concepts** that define how Metasploit operates.

---

## 3.2 The Module-Based Architecture

Metasploit is built entirely around **modules**.

A module is a self-contained piece of functionality that performs a specific task.

All Metasploit capabilities come from modules, including:

- Exploiting vulnerabilities
- Scanning networks
- Generating payloads
- Post-exploitation actions

---

## 3.3 Types of Modules

Metasploit includes five primary module types:

---

### 3.3.1 Exploit Modules

Exploit modules are used to take advantage of vulnerabilities in target systems.

They typically:

- Trigger a known vulnerability
- Deliver a payload to the target
- Establish initial access

Example use cases:
- Remote code execution
- Buffer overflow exploitation
- Web application attacks

---

### 3.3.2 Payloads

A payload is the code executed on the target system after a successful exploit.

Common payload types include:

- Command shell
- Meterpreter session
- Reverse shell
- Bind shell

Payloads define **what happens after exploitation**.

---

### 3.3.3 Auxiliary Modules

Auxiliary modules are used for **non-exploitation tasks**, such as:

- Port scanning
- Service enumeration
- Vulnerability scanning
- Fuzzing targets

They do not create sessions but are essential for reconnaissance.

---

### 3.3.4 Post-Exploitation Modules

These modules are used **after gaining access** to a system.

They help with:

- Privilege escalation
- Credential dumping
- System enumeration
- Persistence mechanisms

---

### 3.3.5 Encoders

Encoders modify payloads to:

- Avoid detection
- Bypass simple security filters
- Obfuscate shellcode

> Encoders are not strong antivirus bypass tools, but they help reduce basic signature detection.

---

## 3.4 Exploit + Payload Relationship

An exploit and a payload work together:

- The **exploit** triggers the vulnerability  
- The **payload** runs on the target system  

Example flow:

1. Select exploit for a vulnerable service  
2. Choose compatible payload  
3. Configure target settings  
4. Execute attack  
5. Gain session access  

---

## 3.5 Sessions in Metasploit

A session represents an active connection to a compromised system.

Types of sessions:

- Shell session (basic command line)
- Meterpreter session (advanced interactive control)

Once a session is established, attackers can:

- Execute commands
- Upload/download files
- Gather system information

---

## 3.6 MSFconsole: The Main Interface

The primary interface for Metasploit is:

```bash
msfconsole
````

It allows you to:

* Search modules
* Configure exploits
* Set payloads
* Manage sessions

Example prompt:

```bash
msf6 >
```

---

## 3.7 Searching for Modules

You can search for modules using keywords:

```bash
search vsftpd
```

Or by type:

```bash
search type:exploit
```

This helps identify relevant exploits or tools quickly.

---

## 3.8 Viewing Module Information

To inspect a module:

```bash
info <module_name>
```

This displays:

* Description
* Required options
* References (CVE IDs)
* Usage details

---

## 3.9 Setting Options

Modules require configuration before execution.

Common parameters:

* `RHOSTS` → Target IP
* `RPORT` → Target port
* `LHOST` → Attacker IP
* `LPORT` → Listener port

Example:

```bash
set RHOSTS 192.168.1.10
set RPORT 21
```

---

## 3.10 Understanding Workspaces

Metasploit supports **workspaces** to organize projects.

You can separate:

* Different penetration tests
* Lab environments
* Client engagements

Commands:

```bash
workspace
workspace -a test_lab
workspace test_lab
```

---

## 3.11 Database Integration

Metasploit integrates with a database to store:

* Hosts
* Services
* Scan results
* Credentials
* Sessions

This helps manage large-scale penetration tests efficiently.

---

## 3.12 Security Perspective

Understanding core concepts helps defenders as well:

* Exploits show how vulnerabilities are abused
* Payloads show attacker goals
* Modules reveal attack patterns

This knowledge improves detection and mitigation strategies.

---

## 3.13 What’s Next?

In the next chapter, we will move into practical usage:

* Reconnaissance with Metasploit
* Scanning and enumeration techniques
* Identifying live hosts and services

This is where theory turns into hands-on penetration testing.

---

## Summary

Metasploit is built on a modular architecture where exploits, payloads, and auxiliary tools work together to simulate real attacks. Understanding these core components is essential before performing real penetration testing workflows.

