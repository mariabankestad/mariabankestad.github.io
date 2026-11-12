---
layout: about
title: about
permalink: /
subtitle: Machine learning for the physical sciences · Researcher at <a href='https://www.ri.se/en/person/maria-bankestad'>RISE Research Institutes of Sweden</a>

profile:
  align: right
  image: me.jpg
  image_circular: true # crops the image to make it circular
  alt: Maria Bånkestad
  more_info: >
    <a href="mailto:maria.bankestad@ri.se">maria.bankestad@ri.se</a>

news: true # includes a list of news items
selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

I develop machine learning methods for scientific problems, at the intersection of machine learning, physics and chemistry. I work with scientists and engineers to understand the underlying problem, and I build both new methods and the software needed to put them into practice.

My research includes equivariant neural networks, probabilistic modelling and differentiable simulation, with applications in chemistry, materials, energy and physics. The problems I enjoy most are those where the measurement, the physics or the mathematical structure changes how the machine learning problem should be posed.

I did my PhD at Uppsala University, supervised by [Thomas B. Schön](https://user.it.uu.se/~thosc112/index.html), with the thesis [*Structured models for scientific machine learning: from graphs to kernels*](http://urn.kb.se/resolve?urn=urn:nbn:se:uu:diva-546022). More of the work is on the [research page]({{ '/projects/' | relative_url }}).

<h2 class="home-section">recent work</h2>
<div class="projects home-highlights">
  <div class="row row-cols-1 row-cols-md-3 g-4">
    {% assign highlight_slugs = "ai-saxs,graph-subsampling,probabilistic-experimental-design" | split: "," %}
    {% for slug in highlight_slugs %}
      {% assign project = site.projects | where_exp: "p", "p.url contains slug" | first %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
</div>
