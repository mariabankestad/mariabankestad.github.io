---
layout: page
title: Accelerating fluid simulations
description: Equivariant graph neural networks as fast surrogates for computational fluid dynamics.
img: assets/img/sim_smoke.gif
importance: 2
area: geometry
areas: [geometry, differentiable-physics]
github: https://github.com/mariabankestad/SE2-GNN
related_publications: true
---

Simulating how fluids move is accurate but slow. A single high-resolution flow can take hours to compute, which rules it out of any setting where you need many simulations quickly: exploring designs, reacting in real time, or running an outer optimization loop. A machine-learned surrogate can be orders of magnitude faster, but a surrogate is only useful if it stays accurate on flows it was not trained on.

The way in is a symmetry. Rotate or translate a flow field and the underlying physics does not change, so a good surrogate should behave the same way. Most networks have to learn this invariance from data, wasting capacity and examples on something we already know. Instead, we build it in.

We designed a graph neural network that is equivariant to 2D rotations and translations and works directly on irregular, non-gridded domains. The key idea is to align the internal representations with the principal axis of the local flow, which lets the architecture stay flexible while still guaranteeing SE(2) equivariance {% cite bankestad2024flexible %}. Because the symmetry is built in rather than learned, the model needs less data and produces more stable long rollouts than non-equivariant baselines.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/sim_smoke.gif" title="Smoke simulation rollout" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Rollout predictions of our SE(2) equivariant GNN (middle), its non-equivariant counterpart (right), and the true simulation (left). The models have only seen the first two seconds of the simulation.
</div>
