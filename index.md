---
layout: home
title: Mr. White | The Professor's Lab Notes
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

/* Hero Section - More Visible */
.hero {
  max-width: 1150px;
  margin: 0 auto;
  padding: 50px 20px 30px 20px;
}

.hero h2 {
  text-align: center;
  color: var(--retro-text);
  font-size: 3rem;
  margin-bottom: 25px;
  text-transform: uppercase;
  letter-spacing: 8px;
  font-weight: 700;
  font-family: 'Courier New', monospace;
  text-shadow: 0 0 20px rgba(197, 197, 197, 0.3);
}

.hero-quote {
  margin: 25px auto;
  padding: 20px 25px;
  background: var(--retro-surface);
  border-left: 3px solid var(--htb-green);
  max-width: 700px;
  font-size: 1rem;
  line-height: 1.7;
  color: var(--retro-text-dim);
  font-family: 'Courier New', monospace;
  box-shadow: 0 0 15px rgba(159, 239, 0, 0.1);
}

/* CUTE & SMALL COMPACT COUNTERS */
.stats-compact {
  display: flex;
  gap: 12px;
  max-width: 1150px;
  margin: 25px auto;
  justify-content: center;
  align-items: stretch;
}

.counter-box {
  flex: 1;
  max-width: 140px;
  background: var(--retro-surface);
  border: 1px solid;
  padding: 12px 10px;
  text-align: center;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  cursor: pointer;
}

.counter-box:hover {
  transform: translateY(-8px) scale(1.1);
}

.htb-counter {
  border-color: var(--htb-green);
}

.htb-counter:hover {
  box-shadow: 0 10px 30px rgba(159, 239, 0, 0.4);
  border-color: var(--htb-green);
  background: rgba(159, 239, 0, 0.05);
}

.thm-counter {
  border-color: var(--thm-red);
}

.thm-counter:hover {
  box-shadow: 0 10px 30px rgba(192, 57, 43, 0.4);
  border-color: var(--thm-red);
  background: rgba(192, 57, 43, 0.05);
}

.total-counter {
  border-color: var(--accent-muted);
}

.total-counter:hover {
  box-shadow: 0 10px 30px rgba(90, 108, 125, 0.4);
  border-color: var(--accent-muted);
  background: rgba(90, 108, 125, 0.05);
}

.counter-icon {
  font-size: 1.5rem;
  margin-bottom: 6px;
  opacity: 0.8;
  transition: all 0.5s ease;
}

.counter-box:hover .counter-icon {
  transform: scale(1.3) rotate(360deg);
  opacity: 1;
}

.counter-number {
  font-size: 1.8rem;
  font-weight: 700;
  margin: 6px 0;
  font-family: 'Courier New', monospace;
  transition: all 0.5s ease;
}

.counter-box:hover .counter-number {
  transform: scale(1.2);
}

.htb-counter .counter-number {
  color: var(--htb-green);
}

.thm-counter .counter-number {
  color: var(--thm-red);
}

.total-counter .counter-number {
  color: var(--retro-text);
}

.counter-label {
  font-size: 0.65rem;
  color: var(--retro-text-dim);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: 600;
  font-family: 'Courier New', monospace;
}

.counter-detail {
  margin-top: 6px;
  padding-top: 6px;
  border-top: 1px solid var(--retro-border);
  font-size: 0.6rem;
  color: var(--retro-text-dim);
  display: flex;
  justify-content: space-around;
  font-family: 'Courier New', monospace;
}

/* POSTS SECTION - Eye Comfortable Font Sizes */
.writeups-header {
  max-width: 1150px;
  margin: 50px auto 30px auto;
  padding: 0 20px;
}

.writeups-title {
  font-size: 2rem;
  font-weight: 700;
  color: var(--retro-text);
  margin-bottom: 10px;
  font-family: 'Courier New', monospace;
  letter-spacing: 3px;
}

.writeups-title::before {
  content: '>';
  margin-right: 12px;
  color: var(--htb-green);
}

.writeups-subtitle {
  color: var(--retro-text-dim);
  font-size: 1rem;
  margin-bottom: 25px;
  padding-bottom: 15px;
  border-bottom: 1px solid var(--retro-border);
  font-family: 'Courier New', monospace;
}

/* Enhanced Post Cards - DRAMATIC HOVER */
.post-list {
  list-style: none;
  padding: 0;
  max-width: 1150px;
  margin: 0 auto;
}

.post-list li {
  margin-bottom: 28px;
  padding: 28px;
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
}

.post-list li::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
  background: var(--retro-border);
  transition: all 0.6s ease;
}

/* DRAMATIC HOVER EFFECTS */
.post-list li:hover::before {
  width: 6px;
  background: var(--htb-green);
  box-shadow: 0 0 20px var(--htb-green);
}

.post-list li:hover {
  border-color: var(--htb-green);
  transform: translateX(15px) translateY(-8px);
  box-shadow: -10px 15px 40px rgba(159, 239, 0, 0.3);
  background: rgba(159, 239, 0, 0.03);
}

.post-link {
  font-size: 1.6rem !important;
  font-weight: 700;
  display: inline-block;
  margin-bottom: 14px;
  text-decoration: none;
  color: var(--retro-text) !important;
  position: relative;
  z-index: 1;
  transition: all 0.5s ease;
  line-height: 1.4;
  font-family: 'Courier New', monospace;
}

.post-link:visited {
  color: var(--retro-text) !important;
  opacity: 0.85;
}

.post-link:hover {
  color: var(--htb-green) !important;
  text-shadow: 0 0 15px rgba(159, 239, 0, 0.5);
  transform: translateX(10px);
  opacity: 1;
}

.post-link:active {
  color: var(--retro-text) !important;
}

/* Platform Indicator */
.post-link::before {
  content: '[';
  margin-right: 6px;
  color: var(--retro-text-dim);
  font-weight: 400;
  transition: all 0.5s ease;
}

.post-link::after {
  content: ']';
  margin-left: 6px;
  color: var(--retro-text-dim);
  font-weight: 400;
  transition: all 0.5s ease;
}

.post-link:hover::before,
.post-link:hover::after {
  color: var(--htb-green);
}

.post-list .post-meta {
  border: none;
  padding: 0;
  margin: 12px 0;
  font-size: 0.95rem;
  color: var(--retro-text-dim);
  display: flex;
  gap: 15px;
  align-items: center;
  flex-wrap: wrap;
  font-family: 'Courier New', monospace;
}

.post-meta span {
  display: flex;
  align-items: center;
  gap: 6px;
}

.post-excerpt {
  margin-top: 14px;
  color: var(--retro-text-dim);
  font-size: 1.05rem;
  line-height: 1.8;
  position: relative;
  z-index: 1;
  font-family: 'Courier New', monospace;
}

/* Difficulty Badge - Minimal Retro with Dramatic Hover */
.difficulty-badge {
  display: inline-flex;
  align-items: center;
  padding: 4px 12px;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
  border: 1px solid;
  font-family: 'Courier New', monospace;
  transition: all 0.5s ease;
}

.post-list li:hover .difficulty-badge {
  transform: scale(1.15);
}

.difficulty-easy {
  background: transparent;
  color: var(--htb-green);
  border-color: var(--htb-green);
}

.post-list li:hover .difficulty-easy {
  background: rgba(159, 239, 0, 0.1);
  box-shadow: 0 0 15px rgba(159, 239, 0, 0.4);
}

.difficulty-easy::before {
  content: '[E]';
  margin-right: 5px;
}

.difficulty-medium {
  background: transparent;
  color: #d4ac0d;
  border-color: #d4ac0d;
}

.post-list li:hover .difficulty-medium {
  background: rgba(212, 172, 13, 0.1);
  box-shadow: 0 0 15px rgba(212, 172, 13, 0.4);
}

.difficulty-medium::before {
  content: '[M]';
  margin-right: 5px;
}

.difficulty-hard {
  background: transparent;
  color: var(--thm-red);
  border-color: var(--thm-red);
}

.post-list li:hover .difficulty-hard {
  background: rgba(192, 57, 43, 0.1);
  box-shadow: 0 0 15px rgba(192, 57, 43, 0.4);
}

.difficulty-hard::before {
  content: '[H]';
  margin-right: 5px;
}

/* Tags - Minimal Style with Dramatic Hover */
.post-list div[style*="margin-top: 10px"] {
  margin-top: 14px !important;
}

.post-list div[style*="margin-top: 10px"] span {
  background: transparent !important;
  color: var(--retro-text-dim) !important;
  border: 1px solid var(--retro-border) !important;
  padding: 4px 10px !important;
  font-size: 0.8rem !important;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  display: inline-block;
  font-family: 'Courier New', monospace;
}

.post-list div[style*="margin-top: 10px"] span:hover {
  border-color: var(--htb-green) !important;
  color: var(--htb-green) !important;
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(159, 239, 0, 0.3);
}

/* Read Time Badge */
.read-time {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  color: var(--retro-text-dim);
  font-size: 0.85rem;
  font-family: 'Courier New', monospace;
}

.read-time::before {
  content: '~';
  font-weight: 700;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .hero h2 {
    font-size: 2rem;
    letter-spacing: 4px;
  }

  .stats-compact {
    flex-direction: column;
    max-width: 280px;
  }
  
  .counter-box {
    max-width: 100%;
  }
  
  .post-link {
    font-size: 1.3rem !important;
  }
  
  .writeups-title {
    font-size: 1.6rem;
  }
  
  .post-list li {
    padding: 20px;
  }

  .post-list li:hover {
    transform: translateX(8px) translateY(-5px);
  }
}

/* Subtle Scan Line Effect */
@keyframes scanline {
  0% {
    transform: translateY(-100%);
  }
  100% {
    transform: translateY(100vh);
  }
}

body::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(transparent, var(--htb-green), transparent);
  opacity: 0.04;
  animation: scanline 8s linear infinite;
  pointer-events: none;
  z-index: 1000;
}

/* Terminal Cursor Effect on Hover */
.post-link:hover::after {
  content: '_';
  animation: blink 1s infinite;
  margin-left: 8px;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
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

.post-list li {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

.post-list li:nth-child(1) { animation-delay: 0.1s; }
.post-list li:nth-child(2) { animation-delay: 0.2s; }
.post-list li:nth-child(3) { animation-delay: 0.3s; }
.post-list li:nth-child(4) { animation-delay: 0.4s; }
.post-list li:nth-child(5) { animation-delay: 0.5s; }

/* Glow effect on hover */
.post-list li:hover {
  animation: pulse-glow 2s infinite;
}

@keyframes pulse-glow {
  0%, 100% {
    box-shadow: -10px 15px 40px rgba(159, 239, 0, 0.3);
  }
  50% {
    box-shadow: -10px 15px 60px rgba(159, 239, 0, 0.5);
  }
}
</style>

<div class="hero">
  <h2>THE PROFESSOR'S LAB</h2>
  
  <div class="hero-quote">
    <p style="margin: 0;">
      > "Say my name."<br>
      > "Heisenberg."<br>
      > <span style="color: var(--htb-green);">"You're goddamn right."</span>
    </p>
  </div>
</div>

<!-- CUTE & SMALL COMPACT STATS -->
<div class="stats-compact">
  <div class="counter-box htb-counter">
    <div class="counter-icon">▣</div>
    <div class="counter-number" id="htb-count">0</div>
    <div class="counter-label">HTB</div>
    <div class="counter-detail">
      <span>E:<span id="htb-easy-compact">0</span></span>
      <span>M:<span id="htb-medium-compact">0</span></span>
      <span>H:<span id="htb-hard-compact">0</span></span>
    </div>
  </div>

  <div class="counter-box thm-counter">
    <div class="counter-icon">▣</div>
    <div class="counter-number" id="thm-count">0</div>
    <div class="counter-label">THM</div>
    <div class="counter-detail">
      <span>E:<span id="thm-easy-compact">0</span></span>
      <span>M:<span id="thm-medium-compact">0</span></span>
      <span>H:<span id="thm-hard-compact">0</span></span>
    </div>
  </div>

  <div class="counter-box total-counter">
    <div class="counter-icon">◈</div>
    <div class="counter-number" id="total-count">0</div>
    <div class="counter-label">Total</div>
    <div class="counter-detail" style="justify-content: center;">
      <span>Root</span>
    </div>
  </div>
</div>

<!-- POSTS SECTION -->
<div class="writeups-header">
  <h2 class="writeups-title">POSTS</h2>
  <p class="writeups-subtitle">
    Penetration testing journey from zero to hero
  </p>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const posts = document.querySelectorAll('.post-list li');
  let htbCount = 0, thmCount = 0;
  let htbEasy = 0, htbMedium = 0, htbHard = 0;
  let thmEasy = 0, thmMedium = 0, thmHard = 0;
  
  posts.forEach(post => {
    const link = post.querySelector('.post-link');
    if (!link) return;
    
    const title = link.textContent.toLowerCase();
    const difficultyBadge = post.querySelector('.difficulty-badge');
    const difficulty = difficultyBadge ? difficultyBadge.textContent.toLowerCase() : 'easy';
    
    if (title.includes('htb:') || title.includes('hackthebox')) {
      htbCount++;
      if (difficulty.includes('easy') || difficulty.includes('[e]')) htbEasy++;
      else if (difficulty.includes('medium') || difficulty.includes('[m]')) htbMedium++;
      else if (difficulty.includes('hard') || difficulty.includes('[h]')) htbHard++;
    } 
    else if (title.includes('thm:') || title.includes('tryhackme')) {
      thmCount++;
      if (difficulty.includes('easy') || difficulty.includes('[e]')) thmEasy++;
      else if (difficulty.includes('medium') || difficulty.includes('[m]')) thmMedium++;
      else if (difficulty.includes('hard') || difficulty.includes('[h]')) thmHard++;
    }
  });
  
  function animateCounter(element, target) {
    let current = 0;
    const increment = Math.ceil(target / 15);
    const timer = setInterval(() => {
      current += increment;
      if (current >= target) {
        element.textContent = target;
        clearInterval(timer);
      } else {
        element.textContent = current;
      }
    }, 60);
  }
  
  const total = htbCount + thmCount;
  
  animateCounter(document.getElementById('htb-count'), htbCount);
  animateCounter(document.getElementById('thm-count'), thmCount);
  animateCounter(document.getElementById('total-count'), total);
  
  document.getElementById('htb-easy-compact').textContent = htbEasy;
  document.getElementById('htb-medium-compact').textContent = htbMedium;
  document.getElementById('htb-hard-compact').textContent = htbHard;
  
  document.getElementById('thm-easy-compact').textContent = thmEasy;
  document.getElementById('thm-medium-compact').textContent = thmMedium;
  document.getElementById('thm-hard-compact').textContent = thmHard;
});
</script>
