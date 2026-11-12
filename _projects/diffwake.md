---
layout: page
title: "DiffWake: differentiable wind farms"
description: A differentiable wind farm solver in JAX for layout optimization and calibration.
img: assets/img/research/diffwake_overview.png
importance: 6
area: differentiable-physics
areas: [differentiable-physics, energy]
github: https://github.com/mariabankestad/DiffWake
related_publications: true
---

A wind turbine slows the air behind it, and that slower, more turbulent wake reduces the power of turbines downstream. Predicting these wake losses is central to how wind farms are laid out and operated. Engineers have good physical wake models for this, but they were not written to be differentiated, which makes obtaining useful gradients difficult.

DiffWake is a general differentiable wind farm solver in JAX, and it includes the first differentiable implementation of the cumulative-curl wake model {% cite bankestad2025diffwake %}. Being differentiable lets us use gradients for two problems.

The first is layout optimization: where to place turbines to maximize power. In our benchmark, L-BFGS with DiffWake gradients converges on a layout about fifty times faster than a FLORIS and SciPy baseline. The second is calibration: parameters such as turbulence intensity have to be inferred from operational data, and DiffWake calibrates them against SCADA measurements by following the gradient.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/diffwake_overview.png" title="Wake field" alt="Simulated wake velocity field behind three wind turbines" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Wake velocity field behind three turbines, computed with DiffWake.
</div>
