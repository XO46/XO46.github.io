---
title: "THM: Internal"
date: 2025-01-10
categories: [TryHackMe]
tags: [Enumeration, Linux, PrivEsc]
---

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
