---
layout: page
title: Certifications
permalink: /certifications/
---

<style>
:root {
  --retro-bg: #0d0d0d;
  --retro-surface: #1a1a1a;
  --retro-text: #c5c5c5;
  --retro-text-dim: #858585;
  --retro-border: #2d2d2d;
  --htb-green: #9fef00;
  --thm-red: #c0392b;
  --cert-gold: #ffd700;
  --cert-blue: #4a90e2;
}

.page-content {
  background: var(--retro-bg) !important;
  max-width: 1150px !important;
  margin: 40px auto !important;
  padding: 40px 20px !important;
}

.page-content h1 {
  font-size: 3rem !important;
  margin-bottom: 15px !important;
  color: var(--retro-text) !important;
  text-align: center !important;
  text-transform: uppercase !important;
  letter-spacing: 8px !important;
  font-weight: 700 !important;
  font-family: 'Courier New', monospace !important;
  text-shadow: 0 0 20px rgba(197, 197, 197, 0.3) !important;
  border-bottom: none !important;
}

/* Subtitle */
.cert-subtitle {
  text-align: center;
  font-size: 1.1rem;
  color: var(--retro-text-dim);
  margin-bottom: 50px;
  font-family: 'Courier New', monospace;
  font-style: italic;
}

/* Stats Dashboard */
.cert-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 20px;
  margin: 40px 0 60px 0;
}

.stat-box {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  padding: 25px 20px;
  text-align: center;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.stat-box::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: var(--retro-border);
  transition: all 0.5s ease;
}

.stat-box:hover {
  transform: translateY(-8px);
  box-shadow: 0 10px 30px rgba(159, 239, 0, 0.2);
  border-color: var(--htb-green);
}

.stat-box:hover::before {
  background: var(--htb-green);
  box-shadow: 0 0 15px var(--htb-green);
}

.stat-icon {
  font-size: 2.2rem;
  margin-bottom: 12px;
  transition: all 0.5s ease;
}

.stat-box:hover .stat-icon {
  transform: scale(1.3) rotate(360deg);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--htb-green);
  font-family: 'Courier New', monospace;
  margin: 10px 0;
  text-shadow: 0 0 15px rgba(159, 239, 0, 0.4);
}

.stat-label {
  font-size: 0.85rem;
  color: var(--retro-text-dim);
  text-transform: uppercase;
  letter-spacing: 1.5px;
  font-family: 'Courier New', monospace;
}

/* Timeline Container */
.timeline-container {
  position: relative;
  margin: 60px 0;
}

.timeline-line {
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(to bottom, var(--retro-border), var(--htb-green));
  transform: translateX(-50%);
}

/* Timeline Items */
.timeline-item {
  display: flex;
  align-items: center;
  margin-bottom: 60px;
  position: relative;
  opacity: 0;
  animation: fadeInTimeline 0.8s ease forwards;
}

.timeline-item:nth-child(1) { animation-delay: 0.2s; }
.timeline-item:nth-child(2) { animation-delay: 0.4s; }
.timeline-item:nth-child(3) { animation-delay: 0.6s; }
.timeline-item:nth-child(4) { animation-delay: 0.8s; }

@keyframes fadeInTimeline {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.timeline-item.left {
  flex-direction: row;
}

.timeline-item.right {
  flex-direction: row-reverse;
}

.timeline-content {
  width: calc(50% - 40px);
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  padding: 30px;
  position: relative;
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

.timeline-content::before {
  content: '';
  position: absolute;
  top: 0;
  width: 4px;
  height: 100%;
  background: var(--retro-border);
  transition: all 0.6s ease;
}

.timeline-item.left .timeline-content::before {
  right: 0;
}

.timeline-item.right .timeline-content::before {
  left: 0;
}

.timeline-content:hover {
  transform: scale(1.05);
  border-color: var(--htb-green);
  box-shadow: 0 10px 40px rgba(159, 239, 0, 0.3);
}

.timeline-content:hover::before {
  background: var(--htb-green);
  box-shadow: 0 0 15px var(--htb-green);
}

/* Timeline Dot */
.timeline-dot {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 20px;
  background: var(--retro-bg);
  border: 3px solid var(--htb-green);
  border-radius: 50%;
  z-index: 10;
  transition: all 0.5s ease;
  box-shadow: 0 0 0 0 rgba(159, 239, 0, 0.7);
}

.timeline-item:hover .timeline-dot {
  transform: translateX(-50%) scale(1.5);
  box-shadow: 0 0 0 10px rgba(159, 239, 0, 0);
  animation: pulse-ring 1.5s infinite;
}

@keyframes pulse-ring {
  0% {
    box-shadow: 0 0 0 0 rgba(159, 239, 0, 0.7);
  }
  100% {
    box-shadow: 0 0 0 15px rgba(159, 239, 0, 0);
  }
}

/* Certification Badge */
.cert-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 12px;
  border-radius: 3px;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-family: 'Courier New', monospace;
  margin-bottom: 15px;
}

.cert-badge.completed {
  background: rgba(159, 239, 0, 0.15);
  color: var(--htb-green);
  border: 1px solid var(--htb-green);
}

.cert-badge.in-progress {
  background: rgba(255, 215, 0, 0.15);
  color: var(--cert-gold);
  border: 1px solid var(--cert-gold);
}

.cert-badge.planned {
  background: rgba(74, 144, 226, 0.15);
  color: var(--cert-blue);
  border: 1px solid var(--cert-blue);
}

/* Cert Title */
.cert-title {
  font-size: 1.6rem;
  font-weight: 700;
  color: var(--retro-text);
  margin-bottom: 12px;
  font-family: 'Courier New', monospace;
  letter-spacing: 1px;
}

.cert-org {
  font-size: 0.9rem;
  color: var(--retro-text-dim);
  margin-bottom: 15px;
  font-family: 'Courier New', monospace;
}

.cert-description {
  color: var(--retro-text-dim);
  font-size: 0.95rem;
  line-height: 1.7;
  font-family: 'Courier New', monospace;
  margin-bottom: 15px;
}

.cert-skills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 15px;
}

.skill-tag {
  background: transparent;
  border: 1px solid var(--retro-border);
  padding: 4px 10px;
  font-size: 0.75rem;
  color: var(--retro-text-dim);
  font-family: 'Courier New', monospace;
  transition: all 0.3s ease;
}

.timeline-content:hover .skill-tag {
  border-color: var(--htb-green);
  color: var(--htb-green);
  transform: translateY(-2px);
}

/* Date Badge */
.cert-date {
  font-size: 0.85rem;
  color: var(--htb-green);
  font-family: 'Courier New', monospace;
  margin-top: 12px;
  display: flex;
  align-items: center;
  gap: 6px;
}

/* Progress Bar */
.progress-container {
  margin-top: 15px;
}

.progress-label {
  font-size: 0.8rem;
  color: var(--retro-text-dim);
  margin-bottom: 6px;
  font-family: 'Courier New', monospace;
}

.progress-bar {
  width: 100%;
  height: 8px;
  background: var(--retro-border);
  border-radius: 4px;
  overflow: hidden;
  position: relative;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--htb-green), var(--cert-gold));
  transition: width 1.5s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 0 10px rgba(159, 239, 0, 0.5);
}

/* Philosophy Box */
.philosophy-box {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  border-left: 4px solid var(--htb-green);
  padding: 30px;
  margin-top: 60px;
  position: relative;
  overflow: hidden;
}

.philosophy-box::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, var(--htb-green), transparent);
}

.philosophy-text {
  font-size: 1.1rem;
  color: var(--retro-text);
  font-family: 'Courier New', monospace;
  line-height: 1.8;
  text-align: center;
  font-style: italic;
}

.philosophy-text strong {
  color: var(--htb-green);
  font-style: normal;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .page-content h1 {
    font-size: 2rem !important;
    letter-spacing: 4px !important;
  }
  
  .cert-stats {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .timeline-line {
    left: 20px;
  }
  
  .timeline-item {
    flex-direction: column !important;
    padding-left: 50px;
  }
  
  .timeline-content {
    width: 100% !important;
  }
  
  .timeline-dot {
    left: 20px !important;
  }
  
  .timeline-item.left .timeline-content::before,
  .timeline-item.right .timeline-content::before {
    left: 0;
    right: auto;
  }
}
</style>

<div class="cert-subtitle">
  "Certifications support learning. Writeups demonstrate understanding."
</div>

<!-- Stats Dashboard -->
<div class="cert-stats">
  <div class="stat-box">
    <div class="stat-icon">✅</div>
    <div class="stat-number" id="completed-count">0</div>
    <div class="stat-label">Completed</div>
  </div>
  
  <div class="stat-box">
    <div class="stat-icon">⚡</div>
    <div class="stat-number" id="progress-count">0</div>
    <div class="stat-label">In Progress</div>
  </div>
  
  <div class="stat-box">
    <div class="stat-icon">🎯</div>
    <div class="stat-number" id="planned-count">0</div>
    <div class="stat-label">Planned</div>
  </div>
  
  <div class="stat-box">
    <div class="stat-icon">🏆</div>
    <div class="stat-number" id="total-count">0</div>
    <div class="stat-label">Total Goals</div>
  </div>
</div>

<!-- Timeline -->
<div class="timeline-container">
  <div class="timeline-line"></div>
  
  <!-- eJPT -->
  <div class="timeline-item left" data-status="completed">
    <div class="timeline-content">
      <span class="cert-badge completed">✓ Completed</span>
      <h3 class="cert-title">eJPT</h3>
      <div class="cert-org">eLearnSecurity Junior Penetration Tester</div>
      <p class="cert-description">
        Entry-level certification covering fundamental penetration testing skills including enumeration, exploitation, and post-exploitation techniques.
      </p>
      <div class="cert-skills">
        <span class="skill-tag">Network Scanning</span>
        <span class="skill-tag">Web Attacks</span>
        <span class="skill-tag">Exploitation</span>
        <span class="skill-tag">Enumeration</span>
      </div>
      <div class="cert-date">📅 Completed: 2024</div>
    </div>
    <div class="timeline-dot"></div>
  </div>
  
  <!-- PNPT -->
  <div class="timeline-item right" data-status="in-progress">
    <div class="timeline-content">
      <span class="cert-badge in-progress">⚡ In Progress</span>
      <h3 class="cert-title">PNPT</h3>
      <div class="cert-org">Practical Network Penetration Tester - TCM Security</div>
      <p class="cert-description">
        Advanced hands-on certification simulating a real-world penetration test with a 5-day practical exam including Active Directory attacks.
      </p>
      <div class="cert-skills">
        <span class="skill-tag">Active Directory</span>
        <span class="skill-tag">OSINT</span>
        <span class="skill-tag">Privilege Escalation</span>
        <span class="skill-tag">Report Writing</span>
      </div>
      <div class="progress-container">
        <div class="progress-label">Progress: 65%</div>
        <div class="progress-bar">
          <div class="progress-fill" style="width: 0%" data-target="65"></div>
        </div>
      </div>
      <div class="cert-date">🎯 Expected: Q2 2025</div>
    </div>
    <div class="timeline-dot"></div>
  </div>
  
  <!-- TryHackMe -->
  <div class="timeline-item left" data-status="completed">
    <div class="timeline-content">
      <span class="cert-badge completed">✓ Completed</span>
      <h3 class="cert-title">TryHackMe Pentester Path</h3>
      <div class="cert-org">TryHackMe Learning Platform</div>
      <p class="cert-description">
        Comprehensive learning path covering offensive security fundamentals through hands-on labs and practical challenges.
      </p>
      <div class="cert-skills">
        <span class="skill-tag">Linux</span>
        <span class="skill-tag">Windows</span>
        <span class="skill-tag">Web Security</span>
        <span class="skill-tag">CTF</span>
      </div>
      <div class="cert-date">📅 Completed: 2024</div>
    </div>
    <div class="timeline-dot"></div>
  </div>
  
  <!-- Future: OSCP -->
  <div class="timeline-item right" data-status="planned">
    <div class="timeline-content">
      <span class="cert-badge planned">🎯 Planned</span>
      <h3 class="cert-title">OSCP</h3>
      <div class="cert-org">Offensive Security Certified Professional</div>
      <p class="cert-description">
        Industry-leading certification with 24-hour practical exam. The gold standard for penetration testing professionals.
      </p>
      <div class="cert-skills">
        <span class="skill-tag">Buffer Overflow</span>
        <span class="skill-tag">Exploit Development</span>
        <span class="skill-tag">Pivoting</span>
        <span class="skill-tag">Advanced AD</span>
      </div>
      <div class="cert-date">🚀 Target: 2025-2026</div>
    </div>
    <div class="timeline-dot"></div>
  </div>
  
</div>

<!-- Philosophy Box -->
<div class="philosophy-box">
  <p class="philosophy-text">
    Certifications validate knowledge.<br>
    <strong>Practical experience builds mastery.</strong><br>
    This portfolio demonstrates both.
  </p>
</div>

<script>
// Animate Counters
document.addEventListener('DOMContentLoaded', function() {
  const items = document.querySelectorAll('.timeline-item');
  let completed = 0;
  let inProgress = 0;
  let planned = 0;
  
  items.forEach(item => {
    const status = item.getAttribute('data-status');
    if (status === 'completed') completed++;
    else if (status === 'in-progress') inProgress++;
    else if (status === 'planned') planned++;
  });
  
  const total = completed + inProgress + planned;
  
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
  
  setTimeout(() => {
    animateCounter(document.getElementById('completed-count'), completed);
    animateCounter(document.getElementById('progress-count'), inProgress);
    animateCounter(document.getElementById('planned-count'), planned);
    animateCounter(document.getElementById('total-count'), total);
  }, 300);
  
  // Animate Progress Bars
  const progressBars = document.querySelectorAll('.progress-fill');
  setTimeout(() => {
    progressBars.forEach(bar => {
      const target = bar.getAttribute('data-target');
      bar.style.width = target + '%';
    });
  }, 800);
});
</script>
