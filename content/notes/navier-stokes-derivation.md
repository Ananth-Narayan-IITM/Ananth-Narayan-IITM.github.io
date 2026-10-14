---
title: "Navier-Stokes Equations from First Principles"
date: 2024-10-01
category: "Derivation"
description: "Reynolds transport theorem applied to momentum conservation, leading to the incompressible Navier-Stokes equations."
tags: ["fluid mechanics", "continuum mechanics", "incompressible flow"]
---

## Starting point: Reynolds Transport Theorem

For an arbitrary extensive property $B$ with intensive counterpart $\beta = dB/dm$, the Reynolds Transport Theorem (RTT) for a control volume (CV) moving with the fluid is:

$$\frac{DB}{Dt} = \frac{\partial}{\partial t}\int_{CV} \rho\beta \, dV + \oint_{CS} \rho\beta \, (\mathbf{v} \cdot \hat{n}) \, dA$$

For **linear momentum**, $B = m\mathbf{v}$ and $\beta = \mathbf{v}$. Newton's second law gives $\frac{D(m\mathbf{v})}{Dt} = \sum \mathbf{F}$, so:

$$\sum \mathbf{F} = \frac{\partial}{\partial t}\int_{CV} \rho\mathbf{v} \, dV + \oint_{CS} \rho\mathbf{v} \, (\mathbf{v} \cdot \hat{n}) \, dA$$

## Forces on the control volume

The forces split into body forces and surface forces:

$$\sum \mathbf{F} = \underbrace{\int_{CV} \rho \mathbf{g} \, dV}_{\text{body}} + \underbrace{\oint_{CS} \boldsymbol{\sigma} \cdot \hat{n} \, dA}_{\text{surface}}$$

The Cauchy stress tensor for a Newtonian fluid is:

$$\boldsymbol{\sigma} = -p\mathbf{I} + \mu\left(\nabla\mathbf{v} + (\nabla\mathbf{v})^T\right) - \frac{2}{3}\mu(\nabla \cdot \mathbf{v})\mathbf{I}$$

## Applying the divergence theorem

Converting the surface integrals to volume integrals via the divergence theorem and collecting terms:

$$\int_{CV}\left[\frac{\partial(\rho\mathbf{v})}{\partial t} + \nabla\cdot(\rho\mathbf{v}\otimes\mathbf{v})\right]dV = \int_{CV}\left[\rho\mathbf{g} + \nabla\cdot\boldsymbol{\sigma}\right]dV$$

Since this holds for **any** CV, the integrands must be equal:

$$\frac{\partial(\rho\mathbf{v})}{\partial t} + \nabla\cdot(\rho\mathbf{v}\otimes\mathbf{v}) = \rho\mathbf{g} - \nabla p + \nabla\cdot\left[\mu\left(\nabla\mathbf{v}+(\nabla\mathbf{v})^T\right)\right]$$

## Incompressible simplification

For **incompressible flow** ($\rho = \text{const}$, $\nabla\cdot\mathbf{v} = 0$):

$$\boxed{\rho\left(\frac{\partial \mathbf{v}}{\partial t} + \mathbf{v}\cdot\nabla\mathbf{v}\right) = -\nabla p + \mu\nabla^2\mathbf{v} + \rho\mathbf{g}}$$

paired with the **continuity equation**:

$$\nabla \cdot \mathbf{v} = 0$$

## Key observations

- The left side is the **material acceleration** $\rho D\mathbf{v}/Dt$ — inertial terms.
- The $\mathbf{v}\cdot\nabla\mathbf{v}$ term is **nonlinear** — the source of turbulence and rich dynamics.
- The viscous diffusion term $\mu\nabla^2\mathbf{v}$ smooths velocity gradients.
- Non-dimensionalizing gives the Reynolds number $Re = \rho UL/\mu$ — the ratio of inertial to viscous forces.

> **Personal note:** The key insight I kept forgetting early on is that RTT is just the Leibniz rule for differentiation under the integral sign, applied to a moving, deforming control volume. Once that clicked, the derivation felt inevitable.
