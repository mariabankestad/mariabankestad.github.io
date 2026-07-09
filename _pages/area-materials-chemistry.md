---
layout: page
title: AI for material design and chemistry
permalink: /projects/materials-chemistry/
description: Machine learning for molecules, materials, and the measurements that probe them.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/research/saxs_overview.png' | relative_url }}" alt="AI for material design and chemistry">

A large part of my work is aimed at chemistry and materials. The methods come from the other themes on this page, equivariant models, probabilistic methods, and differentiable physics, but here they are gathered around the science they serve: predicting properties, guiding experiments, designing proteins, and reading structure out of measurements. The projects below also appear under their method themes; this page collects them from the application side.

Two threads concern prediction from structure. For carbohydrates, an equivariant model predicts NMR chemical shifts far more accurately than structure-blind baselines {% cite bankestad2024carbohydrate %}, and ongoing work carries the same idea to NMR in crystalline solids. Both aim at the same practical goal: getting a property or a spectrum without a slow measurement or calculation.

A second thread is about measurements themselves. Small-angle X-ray scattering probes the internal structure of nanoparticles, and a differentiable, ML-accelerated framework makes that structure recoverable and its uncertainty honest {% cite bankestad2026saxs %}. The ongoing CoSiMa project extends this to soft materials studied at large-scale facilities.

The rest of the work is about deciding what to make and measure next. An active-learning project chooses which solubility experiments to run, and a funded collaboration designs proteins that modify cellulose, using geometry and active learning together.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'materials-chemistry'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
