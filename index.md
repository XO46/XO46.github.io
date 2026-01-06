---
layout: home
title: Mr. White | The Professor's Lab Notes
---

<style>
.hero {
  max-width: 1150px;
  margin: 0 auto;
  padding: 60px 20px;
}

.hero h2 {
  text-align: center;
  color: var(--text-primary);
  font-size: 2.5rem;
  margin-bottom: 40px;
  text-transform: uppercase;
  letter-spacing: 3px;
  font-weight: 300;
}

/* Platform Boxes Styling */
.platform-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
  max-width: 900px;
  margin: 50px auto;
}

.platform-box {
  background: linear-gradient(145deg, #161616, #1f1f1f);
  border: 2px solid #2a2a2a;
  border-radius: 20px;
  padding: 35px 25px;
  text-align: center;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.platform-box::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
  transform: translate(-50%, -50%);
  transition: width 0.6s ease, height 0.6s ease;
}

.platform-box:hover::before {
  width: 350px;
  height: 350px;
}

.platform-box:hover {
  transform: translateY(-12px) scale(1.03);
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
}

.htb-box {
  border-color: #9fef00;
}

.htb-box:hover {
  border-color: #9fef00;
  box-shadow: 0 25px 50px rgba(159, 239, 0, 0.3),
              0 0 30px rgba(159, 239, 0, 0.15) inset;
}

.thm-box {
  border-color: #ff0000;
}

.thm-box:hover {
  border-color: #ff0000;
  box-shadow: 0 25px 50px rgba(255, 0, 0, 0.3),
              0 0 30px rgba(255, 0, 0, 0.15) inset;
}

.platform-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto 20px;
  background: #0a0a0a;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2.5rem;
  border: 3px solid;
  transition: all 0.4s ease;
  position: relative;
  z-index: 1;
}

.htb-box .platform-icon {
  border-color: #9fef00;
  box-shadow: 0 0 20px rgba(159, 239, 0, 0.3);
}

.thm-box .platform-icon {
  border-color: #ff0000;
  box-shadow: 0 0 20px rgba(255, 0, 0, 0.3);
}

.platform-box:hover .platform-icon {
  transform: rotate(360deg) scale(1.1);
}

.htb-box:hover .platform-icon {
  box-shadow: 0 0 40px rgba(159, 239, 0, 0.6);
}

.thm-box:hover .platform-icon {
  box-shadow: 0 0 40px rgba(255, 0, 0, 0.6);
}

.platform-name {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 15px;
  letter-spacing: 1px;
  position: relative;
  z-index: 1;
}

.htb-box .platform-name {
  color: #9fef00;
}

.thm-box .platform-name {
  color: #ff0000;
}

.platform-count {
  font-size: 4rem;
  font-weight: 900;
  margin: 20px 0;
  transition: all 0.3s ease;
  position: relative;
  z-index: 1;
}

.htb-box .platform-count {
  color: #9fef00;
  text-shadow: 0 0 30px rgba(159, 239, 0, 0.5);
}

.thm-box .platform-count {
  color: #ff0000;
  text-shadow: 0 0 30px rgba(255, 0, 0, 0.5);
}

.platform-box:hover .platform-count {
  transform: scale(1.15);
}

.platform-label {
  font-size: 0.9rem;
  color: #808080;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-weight: 600;
  position: relative;
  z-index: 1;
}

.platform-details {
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px solid #2a2a2a;
  display: flex;
  justify-content: space-around;
  font-size: 0.85rem;
  position: relative;
  z-index: 1;
}

.detail-item {
  text-align: center;
}

.detail-value {
  font-weight: 700;
  font-size: 1.2rem;
  margin-bottom: 5px;
}

.htb-box .detail-value {
  color: #9fef00;
}

.thm-box .detail-value {
  color: #ff0000;
}

.detail-label {
  color: #808080;
  font-size: 0.75rem;
  text-transform: uppercase;
}

/* Total Stats */
.total-stats {
  background: linear-gradient(145deg, #161616, #1f1f1f);
  border: 2px solid #00ccff;
  border-radius: 20px;
  padding: 35px;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0, 204, 255, 0.2);
  max-width: 900px;
  margin: 50px auto;
}

.total-stats h2 {
  color: #00ccff;
  margin-bottom: 20px;
  font-size: 1.5rem;
}

.total-number {
  font-size: 5rem;
  font-weight: 900;
  color: #00ccff;
  text-shadow: 0 0 40px rgba(0, 204, 255, 0.6);
  margin: 20px 0;
}

.progress-bar {
  width: 100%;
  height: 8px;
  background: #1f1f1f;
  border-radius: 10px;
  overflow: hidden;
  margin: 20px 0;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #9fef00, #00ccff, #ff0000);
  width: 0;
  transition: width 2s ease;
  box-shadow: 0 0 10px rgba(0, 204, 255, 0.5);
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

@media (max-width: 768px) {
  .platform-grid {
    grid-template-columns: 1fr;
  }
  
  .platform-count {
    font-size: 3rem;
  }
  
  .total-number {
    font-size: 3.5rem;
  }
}
</style>

<div class="hero">
  <h2>THE PROFESSOR'S LAB</h2>
  
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

<!-- Platform Statistics Boxes -->
<div class="platform-grid">
  <div class="platform-box htb-box" id="htb-box">
    <div class="platform-icon">🎯</div>
    <div class="platform-name">HackTheBox</div>
    <div class="platform-count" id="htb-count">0</div>
    <div class="platform-label">Machines Pwned</div>
    <div class="platform-details">
      <div class="detail-item">
        <div class="detail-value" id="htb-easy">0</div>
        <div class="detail-label">Easy</div>
      </div>
      <div class="detail-item">
        <div class="detail-value" id="htb-medium">0</div>
        <div class="detail-label">Medium</div>
      </div>
      <div class="detail-item">
        <div class="detail-value" id="htb-hard">0</div>
        <div class="detail-label">Hard</div>
      </div>
    </div>
  </div>

  <div class="platform-box thm-box" id="thm-box">
    <div class="platform-icon">🔐</div>
    <div class="platform-name">TryHackMe</div>
    <div class="platform-count" id="thm-count">0</div>
    <div class="platform-label">Rooms Completed</div>
    <div class="platform-details">
      <div class="detail-item">
        <div class="detail-value" id="thm-easy">0</div>
        <div class="detail-label">Easy</div>
      </div>
      <div class="detail-item">
        <div class="detail-value" id="thm-medium">0</div>
        <div class="detail-label">Medium</div>
      </div>
      <div class="detail-item">
        <div class="detail-value" id="thm-hard">0</div>
        <div class="detail-label">Hard</div>
      </div>
    </div>
  </div>
</div>

<!-- Total Stats -->
<div class="total-stats">
  <h2>🏆 Total Writeups</h2>
  <div class="total-number" id="total-count">0</div>
  <div class="progress-bar">
    <div class="progress-fill" id="progress"></div>
  </div>
  <p style="color: #808080; font-size: 0.9rem; margin-top: 15px;">
    Keep pushing! Every machine teaches something new.
  </p>
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
  let htbEasy = 0, htbMedium = 0, htbHard = 0;
  let thmEasy = 0, thmMedium = 0, thmHard = 0;
  
  // Count posts by platform and difficulty
  posts.forEach(post => {
    const link = post.querySelector('.post-link');
    if (!link) return;
    
    const title = link.textContent.toLowerCase();
    const difficultyBadge = post.querySelector('.difficulty-badge');
    const difficulty = difficultyBadge ? difficultyBadge.textContent.toLowerCase() : 'easy';
    
    // Check if it's HTB
    if (title.includes('htb:') || title.includes('hackthebox')) {
      htbCount++;
      if (difficulty.includes('easy')) htbEasy++;
      else if (difficulty.includes('medium')) htbMedium++;
      else if (difficulty.includes('hard')) htbHard++;
    } 
    // Check if it's THM
    else if (title.includes('thm:') || title.includes('tryhackme')) {
      thmCount++;
      if (difficulty.includes('easy')) thmEasy++;
      else if (difficulty.includes('medium')) thmMedium++;
      else if (difficulty.includes('hard')) thmHard++;
    }
  });
  
  // Animate counter function
  function animateCounter(element, target) {
    let current = 0;
    const increment = Math.ceil(target / 25);
    const timer = setInterval(() => {
      current += increment;
      if (current >= target) {
        element.textContent = target;
        clearInterval(timer);
      } else {
        element.textContent = current;
      }
    }, 40);
  }
  
  // Update all displays
  const total = htbCount + thmCount;
  
  animateCounter(document.getElementById('htb-count'), htbCount);
  animateCounter(document.getElementById('thm-count'), thmCount);
  animateCounter(document.getElementById('total-count'), total);
  
  document.getElementById('htb-easy').textContent = htbEasy;
  document.getElementById('htb-medium').textContent = htbMedium;
  document.getElementById('htb-hard').textContent = htbHard;
  
  document.getElementById('thm-easy').textContent = thmEasy;
  document.getElementById('thm-medium').textContent = thmMedium;
  document.getElementById('thm-hard').textContent = thmHard;
  
  // Animate progress bar
  const progressBar = document.getElementById('progress');
  const progressPercent = Math.min((total / 50) * 100, 100);
  setTimeout(() => {
    progressBar.style.width = progressPercent + '%';
  }, 300);
  
  // Add hover color changes
  const htbBox = document.querySelector('.htb-box');
  const thmBox = document.querySelector('.thm-box');
  
  htbBox.addEventListener('mouseenter', function() {
    this.style.borderColor = '#9fef00';
  });
  
  htbBox.addEventListener('mouseleave', function() {
    this.style.borderColor = '#9fef00';
  });
  
  thmBox.addEventListener('mouseenter', function() {
    this.style.borderColor = '#ff0000';
  });
  
  thmBox.addEventListener('mouseleave', function() {
    this.style.borderColor = '#ff0000';
  });
});
</script>
