---
layout: home
title: XO46 | Pentest Writeups
---

<style>
/* ===== GLOBAL DARK THEME ===== */
body {
  background: #0a0a0a !important;
  color: #c9ffd6 !important; /* softer readable green */
  font-family: 'Courier New', monospace;
}

/* ===== HERO TERMINAL BOX ===== */
.hero {
  max-width: 900px;
  margin: 80px auto;
  padding: 30px;
  border: 2px solid #00ff00;
  background: #0d0d0d;
  box-shadow: 0 0 25px rgba(0,255,0,0.3);
}

.live-terminal {
  margin-top: 20px;
  font-size: 1.1rem;
}

/* terminal command color */
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

/* ===== 0xdf-STYLE TOP NAVIGATION ===== */
.site-header {
  background: #0a0a0a !important;
  border-bottom: 1px solid #222;
}

.site-title {
  color: #e6e6e6 !important;
  font-weight: 500;
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

/* active page */
.site-nav a.current {
  border-bottom: 2px solid #00ccff;
}
</style>

<div class="hero">

## R. Chandra Shekar

**Junior Penetration Tester | Web · Active Directory · Linux**

Penetration testing writeups documenting my journey into offensive security.

<div class="live-terminal">
  <span>$</span>
  <span id="cmd"></span><span class="cursor">█</span>
  <div id="out" style="margin-top:5px; color:#7CFF7C;"></div>
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
