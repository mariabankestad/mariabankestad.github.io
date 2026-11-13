---
layout: page
title: "AI-SAXS: structure from scattering"
description: Exploring which structures are consistent with an X-ray scattering measurement.
img: assets/img/research/lnp.png
importance: 2
area: differentiable-physics
areas: [differentiable-physics, materials-chemistry, life-sciences]
website: https://mariabankestad.github.io/aisaxs/
related_publications: true
---

Small-angle X-ray scattering (SAXS) shows nanoscale structure without taking the sample apart. But the measurement hides much of that structure: different structures can produce nearly the same curve. I focused the project on that ambiguity. Instead of looking for one best fit, I built models around the physical simulator that show which structures are compatible with a measurement, and what the curve can and cannot tell us.

### Lipid nanoparticles

Lipid nanoparticles deliver nucleic-acid drugs, and their internal structure affects how well they work. Our framework makes realistic SAXS analysis of these particles practical {% cite bankestad2026saxs %}. A neural surrogate replaces the expensive scattering computation, about four orders of magnitude faster, and a differentiable layer accounts for the spread of particle sizes. This makes it possible to fit from many starting points. On real MC3 lipid-nanoparticle data, near-identical fits come from clearly different structures, mainly through a trade-off between particle size and interior structure.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/saxs_workflow.png" title="AI-SAXS framework" alt="Workflow from particle simulation to neural surrogate, polydispersity integration and fitting" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Simulate scattering per particle, learn a neural surrogate, integrate over particle sizes, and fit experimental data with automatic differentiation.
</div>

<p class="project-links">
  <a class="btn-main" href="https://mariabankestad.github.io/aisaxs/lnp.html"><i class="fa-solid fa-play"></i> Try it</a>
  <a href="https://mariabankestad.github.io/aisaxs/lnp_saxs_walkthrough.html"><i class="fa-solid fa-book-open"></i> Walkthrough</a>
  <a href="https://github.com/mariabankestad/aisaxs-poly"><i class="fa-brands fa-github"></i> Code</a>
  <a href="https://doi.org/10.5281/zenodo.20338599"><i class="fa-solid fa-database"></i> Data</a>
</p>

### Cellulose

The second model uses flow matching to learn all the combinations of structural parameters that fit a curve, not a single answer. When we already know some parameters from other measurements, we can give them to the model as exact values or with an uncertainty, and the answer updates without retraining. The paper is under review.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/research/saxs_conditional.gif' | relative_url }}" alt="Animation of a toy example: a curve gives a distribution over size spread and separation, and added information changes it without retraining." loading="lazy">
    </div>
</div>
<div class="caption">
    A toy example: telling the model what we know about one parameter changes the distribution over the others, without retraining.
</div>

<p class="project-links">
  <a class="btn-main" href="https://mariabankestad.github.io/aisaxs/cellulose.html"><i class="fa-solid fa-play"></i> Try it</a>
  <a href="https://mariabankestad.github.io/aisaxs/model.html"><i class="fa-solid fa-book-open"></i> How it works</a>
  <a href="https://github.com/mariabankestad/aisaxs-sbi"><i class="fa-brands fa-github"></i> Code</a>
</p>
