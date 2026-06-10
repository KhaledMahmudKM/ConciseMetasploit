# Using `db_nmap` in Metasploit

`db_nmap` is a command within Metasploit that runs the Nmap network scanner **while also storing the scan results** directly into the Metasploit database. This integration allows you to seamlessly use discovered data (hosts, ports, services) in later exploitation phases.

---

## 🔹 What is `db_nmap`?

`db_nmap` is a wrapper around Nmap that:
- Executes a scan.
- Parses the results.
- Inserts them into the Metasploit workspace database.

This differs from using Nmap separately, where you'd need to manually import results.

---

## 🔹 Syntax

```bash
db_nmap [options] <target>
```

All standard Nmap flags can be used.

---

## 🔹 Examples

### Scan a single host:
```bash
db_nmap 192.168.1.100
```

### Scan multiple ports:
```bash
db_nmap -p 21,22,80 192.168.1.0/24
```

### Version detection:
```bash
db_nmap -sV 192.168.1.105
```

### OS detection:
```bash
db_nmap -O 192.168.1.105
```

### Aggressive scan:
```bash
db_nmap -A 192.168.1.105
```

---

## 🔹 Viewing Results

Once scanned, you can view and use the results with Metasploit's database commands:

```bash
hosts         # Lists discovered hosts
services      # Lists discovered services
vulns         # Shows imported vulnerability data (if available)
```

Example:
```bash
services -p 445
```
Shows hosts with port 445 open.

---

## 🔹 Benefits of `db_nmap`

- No need to import `.xml` or `.gnmap` files.
- Results are immediately available for use with:
  - Auxiliary scanners
  - Exploit targeting
  - Post-exploitation automation

---

## 🔹 Best Practices

- Use `db_nmap` early in the engagement to build a network map.
- Follow up with exploits targeting services discovered via `services`.
- Combine with `workspace` and `notes` to organize findings.

---

## 🔹 Related Commands

| Command        | Purpose                          |
|----------------|----------------------------------|
| `db_status`    | Check DB connection status       |
| `workspace`    | Manage scan/project environments |
| `hosts`        | List discovered hosts            |
| `services`     | List open ports/services         |
| `vulns`        | List known vulnerabilities       |

---

`db_nmap` bridges scanning and exploitation. Mastering it can save you time and streamline your workflow within Metasploit.

---