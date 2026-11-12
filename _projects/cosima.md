---
layout: page
title: "CoSiMa: AI for soft materials"
description: Machine learning for characterizing soft materials from X-ray scattering data.
importance: 7
status: ongoing
area: differentiable-physics
areas: [differentiable-physics, materials-chemistry]
---

Soft materials, from gels and emulsions to structured biological matter, get much of their behavior from structure on the nanometer scale. X-ray scattering, for example at the ForMAX beamline at MAX IV, is one of the best ways to see that structure. The difficulty is the same one that runs through much of my work: a scattering measurement encodes the structure only indirectly, and turning the measured signal back into a physical picture is an inverse problem with no single clean answer.

CoSiMa is where I develop machine learning to make that inversion practical for soft materials. The approach builds on the same differentiable-physics and neural-surrogate ideas as the [AI-SAXS]({{ '/projects/ai-saxs/' | relative_url }}) work: replace the expensive parts of the forward scattering model with fast neural surrogates, keep the pipeline differentiable so that fitting and identifiability analysis become tractable, and make clear what the data can and cannot determine.

I lead the AI modelling in CoSiMa, a Vinnova project on AI for the digital development of soft materials. This is ongoing work.
