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
        {% include figure.liquid loading="eager" path="/assets/img/bigfiber.png" title="Huge fiber" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1: A huge fiber corresponding to the configuration matrix $$A = (1, 2, 3, 12)$$
</div>

Given a starting configuration matrix $$A$$, we can define a toric ideal $$I_A$$ as the binomials corresponding to elements in the integer kernel of $$A$$. Then a Markov basis for $$A$$ is a set of generators of $$I_A$$ and the Markov basis is minimal if no proper subset of the generators generate $$I_A$$. The seminal paper {% cite DS_1998 %} by Diaconis and Sturmfels provided a correspondence between the theory of Markov bases and algebraic statistics and this area of study has flourished in recent year. For an introduction to the association of Markov bases to statistics, see {% cite Kos_2020 %}, or, for a more comprehensive overview, see {% cite ALP_2024 %}.

Macaulay2 already contains a package, *FourTiTwo*, which can compute a minimal Markov basis for a given configuration matrix however minimal Markov bases are almost never unique. The method *markovBases* from our package, *allMarkovBases*, builds on top of *toricMarkov* from *FourTiTwo*, incorporating Theorems 2.6 and 2.7 from {% cite CKT_2007 %} to compute all minimal Markov bases for a given configuration matrix. The package also includes the method *randomMarkov* where, given the *NumberOfBases* option, the method returns the given number of random minimal Markov bases. Both of these methods start by computing the fibers corresponding to the $$A$$-degrees of the minimal generators of the toric ideal $$I_A$$ and this step of the computation can be done by itself using the *fiberGraph* method. The fibers are represented as graphs using the *Graphs* package in order to provide a visualisation of the fibers.

We now present an example. Suppose our configuration matrix is the monomial curve $$A=(1 2 3)$$. The first thing we might want to do is to compute the integer kernel of $$A$$.

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

Therefore, if we let $$x,y,z$$ be variables, we know $$x^2 -y, x^3 - z \in I_A$$. We might suspect that $$I_A := \langle x^u-x^v: u,v \in \mathbb{N}^3, u-v \in \ker_\mathbb{Z}(A)\rangle = \langle x^2 - y, x^3 - z \rangle$$ and while the generators of the integer kernel lattice won't in general be a Markov basis (see $$A=(3 4 5)$$), we can use the method *toricMarkov* from the *FourTiTwo* package to confirm that $$\{\{2,-1,0\},\{3,0,-1\}\}$$ is a Markov basis for $$A$$. Markov bases are outputted as matrices both in the *FourTiTwo* package and in our package.


    i4 : toricMarkov A
    
    o4 = | 2 -1 0  |
         | 3 0  -1 |
    
                  2       3
    o4 : Matrix ZZ  <-- ZZ

We can notice that $$xy-z \in I_A$$ and $$x^3-z \in \langle x^2-y,xy-z \rangle$$ so $$I_A = \langle x^2-y,xy-z \rangle$$ and thus $$\{\{2,-1,0\},\{1,1,-1\}\}$$ is another Markov basis for $$A$$. If we run the *markovBases* method from our package, we can confirm that these are in fact the only two minimal Markov bases for $$A$$.


    i5 : markovBases A
    
    o5 = {| 2 -1 0  |, | 2 -1 0  |}
          | 3 0  -1 |  | 1 1  -1 |
    
    o5 : List

One observation about the minimal Markov bases we have found is that the set of $$A$$-degrees is the same for both since $$\degA (x^2-y)=2$$, $$\degA(x^3-z)=3$$ and $$\degA (x^2-y)=2$$, $$\degA(xy-z)=3$$. Indeed, in general the $$A$$-degrees of a minimal Markov basis are independent of the choice of the minimal Markov basis, see {% cite MS_2004 %}. %Thus, we can look at the fibers corresponding to the $$A$$-degrees of any set of minimal generators of $$I_A$$. 

Thus, the *fiberGraph* method in our package starts by computing the $$A$$-degrees of the one minimal Markov basis computed by *toricMarkov*. Using a breadth-first-search algorithm, it constructs the fibers corresponding to $$A$$-degrees as graphs where two elements $$u,v \in \mathbb{N}^n$$ of a fiber share an edge if they have non-trivial intersection ie. $$u_i>0$$ and $$v_i>0$$ for some $$i$$.



