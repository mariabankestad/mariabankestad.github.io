---
layout: page
title: Active learning for solubility
description: Choosing which experiments to run when predicting molecular solubility.
img: assets/img/research/solubility_ph.png
importance: 2
area: probabilistic
areas: [probabilistic, materials-chemistry]
---

Solubility decides whether a compound can be formulated, processed, or delivered, and it depends on the pairing of a molecule with a solvent under specific conditions. Measuring it across the many combinations that matter is slow and expensive. The practical question is therefore not only how to predict solubility, but which measurements to make so that a useful model emerges from as few experiments as possible.

This is active learning. A probabilistic model ranks the candidate experiments by how much each is expected to reduce uncertainty, and the most informative one is run next. Done well, this can reach a good model with a fraction of the measurements that a fixed screening campaign would need.

A recurring theme in the project is honesty about data. Solubility datasets are noisy and uneven, and an active-learning loop is only as trustworthy as the model's confidence. So a lot of the work is in calibration and data quality, making sure the uncertainty that drives the next experiment can actually be believed.

<div class="caption">
    Placeholder figure. A result figure will replace this as the project matures.
</div>
