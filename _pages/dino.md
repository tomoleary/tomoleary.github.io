---
title: "Derivative-Informed Neural Operators"
layout: single
sitemap: true
permalink: /dino/
author_profile: true
toc: true
toc_label: "Topic"
toc_icon: "gear"
---

<p style="text-align: justify">

</p>

### Conventional neural operator training
Neural operators are neural network surrogates for maps on function spaces, where the neural network parametrization is *independent* of a specific numerical discretization of the target map. Neural operators often arise as surrogates for parametric PDE maps. Neural operators are typically trained in the $$L^2_\mu$$ parametric Bochner space.


### DINO training

$$\min_w \mathbb{E}_{m \sim \mu}\left[\|u(m) - u_w(m)\|^2_{\mathcal{U}} \right]$$


Derivative-informed neural operators ([DINOs](https://www.sciencedirect.com/science/article/pii/S0021999123006502)) are neural operators that are trained to learn both an operator and its (Fréchet) derivatives, that is the training is formulated in the  $$H^1_\mu$$ Bochner space (or $$H^k_\mu$$ with $$k\in \mathbb{N}$$).


$$\min_w \mathbb{E}_{m \sim \mu}\left[\|u(m) - u_w(m)\|^2_{\mathcal{U}} + \|\mathcal{D}u(m) - \mathcal{D}u_w(m)\|^2_{HS(\mathcal{M},\mathcal{U})} \right]$$

The key issue for DINO is to devise representations of the neural operator and the training problem that lead to efficient representations of the derivative $$\mathcal{D}u$$, which leads to efficient offline computation of training data and efficient DINO training. 

## Advantages of DINO


### Improved generalization per unit compute

Derivatives (e.g., Jacobians) of implicitly defined functions can often be computed and compressed at a significantly lower cost when compared to the function itself. Consider an implicitly defined parametric PDE map in a strong residual form.

$$ m \mapsto u(m) \quad \text{such that} \quad R(u,m) = 0 $$

Then the derivative can be computed efficiently as follows.

$$\mathcal{D}u(m) = - \left[\frac{\partial R (u,m)}{\partial u}\right]^{-1}\frac{\partial R(u,m)}{\partial m} $$

Notably, when utilizing (sparse) direct solvers, the factors for $$\left[\frac{\partial R (u,m)}{\partial u}\right]$$ need only be computed once, and then the Jacobian can be compressed, matrix-free, at marginal additional costs. Other amoritizations are possible in other settings such as (i) the use of expensive preconditioners, and (ii) implicit time integrators. In these cases the DINO formulation brings in more, cheap training data; it thereby leads to empirically better $$L^2_\mu$$ generalization accuracy per unit compute of training data. 

### Improved accuracy in optimization and inference tasks

Many tasks regarding the decision support of complex physical systems can
1. be formulated as optimization problems, or 
2. require derivative information for their efficient solution. 

Such tasks include Bayesian inference, stochastic optimization (including optimal design and optimal control), and optimal experimental design. DINOs are uniquely suitable to these tasks as they control not only the operator approximation error but also its derivative(s). These lead to more accurate approximations of optimization gradients and stationary points.


### DINOs for Bayesian Inference

Please see our [preprint](https://arxiv.org/abs/2403.08220) on efficient Markov chain Monte Carlo, led by my collaborator [Lianghao Cao](https://www.lianghaocao.com/home).


### DINOS for PDE-constrained Optimization Under Uncertainty

Please see our [preprint](https://arxiv.org/abs/2305.20053) on efficient PDE-constrained optimization under uncertainty, led by my collaborator [Dingcheng Luo](https://oden.utexas.edu/people/directory/Dingcheng-Luo/). We compare DINOs against conventional $$L^2_\mu$$ neural operators (NO) and reference PDE solver based benchmark. Generally our results demonstrate that DINOs are $$10\times$$ more accurate than NO and $$10 \times$$ more sample efficient than reference PDE solver-based implementations when only amortized over one risk-averse optimization problem. When amortizing over many the benefits of DINO increase substantially. 


DINOs are able to control viscous flow fields with expensive-to-estimate risk measures ([CVaR](https://en.wikipedia.org/wiki/Expected_shortfall)) at $$\mathcal{O}(10^7)$$ online speedup, with little loss of accuracy. 

#### Uncontrolled flow field
<img src="/assets/images/v_uncontrolled_2.png" width="800" height="200" alt="" align="center" style="margin-bottom:0px;margin-top:0px;margin-left:auto;margin-right:auto;padding-left:auto;padding-right:auto;" />

#### Controlled flow field
<img src="/assets/images/v_controlled_2.png" width="800" height="200" alt="" align="center" style="margin-bottom:0px;margin-top:0px;margin-left:auto;margin-right:auto;padding-left:auto;padding-right:auto;" />



### Application to 2011 Tōhoku earthquake

Through our NSF RISE grant, with collaborators Thorsten Becker, Simone Puel and Umberto Villa we are solving Bayesian inverse problems surrounding the 2011 M9 earthquake. Specifically we seek to characterize the elastic properties beneath Japan, as well as the slip that triggered the event; both with uncertainty.


<img src="/assets/images/3D_mesh_Japan_1.png" width="800" height="300" alt="" align="center" style="margin-bottom:1px;margin-top:1px;margin-left:auto;margin-right:auto;padding-left:auto;padding-right:auto;" />

#### Image credit to my collaborator Simone Puel.


### Collaboration

My collaborators on DINO-related topics include [Thorsten Becker](https://www-udc.ig.utexas.edu/external/becker/), [Michael Brennan](https://michaelcbrennan.com/), [Lianghao Cao](https://www.lianghaocao.com/home), [Joshua Chen](https://oden.utexas.edu/people/directory/Joshua-Chen/), [Peng Chen](https://faculty.cc.gatech.edu/~pchen402/), [Omar Ghattas](https://users.oden.utexas.edu/~omar/), [Youssef Marzouk](https://aeroastro.mit.edu/people/youssef-m-marzouk/), [Simone Puel](https://www.linkedin.com/in/simonepuel/?locale=en_US) and [Umberto Villa](https://uvilla.github.io/). 


