---
layout: page
title: AI for energy & fluids
permalink: /projects/energy/
description: Differentiable and learned models for wind energy and fluid flows.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/research/diffwake_overview.png' | relative_url }}" alt="AI for energy and fluids">

Energy systems and fluid flows are governed by physics we understand well, but simulating that physics accurately is expensive, and the standard solvers were not written to be differentiated. That rules out the two things I most want to do with them: optimize over them, and calibrate them against data. Both of my projects here remove that obstacle, either by making the physics differentiable or by replacing its slow parts with a learned surrogate.

Wind energy is the clearest case. Turbine wakes rob downstream turbines of power, and predicting them well is central to how a wind farm is laid out and run. DiffWake rebuilds this machinery in JAX, including the first differentiable cumulative-curl wake model, which makes layout optimization about fifty times faster and lets turbulence parameters be calibrated directly against operational data {% cite bankestad2025diffwake %}.

Fluid simulation more broadly is a natural target for learned surrogates. An equivariant graph neural network that respects the rotational and translational symmetry of a flow gives accurate, stable rollouts from limited data, and runs far faster than the simulation it stands in for {% cite bankestad2024flexible %}.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'energy'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
