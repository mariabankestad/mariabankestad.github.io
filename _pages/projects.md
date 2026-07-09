---
layout: page
title: research
permalink: /projects/
description: My research builds machine learning that respects scientific structure (geometry, physics, and uncertainty) and applies it across chemistry, materials, energy, and the life sciences.
nav: true
nav_order: 3
---

<div class="research-intro">
  <p>My work falls into a few connected themes. Browse them by the <strong>methods</strong> I develop or by the <strong>application areas</strong> they serve; the same projects appear under whichever view fits. Each theme opens to a short overview and the papers behind it.</p>
</div>

<div class="research-toggle" role="tablist">
  <button data-group="method" class="active">By method</button>
  <button data-group="application">By application</button>
</div>

<div class="projects">

<div class="area-group" data-group="method">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign method_areas = site.data.research_areas | where: "group", "method" %}
    {% for area in method_areas %}
      <div class="col">
        <a class="area-tile" href="{{ area.slug | prepend: '/projects/' | append: '/' | relative_url }}">
          <div class="card">
            <img src="{{ area.image | relative_url }}" alt="{{ area.name }}" loading="lazy">
            <div class="tile-body">
              <h2>{{ area.name }}</h2>
              <p>{{ area.teaser }}</p>
            </div>
          </div>
        </a>
      </div>
    {% endfor %}
  </div>
</div>

<div class="area-group" data-group="application" hidden>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign app_areas = site.data.research_areas | where: "group", "application" %}
    {% for area in app_areas %}
      <div class="col">
        <a class="area-tile" href="{{ area.slug | prepend: '/projects/' | append: '/' | relative_url }}">
          <div class="card">
            <img src="{{ area.image | relative_url }}" alt="{{ area.name }}" loading="lazy">
            <div class="tile-body">
              <h2>{{ area.name }}</h2>
              <p>{{ area.teaser }}</p>
            </div>
          </div>
        </a>
      </div>
    {% endfor %}
  </div>
</div>

</div>

<script>
  (function () {
    var buttons = document.querySelectorAll(".research-toggle button");
    var groups = document.querySelectorAll(".area-group");
    buttons.forEach(function (b) {
      b.addEventListener("click", function () {
        buttons.forEach(function (x) { x.classList.toggle("active", x === b); });
        groups.forEach(function (g) { g.hidden = g.dataset.group !== b.dataset.group; });
      });
    });
  })();
</script>
