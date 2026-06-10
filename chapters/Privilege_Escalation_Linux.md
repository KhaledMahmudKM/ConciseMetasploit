# Linux Privilege Escalation with Metasploit

After gaining initial access to a Linux machine, the next step is often privilege escalation. Metasploit can help automate and streamline this process.

## Goal
Gain root-level access on a compromised Linux machine using Metasploit's post-exploitation modules.

## Example Workflow

### 1. Gain Initial Access
Use an exploit to open a Meterpreter session.

### 2. Background the Session
```bash
background
```

### 3. Use the Exploit Suggester
```bash
use post/multi/recon/local_exploit_suggester
set SESSION 1
run
```

### 4. Choose and Launch Suggested Exploit
```bash
use exploit/linux/local/some_priv_esc_exploit
set SESSION 1
set other_options as_required
exploit
```

### 5. Verify Elevated Privileges
```bash
whoami
id
```

## Notes
- Privilege escalation depends on kernel version and system configs.
- The system may require manual tuning or uploading privilege escalation scripts.