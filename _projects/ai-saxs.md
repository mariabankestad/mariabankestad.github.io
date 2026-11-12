---
layout: page
title: "AI-SAXS: structure from scattering"
description: Exploring which structures are consistent with an X-ray scattering measurement.
img: assets/img/research/lnp.png
importance: 2
area: differentiable-physics
areas: [differentiable-physics, materials-chemistry, life-sciences]
website: https://mariabankestad.github.io/aisaxs/
walkthrough: https://mariabankestad.github.io/aisaxs/lnp_saxs_walkthrough.html
related_publications: true
---

Small-angle X-ray scattering (SAXS) lets us look inside nanoparticles without taking them apart. It is a key technique for the lipid nanoparticles that deliver nucleic-acid drugs, where the internal structure affects how well the particle works. We want to learn about the particle's structure from the scattering curve, but the measurement hides much of it: different structures can produce nearly the same curve.

I focused the project on that ambiguity. Instead of looking for one best fit, I built the models around the physical simulator, so that we can investigate which structures are compatible with a measurement.

The first model is a differentiable, machine-learning-accelerated framework for SAXS analysis of heterogeneous, polydisperse nanoparticles {% cite bankestad2026saxs %}. A neural surrogate replaces the expensive per-particle scattering computation, cutting its cost by four orders of magnitude, and a differentiable layer integrates over the distribution of particle sizes. This makes it practical to fit from many starting points and to examine alternative parameter solutions. On real MC3 lipid-nanoparticle data, near-identical fits come from clearly different structures, mainly through a trade-off between the size distribution and the interior structure. You can [try it in the browser](https://mariabankestad.github.io/aisaxs/lnp.html); the [code](https://github.com/mariabankestad/aisaxs-poly) and [data](https://doi.org/10.5281/zenodo.20338599) are open.

The second model, applied to cellulose, uses flow matching for amortized inference. It learns an approximation to the joint posterior over the structural parameters, that is, the combinations of parameters compatible with the measurement and the model, so it keeps several plausible explanations instead of reporting a single fit, and it shows how the conclusions change when more is known about a sample, for example when some parameters are fixed by other measurements. A new question needs no retraining. The paper is under review; you can [try the model](https://mariabankestad.github.io/aisaxs/cellulose.html), read [how it works](https://mariabankestad.github.io/aisaxs/model.html) and see the [code](https://github.com/mariabankestad/aisaxs-sbi).

To make these results usable outside our group, I also built visualisations and a step-by-step walkthrough of the analysis.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/saxs_workflow.png" title="AI-SAXS framework" alt="Workflow from particle simulation to neural surrogate, polydispersity integration and fitting" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The framework: simulate scattering per particle, learn a neural surrogate, integrate over polydispersity, and use automatic differentiation to fit experimental data.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/saxs_accuracy.png" title="Surrogate accuracy" alt="Surrogate-predicted SAXS curves overlaid on physics-based curves" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The neural surrogate reproduces the physics-based SAXS curves closely across the relevant range, accurately enough to use in fitting.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/research/saxs_conditional.gif' | relative_url }}" alt="Animation of a toy example: a curve gives a posterior over size spread and separation, and added information changes that posterior without retraining." loading="lazy">
    </div>
</div>
<div class="caption">
    A toy example of the second model: a scattering curve gives a distribution over two structural parameters, and telling the model more about one parameter changes the distribution without retraining.
</div>
