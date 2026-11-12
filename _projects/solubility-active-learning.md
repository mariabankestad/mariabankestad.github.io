---
layout: page
title: Active learning for solubility
description: Choosing which experiments to run when predicting molecular solubility.
importance: 9
status: ongoing
area: probabilistic
areas: [probabilistic, materials-chemistry]
---

Solubility decides whether a compound can be formulated, processed or delivered, and it depends on the pairing of a molecule with a solvent. Measuring it across all the combinations that matter is slow, so the practical question is not only how to predict solubility, but which solvent to test next.

I built a Gaussian process model of solvent solubility that gives a probability for each candidate and ranks which solvent to test next.
