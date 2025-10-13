---
layout: default
title: "iGaming"
permalink: /igaming/
---

<h2>iGaming Analytics Case Study</h2>

<div style="margin-top: 20px;">
  {% for post in site.posts %}
    {% if post.categories contains 'igaming' %}
      <div style="margin-bottom: 24px; padding: 12px; border: 1px solid #eee; border-radius: 8px;">
        <h3 style="margin-bottom: 6px;">
          <a href="{{ post.url }}" style="text-decoration: none; color: #2176C7;">
            {{ post.title }}
          </a>
        </h3>
        <p style="color: #666; font-size: 0.9em;">
          {{ post.date | date: "%d %B %Y" }}
        </p>
        {% if post.excerpt %}
          <p style="margin-top: 8px;">{{ post.excerpt | strip_html | truncate: 200 }}</p>
        {% endif %}
      </div>
    {% endif %}
  {% endfor %}
</div>
