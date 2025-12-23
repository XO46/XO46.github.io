---
layout: home
title: XO46 | Pentest Writeups
---

# XO46
### R. Chandra Shekar

Penetration testing writeups documenting my journey into offensive security.

---

## 🧪 Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>
