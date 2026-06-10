# Chapter 4: Reconnaissance with Metasploit

## 4.1 Overview

Reconnaissance is the first technical phase of any penetration test. In this stage, the goal is to gather as much information as possible about a target system or network.

Metasploit provides built-in **auxiliary modules** that help perform scanning, enumeration, and service identification.

---

## 4.2 Why Reconnaissance Matters

Without proper reconnaissance, exploitation becomes guesswork.

Reconnaissance helps you:

- Identify live hosts
- Discover open ports
- Detect running services
- Understand service versions
- Map potential attack surfaces

This phase directly determines the success of later exploitation steps.

---

## 4.3 Reconnaissance in Metasploit

Metasploit uses **auxiliary modules** for reconnaissance tasks.

These modules do not exploit systems. Instead, they safely collect information.

Common categories include:

- Port scanners  
- Service scanners  
- SMB enumeration tools  
- FTP/SSH/HTTP probes  

---

## 4.4 Setting Up for Reconnaissance

Before scanning, ensure Metasploit database is active:

```bash
msfconsole
````

Then check database status:

```bash
db_status
```

Expected output:

```bash
connected to msf
```

---

## 4.5 Host Discovery

To identify active hosts in a network, Metasploit can be combined with scanning modules or external tools.

Example using ARP sweep:

```bash
use auxiliary/scanner/discovery/arp_sweep
set RHOSTS 192.168.1.0/24
run
```

This reveals live devices on the local network.

---

## 4.6 Port Scanning

Port scanning identifies open communication ports on a target system.

Example TCP port scan:

```bash
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.1.10
set PORTS 1-1000
run
```

This helps identify potential entry points like:

* SSH (22)
* HTTP (80)
* FTP (21)
* SMB (445)

---

## 4.7 Service Enumeration

Once ports are identified, the next step is to identify running services.

Example FTP version detection:

```bash
use auxiliary/scanner/ftp/ftp_version
set RHOSTS 192.168.1.10
run
```

Example HTTP service check:

```bash
use auxiliary/scanner/http/http_version
set RHOSTS 192.168.1.10
run
```

---

## 4.8 SMB Enumeration

SMB (Server Message Block) is a common target in internal networks.

Example SMB version scan:

```bash
use auxiliary/scanner/smb/smb_version
set RHOSTS 192.168.1.10
run
```

SMB enumeration can reveal:

* Operating system type
* Network configuration
* Potential vulnerabilities

---

## 4.9 SSH Enumeration

SSH services can also be probed:

```bash
use auxiliary/scanner/ssh/ssh_version
set RHOSTS 192.168.1.10
run
```

This helps identify:

* SSH version
* Potential weak or outdated implementations

---

## 4.10 Web Service Reconnaissance

Web servers are a major attack surface.

Basic HTTP banner grabbing:

```bash
use auxiliary/scanner/http/http_header
set RHOSTS 192.168.1.10
run
```

You may discover:

* Server type (Apache, Nginx, IIS)
* Security headers
* Version information

---

## 4.11 Saving Recon Data

When database integration is enabled, scan results are automatically stored.

You can view discovered hosts:

```bash
hosts
```

View services:

```bash
services
```

This helps organize large penetration testing environments.

---

## 4.12 Using Nmap with Metasploit

Metasploit integrates well with external tools like Nmap.

Example:

```bash
db_nmap -sV 192.168.1.0/24
```

This command:

* Scans network
* Detects service versions
* Stores results in Metasploit database

---

## 4.13 Organizing Recon Results

Good reconnaissance requires structured data:

* Host IPs
* Open ports
* Service versions
* Potential vulnerabilities

Metasploit’s database helps centralize this information for later exploitation.

---

## 4.14 Common Recon Mistakes

Avoid these mistakes:

* Scanning without defining scope
* Ignoring service versions
* Skipping database usage
* Jumping directly to exploitation

Reconnaissance should always be systematic.

---

## 4.15 Security Perspective

From a defender’s point of view, reconnaissance activity often appears as:

* Port scans
* Service probing
* Banner grabbing attempts

Monitoring tools like IDS/IPS can detect these patterns early.

---

## 4.16 What’s Next?

In the next chapter, we will move into:

* Vulnerability mapping
* Matching services to exploits
* Understanding CVEs in Metasploit
* Preparing for exploitation

---

## Summary

Reconnaissance is the foundation of penetration testing. Metasploit provides powerful auxiliary modules to identify hosts, services, and potential vulnerabilities before any exploitation begins.


