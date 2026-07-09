---
layout: page
title: "CoSiMa: AI for soft materials"
description: Machine learning for characterizing soft materials from X-ray scattering data.
img: assets/img/research/cosima_ph.png
importance: 3
area: differentiable-physics
areas: [differentiable-physics, materials-chemistry]
---

Soft materials, from gels and emulsions to structured biological matter, get much of their behavior from structure on the nanometer scale. X-ray scattering, including the beamlines at large facilities such as ForMAX, is one of the best ways to see that structure. The difficulty is the same one that runs through much of my work: a scattering measurement encodes the structure only indirectly, and turning the measured signal back into a physical picture is an inverse problem with no single clean answer.

CoSiMa is where I develop machine learning to make that inversion practical for soft materials. The approach builds on the same differentiable-physics and neural-surrogate ideas as the [AI-SAXS]({{ '/projects/ai-saxs/' | relative_url }}) work: replace the expensive parts of the forward scattering model with fast neural surrogates, keep the pipeline differentiable so that fitting and identifiability analysis become tractable, and be explicit about what the data can and cannot determine.

This is ongoing work rather than a finished result. It is a substantial part of my current research, funded through the Vinnova CoSiMa project on AI for soft materials, and it connects the methods I care about to a stream of real experimental data. Publications will follow as the project matures.

<div class="caption">
    Placeholder illustration. A result figure will replace this as the work is published.
</div>
