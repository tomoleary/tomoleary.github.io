---
title: "Research"
layout: single
sitemap: true
permalink: /research/
author_profile: true
toc: true
toc_label: "Research"
toc_icon: "gear"
---

Regardless of scale, in order to bridge the gap between observation and theory, modern science has come to heavily rely on computational means.
From simulating star formation to proton transport, from climate change and sea level rise to turbulence and combustion (not to mention turbulent combustion), or from structural design to the design of personalized treatment pathways in state-of-the-art medical practice, computer simulations are indispensable.
Through simulation, I strive to bring clarity and insight into such otherwise intractable problems.

In addition to discovering a new class of finite element methods, called [DPG* methods](https://arxiv.org/abs/1710.05223), and also classifying its dual category of finite element methods called [discrete least-squares methods (DLS methods)](https://doi.org/10.1016/j.cma.2017.08.043), I have written general and portable software for high-order and adaptive finite element methods and developed specific methods for structural, fluid, and wave mechanics problems.

## Numerical Methods

Much of my PhD research was spent studying discontinuous Petrov-Galerkin finite element methods (DPG methods) which have significant properties amenable to high-order and adaptive simulations.

### DLS Methods

From extensive research on DPG methods, the term discrete least-squares finite element method (DLS method) was coined.
The discrete system in DLS methods have a very specific algebraic structure which can be exploited to accelerate computation times or reduce the round-off error.

The following figure (left) depicts the condition number of two coefficient matrices (blue and red) often used in computation.
In green is a coefficient matrix which I discovered could also be used, but has a square root growth in its condition number, versus the other standards.
The benefits of this greatly reduced condition number are demonstrated (far right) with frequency domain acoustic wave equation experiments _near resonance_.

<figure>
  <img src="/assets/images/ResearchDLS2.png" alt="">
  <figcaption>Condition number growth of various stiffness matrices; notice the linear growth in green (left). A study in robustness and sensitivity to round-off error of frequency-domain acoustic wave equation near resonance (right) </figcaption>
</figure>

### DPG* Methods

DPG* methods are dual to DPG methods.
This new class of finite element method uses the same coefficient matrix as the associated DPG method but has a different load and involves a post-processing step to solve render the solution.
In the DLS theory, DPG methods can be identified with the least-squares problem corresponding to an overdetermined system of equations.
An analogous identification can be made with DPG* methods.
However, DPG* methods are associated with the least-squares problem corresponding to the _underdetermined_ systems of equations.

Currently, I am studying the properties of DPG* methods, including _a posteriori_ error estimation, superconvergence, and applications to special problems without uniqueness of solutions.

### Goal-oriented Methods

<img src="/assets/images/CodeCogsEqn.png" width="440px" alt="Brendan Keith" align="right" />

## Applications

### Solids

### Fluids

### Waves

## Software

I focus on many aspects of finite element analysis, and have developed, both in terms of software and the underlying mathematics, several finite element methods which are characterized by having:
- High-order convergence (heirarchical high-order discretizations for different element shapes and "energy" spaces).
- Proofs of numerical stability (inf-sup conditions satisfied for variational formulations).
- Adaptivity (so the meshes spatially refine in a particular area of interest).
- Desirable linear algebra properties to exploit in solvers.

Some highlights are shown next.

### hp2d/hp3D

<figure>
  <img src="/assets/images/ResearchShapeFunctions.png" alt="">
  <figcaption>Unified construction of high-order hierarchical discretizations of <em>H</em><sup>1</sup>, <em>H</em>(curl), <em>H</em>(div) and <em>L</em><sup>2</sup> by systematically projecting to faces and edges. </figcaption>
</figure>
Developed a unified and systematic approach to constructing arbitrary high-order conforming discretizations of the traditional Sobolev spaces lying in a differential de Rahm sequence (<em>H</em><sup>1</sup>, <em>H</em>(curl), <em>H</em>(div) and <em>L</em><sup>2</sup>) for each of the "standard" element shapes: tetrahedra,hexahedra, triangular prisms and pyramids. 
The code can be found [here](https://github.com/libESEAS/ESEAS).

### Camellia

<figure>
  <img src="/assets/images/ResearchElasticity.png" alt="">
  <figcaption>Linear elasticity in the L-shape domain solved with different DPG variational formulations, all converging, but displaying different refinement patterns (left). Sheathed hose composed of a thick inner layer of rubbber, and a very thin outer layer of steel (middle). It was solved using a coupled linear elasticity DPG method which is robust in the incompressible limit inside the rubber subdomain and computationally cheap in the steel layer (right). </figcaption>
</figure>

Disontinuous Petrov-Galerkin (DPG) methods are crafted to be stable for any linear well-posed variational formulation of a PDE.
We showed their applicability by solving the equations of linear elasticity with various variational formulations, some being fast, others being slower, but robust in the near-incompressible limit.
We also derived DPG methods that combine different formulations, as they are useful in physical problems like racing-engine hoses and biomedical devices.
Using DPG methods, we also successfully validated data from dynamic mechanical analysis (DMA) calibration experiments involving viscoelastic materials to within 5% of the quantity of interest.

<figure>
  <img src="/assets/images/ResearchDMAViscoelasticity.png" alt="">
  <figcaption>Experimental setup of DMA calibration experiments (left) which were then adaptively simulated using a DPG method (mid-right). By post-processing the central clamp force, the manufacturer's calibration model was validated to within 5% of experimental measurements (right). </figcaption>
</figure>

### ESEAS

<figure>
  <img src="/assets/images/ResearchDLS.png" alt="">
  <figcaption>Numerically stable FEMs posed as a discrete least-squares (DLS) problem that deals directly with rectangular matrices (left). Using DLS FEMs, conditioning of near-resonant acoustics was shown to grow as <em>O</em>(<em>h</em><sup>-1</sup>), and the solution was found to converge even when traditional methods started to diverge (right). </figcaption>
</figure>

As an outgrowth of DPG methods, we exploited not only that DPG methods have positive definite stiffness matrices, but that they are a product of the transpose of a known rectangular matrix times itself.
Thus, it can be posed as a discrete-least squares problem and solved with much better conditioning properties via QR-based solvers.
These are very suitable for ill-conditioned problems, like near-resonant acoustics.
