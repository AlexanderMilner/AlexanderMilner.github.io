---
layout: page
title: Computing minimal Markov bases
description: A Macaulay2 package to compute all minimal Markov bases
img: assets/img/bigfiber.png
importance: 3
category: Projects
related_publications: true
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/bigfiber.png" title="Bipartite graph" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1: A huge fiber corresponding to the configuration matrix $$A = (1 2 3 12)$$
</div>

Given a starting configuration matrix $$A$$, we can define a toric ideal $$I_A$$ as the binomials corresponding to elements in the integer kernel of $$A$$. Then a Markov basis for $$A$$ is a set of generators of $$I_A$$ and the Markov basis is minimal if no proper subset of the generators generate $$I_A$$. The seminal paper {% cite DS_1998 %} by Diaconis and Sturmfels provided a correspondence between the theory of Markov bases and algebraic statistics and this area of study has flourished in recent year. For an introduction to the association of Markov bases to statistics, see {% cite Kos_2020 %}, or, for a more comprehensive overview, see {% cite ALP_2024 %}.

Macaulay2 already contains a package, *FourTiTwo*, which can compute a minimal Markov basis for a given configuration matrix however minimal Markov bases are almost never unique. The method *markovBases* from our package, *allMarkovBases*, builds on top of *toricMarkov* from *FourTiTwo*, incorporating Theorems 2.6 and 2.7 from {% cite CKT_2007 %} to compute all minimal Markov bases for a given configuration matrix. The package also includes the method *randomMarkov* where, given the *NumberOfBases* option, the method returns the given number of random minimal Markov bases. Both of these methods start by computing the fibers corresponding to the $$A$$-degrees of the minimal generators of the toric ideal $$I_A$$ and this step of the computation can be done by itself using the *fiberGraph* method. The fibers are represented as graphs using the *Graphs* package in order to provide a visualisation of the fibers.

We now present an example. Suppose our configuration matrix is the monomial curve $$A=(1 2 3)$$. The first thing we might want to do is to compute the integer kernel of $$A$$.

    Macaulay2, version 1.24.11
    with packages: ConwayPolynomials, Elimination, IntegralClosure, InverseSystems, Isomorphism, LLLBases, MinimalPrimes, OnlineLookup, PackageCitations, Polyhedra, PrimaryDecomposition, ReesAlgebra, Saturation, TangentCone, Truncations, Varieties
    
    i1 : installPackage "allMarkovBases";
    
    i2 : A = matrix "1,2,3";
    
                  1       3
    o2 : Matrix ZZ  <-- ZZ
    
    i3 : ker A
    
    o3 = image | 2  3  |
               | -1 0  |
               | 0  -1 |
    
                                   3
    o3 : ZZ-module, submodule of ZZ

Therefore,
