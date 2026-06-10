# Chapter 2: Installation & Setup

## 2.1 Overview

Before using Metasploit for penetration testing, you must properly install and configure the framework in a stable environment.

Metasploit can be installed on multiple operating systems, but it is most commonly used on Linux-based distributions designed for security testing.

This chapter focuses on setting up Metasploit and verifying that it is ready for use.

---

## 2.2 Recommended Environment

For learning and testing purposes, the following environments are recommended:

### Operating Systems

- Kali Linux (preferred)
- Parrot Security OS
- Ubuntu (manual setup required)

### Virtualization Platforms

- VirtualBox
- VMware Workstation / Player

> Using a virtual machine is strongly recommended to isolate your testing environment from your main system.

---

## 2.3 Installing Metasploit on Kali Linux

Kali Linux usually comes with Metasploit pre-installed.

### Step 1: Update System

```bash
sudo apt update && sudo apt upgrade -y
````

### Step 2: Install Metasploit (if not installed)

```bash
sudo apt install metasploit-framework -y
```

### Step 3: Verify Installation

```bash
msfconsole
```

If installed correctly, you will see the Metasploit banner and console prompt:

```bash
msf6 >
```

---

## 2.4 Installing Metasploit on Ubuntu

Ubuntu does not include Metasploit by default.

### Step 1: Install Dependencies

```bash
sudo apt update
sudo apt install curl postgresql -y
```

### Step 2: Install Metasploit Framework

One common method is using the Rapid7 installer:

```bash
curl https://raw.githubusercontent.com/rapid7/metasploit-framework/master/msfinstall | sudo bash
```

---

## 2.5 Database Configuration

Metasploit uses a PostgreSQL database to store:

* Scan results
* Exploit data
* Host information
* Session details

### Step 1: Start PostgreSQL

```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

### Step 2: Initialize Metasploit Database

```bash
msfdb init
```

### Step 3: Check Database Status

Inside msfconsole:

```bash
db_status
```

Expected output:

```bash
connected to msf
```

---

## 2.6 Launching Metasploit

Start the framework using:

```bash
msfconsole
```

This opens the primary Metasploit interface where all operations are performed.

---

## 2.7 Understanding First Launch Output

When Metasploit starts, you will see:

* Version information
* Loaded modules
* Database connection status (if configured)

Example prompt:

```bash
msf6 >
```

This indicates the framework is ready for commands.

---

## 2.8 Basic Configuration Checks

After launching Metasploit, verify:

### Check database connection

```bash
db_status
```

### Check available modules

```bash
show exploits
```

### Check payloads

```bash
show payloads
```

If results appear, your installation is functioning correctly.

---

## 2.9 Updating Metasploit

To keep Metasploit updated:

### On Kali Linux

```bash
sudo apt update && sudo apt upgrade metasploit-framework
```

### Using msfupdate (if available)

```bash
msfupdate
```

---

## 2.10 Common Installation Issues

### 1. msfconsole not found

* Ensure Metasploit is installed
* Check PATH variables

### 2. Database not connected

Run:

```bash
msfdb init
```

### 3. PostgreSQL not running

```bash
sudo systemctl start postgresql
```

---

## 2.11 Security Note

Metasploit should always be installed and used in a:

* Controlled lab environment
* Virtual machine
* Isolated network

Never run penetration testing tools on production systems without explicit authorization.

---

## 2.12 What’s Next?

In the next chapter, we will explore:

* Metasploit core architecture
* Module types in detail
* How exploits and payloads interact
* Internal workflow of the framework

---

## Summary

Installing Metasploit correctly is essential for a smooth penetration testing experience. Once set up, you gain access to a powerful framework capable of simulating real-world attack scenarios in a controlled and ethical environment.


