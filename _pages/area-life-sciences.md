---
layout: page
title: AI for the life sciences
permalink: /projects/life-sciences/
description: Geometry and scattering for proteins and drug-delivery nanoparticles.
related_publications: true
nav: false
---

<img class="area-hero" src="{{ 'assets/img/research/lnp.png' | relative_url }}" alt="AI for the life sciences">

Biological structure is three-dimensional, and it is usually hard to observe directly. Whether the object is a protein pocket or the interior of a nanoparticle, the interesting behavior comes from a spatial arrangement we can only measure indirectly. The projects here bring geometry-aware and differentiable methods to that problem, from the same toolkit that runs through the rest of my work.

One thread is protein design. Enzymes that modify cellulose depend on how a protein recognizes and binds a carbohydrate, which is a question about the three-dimensional fit between two structures. This is a natural place for equivariant models, and because experimental validation is expensive, the design loop is framed as active learning. This is ongoing, funded work.

The other thread is reading structure out of measurements. Small-angle X-ray scattering probes the internal structure of lipid nanoparticles, the delivery systems behind nucleic-acid drugs, but recovering that structure from a scattering curve is an inverse problem with non-unique solutions. A differentiable, machine-learning-accelerated framework makes the fitting tractable and its uncertainty honest {% cite bankestad2026saxs %}.

<span class="area-projects-label">Projects in this area</span>
<div class="projects">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign area_projects = site.projects | where_exp: "p", "p.areas contains 'life-sciences'" | sort: "importance" %}
    {% for project in area_projects %}{% include projects.liquid %}{% endfor %}
  </div>
</div>
