---
layout: page
title: "AI-SAXS: structure from scattering"
description: A differentiable, ML-accelerated framework for SAXS analysis of nanoparticles.
img: assets/img/research/lnp.png
importance: 2
area: differentiable-physics
areas: [differentiable-physics, materials-chemistry]
github: https://github.com/mariabankestad/aisaxs
website: https://mariabankestad.github.io/aisaxs/
walkthrough: https://mariabankestad.github.io/aisaxs/lnp_saxs_walkthrough.html
related_publications: true
---

Small-angle X-ray scattering (SAXS) lets us look inside nanoparticles without taking them apart. It is a key technique for the lipid nanoparticles that deliver nucleic-acid drugs, where the internal structure controls how well the particle works. But a scattering curve does not hand you a structure. Recovering the internal arrangement and the spread of particle sizes is an inverse problem, and different structures can produce almost the same curve. Realistic forward models are also slow, which makes systematic exploration impractical.

We built a differentiable, machine-learning-accelerated framework for SAXS analysis of heterogeneous, polydisperse nanoparticles {% cite bankestad2026saxs %}. Two ideas do the heavy lifting. First, a neural surrogate replaces the expensive per-particle scattering computation, cutting its cost by four orders of magnitude. Second, a differentiable integration layer sums over the distribution of particle sizes, so the whole pipeline, from structural parameters to predicted curve, is differentiable end to end.

Differentiability is what makes the analysis honest. We can run large-scale multi-start fitting to escape local optima, and, just as importantly, analyze which structural parameters are actually identifiable from the data and which are traded off against each other. On real MC3 lipid-nanoparticle data, the framework shows that near-identical fits can come from genuinely different structures, a caution that matters whenever SAXS is used to draw structural conclusions.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/saxs_workflow.png" title="AI-SAXS framework" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The framework: simulate scattering per particle, learn a neural surrogate, integrate over polydispersity, and use automatic differentiation to fit experimental data.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/saxs_accuracy.png" title="Surrogate accuracy" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The neural surrogate reproduces the physics-based SAXS curves closely across the relevant range, which is what makes the fast, differentiable fitting reliable.
</div>
