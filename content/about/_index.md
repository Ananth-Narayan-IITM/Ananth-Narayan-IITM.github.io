---
title: "About"
description: "Researcher in Computational Fluid Dynamics at IIT Madras."
# photo: "/images/profile.jpg"   ← uncomment and add your photo to static/images/
---

## Hello

I'm Ananth Narayan, a researcher in Computational Fluid Dynamics at **IIT Madras**. My work lives at the intersection of numerical methods, fluid mechanics, and computational optimization — building tools that simulate physical flows and then make them better.

My primary research interest is **adjoint-based aerodynamic shape optimization**: using the mathematical elegance of the adjoint method to compute gradients of aerodynamic objective functions with respect to hundreds of design variables at the cost of only two flow solves. I implement this using DAFoam on top of OpenFOAM.

Alongside optimization, I run high-fidelity turbulence simulations (LES, RANS) with OpenFOAM, and study free-surface and multiphase flow phenomena using Basilisk's adaptive mesh refinement framework.

## Education

<div class="timeline">
  <div class="timeline-item">
    <div class="timeline-item__year">2022 — Present</div>
    <div>
      <div class="timeline-item__title">M.Tech / Ph.D (replace with your degree)</div>
      <div class="timeline-item__sub">IIT Madras · Department of Aerospace / Applied Mechanics</div>
    </div>
  </div>
  <div class="timeline-item">
    <div class="timeline-item__year">2018 — 2022</div>
    <div>
      <div class="timeline-item__title">B.Tech (replace with your degree and institute)</div>
      <div class="timeline-item__sub">Your undergraduate institution</div>
    </div>
  </div>
</div>

## Research Interests

- Turbulent flow simulation (LES, DNS, RANS)
- Adjoint-based PDE-constrained optimization
- Free-surface and multiphase flows (VOF, level set)
- Numerical methods: finite volume, pressure-velocity coupling
- High-performance computing for CFD

## What I use

Day-to-day I work with **OpenFOAM** for solver development and turbulence simulation, **DAFoam** for adjoint-based optimization, and **Basilisk** for interfacial flow problems. All of this runs on Linux HPC clusters with MPI parallelism.

For scripting, post-processing, and custom solvers I use **Python** (NumPy, SciPy, Matplotlib) and **C/C++**. Visualization is primarily in **ParaView**.
