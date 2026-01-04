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

## Enumeration
```bash
nmap -sC -sV -p- 10.10.10.10
```
I began with basic enumeration to identify exposed services and potential
attack surfaces. An HTTP service stood out as the most likely entry point.

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
