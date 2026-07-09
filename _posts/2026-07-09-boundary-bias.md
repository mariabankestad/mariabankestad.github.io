---
layout: post
title: "Why our experimental design kept losing to Sobol"
date: 2026-07-09
description: Our sequential Bayesian experimental design kept losing to Sobol sequences and farthest-point sampling. The culprit turned out to be a geometric artifact in Gaussian processes, not a bug in our code.
tags: gaussian-processes experimental-design bayesian-optimization
related_publications: true
---

For a long time, one of our methods refused to work, and it failed in a humbling way.

We were doing sequential Bayesian experimental design: fit a Gaussian process surrogate, use an acquisition function to pick the most informative next experiment, measure, and repeat. In principle this should beat choosing points blindly. In practice it kept losing to methods that never look at the data at all: low-discrepancy Sobol sequences, farthest-point sampling, plain space-filling designs. Our careful, adaptive loop was being beaten by a quasi-random number generator.

That is the kind of result you don't quite believe. We spent a long time assuming it was a bug, a bad kernel, or a hyperparameter set wrong. It was none of those. The cause was geometric, and once we saw it, we saw it everywhere.

Here is the intuition. A stationary Gaussian process kernel says that two points are informative about each other when they are close. In the middle of the domain, a point has neighbors on all sides. Near an edge, half of those neighbors fall outside the domain and are never measured, so the model is genuinely less informed there and its posterior variance is inflated. The important part is that this inflation depends only on the shape of the domain, not on any data you collect. It also gets worse as the dimension grows, because in a high-dimensional box almost everything is near the boundary.

Now hand that inflated uncertainty to an acquisition function whose job is to chase uncertainty. Variance maximization goes straight for the most uncertain points, which sit in the corners, so it spends its budget stapling samples to the extremes of the space. Other acquisitions express the same pull more subtly: negative integrated posterior variance and expected predictive information gain do not run all the way to the corners, but they settle onto axis-aligned interior shells. Either way, the acquisition is being steered by the geometry of the box rather than by the objective you actually care about.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/gp_boundary_surface.png" title="Acquisition surfaces and argmax densities" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: acquisition surfaces for a single design. Right: where each method actually chooses to sample across ten thousand designs. The selections crowd onto edges and corners, with no objective function anywhere in sight.
</div>

Suddenly the Sobol result made sense. A space-filling sequence has no opinion about the boundary and simply covers the domain evenly. Our method had a strong opinion, and it was the wrong one. It kept re-confirming that the edges of the box are uncertain, which they are, instead of spending measurements on the function inside. Even coverage beats confident nonsense.

The practical lesson is short. If your sequential experimental design is quietly losing to space-filling baselines, do not assume you implemented it wrong. Look at where it puts its samples. If they pile up on the boundary, you are probably watching kernel geometry rather than task-specific uncertainty.

In the paper we make this precise and give a function-free diagnostic: a selection profile you can compute for any acquisition, any kernel, and any bounded domain, without reference to a test function, so you can see how much of an acquisition's behavior is geometry rather than signal {% cite bankestad2026boundary %}. If you run Bayesian optimization or active learning on a bounded space, it is worth a look.
