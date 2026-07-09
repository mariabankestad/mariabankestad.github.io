---
layout: page
title: Differentiable physics & scientific surrogates
permalink: /projects/differentiable-physics/
description: Differentiable simulators and neural surrogates for optimization and inverse problems.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/research/diffwake_overview.png' | relative_url }}" alt="Differentiable physics and scientific surrogates">

Many scientific problems already come with a physical model. The trouble is that the model is often too slow, or not differentiable, to sit inside a learning or optimization loop. This theme is about removing that obstacle: make the physics itself differentiable, or replace its expensive parts with neural surrogates, so that gradients flow from end to end. Once they do, hard search and calibration problems turn into gradient descent.

Wind energy is a clear example. Turbine wakes reduce the power of downstream turbines, and engineers model them well, but the standard models were not written to be differentiated. DiffWake rebuilds this machinery in JAX, including the first differentiable cumulative-curl wake model, which makes layout optimization about fifty times faster and lets turbulence parameters be calibrated directly against operational data {% cite bankestad2025diffwake %}.

The same approach reads structure out of measurements. In small-angle X-ray scattering, recovering a nanoparticle's internal structure from its scattering curve is an inverse problem with non-unique solutions and a slow forward model. A neural surrogate plus a differentiable pipeline makes large-scale fitting and honest identifiability analysis possible {% cite bankestad2026saxs %}. Ongoing work in the CoSiMa project extends this line to soft materials characterized at synchrotron beamlines.

The fluid surrogates developed under the geometry theme belong here too: an equivariant network that stands in for an expensive flow simulation is exactly this kind of fast, learned surrogate {% cite bankestad2024flexible %}.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'differentiable-physics'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
