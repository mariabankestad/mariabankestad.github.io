---
layout: page
title: Predicting molecular spectra and properties
description: Equivariant and pre-trained models for NMR chemical shifts and molecular property prediction.
img: assets/img/publication_preview/drawing_small.png
importance: 4
area: geometry
areas: [geometry, materials-chemistry]
github: https://github.com/mariabankestad/GeqShift
related_publications: true
---

I develop models that predict molecular properties and NMR chemical shifts from structure. Molecules are naturally graphs, but their behaviour depends on the full three-dimensional geometry, which transforms under rotations and reflections.

NMR is a good example of why this matters. Assigning a structure from an NMR spectrum is slow, expert work, and carbohydrates are among the hardest cases because of their structural diversity. GeqShift is an E(3) equivariant graph neural network that predicts carbohydrate NMR chemical shifts from 3D structure {% cite bankestad2024carbohydrate %}. It reduces the prediction error up to threefold compared with models that only see the 2D structure, and it holds up when training data is scarce.

Labelled molecular data is often scarce, so it helps to borrow information from related tasks. In earlier work we pre-trained a transformer on chemical reaction data and showed that the representation improves downstream property prediction on several MoleculeNet benchmarks {% cite broberg2022pretraining %}.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/model_overview.png" title="Model overview" alt="GeqShift model: molecular graph with 3D geometry, equivariant layers and per-atom shift predictions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
