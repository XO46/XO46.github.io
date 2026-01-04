---
title: "HTB: DemoMachine"
date: 2026-01-06
tags: [hackthebox, linux, web]
summary: >
  DemoMachine starts with a vulnerable web application that allows command
  execution as a low-privileged user. Careful local enumeration then reveals
  a misconfigured sudo rule, which provides a straightforward path to full
  root compromise.
thumbnail: /assets/img/thumbnails/wreath.png
---

## Initial Scanning

I started with a full TCP scan to identify open ports on the target.

<div class="terminal">
<pre><code class="cmd"><span class="prompt">elliot@kali</span>:~$ nmap -p- --min-rate 10000 10.10.11.69</code></pre>
</div>

<div class="terminal">
<pre><code class="out">PORT     STATE SERVICE
53/tcp   open  domain
88/tcp   open  kerberos-sec
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds</code></pre>
</div>

The presence of Kerberos, LDAP, and SMB-related services suggests this host is
likely an Active Directory domain controller.

## Initial Access

The web application was vulnerable to command injection, allowing execution
of arbitrary commands as a low-privileged user.

## Privilege Escalation

Local enumeration revealed a sudo configuration that permitted execution
of a privileged binary without a password, which could be abused to gain
root access.

## Conclusion

This machine reinforces the importance of thorough local enumeration after
initial access, as simple misconfigurations can often lead directly to full
compromise.
