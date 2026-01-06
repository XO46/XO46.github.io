---
layout: home
title: XO46 | Pentest Writeups
---

<style>
/* Your existing styles... */

/* IMPROVED: Post list styling */
.post-list {
  list-style: none;
  padding: 0;
}

.post-list li {
  margin-bottom: 30px;
  padding: 20px;
  background: rgba(0, 255, 0, 0.02);
  border-left: 3px solid #00ff00;
  border-radius: 6px;
  transition: all 0.2s ease;
}

.post-list li:hover {
  background: rgba(0, 255, 0, 0.04);
  transform: translateX(5px);
}

.post-link {
  font-size: 1.3rem !important;
  font-weight: 600;
  display: block;
  margin-bottom: 8px;
}

.post-meta {
  color: #888;
  font-size: 0.9rem;
}

.post-excerpt {
  margin-top: 10px;
  color: #aaa;
  font-size: 0.95rem;
  line-height: 1.6;
}
</style>

<!-- Your existing hero section -->

<h2>Latest Writeups</h2>

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
      </a>
      <div class="post-meta">
        {{ post.date | date: "%b %d, %Y" }}
        {% if post.difficulty %} • {{ post.difficulty }}{% endif %}
        {% if post.os %} • {{ post.os }}{% endif %}
      </div>
      {% if post.summary %}
        <div class="post-excerpt">{{ post.summary }}</div>
      {% endif %}
    </li>
  {% endfor %}
</ul>
