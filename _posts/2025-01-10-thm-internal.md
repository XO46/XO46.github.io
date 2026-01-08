---
title: "THM: Internal"
date: 2025-01-10
categories: [TryHackMe]
tags: [Enumeration, Linux, PrivEsc]
---
| Finding | CVSS Score | Risk Level |
|---------|-----------|------------|
| Webmin CVE-2019-15107 | 9.8 | Critical |
| GitStack RCE | 8.1 | High |
| File Upload Bypass | 7.5 | High |
| Unquoted Service Path | 7.8 | High |

## Recon

I started with basic enumeration to understand the attack surface.
The initial scan revealed SSH and HTTP services.

---

## Web Enumeration

Further enumeration of the web service revealed hidden functionality
that could be abused for initial access.

---

## Initial Access

Using the discovered weakness, I gained a low-privilege shell
on the system.

---

## Privilege Escalation

Local enumeration revealed misconfigurations that allowed
privilege escalation to root.

---

## Takeaways

- Enumeration is the most important phase
- Small misconfigurations lead to full compromise
