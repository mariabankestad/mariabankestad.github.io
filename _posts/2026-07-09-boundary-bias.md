---
layout: post
title: "When experimental design loses to Sobol"
date: 2026-07-09
last_updated: 2026-11-12
description: Comparing Gaussian-process experimental design with space-filling baselines led us to investigate how kernel and domain geometry influence where we measure next.
tags: gaussian-processes experimental-design bayesian-optimization
related_publications: true
compact_references: true
---

In our experimental-design experiments, methods that chose measurements using a Gaussian process sometimes performed worse than Sobol sequences or farthest-point sampling. These space-filling methods spread measurements across the input range without using the measured outputs. I wanted to understand what the adaptive methods were choosing to measure.

Suppose we want to learn how a material property varies with temperature and composition. A Gaussian process (GP) estimates the property and its uncertainty from the measurements available. An acquisition function scores possible next measurements using that model. We measure, update the model and repeat.

### Why boundaries matter

With commonly used stationary kernels, nearby measurements inform each other. Inside the input domain, measurements can surround a point; near a boundary, part of that neighbourhood lies outside the allowed range. For the kernels and designs we studied, this produces higher uncertainty near the boundary.

That uncertainty is not necessarily wrong. But choosing the most uncertain point can spend measurements near the boundary when our goal is to improve predictions across the whole domain.

In standard GP regression with Gaussian noise, fixing the kernel settings and noise variance makes the posterior variance depend on measurement locations, not measured values. Acquisitions based only on that covariance can therefore favour particular regions without using any observed outputs.

In our box-domain experiments, variance maximisation favoured corners, while two other criteria favoured interior shells {% cite bankestad2026boundary %}.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/gp_boundary_surface.png" title="Acquisition scores and selection densities" alt="Scores and selection densities for three measurement-selection criteria, showing corner and interior-shell preferences" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: acquisition scores for one sampling design. Right: selected-point densities across 10,000 designs. Variance maximisation favours corners; negative integrated posterior variance and expected predictive information gain favour interior shells in these experiments.
</div>

### What we learned and changed

We developed a selection-profile diagnostic that shows where an acquisition tends to select points across a collection of designs, without choosing a test function {% cite bankestad2026boundary %}. It exposes a sampling preference; whether that preference helps depends on the task.

We then explored two adjustments. A geometric equaliser counters boundary bias in the acquisition scores. An input warp reshapes distances using the GP's current prediction, directing more measurements towards regions where the estimated function changes rapidly. The equaliser improved reconstruction in our experiments, with further gains from the warp {% cite jarl2026observation %}.

In related Bayesian optimisation work, we kept the predictive GP fixed and changed the spatial preferences of its exploration term. Alternative preferences often improved optimisation performance early in our experiments {% cite bankestad2026hidden %}.

These results show that sampling preferences matter, but do not establish that boundary bias explains every loss to Sobol. When an adaptive design underperforms, I now look at where it samples as well as its prediction errors.
