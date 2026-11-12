---
layout: page
title: Probabilistic models & experimental design
description: Addressing boundary bias in Bayesian experimental design and optimization.
img: assets/img/research/warped_gp.png
importance: 3
area: probabilistic
areas: [probabilistic]
github: https://github.com/mariabankestad/gp-boundary-bias
related_publications: true
---

When an experiment or a simulation is expensive, the model has to do more than predict: it also has to say how certain it is, and where to measure next. Gaussian processes are the standard tool for this. Working with them on real active-learning problems, I kept seeing that most acquisition methods spend too many measurements at the edges of the domain. Instead of accepting that as something to live with, we traced where it comes from and corrected it.

**Where the boundary bias comes from.** A stationary kernel lets nearby points inform each other. Near the edge of a bounded domain, part of that neighbourhood lies outside, so the posterior variance is inflated there, whatever values have been observed. Variance maximization therefore picks the corners, while the two other criteria we studied (integrated posterior variance and expected predictive information gain) settle on interior shells aligned with the axes. We characterize this effect and give a function-free diagnostic for any acquisition, kernel and bounded domain {% cite bankestad2026boundary %}.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/gp_boundary_surface.png" title="Acquisition surfaces and argmax densities" alt="Acquisition surfaces and densities of selected points for three acquisition functions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Acquisition surfaces for a single design (left) and the density of selected points over 10,000 designs (right), for three acquisition functions. Variance maximization concentrates at the corners; the other two settle on interior shells. No objective function is involved.
</div>

**Adapting to what is measured.** With a fixed kernel, the posterior variance of a Gaussian process depends only on where samples are taken, not on the values measured. We derive a reconstruction-driven design density and use the posterior mean to build a training-free warp of the input space, which places more measurements where the function varies rapidly, together with a geometric equalizer for the boundary bias {% cite jarl2026observation %}. Across sixteen synthetic and two real-data benchmarks, including photoluminescence maps of solar cells, the equalizer improves function reconstruction and the warp adds further gains, so the active-learning loop learns about the material faster.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/research/warped_gp.png" title="Warped input space for experimental design" alt="Input space warped by the posterior mean, with measurements concentrated where the function varies" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A warp built from the posterior mean reshapes the input geometry, so that measurements concentrate where the function actually varies.
</div>

**Controlling exploration in Bayesian optimization.** The same spatial preference affects Bayesian optimization. Keeping the surrogate fixed, we control the spatial preference of the exploration term with weight fields, amortized with neural surrogates. On benchmark functions and stochastic robot-pushing tasks, alternative exploration principles often lower regret, especially early in the optimization {% cite bankestad2026hidden %}.

**Beyond Gaussian processes.** Variational elliptical processes form a broader family of processes that includes Gaussian and Student's t processes, with flexible heavy tails in the process model itself, trained with variational inference {% cite bankestad2023variational %}. They are useful when the data has heavier tails than a Gaussian allows.
