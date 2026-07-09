---
layout: page
title: Probabilistic models & experimental design
description: Gaussian and elliptical processes, and uncertainty-guided experimental design.
img: assets/img/research/prob_ph.png
importance: 1
area: probabilistic
areas: [probabilistic]
github: https://github.com/mariabankestad/gp-boundary-bias
related_publications: true
---

When an experiment or a simulation is expensive, the model's job is not just to predict. It also has to say how certain it is, and where to look next. That puts uncertainty at the center: a design policy is only as good as the uncertainty estimates it relies on. This project develops probabilistic models whose uncertainty is trustworthy enough to steer real decisions.

Gaussian processes are the default tool for this, and they have a surprising blind spot. Their posterior variance depends on the observed outputs only through the hyperparameters, so exploration is largely insensitive to what the measurements actually were. We address this by warping the input space with a learned, monotone transformation, which lets the acquisition policy stretch or compress regions in response to observed variability {% cite jarl2026observation %}.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/warped_gp.png" title="Input-warped Gaussian process" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A learned, monotone warp reshapes the input geometry so that the same design choice, seen in the warped space, responds to where the function actually varies.
</div>

In related work, we traced a second issue: stationary kernels inflate the posterior variance near the boundary of the domain, which quietly biases acquisition toward corners and edges regardless of the objective. We characterize this effect and give a diagnostic for measuring it {% cite bankestad2026boundary %}.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/gp_boundary_surface.png" title="Acquisition surfaces and argmax densities" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Acquisition surfaces for a single design (left) and the density of selected points over 10,000 designs (right), for three acquisition functions. The selections concentrate at the corners and edges of the domain, driven by kernel geometry rather than the objective.
</div>

On the modeling side, elliptical processes generalize Gaussian and Student's t processes into a single family with flexible heavy-tailed behavior, trained with variational inference {% cite bankestad2023variational %}. They are useful when the likelihood is non-Gaussian, or when getting the tails right actually matters.
