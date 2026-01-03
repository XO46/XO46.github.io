---
layout: home
title: XO46 | Pentest Writeups
---

<style>
/* ===== GLOBAL DARK THEME ===== */
body {
  background: #0a0a0a !important;
  color: #c9ffd6 !important;
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
}

/* ===== REMOVE MINIMA HOME TITLE (XO46 BLOCK) ===== */
.home h1,
.home .post-title,
.home .page-heading {
  display: none !important;
}

/* ===== REMOVE EXTRA TOP SPACE ===== */
.home .page-content {
  padding-top: 0 !important;
  margin-top: 0 !important;
}

.home .wrapper {
  padding-top: 0 !important;
}

/* ===== EXPAND HOME CONTENT WIDTH ===== */
.home .wrapper {
  max-width: 1400px;
}

.home .page-content {
  padding-left: 0;
  padding-right: 0;
}

/* ===== HERO TERMINAL BOX ===== */
.hero {
  max-width: 1150px;
  margin: 40px auto; /* compact */
  padding: 30px;
  border: 2px solid #00ff00;
  background: #0d0d0d;
  box-shadow: 0 0 25px rgba(0,255,0,0.3);
}

/* ===== HERO TYPOGRAPHY ===== */
.hero h2 {
  font-size: 2.1rem;
  margin-bottom: 6px;
}

.hero span {
  font-size: 1.05rem;
}

.hero p {
  font-size: 1rem;
  line-height: 1.6;
  max-width: 900px;
}

/* ===== TERMINAL ===== */
.live-terminal {
  margin-top: 18px;
  font-size: 0.95rem;
}

.live-terminal span {
  color: #00ccff;
}

.cursor {
  color: #00ff00;
  animation: blink 1s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

/* ===== HIDE SITE TITLE ON HOMEPAGE ONLY ===== */
.home .site-title {
  display: none !important;
}

.home .site-header {
  padding-bottom: 0;
}

/* ===== NAVIGATION STYLE ===== */
.site-header {
  background: #0a0a0a !important;
  border-bottom: 1px solid #222;
}

.site-nav a {
  color: #e6e6e6 !important;
  font-weight: 500;
  text-decoration: none;
}

.site-nav a:hover {
  color: #00ccff !important;
  text-decoration: underline;
}

/* ===== POSTS SECTION ===== */
.home h2 {
  font-size: 1.8rem;
  color: #00ff00;
  margin-top: 40px;
  margin-bottom: 20px;
  text-shadow: 0 0 8px rgba(0,255,0,0.4);
}

.home h2::after {
  content: "";
  display: block;
  width: 80px;
  height: 2px;
  background: #00ff00;
  margin-top: 10px;
}

/* ===== ALIGN POSTS WITH HERO ===== */
.home .post-list,
.home .post-list-heading,
.home .post-list li {
  max-width: 1150px;
  margin-left: auto;
  margin-right: auto;
}

/* ===== REMOVE BOTTOM GAP ===== */
.home footer,
.home .site-footer {
  margin-top: 40px !important;
}
</style>

<div class="hero">

## R. Chandra Shekar

<span style="color:#00ff00; font-weight:600;">
Junior Penetration Tester | Web · Active Directory · Linux
</span>

<p style="margin-top:10px;">
Penetration testing writeups documenting my journey into offensive security.
</p>

<div class="live-terminal">
  <span>$</span>
  <span id="cmd"></span><span class="cursor">█</span>
  <div id="out" style="margin-top:6px; color:#7CFF7C;"></div>
</div>

</div>

<script>
let command = "whoami";
let output = "R. Chandra Shekar";
let i = 0;

function typeCmd() {
  if (i < command.length) {
    document.getElementById("cmd").innerHTML += command[i];
    i++;
    setTimeout(typeCmd, 120);
  } else {
    setTimeout(() => {
      document.getElementById("out").innerHTML = output;
    }, 500);
  }
}

typeCmd();
</script>
