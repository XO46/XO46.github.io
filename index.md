---
layout: home
title: Mr. White | The Professor's Lab Notes
---

<div class="hero">
  <h2 style="font-weight: 300; letter-spacing: 3px;">THE PROFESSOR'S LAB</h2>
  
  <div style="margin: 40px 0; padding: 30px; background: var(--bg-secondary); border-left: 4px solid var(--accent-blue); border-radius: 10px; box-shadow: 0 4px 20px rgba(0, 204, 255, 0.1);">
    <p style="font-size: 1.15rem; color: var(--text-secondary); margin: 0; line-height: 1.8;">
      "Say my name."
    </p>
    <p style="font-size: 1.15rem; color: var(--text-primary); margin: 15px 0 15px 30px; line-height: 1.8;">
      "Heisenberg."
    </p>
    <p style="font-size: 1.15rem; color: var(--accent-blue); margin: 0; font-weight: 600; line-height: 1.8;">
      "You're goddamn right."
    </p>
  </div>

  <div style="margin-top: 40px;">
    <p style="font-size: 1.1rem; line-height: 1.8; color: var(--text-primary); text-align: center; max-width: 850px; margin: 0 auto;">
      Penetration testing writeups documenting vulnerabilities, exploitation techniques, and privilege escalation paths. 
      Each report follows a systematic methodology from reconnaissance to post-exploitation.
    </p>
  </div>
</div>

<!-- Platform Statistics -->
<div class="platform-boxes">
  <div class="platform-box htb-box">
    <div class="platform-logo">🎯</div>
    <div class="platform-name">HackTheBox</div>
    <div class="platform-count" id="htb-count">0</div>
    <div class="platform-label">Machines Pwned</div>
  </div>
  
  <div class="platform-box thm-box">
    <div class="platform-logo">🔐</div>
    <div class="platform-name">TryHackMe</div>
    <div class="platform-count" id="thm-count">0</div>
    <div class="platform-label">Rooms Completed</div>
  </div>
</div>

<!-- Overall Stats -->
<div style="margin: 60px auto; max-width: 1150px;">
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 25px;">
    <div class="stat-card">
      <div class="stat-number" id="total-writeups">0</div>
      <div class="stat-label">Total Writeups</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">50+</div>
      <div class="stat-label">CVEs Exploited</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">100%</div>
      <div class="stat-label">Root Access</div>
    </div>
  </div>
</div>

<div style="margin-top: 80px;">
  <h2 style="font-size: 1.8rem; font-weight: 600; color: var(--text-primary); margin-bottom: 35px; padding-bottom: 15px; border-bottom: 2px solid var(--border-primary); max-width: 1150px; margin-left: auto; margin-right: auto;">
    Latest Writeups
  </h2>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Get all posts from the page
  const posts = document.querySelectorAll('.post-list li');
  let htbCount = 0;
  let thmCount = 0;
  
  // Count posts by platform
  posts.forEach(post => {
    const title = post.querySelector('.post-link').textContent.toLowerCase();
    if (title.includes('htb:') || title.includes('hackthebox')) {
      htbCount++;
    } else if (title.includes('thm:') || title.includes('tryhackme')) {
      thmCount++;
    }
  });
  
  // Animate counters
  function animateCounter(element, target) {
    let current = 0;
    const increment = target / 50;
    const timer = setInterval(() => {
      current += increment;
      if (current >= target) {
        element.textContent = target;
        clearInterval(timer);
      } else {
        element.textContent = Math.floor(current);
      }
    }, 20);
  }
  
  // Update counts with animation
  animateCounter(document.getElementById('htb-count'), htbCount);
  animateCounter(document.getElementById('thm-count'), thmCount);
  animateCounter(document.getElementById('total-writeups'), posts.length);
  
  // Add platform-specific colors
  const htbBox = document.querySelector('.htb-box');
  const thmBox = document.querySelector('.thm-box');
  
  htbBox.addEventListener('mouseenter', function() {
    this.style.borderColor = '#9fef00';
    this.querySelector('.platform-count').style.color = '#9fef00';
  });
  
  htbBox.addEventListener('mouseleave', function() {
    this.style.borderColor = '';
    this.querySelector('.platform-count').style.color = '';
  });
  
  thmBox.addEventListener('mouseenter', function() {
    this.style.borderColor = '#ff0000';
    this.querySelector('.platform-count').style.color = '#ff0000';
  });
  
  thmBox.addEventListener('mouseleave', function() {
    this.style.borderColor = '';
    this.querySelector('.platform-count').style.color = '';
  });
});
</script>

<style>
/* Additional platform-specific styles */
.htb-box .platform-logo {
  filter: drop-shadow(0 0 10px rgba(159, 239, 0, 0.3));
}

.thm-box .platform-logo {
  filter: drop-shadow(0 0 10px rgba(255, 0, 0, 0.3));
}

.platform-box:hover .platform-logo {
  animation: bounce 0.6s ease;
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
</style>
