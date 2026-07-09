---
layout: page
title: Probabilistic models & experimental design
permalink: /projects/probabilistic/
description: Gaussian and elliptical processes, and uncertainty-guided experimental design.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/publication_preview/elliptical.png' | relative_url }}" alt="Probabilistic models and experimental design">

When an experiment or a simulation is expensive, a model has to do more than predict. It has to say how sure it is, and where to look next. That puts uncertainty at the center of the work, because a plan for the next experiment is only as good as the uncertainty it is built on. This theme develops probabilistic models whose uncertainty is trustworthy enough to steer real decisions.

Gaussian processes are the standard tool here, and they have a surprising blind spot: their posterior variance depends on the measurements only through the hyperparameters, so exploration barely reacts to what was actually observed. Warping the input space with a learned, monotone transformation fixes this, letting the acquisition policy stretch or compress regions in response to observed variability {% cite jarl2026observation %}. A second, subtler problem is geometric: stationary kernels inflate the variance near the boundary of the domain, which quietly pushes sampling toward corners and edges regardless of the objective. We characterize this effect and give a diagnostic for it {% cite bankestad2026boundary %}.

On the modeling side, elliptical processes generalize Gaussian and Student's t processes into one family with flexible heavy tails, trained by variational inference {% cite bankestad2023variational %}. They are useful whenever the likelihood is non-Gaussian or the tails genuinely matter.

These ideas are meant to be used. An ongoing project applies active learning to molecular solubility, choosing which measurements to run so that a useful model emerges from as few experiments as possible.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'probabilistic'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
