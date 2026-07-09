---
layout: page
title: NMR shifts for crystalline solids
description: Equivariant atomistic models for predicting NMR chemical shifts in the solid state.
img: assets/img/properties.png
importance: 4
area: geometry
areas: [geometry, materials-chemistry]
---

Solid-state NMR is one of the sharpest probes we have for atomic structure in crystals. The catch is interpretation: to connect a measured spectrum back to a structure, you need accurate predictions of the chemical shifts a candidate structure would produce. First-principles calculations can deliver those shifts, but they are expensive, which makes them a natural target for a machine-learned surrogate.

The same argument that works for molecules applies here. A crystal is an arrangement of atoms in space, and its NMR shifts depend on the local geometry around each site in a way that respects the symmetries of that geometry. Equivariant atomistic models encode those symmetries directly, so they can learn accurate shift predictions from limited data rather than memorizing orientations.

This project studies how well modern equivariant architectures predict shifts in the solid state, and where geometry-aware models help most compared with established baselines. It is part of my supervision of master's theses at Uppsala University on machine learning for atomistic systems.

<div class="caption">
    Placeholder figure. A result figure will replace this as the work matures.
</div>
