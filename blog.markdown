---
layout: page
title: Blog
permalink: /blog/
---

<div class="content-section">
  <div class="section-header">
    <h2>Latest Strategies</h2>
    <p class="section-subtitle">
      Actionable insights and proven tactics for indie authors
    </p>
  </div>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {% if post.description %}
          <p class="post-excerpt">{{ post.description }}</p>
        {% elsif post.excerpt %}
          <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
</div>
