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

In order to bridge the gap between observation, theory, and prediction, modern science has come to heavily rely on computational means.
From simulating star formation to proton transport, from climate change and sea level rise to turbulence and combustion (not to mention turbulent combustion), or from structural design to the design of personalized treatment pathways in state-of-the-art medical practice, computer simulations are indispensable, regardless of scale.
By studying the mathematics behind computer simulations, I strive to bring clarity and insight into these otherwise intractable problems.

My recent research has resulted in discovering a new class of finite element methods, called [DPG* methods](https://arxiv.org/abs/1809.03153), and classifying a large category of related methods, called [discrete least-squares methods (DLS methods)](https://doi.org/10.1016/j.cma.2017.08.043).
In addition, I have written general and portable software for high-order and adaptive simulations and applied my work to several structural, fluid, and wave mechanics problems.
I am interested in applying my work to problems at the frontiers of science and engineering research by expanding on state-of-the-art techniques in optimal control, uncertainty quantification, and high performance computing.

## Numerical Methods

Much of my [PhD research](http://hdl.handle.net/2152/68919) was spent focusing on discontinuous Petrov-Galerkin finite element methods (DPG methods) which have been used extensively in engineering and scientific applications.
Since beginning my postdoctoral research, I have been focused on an emerging approach to finite element analysis which has been dubbed the "[surrogate matrix methodology](https://www-m2.ma.tum.de/bin/view/Allgemeines/M2SURR)."
In additional, as part of my role in the EU's Horizon 2020 research and innovation program [ExaQUte](http://exaqute.eu/), my research has also included shape optimization under uncertainty, multilevel Monte Carlo methods, and turbulent inlet generation for large eddy simulation.
The following summaries only pertain to my contributions to the field of finite element methods.

### DPG* Methods

<figure>
  <img src="/assets/images/Research2DPlot.png" alt="">
  <figcaption> <em>hp</em>-adaptive mesh refinement with a DPG* method for Poisson's equation on the L-shaped domain. Left: The DPG* solution. (Color scale represents solution values.) Right: The corresponding <em>hp</em> quadtree mesh delivered by an <em>hp</em>-adaptive algorithm after fifteen refinements. (Colors represent the polynomial degree <em>p</em>.) </figcaption>
</figure>

DPG* methods are dual to DPG methods.
In a well-defined sense, DPG, as a methodology, can be viewed as a practical means to solve overdetermined discretizations of boundary value problems.
In a similar way, DPG* delivers a methodology for underdetermined discretizations. 

###### Demkowicz, L., Gopalakrishnan, J., and Keith, B. (2018). The DPG-star method. _ArXiv e-print arXiv:1809.03153 [math.NA]_ [[link](https://arxiv.org/abs/1809.03153)]

### Surrogate Matrix Methods

<figure>
  <img src="/assets/images/Research_ComputationalCost.png" alt="">
  <figcaption> Left: Distribution of computational cost with traditional NURBS assembly in IGA. Right: Distribution of computational cost with a corresponding surrogate method. </figcaption>
</figure>

[Surrogate matrix methods](https://www-m2.ma.tum.de/bin/view/Allgemeines/M2SURR) provide low-cost and low-memory coefficient matrices for Galerkin finite element methods.
They are assembled by enforcing a local structure in the finite element basis which can be successfully achieved in classical finite element methods with lowest order simplicial elements or with a high-order B-spline or NURBS bases, as used by the isogeometric community.
In an ongoing series of papers, surrogate matrix methods have been successfully applied to a large number of problems with steady or transient characteristics.
This includes Poisson’s equation and <em>p</em>-Laplacian diffusion, membrane vibration, plate bending, Stokes’ flow, linear and nonlinear elasticity, and a number of high frequency time-harmonic problems.
Using surrogate methods can significantly reduce the time to solution in isogeometric analysis at a few million degrees of freedom or in large-scale matrix-free applications with billions of degrees of freedom.
This ongoing work is part of [Daniel Drzisga's](https://www-m2.ma.tum.de/bin/view/Allgemeines/DanielDrzisga) PhD research.

###### Drzisga, D., Keith, B., and Wohlmuth, B. (2019). The surrogate matrix methodology: Accelerating isogeometric structural analysis. _In preparation_

###### Drzisga, D., Keith, B., and Wohlmuth, B. (2019). The surrogate matrix methodology: A reference implementation for low-cost assembly in isogeometric analysis. _Submitted_

###### Drzisga, D., Keith, B., and Wohlmuth, B. (2019). The surrogate matrix methodology: Low-cost assembly for isogeometric analysis. _ArXiv e-print   arXiv:1904.06971 [math.NA]_ [[preprint](https://arxiv.org/abs/1904.06971)]

###### Drzisga, D., Keith, B., and Wohlmuth, B. (2019). The surrogate matrix methodology: a priori error estimation. _ArXiv e-print arXiv:1902.07333 [math.NA]_ [[preprint](https://arxiv.org/abs/1902.07333)]

### DLS Methods

<figure>
  <img src="/assets/images/ResearchDLS2.png" alt="">
  <figcaption>Left: Condition number growth of various stiffness matrices. Notice the <em>O</em>(<em>h</em><sup>-1</sup>) growth in green. This is comes from reformulating the assembly algorithm, <em>not</em> from a new preconditioner. Right: A study in robustness and sensitivity to round-off error with the frequency-domain acoustic wave equation <em>near resonance</em>. Here, the DLS solutions converge while the others diverge. </figcaption>
</figure>

From extensive research on DPG methods, the term discrete least-squares finite element method (DLS method) was coined.
The discrete linear systems in DLS methods have a very specific algebraic structure which can be exploited to accelerate computation or to reduce round-off error.

###### Keith, B., Petrides, S., Fuentes, F., and Demkowicz, L. (2017). Discrete least-squares finite element methods. _Comput. Methods Appl. Mech. Engrg._, 327:226-255. [[preprint](https://arxiv.org/abs/1705.02078)] [[doi](https://doi.org/10.1016/j.cma.2017.08.043)]

### Goal-Oriented Methods

<figure>
  <img src="/assets/images/ResearchGMR.png" alt="">
  <figcaption> Far left: Manufactured solution with a large gradient in the region coloured deep red. Center left: A region of interest (shaded light red) where the solution is declared to be of primary interest. Center right: A goal-oriented adaptive mesh refinement pattern which seeks to minimize the numerical error in the region of interest. Far right: Vast improvement in the efficiency across three new goal-oriented refinement strategies, shown in red, green, and blue, in comparison to a standard adaptive mesh refinement strategy, shown in black. </figcaption>
</figure>

Goal-oriented methods are tailored for accuracy in a specific output.
With goal-oriented methods, great efficiency improvements can be achieved because a globally high-quality solution is often not necessary.
Once the output is determined, there are many different ways in which to seek efficiency improvements.
One way is through goal-oriented adaptive mesh refinement, which can be rigorously formulated in non-symmetric functional settings and applied to DPG methods. 

###### Keith, B., Vaziri Astaneh, A., and Demkowicz, L. (2019). Goal-oriented adaptive mesh refinement for discontinuous Petrov–Galerkin methods. _SIAM J. Numer. Anal. (To appear)_ [[preprint](https://arxiv.org/abs/1711.01996)]

## Applications

### Solids

<figure>
  <img src="/assets/images/ResearchElasticity.png" alt="">
  <figcaption>Left: Adaptive mesh refinement with different formulations for a singular solution. Center: Schematic diagrams of a complicated sheathed hose problem. Right: The computed azimuthal stress on the two materials in the hose. </figcaption>
</figure>

In a sequence of two papers, Federico Fuentes and I analyzed four different formulations — denoted strong, mixed, primal, and ultraweak, respectively (see figure; left) — of a common linearized elasticity model.
This project culminated in the analysis of a very difficult high material contrast coupled rubber and steel model (see figure; center and right).
Here, due to the incompressibility of the rubber, standard displacement-only methods will often break down or ''lock.''
Additionally, the steel in the model is very thin and so, likewise, some alternative formulations will often break down there.
Our solution was to develop a special method coupling two different formulations together at the material interface; hence, greatly improving the accuracy possible solely with either individual formulation.

###### Fuentes, F., Keith, B., Demkowicz, L., and Le Tallec, P. (2017). Coupled variational formulations of linear elasticity and the DPG methodology. _J. Comput. Phys._, 348:715-731. [[preprint](https://arxiv.org/abs/1609.08180)] [[doi](https://doi.org/10.1016/j.jcp.2017.07.051)]
###### Keith, B., Fuentes, F., and Demkowicz, L. (2016). The DPG methodology applied to different variational formulations of linear elasticity. _Comput. Methods Appl. Mech. Engrg._, 309:579-609. [[preprint](https://arxiv.org/abs/1601.07937)] [[doi](https://doi.org/10.1016/j.cma.2016.05.034)]


### Fluids

<figure>
  <img src="/assets/images/ResearchFluid.png" alt="">
  <figcaption> Left: Velocity field and stress tensor component profiles from an Oldroyd-B fluid model. Center: Convergence through adaptive mesh refinements of the horizontal traction component of the solution. Right: An example of an adaptively refined mesh after five refinement steps. </figcaption>
</figure>

Viscoelastic fluid models are commonly used in engineering to simulate blood and polymer melts.
These models are well-known to very challenging both in simulation and in mathematical analysis.

I developed a new DPG finite element method of the Oldroyd-B viscoelastic fluid model which is intrinsically stable throughout a broad range of model parameters.
I then studied parameter-dependent adaptive mesh refinement with the method.
The simulations for this project were completed using the [Camellia software library](https://www.osti.gov/scitech/biblio/1334186), which I assisted in developing.
I am currently working on a follow-up project to study goal-oriented adaptive mesh refinement strategies for this model.

###### Keith, B., Knechtges, P., Roberts, N.V., Elgeti, S., Behr, M., and Demkowicz, L (2017). An ultraweak DPG method for viscoelastic fluids. _J. Non-Newton. Fluid Mech._, 247:107-122. [[preprint](https://arxiv.org/abs/1612.03124)] [[doi](https://doi.org/10.1016/j.jnnfm.2017.06.006)]

### Waves

<figure>
  <img src="/assets/images/ResearchWaves.png" alt="">
  <figcaption> Far left: A 2D computational domain with a perfectly matched layer (PML). Center left: A 3D computational domain with a PML. Center right: The <em>x</em>-component of the displacement from a 2D elastodynamics model. Far right: The <em>x</em>-component of the electric field from a 3D electromagnetics model. </figcaption>
</figure>

Perfectly matched layers (PMLs) are a very widespread type of artificial absorbing boundary layer used in numerical methods for wave propagation problems defined on unbounded domains.
In order to lay the groundwork for some of my colleagues to begin their dissertation research, Dr Ali Vaziri Astaneh and I recently developed PMLs for high-order DPG methods for several acoustic, elastodynamic, and electromagnetic models.
Results from our numerical verification experiments are given in the figure above.

###### Vaziri Astaneh, A., Keith, B., and Demkowicz, L. (2019). On perfectly matched layers for discontinuous Petrov–Galerkin methods. _Computational Mechanics_, 63(6):1131-1145 [[preprint](https://arxiv.org/abs/1804.04496)] [[doi](https://doi.org/10.1007/s00466-018-1640-3)]

### Mixing patterns

<figure>
  <img src="/assets/images/ResearchLCS.png" alt="">
  <figcaption> Lagrangian Coherent Structures (LCSs) in the ABC flow. Elliptic LCS families in blue, red, and green, and Parabolic LCS in yellow. </figcaption>
</figure>

A Lagrangian coherent structure (LCS) is an influential material surface which acts as a skeleton of observed mixing patterns in a dynamical system.
During my Master's studies supervised by [Professor George Haller](http://georgehaller.com/), I analyzed several problems via new variational characterizations of LCSs.

###### Keith, B. (2014). Lagrangian coherent structures in three-dimensional steady flows. Master's Thesis, McGill University, Montreal, Quebec, Canada. [[link](http://digitool.Library.McGill.CA:80/R/-?func=dbin-jump-full&object_id=121521&silo_library=GEN01)]

## Software

I have written a significant amount of software in Fortran, Matlab, and C++.
Some of the software projects which I have led or contributed to are described below.

### <em>hp</em>2D/<em>hp</em>3D

I contribute to and help maintain the two Fortran finite element softwares <em>hp</em>2D and <em>hp</em>3D which have complete 2D/3D support for local hierarchical anisotropic <em>h</em>- and <em>p</em>-refinement with one level of hanging nodes and shape functions for all standard elements conforming in each of the canonical de Rahm complex of Hilbert spaces:
<figure>
  <img src="/assets/images/ResearchExactSequence.png" style="width: 60%; height: 60%" align="middle" alt="">
</figure>
The code is not openly available due to limited documentation but it is well-used within the Electromagnetics and Acoustics Group at ICES and among many collaborators.

### ESEAS

<figure>
  <img src="/assets/images/ReseachESEAS.png" style="width: 90%; height: 90%" align="middle" alt="">
  <figcaption> Left: Illustrations of the 1D, 2D, and 3D elements supported by the ESEAS software. Right: Illustration of the novel shape function construction for pyramid elements. </figcaption>
</figure>

The ESEAS (exact sequence elements of all shapes) software library supports a complete set of features for evaluating shape functions in high-order finite element methods written in the Fortran 77 standard.
The library is innovative for its support for all standard elements in one, two, and three spatial dimensions for arbitrary polynomial order (see figure above; left).
It relies on a minimal set of hierarchical routines to construct all the shape functions.
This hierarchical construction was the breakthrough which lead to the first explicit construction of arbitrary order pyramid elements (see figure above; right).
ESEAS is currently being used inside <em>hp</em>2D and <em>hp</em>3D and [HOFEM](https://doi.org/10.23919/EuMC.2018.8541806).
It is being rewritten in C++ for [Trilinos](https://trilinos.org/) and for the [MFEM](https://mfem.org/) library. 

###### Fuentes, F., Keith, B., Demkowicz, L., and Nagaraj, S. (2015). Orientation embedded high order shape functions for the exact sequence elements of all shapes. _Computers & Mathematics with Applications_, 70(4):353-458. [[preprint](https://arxiv.org/abs/1504.03025)] [[doi](https://doi.org/10.1016/j.camwa.2015.04.027)] [[code](https://github.com/libESEAS/ESEAS)]

### Camellia

The Camellia software library is a C++ toolbox developed by Dr Nathan V. Roberts which uses Sandia's Trilinos library of packages.
It is a publicly available software with many tools for rapid implementation of finite element methods including discontinuous Galerkin (DG), discontinuous Petrov-Galerkin (DPG), DPG*,  hybridizable discontinuous Galerkin (HDG), and first-order system least-squares methods (FOSLS).

<!-- Camellia's mechanisms allow the user to simply provide the bilinear form, boundary conditions, polynomial order, and material and load data before solving a problem. -->

[Download Camellia](https://bitbucket.org/nateroberts/camellia.git)

[Download the Camellia manual](https://www.osti.gov/scitech/biblio/1334186)