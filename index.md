---
layout: home
title: XO46 | Pentest Writeups
---

<style>
body {
  background: #0a0a0a !important;
  color: #00ff00 !important;
  font-family: 'Courier New', monospace;
}

.hero {
  max-width: 900px;
  margin: 100px auto;
  padding: 30px;
  border: 2px solid #00ff00;
  background: #0d0d0d;
  box-shadow: 0 0 25px rgba(0,255,0,0.3);
}

.live-terminal {
  margin-top: 20px;
  font-size: 1.1rem;
}

.cursor {
  animation: blink 1s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}
</style>

<div class="hero">

# R. Chandra Shekar

**Penetration testing writeups documenting my journey into offensive security.**

<div class="live-terminal">
  <span>$</span>
  <span id="cmd"></span><span class="cursor">█</span>
  <div id="out" style="margin-top:5px;"></div>
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
