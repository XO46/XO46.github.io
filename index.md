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

/* ===== REMOVE MINIMA HOME TITLE ===== */
.home h1,
.home .post-title,
.home .page-heading {
  display: none !important;
}

/* ===== REMOVE EXTRA TOP SPACE ===== */
.home .page-content,
.home .wrapper {
  padding-top: 0 !important;
  margin-top: 0 !important;
}

/* ===== EXPAND WIDTH ===== */
.home .wrapper {
  max-width: 1400px;
}

.home .page-content {
  padding-left: 0;
  padding-right: 0;
}

/* ===== HERO (NO BOX) ===== */
.hero {
  max-width: 1150px;
  margin: 40px auto;
  padding: 10px 0;      /* no box padding */
}

/* ===== TYPOGRAPHY ===== */
.hero h2 {
  font-size: 2.1rem;
  margin-bottom: 6px;
}

.hero span {
  font-size: 1.05rem;
  color: #00ff00;
  font-weight: 600;
}

.hero p {
  font-size: 1rem;
  line-height: 1.6;
  max-width: 900px;
  margin-top: 10px;
}

/* ===== TERMINAL LINE ===== */
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

/* ===== NAVIGATION ===== */
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

/* ===== POSTS HEADING ===== */
.home h2 {
  font-size: 1.8rem;
  color: #00ff00;
  margin-top: 40px;
  margin-bottom: 20px;
}

.home h2::after {
  content: "";
  display: block;
  width: 80px;
  height: 2px;
  background: #00ff00;
  margin-top: 8px;
}

/* ===== ALIGN POSTS ===== */
.home .post-list,
.home .post-list li {
  max-width: 1150px;
  margin-left: auto;
  margin-right: auto;
}
</style>

<!-- Subtle ambient background -->
<canvas id="matrix-bg"></canvas>

<style>
#matrix-bg {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  opacity: 0.05;       /* VERY subtle */
  pointer-events: none;
}
</style>

<div class="hero">
  
<span>
Junior Penetration Tester | Web · Active Directory · Linux
</span>

<p>
Penetration testing writeups documenting my journey into offensive security.
</p>

<div class="live-terminal">
  <span>$</span>
  <span id="cmd"></span><span class="cursor">█</span>
  <div id="out" style="margin-top:6px; color:#7CFF7C;"></div>
</div>

</div>

<script>
/* terminal typing */
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

/* subtle matrix background */
const canvas = document.getElementById("matrix-bg");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const chars = "01$~";
const fontSize = 14;
const columns = canvas.width / fontSize;
const drops = Array(Math.floor(columns)).fill(1);

function draw() {
  ctx.fillStyle = "rgba(10,10,10,0.08)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "rgba(0,255,0,0.05)";
  ctx.font = fontSize + "px monospace";

  for (let i = 0; i < drops.length; i++) {
    const text = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);

    if (drops[i] * fontSize > canvas.height && Math.random() > 0.98) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(draw, 120);

window.addEventListener("resize", () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});
</script>
