---
layout: page
title: About Me
permalink: /about/
---

<style>
/* Retro Moody Color Palette */
:root {
  --retro-bg: #0d0d0d;
  --retro-surface: #1a1a1a;
  --retro-text: #c5c5c5;
  --retro-text-dim: #858585;
  --retro-border: #2d2d2d;
  --htb-green: #9fef00;
  --thm-red: #c0392b;
  --accent-muted: #5a6c7d;
}

/* Override page.html styles for about page */
.page-content {
  background: var(--retro-bg) !important;
  max-width: 1150px !important;
  margin: 40px auto !important;
  padding: 40px 20px !important;
}

.page-content h1 {
  font-size: 3rem !important;
  margin-bottom: 25px !important;
  color: var(--retro-text) !important;
  text-align: center !important;
  text-transform: uppercase !important;
  letter-spacing: 8px !important;
  font-weight: 700 !important;
  font-family: 'Courier New', monospace !important;
  text-shadow: 0 0 20px rgba(197, 197, 197, 0.3) !important;
  border-bottom: none !important;
  padding-bottom: 0 !important;
}

.page-content h2 {
  font-size: 2rem !important;
  margin-top: 50px !important;
  margin-bottom: 20px !important;
  color: var(--retro-text) !important;
  font-weight: 700 !important;
  font-family: 'Courier New', monospace !important;
  letter-spacing: 3px !important;
  border-bottom: 1px solid var(--retro-border) !important;
  padding-bottom: 12px !important;
}

.page-content h2::before {
  content: '>';
  margin-right: 12px;
  color: var(--htb-green);
}

.page-content p,
.page-content li {
  font-size: 1.05rem !important;
  line-height: 1.8 !important;
  color: var(--retro-text-dim) !important;
  font-family: 'Courier New', monospace !important;
}

.page-content ul {
  list-style: none;
  padding-left: 0;
}

.page-content li {
  padding-left: 25px;
  position: relative;
  margin: 12px 0;
}

.page-content li::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: var(--htb-green);
  font-weight: bold;
}

.page-content strong {
  color: var(--retro-text);
  font-weight: 700;
}

/* Hero Quote Box */
.hero-intro {
  padding: 25px 30px;
  background: var(--retro-surface);
  border-left: 4px solid var(--htb-green);
  border-radius: 0;
  margin: 30px auto 50px auto;
  box-shadow: 0 0 15px rgba(159, 239, 0, 0.1);
  max-width: 900px;
}

.hero-intro p {
  font-size: 1.2rem !important;
  line-height: 1.8 !important;
  color: var(--retro-text) !important;
  margin: 0 !important;
}

/* Section Cards */
.section-card {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  padding: 30px;
  margin: 30px 0;
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
}

.section-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
  background: var(--retro-border);
  transition: all 0.6s ease;
}

.section-card:hover {
  border-color: var(--htb-green);
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(159, 239, 0, 0.2);
}

.section-card:hover::before {
  width: 4px;
  background: var(--htb-green);
  box-shadow: 0 0 10px var(--htb-green);
}

/* Numbered List Styling */
.page-content ol {
  list-style: none;
  counter-reset: item;
  padding-left: 0;
}

.page-content ol li {
  counter-increment: item;
  padding-left: 40px;
  position: relative;
  margin: 16px 0;
}

.page-content ol li::before {
  content: counter(item);
  position: absolute;
  left: 0;
  top: 0;
  background: var(--retro-surface);
  color: var(--htb-green);
  border: 1px solid var(--htb-green);
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 0.85rem;
  font-family: 'Courier New', monospace;
}

/* Footer Quote */
.footer-quote {
  margin-top: 60px;
  padding: 25px 30px;
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  border-radius: 0;
  position: relative;
  overflow: hidden;
}

.footer-quote::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, var(--htb-green), transparent);
}

.footer-quote p {
  color: var(--retro-text-dim) !important;
  font-size: 0.95rem !important;
  margin: 0 !important;
  font-style: italic !important;
  font-family: 'Courier New', monospace !important;
}

/* Fade In Animation */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.section-card {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

.section-card:nth-child(1) { animation-delay: 0.1s; }
.section-card:nth-child(2) { animation-delay: 0.2s; }
.section-card:nth-child(3) { animation-delay: 0.3s; }
.section-card:nth-child(4) { animation-delay: 0.4s; }

/* Mobile Responsive */
@media (max-width: 768px) {
  .page-content h1 {
    font-size: 2rem !important;
    letter-spacing: 4px !important;
  }
  
  .page-content h2 {
    font-size: 1.6rem !important;
  }
  
  .hero-intro p {
    font-size: 1.05rem !important;
  }
  
  .section-card {
    padding: 20px;
  }
}
</style>

<div class="hero-intro">
  <p>
    <strong>I'm a regular kid with an uncommon curiosity</strong> — how systems think, where they trust too much, and what happens when that trust is misplaced.
  </p>
</div>

<div class="section-card">

## THE JOURNEY

I couldn't become a hero that saves the world. So I chose something more realistic:

- **Learn how attackers think**
- **Think like a defender**
- **Work toward becoming a penetration tester / red teamer**

This site documents that process — the wins, the confusion, and the lessons.

</div>

<div class="section-card">

## WHAT YOU'LL FIND HERE

Every writeup follows a structured methodology:

1. **Reconnaissance** - Information gathering and enumeration
2. **Vulnerability Analysis** - Identifying attack vectors
3. **Exploitation** - Gaining initial access
4. **Privilege Escalation** - Achieving full system compromise
5. **Post-Exploitation** - Maintaining access and covering tracks

</div>

<div class="section-card">

## MY APPROACH

I believe in:

- **Thorough documentation** - Every step matters
- **Understanding, not just exploitation** - Know why it works
- **Ethical practice** - Legal environments only
- **Continuous learning** - Every machine teaches something new

</div>

<div class="section-card">

## CURRENT FOCUS

- Completing PNPT certification
- Expanding Linux privilege escalation techniques
- Studying Active Directory attacks
- Building custom exploitation tools

</div>

<div class="footer-quote">
  <p>
    "In the world of penetration testing, you're always learning. The moment you think you know everything is the moment you become vulnerable."
  </p>
</div>
