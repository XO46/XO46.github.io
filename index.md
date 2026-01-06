---
layout: home
title: Mr. White | The Professor's Lab Notes
---

<style>
/* Hero Section - Compact */
.hero {
  max-width: 1150px;
  margin: 0 auto;
  padding: 40px 20px 30px 20px;
}

.hero h2 {
  text-align: center;
  color: #00ccff;
  font-size: 2rem;
  margin-bottom: 20px;
  text-transform: uppercase;
  letter-spacing: 3px;
  font-weight: 300;
}

.hero-quote {
  margin: 20px auto;
  padding: 20px;
  background: var(--bg-secondary);
  border-left: 3px solid var(--accent-blue);
  border-radius: 8px;
  max-width: 700px;
  font-size: 0.95rem;
  line-height: 1.6;
  color: var(--text-secondary);
}

/* COMPACT PLATFORM COUNTERS - Side by Side */
.stats-compact {
  display: flex;
  gap: 15px;
  max-width: 1150px;
  margin: 30px auto;
  justify-content: center;
  align-items: stretch;
}

.counter-box {
  flex: 1;
  max-width: 200px;
  background: linear-gradient(145deg, #161616, #1f1f1f);
  border: 2px solid;
  border-radius: 15px;
  padding: 20px 15px;
  text-align: center;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.counter-box::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.05) 0%, transparent 70%);
  opacity: 0;
  transition: opacity 0.3s;
}

.counter-box:hover::before {
  opacity: 1;
}

.counter-box:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.htb-counter {
  border-color: #9fef00;
}

.htb-counter:hover {
  box-shadow: 0 10px 30px rgba(159, 239, 0, 0.3);
}

.thm-counter {
  border-color: #ff0000;
}

.thm-counter:hover {
  box-shadow: 0 10px 30px rgba(255, 0, 0, 0.3);
}

.total-counter {
  border-color: #00ccff;
}

.total-counter:hover {
  box-shadow: 0 10px 30px rgba(0, 204, 255, 0.3);
}

.counter-icon {
  font-size: 2rem;
  margin-bottom: 10px;
}

.counter-number {
  font-size: 2.5rem;
  font-weight: 900;
  margin: 10px 0;
  position: relative;
  z-index: 1;
}

.htb-counter .counter-number {
  color: #9fef00;
  text-shadow: 0 0 20px rgba(159, 239, 0, 0.4);
}

.thm-counter .counter-number {
  color: #ff0000;
  text-shadow: 0 0 20px rgba(255, 0, 0, 0.4);
}

.total-counter .counter-number {
  color: #00ccff;
  text-shadow: 0 0 20px rgba(0, 204, 255, 0.4);
}

.counter-label {
  font-size: 0.75rem;
  color: #808080;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: 600;
}

.counter-detail {
  margin-top: 10px;
  padding-top: 10px;
  border-top: 1px solid #2a2a2a;
  font-size: 0.7rem;
  color: #666;
  display: flex;
  justify-content: space-around;
}

.counter-detail span {
  display: block;
}

/* WRITEUPS SECTION - MAIN FOCUS */
.writeups-header {
  max-width: 1150px;
  margin: 50px auto 30px auto;
  padding: 0 20px;
}

.writeups-title {
  font-size: 2rem;
  font-weight: 700;
  color: #00ccff;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 15px;
}

.writeups-title::before {
  content: '📝';
  font-size: 2rem;
}

.writeups-subtitle {
  color: var(--text-secondary);
  font-size: 1rem;
  margin-bottom: 25px;
  padding-bottom: 20px;
  border-bottom: 2px solid var(--border-primary);
}

/* Enhanced Post Cards - BIGGER & MORE PROMINENT */
.post-list {
  list-style: none;
  padding: 0;
  max-width: 1150px;
  margin: 0 auto;
}

.post-list li {
  margin-bottom: 30px;
  padding: 30px;
  background: linear-gradient(145deg, #161616, #1f1f1f);
  border: 2px solid var(--border-primary);
  border-radius: 12px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.post-list li::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, #00ccff, #9fef00, #ff0000);
  opacity: 0;
  transition: opacity 0.3s;
}

.post-list li::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 204, 255, 0.05), transparent);
  transition: left 0.6s ease;
}

.post-list li:hover::before {
  opacity: 1;
}

.post-list li:hover::after {
  left: 100%;
}

.post-list li:hover {
  background: linear-gradient(145deg, #1a1a1a, #242424);
  border-color: #00ccff;
  transform: translateX(8px) translateY(-3px);
  box-shadow: 0 12px 35px rgba(0, 204, 255, 0.2);
}

.post-link {
  font-size: 1.6rem !important;
  font-weight: 700;
  display: inline-block;
  margin-bottom: 12px;
  text-decoration: none;
  color: #00ccff !important;
  position: relative;
  z-index: 1;
  transition: all 0.3s ease;
  line-height: 1.3;
}

.post-link:hover {
  color: #00aadd !important;
  text-shadow: 0 0 10px rgba(0, 204, 255, 0.5);
}

/* Platform Badge in Title */
.post-link::before {
  content: '🎯';
  margin-right: 8px;
  font-size: 1.4rem;
}

.post-list .post-meta {
  border: none;
  padding: 0;
  margin: 10px 0;
  font-size: 0.95rem;
  color: var(--text-tertiary);
  display: flex;
  gap: 20px;
  align-items: center;
  flex-wrap: wrap;
}

.post-meta span {
  display: flex;
  align-items: center;
  gap: 6px;
}

.post-excerpt {
  margin-top: 15px;
  color: var(--text-secondary);
  font-size: 1.05rem;
  line-height: 1.7;
  position: relative;
  z-index: 1;
}

/* Difficulty Badge - More Prominent */
.difficulty-badge {
  display: inline-flex;
  align-items: center;
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  gap: 5px;
}

.difficulty-easy {
  background: rgba(0, 255, 0, 0.2);
  color: #00ff00;
  border: 2px solid #00ff00;
}

.difficulty-easy::before {
  content: '⭐';
}

.difficulty-medium {
  background: rgba(255, 191, 0, 0.2);
  color: #ffbf00;
  border: 2px solid #ffbf00;
}

.difficulty-medium::before {
  content: '⭐⭐';
}

.difficulty-hard {
  background: rgba(248, 81, 73, 0.2);
  color: #f85149;
  border: 2px solid #f85149;
}

.difficulty-hard::before {
  content: '⭐⭐⭐';
}

.post-link:hover .difficulty-badge {
  transform: scale(1.1);
}

/* Tags - Enhanced */
.post-list div[style*="margin-top: 10px"] {
  margin-top: 15px !important;
}

.post-list div[style*="margin-top: 10px"] span {
  background: var(--bg-tertiary) !important;
  color: #00ccff !important;
  border: 1px solid var(--border-primary);
  padding: 4px 12px !important;
  border-radius: 6px !important;
  font-size: 0.8rem !important;
  transition: all 0.3s ease;
  display: inline-block;
}

.post-list div[style*="margin-top: 10px"] span:hover {
  background: var(--bg-primary) !important;
  border-color: #00ccff;
  color: #00ccff !important;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 204, 255, 0.2);
}

/* Read Time Badge */
.read-time {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  color: var(--text-tertiary);
  font-size: 0.9rem;
  background: var(--bg-tertiary);
  padding: 4px 10px;
  border-radius: 6px;
}

.read-time::before {
  content: '⏱️';
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .stats-compact {
    flex-direction: column;
    max-width: 300px;
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

/* Scroll Animation */
@keyframes slideInUp {
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
  animation: slideInUp 0.6s ease forwards;
  opacity: 0;
}

.post-list li:nth-child(1) { animation-delay: 0.1s; }
.post-list li:nth-child(2) { animation-delay: 0.2s; }
.post-list li:nth-child(3) { animation-delay: 0.3s; }
.post-list li:nth-child(4) { animation-delay: 0.4s; }
.post-list li:nth-child(5) { animation-delay: 0.5s; }
</style>

<div class="hero">
  <h2>THE PROFESSOR'S LAB</h2>
  
  <div class="hero-quote">
    <p style="margin: 0; font-style: italic;">
      "Say my name." — "Heisenberg." — <strong style="color: #00ccff;">"You're goddamn right."</strong>
    </p>
  </div>
</div>

<!-- COMPACT STATS - Quick Overview -->
<div class="stats-compact">
  <div class="counter-box htb-counter">
    <div class="counter-icon">🎯</div>
    <div class="counter-number" id="htb-count">0</div>
    <div class="counter-label">HackTheBox</div>
    <div class="counter-detail">
      <span id="htb-easy-compact">0</span>
      <span id="htb-medium-compact">0</span>
      <span id="htb-hard-compact">0</span>
    </div>
  </div>

  <div class="counter-box thm-counter">
    <div class="counter-icon">🔐</div>
    <div class="counter-number" id="thm-count">0</div>
    <div class="counter-label">TryHackMe</div>
    <div class="counter-detail">
      <span id="thm-easy-compact">0</span>
      <span id="thm-medium-compact">0</span>
      <span id="thm-hard-compact">0</span>
    </div>
  </div>

  <div class="counter-box total-counter">
    <div class="counter-icon">🏆</div>
    <div class="counter-number" id="total-count">0</div>
    <div class="counter-label">Total Writeups</div>
    <div class="counter-detail" style="justify-content: center;">
      <span style="color: #00ccff;">100% Root</span>
    </div>
  </div>
</div>

<!-- WRITEUPS SECTION - MAIN FOCUS -->
<div class="writeups-header">
  <h2 class="writeups-title">Latest Writeups</h2>
  <p class="writeups-subtitle">
    Detailed penetration testing reports documenting vulnerabilities, exploitation techniques, and privilege escalation paths from reconnaissance to full system compromise.
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
      if (difficulty.includes('easy')) htbEasy++;
      else if (difficulty.includes('medium')) htbMedium++;
      else if (difficulty.includes('hard')) htbHard++;
    } 
    else if (title.includes('thm:') || title.includes('tryhackme')) {
      thmCount++;
      if (difficulty.includes('easy')) thmEasy++;
      else if (difficulty.includes('medium')) thmMedium++;
      else if (difficulty.includes('hard')) thmHard++;
    }
  });
  
  function animateCounter(element, target) {
    let current = 0;
    const increment = Math.ceil(target / 20);
    const timer = setInterval(() => {
      current += increment;
      if (current >= target) {
        element.textContent = target;
        clearInterval(timer);
      } else {
        element.textContent = current;
      }
    }, 50);
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
