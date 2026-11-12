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

While working on experimental design, we found that Gaussian-process methods sometimes struggled to beat Sobol sampling and other simple space-filling designs. These methods use the model to choose the next measurement. I wanted to understand where they were sampling and why the model's guidance was not helping.

One issue I noticed was the preference for boundaries. In our box-domain experiments, some acquisition functions—the rules that choose the next measurement—favoured corners, while others concentrated on interior shells. These patterns arose from the model and domain geometry without using observed function values {% cite bankestad2026boundary %}.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/gp_boundary_surface.png" title="Acquisition scores and selection densities" alt="Three acquisition criteria showing corner and interior-shell sampling preferences" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Acquisition scores for one design (left) and selected-point densities across 10,000 designs (right). Variance maximisation favours corners; the other two criteria favour interior shells in these experiments.
</div>

What interested me was that we could study these preferences separately from the function we wanted to learn. We developed a diagnostic to show where an acquisition tends to select points across sampling designs, without choosing a test function.

I also wanted to change the sampling behaviour. We developed methods to counter that boundary preference and make sampling respond to where the estimated function changes rapidly {% cite jarl2026observation %}. We explored alternative spatial preferences in Bayesian optimisation too, while keeping the predictive model fixed {% cite bankestad2026hidden %}.

I still compare adaptive methods with simple space-filling baselines. When they perform worse, I look at where they sample as well as their prediction errors.
