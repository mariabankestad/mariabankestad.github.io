---
layout: page
title: Task-specific graph subsampling
description: Using the Ising model to learn which subgraphs a task needs.
img: assets/img/dog_sampling2.png
importance: 1
area: geometry
areas: [geometry]
github: https://github.com/mariabankestad/IsingOnGraphs
related_publications: true
---

Graphs in science are often too large to work with directly, so they get reduced, by removing edges or merging nodes. Most reduction methods aim to preserve general properties of the graph rather than what a particular downstream task needs. I wanted a model that learns which parts of a graph to keep for a given task, where the decision for one node depends on what is chosen for the others.

An Ising model provides a way to represent those dependencies. Each node or edge gets a spin that decides whether it is kept or dropped, and a graph neural network learns the external field of the Ising model {% cite bankestad2025ising %}. Training samples keep-or-drop configurations and needs no gradients through the task loss, so the task objective does not even have to be differentiable.

We evaluated the model on image segmentation, explaining graph classifiers, simplifying 3D shapes and computing sparse approximate matrix inverses. In each case it learns which subgraphs are useful for the task.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dog_sampling2.png" title="Graph subsampling of a 3D shape" alt="A 3D dog shape reduced to the nodes selected by the learned Ising model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Task-specific subsampling of a 3D shape graph with the learned Ising model.
</div>
