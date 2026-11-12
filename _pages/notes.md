---
layout: page
title: notes
permalink: /notes/
nav: true
nav_order: 4
description: Occasional companion notes to my papers — the intuition and the backstory behind the results.
---


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
