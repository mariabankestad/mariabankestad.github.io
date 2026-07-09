---
layout: page
title: Probabilistic models & experimental design
description: Gaussian and elliptical processes, and uncertainty-guided experimental design.
img: assets/img/research/prob_ph.png
importance: 1
area: probabilistic
areas: [probabilistic]
related_publications: true
---

When an experiment or a simulation is expensive, the model's job is not just to predict. It also has to say how certain it is, and where to look next. That puts uncertainty at the center: a design policy is only as good as the uncertainty estimates it relies on. This project develops probabilistic models whose uncertainty is trustworthy enough to steer real decisions.

Gaussian processes are the default tool for this, and they have a surprising blind spot. Their posterior variance depends on the observed outputs only through the hyperparameters, so exploration is largely insensitive to what the measurements actually were. We address this by warping the input space with a learned, monotone transformation, which lets the acquisition policy stretch or compress regions in response to observed variability {% cite jarl2026observation %}. In related work, we traced a second issue: stationary kernels inflate the posterior variance near the boundary of the domain, which quietly biases acquisition toward corners and edges regardless of the objective. We characterize this effect and give a diagnostic for measuring it {% cite bankestad2026boundary %}.

On the modeling side, elliptical processes generalize Gaussian and Student's t processes into a single family with flexible heavy-tailed behavior, trained with variational inference {% cite bankestad2023variational %}. They are useful when the likelihood is non-Gaussian, or when getting the tails right actually matters.
