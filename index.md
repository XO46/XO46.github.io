---
layout: home
title: XO46 | Pentest Writeups
---

# XO46
### (R. Chandra Shekar)

```text
██╗  ██╗███████╗██╗     ██╗      ██████╗     ███████╗██████╗ ███╗   ██╗██████╗ 
██║  ██║██╔════╝██║     ██║     ██╔═══██╗    ██╔════╝██╔══██╗████╗  ██║██╔══██╗
███████║█████╗  ██║     ██║     ██║   ██║    █████╗  ██████╔╝██╔██╗ ██║██║  ██║
██╔══██║██╔══╝  ██║     ██║     ██║   ██║    ██╔══╝  ██╔══██╗██║╚██╗██║██║  ██║
██║  ██║███████╗███████╗███████╗╚██████╔╝    ██║     ██║  ██║██║ ╚████║██████╔╝
╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝ ╚═════╝     ╚═╝     ╚═╝  ╚═╝╚═╝  ╚═══╝╚═════╝ 

                         hello, frnd.   :)
---

Penetration testing writeups documenting my journey into offensive security.

I started like most of us did —
watching systems fail on screen,
wondering how it worked,
and thinking maybe I could help fix the world one day.

Turns out the closest path was learning **how to break things properly**.

---

## 👤 About Me

I’m a regular kid with an uncommon curiosity —
how systems think, where they trust too much,
and what happens when that trust is misplaced.

I couldn’t become a hero that saves the world.
So I chose something more realistic:

**Learn how attackers think.  
Think like a defender.  
Work toward becoming a penetration tester / red teamer.**

This site documents that process — the wins, the confusion, and the lessons.

_No drama. No shortcuts. Just learning._

---

## 🧠 Platforms & Scope

I practice and document my skills using **legal, controlled environments only**:

- **TryHackMe (THM)** — learning paths and structured labs  
- **Hack The Box (HTB – retired machines)** — realistic adversarial scenarios  

All content here:
- stays within ethical boundaries  
- avoids active targets  
- focuses on understanding, not exploitation for exploitation’s sake  

Clear scope. No ambiguity.

---

## 🧪 Writeups

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>

_Writeups are added as labs are completed.  
No manual curation. No noise._

---

## 🎓 Certifications

- **eJPT** — completed  
- **PNPT** — in progress  
- **TryHackMe Pentester Path** — completed (certified)

Certifications support learning.  
Writeups show the work.

---

## 📫 Contact
- Email: 2100032482@kluniversity.in
- LinkedIn: https://www.linkedin.com/in/r-chandra-shekar-a620aa252
- TryHackMe : https://tryhackme.com/api/v2/badges/public-profile?userPublicId=4907711
---

## ⚠️ Disclaimer

All content on this site is for **educational purposes only**.

Every technique demonstrated here is practiced against
**intentionally vulnerable labs or retired machines**.

If you’re here as a defender —
yes, these issues still exist.
And yes, they’re worth fixing.
