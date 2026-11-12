---
layout: page
title: Accelerating fluid simulations
description: Equivariant graph neural networks as fast surrogates for computational fluid dynamics.
img: assets/img/sim_smoke.gif
importance: 5
area: geometry
areas: [geometry, differentiable-physics, energy]
github: https://github.com/mariabankestad/SE2-GNN
related_publications: true
---

Simulating how fluids move is accurate but slow. A high-resolution flow can take hours to compute, which can make repeated simulation impractical, for example in design exploration or an outer optimization loop. A learned surrogate can be much faster, but it is only useful if it stays accurate on flows it was not trained on.

The way in is a symmetry. Rotate or translate a flow field and the physics does not change, so the surrogate's predictions should rotate and translate with it: the model should be equivariant. A standard network has to learn this from data. We build it in.

We designed a graph neural network that is equivariant to 2D rotations and translations and works directly on irregular, non-gridded domains. The key idea is to align the internal representations with the principal axis of the local flow, which keeps the architecture flexible while guaranteeing SE(2) equivariance {% cite bankestad2024flexible %}. In our experiments it needed less data and gave more stable long rollouts than its non-equivariant counterpart.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/sim_smoke.gif" title="Smoke simulation rollout" alt="Animated smoke simulation: ground truth, equivariant model and non-equivariant model side by side" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Rollout predictions of our SE(2) equivariant GNN (middle), its non-equivariant counterpart (right), and the true simulation (left). The models have only seen the first two seconds of the simulation.
</div>
