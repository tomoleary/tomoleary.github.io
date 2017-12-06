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
The discrete systems in DLS methods have a very specific algebraic structure which can be exploited to accelerate computation times or reduce the round-off error.

<figure>
  <img src="/assets/images/ResearchDLS2.png" alt="">
  <figcaption>(Left) Condition number growth of various stiffness matrices. Notice the <em>O</em>(<em>h</em><sup>-1</sup>) growth in green. This is comes reformulating the assembly algorithm, <em>not</em> from a new preconditioner. (Right) A study in robustness and sensitivity to round-off error of frequency-domain acoustic wave equation <em>near resonance</em>. Here, the DLS solutions converge while the others diverge. </figcaption>
</figure>

###### Keith, B., Petrides, S., Fuentes, F., and Demkowicz, L. (2017). Discrete least-squares finite element methods. _Comput. Methods Appl. Mech. Engrg._, 327:226-255. [[preprint](https://arxiv.org/abs/1705.02078)] [[doi](https://doi.org/10.1016/j.cma.2017.08.043)]

### DPG* Methods

DPG* methods are dual to DPG methods.
This new class of finite element method uses the same coefficient matrix as the associated DPG method but has a different load and involves a post-processing step to solve render the solution.
In the DLS theory, DPG methods can be identified with the least-squares problem corresponding to an overdetermined system of equations.
An analogous identification can be made with DPG* methods.
However, DPG* methods are associated with the least-squares problem corresponding to the _underdetermined_ systems of equations.

Currently, I am studying the properties of DPG* methods, including _a posteriori_ error estimation, superconvergence, and applications to special problems without uniqueness of solutions.

###### Keith, B., Demkowicz, L., and Gopalakrishnan, J. (2017). DPG* Method. _arXiv:1710.05223 [math.NA]_ [[link](https://arxiv.org/abs/1710.05223)]

### Goal-oriented Methods

Goal-oriented methods are tailored for accuracy in a specific output.
Naturally, with goal-oriented methods, great efficiency improvements can be achieved when a globally high-quality solution is not necessary.
Once the output is determined are many different ways to seek efficiency improvements.
One way is through goal-oriented adaptive mesh refinement, which was I explored for non-symmetric functional setting through a new Petrov-Galerkin duality theory. 

<figure>
  <img src="/assets/images/ResearchGMR.png" alt="">
  <figcaption>(Left) Condition number growth of various stiffness matrices. Notice the <em>O</em>(<em>h</em><sup>-1</sup>) growth in green. This is comes reformulating the assembly algorithm, <em>not</em> from a new preconditioner. (Right) A study in robustness and sensitivity to round-off error of frequency-domain acoustic wave equation <em>near resonance</em>. Here, the DLS solutions converge while the others diverge. </figcaption>
</figure>

###### Keith, B., Vaziri Astaneh, A., and Demkowicz, L. (2017). Goal-oriented adaptive mesh refinement for non-symmetric functional settings. _arXiv:1711.01996 [math.NA]_ [[preprint](https://arxiv.org/abs/1711.01996)]

## Applications

### Solids

##### Fuentes, F., Keith, B., Demkowicz, L., and Le Tallec, P. (2017). Coupled variational formulations of linear elasticity and the DPG methodology. _J. Comput. Phys._, 247:715-731. [[preprint](https://arxiv.org/abs/1609.08180)] [[doi](https://doi.org/10.1016/j.jcp.2017.07.051)]
##### Keith, B., Fuentes, F., and Demkowicz, L. (2016). The DPG methodology applied to different variational formulations of linear elasticity. _Comput. Methods Appl. Mech. Engrg._, 309:579-609. [[preprint](https://arxiv.org/abs/1601.07937)] [[doi](https://doi.org/10.1016/j.cma.2016.05.034)]


### Fluids

##### Keith, B., Knechtges, P., Roberts, N.V., Elgeti, S., Behr, M., and Demkowicz, L (2017). An ultraweak DPG method for viscoelastic fluids. _J. Non-Newton. Fluid Mech._, 247:107-122. [[preprint](https://arxiv.org/abs/1612.03124)] [[doi](https://doi.org/10.1016/j.jnnfm.2017.06.006)]

### Waves

##### Vaziri Astaneh, A., Keith, B., and Demkowicz, L. (2017). On perfectly matched layers and non-symmetric variational formulations. [[preprint]()]

## Software

I focus on many aspects of finite element analysis, and have developed, both in terms of software and the underlying mathematics, several finite element methods which are characterized by having:
- High-order convergence (heirarchical high-order discretizations for different element shapes and "energy" spaces).
- Proofs of numerical stability (inf-sup conditions satisfied for variational formulations).
- Adaptivity (so the meshes spatially refine in a particular area of interest).
- Desirable linear algebra properties to exploit in solvers.

Some highlights are shown next.

### hp2d/hp3D


### Camellia

<figure>
  <img src="/assets/images/ResearchElasticity.png" alt="">
  <figcaption>Linear elasticity in the L-shape domain solved with different DPG variational formulations, all converging, but displaying different refinement patterns (left). Sheathed hose composed of a thick inner layer of rubbber, and a very thin outer layer of steel (middle). It was solved using a coupled linear elasticity DPG method which is robust in the incompressible limit inside the rubber subdomain and computationally cheap in the steel layer (right). </figcaption>
</figure>

Disontinuous Petrov-Galerkin (DPG) methods are crafted to be stable for any linear well-posed variational formulation of a PDE.
We showed their applicability by solving the equations of linear elasticity with various variational formulations, some being fast, others being slower, but robust in the near-incompressible limit.
We also derived DPG methods that combine different formulations, as they are useful in physical problems like racing-engine hoses and biomedical devices.
Using DPG methods, we also successfully validated data from dynamic mechanical analysis (DMA) calibration experiments involving viscoelastic materials to within 5% of the quantity of interest.

### ESEAS

<figure>
  <img src="/assets/images/ResearchShapeFunctions.png" alt="">
  <figcaption>Unified construction of high-order hierarchical discretizations of <em>H</em><sup>1</sup>, <em>H</em>(curl), <em>H</em>(div) and <em>L</em><sup>2</sup> by systematically projecting to faces and edges. </figcaption>
</figure>
Developed a unified and systematic approach to constructing arbitrary high-order conforming discretizations of the traditional Sobolev spaces lying in a differential de Rahm sequence (<em>H</em><sup>1</sup>, <em>H</em>(curl), <em>H</em>(div) and <em>L</em><sup>2</sup>) for each of the "standard" element shapes: tetrahedra,hexahedra, triangular prisms and pyramids. 
The code can be found [here](https://github.com/libESEAS/ESEAS).