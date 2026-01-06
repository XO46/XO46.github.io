---
layout: home
title: XO46 | Pentest Writeups
---

<style>
/* ===== REMOVE DEFAULT HOME STYLES ===== */
.home h1.page-heading,
.home .post-title {
  display: none !important;
}

.home .page-content,
.home .wrapper {
  padding-top: 0 !important;
  margin-top: 0 !important;
}

.home .wrapper {
  max-width: 1400px;
}

/* ===== HERO SECTION ===== */
.hero {
  max-width: 1150px;
  margin: 40px auto;
  padding: 10px 0;
}

.hero h2 {
  font-size: 2.4rem;
  margin-bottom: 10px;
  color: var(--text-primary);
}

.hero span {
  font-size: 1.15rem;
  color: var(--text-secondary);
}

.hero p {
  font-size: 1.1rem;
  line-height: 1.75;
  max-width: 900px;
  margin-top: 12px;
  color: var(--text-primary);
}

.live-terminal {
  font-size: 1rem;
  margin-top: 22px;
  font-family: "SFMono-Regular", Consolas, monospace;
}

.live-terminal span {
  color: var(--accent-blue);
}

.cursor {
  color: var(--accent-green);
  animation: blink 1s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

/* ===== POSTS HEADING ===== */
.home h2.posts-heading {
  font-size: 1.8rem;
  color: var(--text-primary);
  margin-top: 60px;
  margin-bottom: 30px;
  font-weight: 600;
  max-width: 1150px;
  margin-left: auto;
  margin-right: auto;
  padding-bottom: 10px;
  border-bottom: 1px solid var(--border-primary);
}

/* ===== POST LIST STYLING ===== */
.home .post-list {
  list-style: none;
  padding: 0;
  max-width: 1150px;
  margin: 0 auto;
}

.home .post-list li {
  margin-bottom: 25px;
  padding: 20px;
  background: var(--bg-secondary);
  border: 1px solid var(--border-primary);
  border-radius: 6px;
  transition: all 0.2s ease;
}

.home .post-list li:hover {
  background: var(--bg-tertiary);
  border-color: var(--accent-blue);
  transform: translateX(3px);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
}

.home .post-list .post-link {
  font-size: 1.3rem !important;
  font-weight: 600;
  display: block;
  margin-bottom: 8px;
  text-decoration: none;
  color: var(--accent-blue) !important;
}

.home .post-list .post-link:hover {
  color: var(--accent-blue-hover) !important;
  text-decoration: none;
}

.home .post-list .post-meta {
  color: var(--text-secondary);
  font-size: 0.85rem;
  border: none;
  padding: 0;
  margin: 0;
}

.home .post-list .post-excerpt {
  margin-top: 10px;
  color: var(--text-secondary);
  font-size: 0.95rem;
  line-height: 1.6;
}

/* ===== MATRIX BACKGROUND ===== */
#matrix-bg {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  opacity: 0.03;
  pointer-events: none;
}
</style>

<canvas id="matrix-bg"></canvas>

<div class="hero">
  <h2>XO46</h2>
  <span>Junior Penetration Tester | Web · Active Directory · Linux</span>

  <p>
    Penetration testing writeups documenting my journey into offensive security.
  </p>

  <div class="live-terminal">
    <span>$</span>
    <span id="cmd"></span><span class="cursor">█</span>
    <div id="out" style="margin-top:6px; color: var(--accent-green);"></div>
  </div>
</div>

<h2 class="posts-heading">Latest Writeups</h2>

<script>
// Terminal typing animation
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

// Matrix background
const canvas = document.getElementById("matrix-bg");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const chars = "01$~";
const fontSize = 14;
const columns = canvas.width / fontSize;
const drops = Array(Math.floor(columns)).fill(1);

function draw() {
  ctx.fillStyle = "rgba(13, 17, 23, 0.08)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "rgba(88, 166, 255, 0.05)";
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
