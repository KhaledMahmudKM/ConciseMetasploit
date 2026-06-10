# Appendix A: Metasploit Command Reference

## A.1 Overview

This appendix provides a structured reference of commonly used Metasploit commands. It is intended as a quick lookup guide during penetration testing sessions.

Commands are grouped by functionality for easier navigation.

---

## A.2 Core Framework Commands

### Start Metasploit

```bash
msfconsole
````

Launches the Metasploit Framework interface.

---

### Exit Metasploit

```bash
exit
```

Closes the Metasploit console.

---

### Show Help

```bash
help
```

Displays general command help.

---

## A.3 Module Management Commands

### Search for modules

```bash
search <keyword>
```

Example:

```bash
search ftp
```

---

### Use a module

```bash
use <module_path>
```

Example:

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
```

---

### Show module options

```bash
show options
```

Displays required and optional parameters.

---

### Show payloads

```bash
show payloads
```

Lists compatible payloads for a selected exploit.

---

### Show exploits

```bash
show exploits
```

Displays available exploit modules.

---

### Show auxiliary modules

```bash
show auxiliary
```

Lists scanning and enumeration tools.

---

## A.4 Configuration Commands

### Set a parameter

```bash
set <option> <value>
```

Example:

```bash
set RHOSTS 192.168.1.10
```

---

### Set global option

```bash
setg <option> <value>
```

Applies setting across modules.

---

### Unset a parameter

```bash
unset <option>
```

---

### Unset all parameters

```bash
unset all
```

---

## A.5 Target and Payload Configuration

### Set target host(s)

```bash
set RHOSTS <ip_or_range>
```

---

### Set target port

```bash
set RPORT <port>
```

---

### Set local host (attacker)

```bash
set LHOST <ip>
```

---

### Set local port

```bash
set LPORT <port>
```

---

### Set payload

```bash
set payload <payload_name>
```

Example:

```bash
set payload cmd/unix/interact
```

---

## A.6 Execution Commands

### Run module

```bash
run
```

---

### Execute exploit

```bash
exploit
```

Both commands perform the same action in most cases.

---

### Run in background

```bash
exploit -j
```

Runs exploit as a job.

---

## A.7 Session Management Commands

### List sessions

```bash
sessions
```

---

### Interact with session

```bash
sessions -i <id>
```

Example:

```bash
sessions -i 1
```

---

### Kill session

```bash
sessions -k <id>
```

---

### Background session

Inside session:

```bash
background
```

---

## A.8 Database Commands

### Check database status

```bash
db_status
```

---

### View hosts

```bash
hosts
```

---

### View services

```bash
services
```

---

### View credentials

```bash
creds
```

---

### Run Nmap and store results

```bash
db_nmap -sV <target>
```

---

## A.9 Reconnaissance Commands

### ARP scan

```bash
use auxiliary/scanner/discovery/arp_sweep
```

---

### TCP port scan

```bash
use auxiliary/scanner/portscan/tcp
```

---

### FTP version scan

```bash
use auxiliary/scanner/ftp/ftp_version
```

---

### SMB version scan

```bash
use auxiliary/scanner/smb/smb_version
```

---

## A.10 Meterpreter Commands

### System information

```bash
sysinfo
```

---

### Current user

```bash
getuid
```

---

### Process list

```bash
ps
```

---

### File system navigation

```bash
ls
cd
pwd
```

---

### Download file

```bash
download <file>
```

---

### Upload file

```bash
upload <file>
```

---

### Screenshot

```bash
screenshot
```

---

### Webcam snapshot

```bash
webcam_snap
```

---

### Keylogging

```bash
keyscan_start
keyscan_dump
keyscan_stop
```

---

### Hash dumping (Windows)

```bash
hashdump
```

---

## A.11 Post-Exploitation Commands

### System info

```bash
sysinfo
```

---

### Privilege check

```bash
getuid
```

---

### Network configuration

```bash
ipconfig
route
```

---

### Migrate process

```bash
migrate <pid>
```

---

## A.12 Workspace Commands

### List workspaces

```bash
workspace
```

---

### Create workspace

```bash
workspace -a <name>
```

---

### Switch workspace

```bash
workspace <name>
```

---

## A.13 Resource Automation

### Run script

```bash
resource <file.rc>
```

---

## A.14 Summary

This appendix covers the most frequently used Metasploit commands across:

* Exploitation
* Reconnaissance
* Post-exploitation
* Session management
* Database interaction

It serves as a quick reference during practical penetration testing engagements.

