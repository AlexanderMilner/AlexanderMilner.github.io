---
layout: page
title: Rotating matrices
description: Does an invertible matrix stay invertible if you rotate its rows?
img: assets/img/12.jpg
importance: 1
category: Research-related
related_publications: true
output: 
  bookdown::pdf_book:
    latex_engine: lualatex

header-includes:
  - \usepackage{amsmath}
---

This project is based on [this write-up](assets/pdf/Unlocking_Matrices.pdf) of the final chapter of my [masters dissertation](assets/pdf/PM.pdf).

Our first question is: given a matrix, under what conditions can we rotate its rows to make it invertible?

The matrix $\pi=
    \begin{pmatrix}
        3 & -1 & -4 \\
        1 & 5 & -9 \\
        2 & -6 & 5
    \end{pmatrix} \in M_3(\mathbb{Q})$ can be unlocked by row rotations as even though $\DeclareMathOperator{det}(\pi)=0$, $r_3(\pi)=\pi[e_3]=
    \begin{pmatrix}
        3 & -1 & -4 \\
        1 & 5 & -9 \\
        -6 & 5 & 2
    \end{pmatrix}$ has determinant $-27$. $\gamma =
    \begin{pmatrix}
        2 & -7 & 5 \\
        -3 & -8 & 11 \\
        2 & 0 & -2
    \end{pmatrix} \in M_3(\mathbb{Q})$, however, can not be unlocked by row rotations ie. $\operatorname{det}(\sigma(\gamma)) = 0$ for all $\sigma \in \langle R \rangle$. This is simply due to the fact that the digits in each row of $\gamma$ add up to $0$. An easy way to see that this is the case is that $(1,1,1)$ is an eigenvector of $\sigma(\gamma)$  with eigenvalue $0$ for all $\sigma \in \langle R \rangle$. Since the determinant of a matrix is equal to the product of its eigenvalues then $\operatorname{det}(\sigma(\gamma)) = 0$ for all $\sigma \in \langle R \rangle$. But, as we will see, the rows of a matrix all adding up to $0$ is not a necessary condition for a matrix not to be able to be unlocked by row rotations.

Okay its time to do some maths:

**The Cauchy-Schwarz Inequality**\
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$
and
$$f(x_1)=x_1^3+\sqrt{2+x_1} \in \mathbb{Q}[x_1]$$

\begin{equation}
S=x^2+\frac{x}{y} \in \mathbb{Z}(x,y)
\end{equation}


