---
layout: home
title: XO46 | Pentest Writeups
---

# 👋 XO46 – Penetration Testing Writeups

This site contains my personal writeups from:

- Hack The Box (retired machines)
- TryHackMe labs

My focus is on:

- Enumeration methodology
- Web & Network exploitation
- Active Directory attacks
- Clear documentation with screenshots

> Goal: document **thinking**, not just commands.

---

## 📝 Writeups

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>
