---
layout: page
title: Task-specific graph subsampling
description: Learning to reduce graphs for a downstream task using the Ising model.
img: assets/img/dog_sampling2.png
importance: 3
area: geometry
areas: [geometry]
github: https://github.com/mariabankestad/IsingOnGraphs
related_publications: true
---

Graphs are everywhere in science and engineering, and they are often too large to work with directly. The usual response is to reduce them, either by removing edges or by merging nodes. But classical reduction methods do this in the dark: they try to preserve the graph in general, with no idea of what the smaller graph will actually be used for. The result is often a graph that looks reasonable but throws away exactly the structure the downstream task needed.

We turn the problem around and let the task decide. The idea is to place an Ising model on the nodes or edges of the graph, where each element is kept or dropped according to a spin, and to learn the external magnetic field of that Ising model with a graph neural network {% cite bankestad2025ising %}. Because the whole thing is trained end-to-end against the downstream objective, the model learns to keep precisely the structure that objective depends on. A useful consequence of working through the Ising model is that the task loss does not even have to be differentiable.

The same recipe transfers across very different problems. We demonstrate it on image segmentation, explainability for graph classification, 3D shape sparsification, and computing sparse approximate matrix inverses.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dog_sampling2.png" title="Graph subsampling of a 3D shape" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Task-specific subsampling of a 3D shape graph via the learned Ising model.
</div>
