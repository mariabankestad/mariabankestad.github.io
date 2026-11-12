---
layout: page
title: research
permalink: /projects/
description: My research builds machine learning that respects scientific structure (geometry, physics, and uncertainty) and applies it across chemistry, materials, energy, and the life sciences.
nav: true
nav_order: 3
---

<div class="research-intro">
  <p>All projects are shown below, starting with the methods work. You can also browse by the <strong>methods</strong> I develop or by the <strong>application areas</strong> they serve; each theme opens to a short overview and the papers behind it.</p>
</div>

<div class="research-toggle" role="tablist" aria-label="Browse research">
  <button role="tab" id="tab-all" aria-controls="panel-all" aria-selected="true" class="active">All projects</button>
  <button role="tab" id="tab-method" aria-controls="panel-method" aria-selected="false" tabindex="-1">By method</button>
  <button role="tab" id="tab-application" aria-controls="panel-application" aria-selected="false" tabindex="-1">By application</button>
</div>

<div class="projects">
<div class="area-group" id="panel-all" role="tabpanel" aria-labelledby="tab-all">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign all_projects = site.projects | sort: "importance" %}
    {% for project in all_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>

{% assign groups = "method,application" | split: "," %}
{% for group in groups %}
<div class="area-group" id="panel-{{ group }}" role="tabpanel" aria-labelledby="tab-{{ group }}" hidden>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign areas = site.data.research_areas | where: "group", group %}
    {% for area in areas %}
      <div class="col">
        <a class="area-tile" href="{{ area.slug | prepend: '/projects/' | append: '/' | relative_url }}">
          <div class="card">
            <img src="{{ area.image | relative_url }}" alt="" loading="lazy">
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
{% endfor %}

</div>

<script>
  (function () {
    var tabs = Array.prototype.slice.call(document.querySelectorAll('.research-toggle [role="tab"]'));
    function select(tab) {
      tabs.forEach(function (t) {
        var on = t === tab;
        t.classList.toggle("active", on);
        t.setAttribute("aria-selected", on);
        t.tabIndex = on ? 0 : -1;
        document.getElementById(t.getAttribute("aria-controls")).hidden = !on;
      });
    }
    tabs.forEach(function (t, i) {
      t.addEventListener("click", function () { select(t); });
      t.addEventListener("keydown", function (e) {
        var step = e.key === "ArrowRight" ? 1 : e.key === "ArrowLeft" ? -1 : 0;
        if (!step) return;
        var next = tabs[(i + step + tabs.length) % tabs.length];
        select(next); next.focus();
      });
    });
  })();
</script>
