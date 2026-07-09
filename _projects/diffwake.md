---
layout: page
title: "DiffWake: differentiable wind farms"
description: A differentiable wind farm solver in JAX for layout optimization and calibration.
img: assets/img/research/diffwake_overview.png
importance: 1
area: differentiable-physics
areas: [differentiable-physics, energy]
github: https://github.com/mariabankestad/DiffWake
related_publications: true
---

A wind turbine slows the air behind it, and that slower, more turbulent wake reduces the power of any turbine downstream. Predicting and managing these wake losses is central to how wind farms are laid out and operated. Engineers have good physical wake models for this, but they were not written to be differentiated, which shuts them out of gradient-based optimization and calibration.

DiffWake rebuilds this machinery so that gradients flow through it. It is a general differentiable wind farm solver in JAX, and it includes the first differentiable implementation of the cumulative-curl wake model {% cite bankestad2025diffwake %}. Once the simulation is differentiable, two hard problems turn into gradient descent.

The first is layout optimization: where to place turbines to maximize power. With gradients, L-BFGS converges on a layout about fifty times faster than a FLORIS and SciPy baseline. The second is calibration: the models have parameters, such as turbulence intensity, that must be inferred from operational data. DiffWake makes it possible to calibrate these directly against real SCADA measurements by following the gradient.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/diffwake_overview.png" title="Wake field" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Wake velocity field behind three turbines. Because the solver is differentiable, gradients flow through this simulation for optimization and calibration.
</div>
