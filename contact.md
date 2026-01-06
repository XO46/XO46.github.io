---
layout: page
title: Contact
permalink: /contact/
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
  --accent-blue: #00ccff;
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
  padding-bottom: 0 !important;
}

.page-content h2,
.page-content h3 {
  font-family: 'Courier New', monospace !important;
  color: var(--retro-text) !important;
}

/* Subtitle Typing Effect */
.contact-subtitle {
  text-align: center;
  font-size: 1.1rem;
  color: var(--retro-text-dim);
  margin-bottom: 50px;
  font-family: 'Courier New', monospace;
  min-height: 30px;
}

.typing-cursor {
  display: inline-block;
  width: 3px;
  height: 1.1rem;
  background: var(--htb-green);
  margin-left: 3px;
  animation: blink 1s infinite;
  vertical-align: middle;
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

/* Contact Grid */
.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 25px;
  margin: 40px 0 60px 0;
}

/* Contact Cards with Hover Effects */
.contact-card {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  padding: 30px;
  position: relative;
  overflow: hidden;
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

.contact-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
  background: var(--retro-border);
  transition: all 0.6s ease;
}

.contact-card:hover {
  transform: translateY(-8px);
  border-color: var(--htb-green);
  box-shadow: 0 10px 30px rgba(159, 239, 0, 0.25);
}

.contact-card:hover::before {
  width: 5px;
  background: var(--htb-green);
  box-shadow: 0 0 15px var(--htb-green);
}

.contact-card:hover::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(159, 239, 0, 0.08) 0%, transparent 70%);
  animation: pulse 2s infinite;
}

.contact-icon {
  font-size: 2.5rem;
  margin-bottom: 15px;
  display: block;
  transition: all 0.5s ease;
}

.contact-card:hover .contact-icon {
  transform: scale(1.2) rotate(360deg);
}

.contact-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--htb-green);
  margin-bottom: 15px;
  font-family: 'Courier New', monospace;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.contact-detail {
  font-size: 1rem;
  color: var(--retro-text-dim);
  margin: 10px 0;
  font-family: 'Courier New', monospace;
  word-break: break-word;
}

.contact-detail a {
  color: var(--accent-blue);
  text-decoration: none;
  transition: all 0.3s ease;
  position: relative;
}

.contact-detail a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--htb-green);
  transition: width 0.3s ease;
}

.contact-detail a:hover {
  color: var(--htb-green);
}

.contact-detail a:hover::after {
  width: 100%;
}

/* Copy Button */
.copy-btn {
  background: transparent;
  border: 1px solid var(--retro-border);
  color: var(--retro-text-dim);
  padding: 6px 14px;
  font-size: 0.8rem;
  cursor: pointer;
  font-family: 'Courier New', monospace;
  margin-top: 12px;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.copy-btn:hover {
  background: var(--htb-green);
  color: var(--retro-bg);
  border-color: var(--htb-green);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(159, 239, 0, 0.3);
}

.copy-btn.copied {
  background: var(--htb-green);
  color: var(--retro-bg);
  border-color: var(--htb-green);
}

/* Status Indicator */
.status-box {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  border-left: 4px solid var(--htb-green);
  padding: 25px 30px;
  margin: 50px 0;
  position: relative;
  overflow: hidden;
}

.status-box::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, var(--htb-green), transparent);
}

.status-indicator {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-family: 'Courier New', monospace;
  color: var(--retro-text);
  font-size: 1.05rem;
  margin-bottom: 12px;
}

.status-dot {
  width: 12px;
  height: 12px;
  background: var(--htb-green);
  border-radius: 50%;
  animation: pulse-dot 2s infinite;
  box-shadow: 0 0 10px var(--htb-green);
}

@keyframes pulse-dot {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.3); opacity: 0.7; }
}

.status-text {
  color: var(--retro-text-dim);
  font-family: 'Courier New', monospace;
  font-size: 1rem;
  line-height: 1.6;
}

/* Disclaimer */
.disclaimer-box {
  background: var(--retro-surface);
  border: 1px solid var(--thm-red);
  padding: 20px 25px;
  margin-top: 50px;
  font-family: 'Courier New', monospace;
  position: relative;
}

.disclaimer-box::before {
  content: '⚠';
  position: absolute;
  top: -15px;
  left: 20px;
  background: var(--retro-bg);
  padding: 0 10px;
  font-size: 1.5rem;
  color: var(--thm-red);
}

.disclaimer-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--thm-red);
  margin-bottom: 10px;
  text-transform: uppercase;
  letter-spacing: 1.5px;
}

.disclaimer-text {
  color: var(--retro-text-dim);
  font-size: 0.95rem;
  line-height: 1.6;
}

/* Social Links Grid */
.social-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 15px;
  margin: 30px 0;
}

.social-btn {
  background: var(--retro-surface);
  border: 1px solid var(--retro-border);
  padding: 15px;
  text-align: center;
  text-decoration: none;
  color: var(--retro-text);
  font-family: 'Courier New', monospace;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}

.social-btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(159, 239, 0, 0.1);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.5s ease, height 0.5s ease;
}

.social-btn:hover::before {
  width: 300px;
  height: 300px;
}

.social-btn:hover {
  border-color: var(--htb-green);
  color: var(--htb-green);
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(159, 239, 0, 0.2);
}

.social-icon {
  font-size: 1.8rem;
  display: block;
  margin-bottom: 8px;
  position: relative;
  z-index: 1;
}

.social-name {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  position: relative;
  z-index: 1;
}

/* Response Time Indicator */
.response-time {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: rgba(159, 239, 0, 0.1);
  border: 1px solid var(--htb-green);
  padding: 8px 15px;
  border-radius: 3px;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  color: var(--htb-green);
  margin-top: 15px;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .page-content h1 {
    font-size: 2rem !important;
    letter-spacing: 4px !important;
  }
  
  .contact-grid {
    grid-template-columns: 1fr;
  }
  
  .social-grid {
    grid-template-columns: repeat(2, 1fr);
  }
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

.contact-card {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

.contact-card:nth-child(1) { animation-delay: 0.1s; }
.contact-card:nth-child(2) { animation-delay: 0.2s; }
.contact-card:nth-child(3) { animation-delay: 0.3s; }
.contact-card:nth-child(4) { animation-delay: 0.4s; }
</style>

<div class="contact-subtitle">
  <span id="typing-text"></span><span class="typing-cursor"></span>
</div>

<!-- Status Box -->
<div class="status-box">
  <div class="status-indicator">
    <span class="status-dot"></span>
    <strong>CURRENTLY AVAILABLE</strong>
  </div>
  <div class="status-text">
    Open to junior penetration testing roles, internships, and learning opportunities in offensive security.
    <div class="response-time">
      ⚡ Average response time: 24-48 hours
    </div>
  </div>
</div>

<!-- Contact Grid -->
<div class="contact-grid">
  
  <!-- Email Card 1 -->
  <div class="contact-card">
    <span class="contact-icon">📧</span>
    <div class="contact-title">Personal Email</div>
    <div class="contact-detail">
      <a href="mailto:chandur483@gmail.com">chandur483@gmail.com</a>
    </div>
    <button class="copy-btn" onclick="copyToClipboard('chandur483@gmail.com', this)">
      Copy Email
    </button>
  </div>
  
  <!-- Email Card 2 -->
  <div class="contact-card">
    <span class="contact-icon">🎓</span>
    <div class="contact-title">University Email</div>
    <div class="contact-detail">
      <a href="mailto:2100032482@kluniversity.in">2100032482@kluniversity.in</a>
    </div>
    <button class="copy-btn" onclick="copyToClipboard('2100032482@kluniversity.in', this)">
      Copy Email
    </button>
  </div>
  
  <!-- LinkedIn -->
  <div class="contact-card" onclick="window.open('https://www.linkedin.com/in/r-chandra-shekar-a620aa252', '_blank')">
    <span class="contact-icon">💼</span>
    <div class="contact-title">LinkedIn</div>
    <div class="contact-detail">
      <a href="https://www.linkedin.com/in/r-chandra-shekar-a620aa252" target="_blank">
        r-chandra-shekar
      </a>
    </div>
    <button class="copy-btn" onclick="event.stopPropagation(); copyToClipboard('https://www.linkedin.com/in/r-chandra-shekar-a620aa252', this)">
      Copy Link
    </button>
  </div>
  
  <!-- GitHub -->
  <div class="contact-card" onclick="window.open('https://github.com/xo46', '_blank')">
    <span class="contact-icon">💻</span>
    <div class="contact-title">GitHub</div>
    <div class="contact-detail">
      <a href="https://github.com/xo46" target="_blank">
        github.com/xo46
      </a>
    </div>
    <button class="copy-btn" onclick="event.stopPropagation(); copyToClipboard('https://github.com/xo46', this)">
      Copy Link
    </button>
  </div>

</div>

<!-- Additional Social Links -->
<h2 style="text-align: center; color: var(--retro-text); font-family: 'Courier New', monospace; letter-spacing: 3px; margin-top: 60px; margin-bottom: 30px;">
  > CONNECT WITH ME
</h2>

<div class="social-grid">
  <a href="https://tryhackme.com/p/xo46" target="_blank" class="social-btn">
    <span class="social-icon">🎯</span>
    <span class="social-name">TryHackMe</span>
  </a>
  
  <a href="https://app.hackthebox.com/profile/xo46" target="_blank" class="social-btn">
    <span class="social-icon">🟩</span>
    <span class="social-name">HackTheBox</span>
  </a>
  
  <a href="https://twitter.com/your_handle" target="_blank" class="social-btn">
    <span class="social-icon">🐦</span>
    <span class="social-name">Twitter/X</span>
  </a>
  
  <a href="https://discord.gg/your_server" target="_blank" class="social-btn">
    <span class="social-icon">💬</span>
    <span class="social-name">Discord</span>
  </a>
</div>

<!-- Disclaimer -->
<div class="disclaimer-box">
  <div class="disclaimer-title">⚠ Ethical Disclaimer</div>
  <div class="disclaimer-text">
    All content on this site is for <strong>educational purposes only</strong> and practiced exclusively on <strong>legal, controlled environments</strong>. I do not condone or engage in unauthorized access to systems or networks.
  </div>
</div>

<script>
// Typing Effect
const phrases = [
  "Let's connect and collaborate...",
  "Available for penetration testing opportunities...",
  "Open to security research discussions...",
  "Ready to learn and contribute..."
];
let phraseIndex = 0;
let charIndex = 0;
let isDeleting = false;
const typingSpeed = 100;
const deletingSpeed = 50;
const pauseTime = 2000;

function typeText() {
  const currentPhrase = phrases[phraseIndex];
  const typingElement = document.getElementById('typing-text');
  
  if (!isDeleting) {
    typingElement.textContent = currentPhrase.substring(0, charIndex + 1);
    charIndex++;
    
    if (charIndex === currentPhrase.length) {
      setTimeout(() => { isDeleting = true; }, pauseTime);
      setTimeout(typeText, pauseTime);
      return;
    }
  } else {
    typingElement.textContent = currentPhrase.substring(0, charIndex - 1);
    charIndex--;
    
    if (charIndex === 0) {
      isDeleting = false;
      phraseIndex = (phraseIndex + 1) % phrases.length;
    }
  }
  
  setTimeout(typeText, isDeleting ? deletingSpeed : typingSpeed);
}

// Start typing effect
document.addEventListener('DOMContentLoaded', function() {
  setTimeout(typeText, 500);
});

// Copy to Clipboard Function
function copyToClipboard(text, button) {
  navigator.clipboard.writeText(text).then(() => {
    const originalText = button.textContent;
    button.textContent = '✓ Copied!';
    button.classList.add('copied');
    
    setTimeout(() => {
      button.textContent = originalText;
      button.classList.remove('copied');
    }, 2000);
  }).catch(err => {
    console.error('Failed to copy:', err);
    button.textContent = '✗ Failed';
    setTimeout(() => {
      button.textContent = originalText;
    }, 2000);
  });
}
</script>
