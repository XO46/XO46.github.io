---
layout: home
title: Mr. White | The Professor's Lab Notes
---

<canvas id="matrix-bg" style="position: fixed; top: 0; left: 0; z-index: -1; opacity: 0.03; pointer-events: none;"></canvas>

<div class="hero">
  <h2>HELLO FRNDS</h2>

  <p style="font-style: italic; color: var(--text-secondary); margin-top: 20px; font-size: 1.1rem; font-weight: 500;">
    "Say my name."<br>
    <span style="color: var(--text-primary); margin-left: 20px;">"Heisenberg."</span><br>
    <span style="color: var(--accent-blue);">"You're goddamn right."</span>
  </p>

  <p style="margin-top: 25px;">
    Breaking into systems with the precision of chemistry. Every exploit is a formula waiting to be perfected.
  </p>

  <div class="live-terminal">
    <span>$</span>
    <span id="cmd"></span><span class="cursor">█</span>
    <div id="out" style="margin-top:6px;"></div>
  </div>
</div>

<h2 style="max-width: 1150px; margin: 60px auto 30px; padding-bottom: 10px; border-bottom: 1px solid var(--border-primary);">Lab Reports</h2>

<script>
let command = "python3 synthesis.py --purity 99.1";
let output = "[+] Vulnerability chain identified\n[+] Exploit formula synthesized\n[+] Root access obtained. Respect the chemistry.";
let i = 0;

function typeCmd() {
  if (i < command.length) {
    document.getElementById("cmd").innerHTML += command[i];
    i++;
    setTimeout(typeCmd, 80);
  } else {
    setTimeout(() => {
      document.getElementById("out").innerHTML = output;
      document.getElementById("out").style.color = "var(--accent-green)";
    }, 700);
  }
}

typeCmd();

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
```

---

## **What Changed:**

✅ **Quote dialogue format:**
```
"Say my name."
    "Heisenberg."
"You're goddamn right."
