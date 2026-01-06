---
layout: home
title: Mr. White | The Professor's Lab Notes
---

<div class="hero">
  <h2 style="font-weight: 300; letter-spacing: 2px;">THE PROFESSOR'S LAB</h2>
  
  <div style="margin: 40px 0; padding: 30px; background: var(--bg-secondary); border-left: 3px solid var(--accent-blue); border-radius: 6px;">
    <p style="font-size: 1.1rem; color: var(--text-secondary); margin: 0; line-height: 1.8;">
      "Say my name."
    </p>
    <p style="font-size: 1.1rem; color: var(--text-primary); margin: 15px 0 15px 30px; line-height: 1.8;">
      "Heisenberg."
    </p>
    <p style="font-size: 1.1rem; color: var(--accent-blue); margin: 0; font-weight: 500; line-height: 1.8;">
      "You're goddamn right."
    </p>
  </div>

  <div style="margin-top: 40px;">
    <p style="font-size: 1.05rem; line-height: 1.8; color: var(--text-primary); text-align: center; max-width: 800px; margin: 0 auto;">
      Penetration testing writeups documenting vulnerabilities, exploitation techniques, and privilege escalation paths. 
      Each report follows a systematic methodology from reconnaissance to post-exploitation.
    </p>
  </div>

  <div style="margin-top: 50px; display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 25px;">
    <div class="stat-card">
      <div class="stat-number">15+</div>
      <div class="stat-label">Machines Pwned</div>
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
  <h2 style="font-size: 1.6rem; font-weight: 600; color: var(--text-primary); margin-bottom: 30px; padding-bottom: 10px; border-bottom: 2px solid var(--border-primary); max-width: 1150px; margin-left: auto; margin-right: auto;">
    Latest Writeups
  </h2>
</div>

<style>
.stat-card {
  padding: 30px 20px;
  background: var(--bg-secondary);
  border-radius: 8px;
  border: 1px solid var(--border-primary);
  text-align: center;
  transition: all 0.3s ease;
}

.stat-card:hover {
  background: var(--bg-tertiary);
  border-color: var(--accent-blue);
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--accent-blue);
  margin-bottom: 10px;
}

.stat-label {
  font-size: 0.95rem;
  color: var(--text-secondary);
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* Enhanced Post Cards */
.post-list li {
  position: relative;
  overflow: hidden;
}

.post-list li::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(88, 166, 255, 0.1), transparent);
  transition: left 0.5s ease;
}

.post-list li:hover::before {
  left: 100%;
}

.post-link {
  position: relative;
  z-index: 1;
}

.post-list li:hover .post-link {
  color: var(--accent-blue-hover) !important;
}

/* Add difficulty badges */
.difficulty-badge {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin-left: 10px;
}

.difficulty-easy {
  background: rgba(63, 185, 80, 0.2);
  color: var(--accent-green);
  border: 1px solid var(--accent-green);
}

.difficulty-medium {
  background: rgba(255, 191, 0, 0.2);
  color: #ffbf00;
  border: 1px solid #ffbf00;
}

.difficulty-hard {
  background: rgba(248, 81, 73, 0.2);
  color: #f85149;
  border: 1px solid #f85149;
}

/* Reading time indicator */
.read-time {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  color: var(--text-tertiary);
  font-size: 0.85rem;
  margin-left: 15px;
}

.read-time::before {
  content: '📖';
}
</style>
