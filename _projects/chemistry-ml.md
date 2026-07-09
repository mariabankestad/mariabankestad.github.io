---
layout: page
title: Predicting molecular spectra and properties
description: Equivariant and pre-trained models for NMR chemical shifts and molecular property prediction.
img: assets/img/publication_preview/drawing_small.png
importance: 1
area: geometry
areas: [geometry, materials-chemistry]
github: https://github.com/mariabankestad/GeqShift
related_publications: true
---

Much of chemistry comes down to a single question: given a molecule, what will it do? Predicting properties and spectra directly from structure could replace slow measurements and calculations, but molecules are awkward objects for a model. They are naturally graphs, yet their behavior depends on the full three-dimensional geometry, which transforms under rotations and reflections.

NMR spectroscopy is a good example of why this matters. Reading a molecular structure out of an NMR spectrum is slow, expert work, and carbohydrates are among the hardest cases because of their structural diversity. We built GeqShift, an E(3) equivariant graph neural network that predicts carbohydrate NMR chemical shifts directly from 3D structure {% cite bankestad2024carbohydrate %}. By respecting the geometry, it reduces the prediction error up to threefold compared with models that only see the flat 2D structure, and it stays robust even when training data is scarce.

A second difficulty is that labelled molecular data is often scarce, which makes it worth borrowing information from related tasks. In earlier work we pre-trained a transformer on chemical reaction data and showed that this representation improves downstream property prediction across several MoleculeNet benchmarks {% cite broberg2022pretraining %}.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/model_overview.png" title="Model overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
