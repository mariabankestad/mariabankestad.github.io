---
layout: page
title: Geometry, symmetry & graphs
permalink: /projects/geometry/
description: Building symmetry and structure into models for molecules, materials, and simulation.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/model_overview.png' | relative_url }}" alt="Geometry, symmetry and graphs">

Scientific data usually comes with structure we already understand. A molecule has the same energy however you rotate it. A fluid behaves the same wherever you place the origin. A graph does not care in what order you happen to list its nodes. A model that has to rediscover these facts from data wastes capacity and examples on something we could simply tell it. The theme running through this work is to build that structure into the model instead, mainly through equivariant graph neural networks, so the symmetry holds by construction and the model learns more from less data.

In chemistry this pays off directly. Predicting NMR chemical shifts for carbohydrates is a hard, geometry-dependent problem, and an E(3) equivariant network cuts the error up to threefold over models that only see the flat 2D structure {% cite bankestad2024carbohydrate %}. When labelled data is scarce, a related idea helps: pre-training a transformer on reaction data gives a representation that transfers to downstream property prediction {% cite broberg2022pretraining %}. The same geometric thinking extends to crystalline solids, where I supervise ongoing work on equivariant models for solid-state NMR.

The physics side looks different but uses the same principle. A fluid surrogate that is equivariant to rotations and translations gives more accurate, more stable rollouts than a plain network, and needs less training data to get there {% cite bankestad2024flexible %}.

Graphs bring their own structure. Rather than reducing a large graph in the dark, we learn to keep exactly the parts a downstream task needs, by placing an Ising model on the graph and learning its field with a neural network {% cite bankestad2025ising %}. The same geometric, structure-aware view also drives ongoing work on designing proteins that bind and modify cellulose.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'geometry'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
