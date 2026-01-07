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

/* REMOVE DEFAULT PADDING/MARGINS */
body {
  margin: 0 !important;
  padding: 0 !important;
}

.page-content, .wrapper {
  padding: 0 !important;
  margin: 0 !important;
  max-width: 100% !important;
}

/* ===================================================
   FULL-WIDTH HERO BANNER - NO GAPS
   =================================================== */
.hero-banner {
  width: 100%;
  background: linear-gradient(135deg, #0d0d0d 0%, #1a1a1a 50%, #0d0d0d 100%);
  border-bottom: 2px solid var(--htb-green);
  box-shadow: 0 4px 20px rgba(159, 239, 0, 0.2);
  position: relative;
  overflow: hidden;
  margin: 0;
  padding: 0;
}

/* Animated grid pattern background */
.hero-banner::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(159, 239, 0, 0.03) 2px,
      rgba(159, 239, 0, 0.03) 4px
    );
  pointer-events: none;
  animation: scan 8s linear infinite;
}

@keyframes scan {
  0% { transform: translateY(0); }
  100% { transform: translateY(100px); }
}

.hero-content {
  max-width: 1150px;
  margin: 0 auto;
  padding: 80px 20px 60px;
  text-align: center;
  position: relative;
  z-index: 1;
}

.hero-title {
  font-size: 4rem;
  font-weight: 900;
  color: var(--htb-green);
  text-transform: uppercase;
  letter-spacing: 12px;
  margin-bottom: 20px;
  font-family: 'Courier New', monospace;
  text-shadow: 
    0 0 10px rgba(159, 239, 0, 0.5),
    0 0 20px rgba(159, 239, 0, 0.3),
    0 0 30px rgba(159, 239, 0, 0.2);
  animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    text-shadow: 
      0 0 10px rgba(159, 239, 0, 0.5),
      0 0 20px rgba(159, 239, 0, 0.3),
      0 0 30px rgba(159, 239, 0, 0.2);
  }
  to {
    text-shadow: 
      0 0 20px rgba(159, 239, 0, 0.8),
      0 0 30px rgba(159, 239, 0, 0.5),
      0 0 40px rgba(159, 239, 0, 0.3);
  }
}

.hero-subtitle {
  font-size: 1.2rem;
  color: var(--retro-text-dim);
  letter-spacing: 3px;
  margin-bottom: 40px;
  text-transform: uppercase;
  font-family: 'Courier New', monospace;
}

.hero-quote-box {
  max-width: 700px;
  margin: 0 auto;
  padding: 30px;
  background: rgba(26, 26, 26, 0.8);
  border-left: 4px solid var(--htb-green);
  border-radius: 6px;
  text-align: left;
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.hero-quote-box p {
  font-size: 1.1rem;
  line-height: 1.8;
  margin: 0;
  color: var(--retro-text-dim);
  font-family: 'Courier New', monospace;
}

.quote-highlight {
  color: var(--htb-green);
  font-weight: 700;
}

/* ===================================================
   STATS SECTION - FULL WIDTH BACKGROUND
   =================================================== */
.stats-wrapper {
  width: 100%;
  background: var(--retro-bg);
  padding: 40px 20px;
  margin: 0;
}

.stats-compact {
  display: flex;
  gap: 12px;
  max-width: 1150px;
  margin: 0 auto;
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

/* ===================================================
   POSTS SECTION - FULL WIDTH BACKGROUND
   =================================================== */
.posts-wrapper {
  width: 100%;
  background: var(--retro-bg);
  padding: 50px 20px;
  margin: 0;
}

.writeups-header {
  max-width: 1150px;
  margin: 0 auto 30px;
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

/* POST CARDS */
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

.post-list li:hover::before {
  width: 4px;
  background: var(--htb-green);
  box-shadow: 0 0 10px var(--htb-green);
}

.post-list li:hover {
  border-color: var(--htb-green);
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(159, 239, 0, 0.2);
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

.post-link:hover {
  color: var(--htb-green) !important;
  text-shadow: 0 0 8px rgba(159, 239, 0, 0.3);
}

.post-link::before {
  content: '[';
  margin-right: 6px;
  color: var(--retro-text-dim);
  font-weight: 400;
}

.post-link::after {
  content: ']';
  margin-left: 6px;
  color: var(--retro-text-dim);
  font-weight: 400;
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

/* MOBILE RESPONSIVE */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
    letter-spacing: 6px;
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .hero-content {
    padding: 50px 20px 40px;
  }

  .hero-quote-box {
    padding: 20px;
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
}

/* FADE IN ANIMATIONS */
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
</style>

<!-- FULL-WIDTH HERO BANNER -->
<section class="hero-banner">
  <div class="hero-content">
    <h1 class="hero-title">THE PROFESSOR'S LAB</h1>
    <p class="hero-subtitle">Penetration Testing & Security Research</p>
    
    <div class="hero-quote-box">
      <p>
        > "Say my name."<br>
        > "Heisenberg."<br>
        > <span class="quote-highlight">"You're goddamn right."</span>
      </p>
    </div>
  </div>
</section>

<!-- STATS SECTION WITH FULL BACKGROUND -->
<section class="stats-wrapper">
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
</section>

<!-- POSTS SECTION WITH FULL BACKGROUND -->
<section class="posts-wrapper">
  <div class="writeups-header">
    <h2 class="writeups-title">POSTS</h2>
    <p class="writeups-subtitle">
      Penetration testing journey from zero to hero
    </p>
  </div>
</section>

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
