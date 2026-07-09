---
layout: page
title: Designing carbohydrate-binding proteins
description: Geometric deep learning and active learning to design proteins that modify cellulose.
img: assets/img/research/enzyme_ph.png
importance: 5
area: geometry
areas: [geometry, materials-chemistry, life-sciences]
---

Cellulose is the most abundant polymer on Earth, and modifying it enzymatically is a route to greener materials and processes. That modification depends on proteins that recognize and bind the carbohydrate in exactly the right way. Designing such proteins is a hard structural problem, because binding is governed by the three-dimensional fit between the protein pocket and the sugar, not by sequence alone.

This is a natural place for geometric deep learning. A binding event is a relationship between two 3D structures, so a model that takes both structures as input and respects their symmetries can reason about fit in a way that a sequence model cannot. Equivariant architectures are also sample-efficient, which matters here because experimental data on binding is limited.

Experiments are the real bottleneck: each candidate protein is expensive to make and test. So we frame the design loop as active learning, using the model's uncertainty to choose which candidates to synthesize, so that every round of experiments is as informative as possible. The project is a funded collaboration on AI-designed proteins for modifying cellulose, and it sits at the meeting point of geometry, active learning, and the life sciences.

<div class="caption">
    Placeholder figure. A result figure will replace this as the project matures.
</div>
