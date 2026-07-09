---
layout: page
title: notes
permalink: /notes/
nav: true
nav_order: 4
description: Occasional companion notes to my papers — the intuition and the backstory behind the results.
---

<style>
  .notes-list { margin-top: 1rem; }
  .note-item { padding: 1.1rem 0; border-bottom: 1px solid var(--global-divider-color); }
  .note-item:first-child { padding-top: 0; }
  .note-item h2 { font-size: 1.3rem; margin: 0 0 0.3rem; }
  .note-item h2 a { text-decoration: none; }
  .note-item .note-meta { font-size: 0.85rem; color: var(--global-text-color-light); margin: 0 0 0.5rem; text-transform: uppercase; letter-spacing: 0.03em; }
  .note-item .note-desc { margin: 0; color: var(--global-text-color-light); }
</style>

<div class="notes-list">
{% assign notes = site.posts | sort: "date" | reverse %}
{% for post in notes %}
  <article class="note-item">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="note-meta">{{ post.date | date: "%B %-d, %Y" }}</p>
    <p class="note-desc">{{ post.description }}</p>
  </article>
{% endfor %}
</div>
