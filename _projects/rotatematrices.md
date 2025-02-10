---
layout: page
title: Rotating matrices
description: Does an invertible matrix stay invertible if you rotate its rows?
img: assets/img/12.jpg
importance: 1
category: Projects
related_publications: true
output: 
  bookdown::pdf_book:
    latex_engine: lualatex
    
header-includes:
  - \usepackage{amsmath}
  - \DeclareMathOperator{\det}{det}
---

This project is designed to give an introduction to [this write-up](assets/pdf/Unlocking_Matrices.pdf), which is based on the final chapter of my [masters dissertation](assets/pdf/PM.pdf).

A slightly random but fun question we can ask is: given a matrix, when can we rotate its rows to make it invertible? We will say that a matrix can be unlocked if there is a way we can rotate its rows so that it becomes invertible.

For example, the matrix $\pi=
    \begin{pmatrix}
        3 & -1 & -4 \\
        1 & 5 & -9 \\
        2 & -6 & 5
    \end{pmatrix}$ is not currently invertible since $\det(\pi)=0$. However, if we let the $r_i$ operator rotate the $i$th row to the left by one step, we see that $r_3(\pi)=
    \begin{pmatrix}
        3 & -1 & -4 \\
        1 & 5 & -9 \\
        -6 & 5 & 2
    \end{pmatrix}$, which has determinant $-27$ and thus is invertible. So $\pi$ can indeed be unlocked.
    
Now let's look at another example. Take $\gamma =
    \begin{pmatrix}
        2 & -7 & 5 \\
        -3 & -8 & 11 \\
        2 & 0 & -2
    \end{pmatrix}$. 
    
    Now, however hard you try, you will never be able to rotate the rows of $\gamma$ such that its determinant is non-zero and thus $\gamma$ can never be unlocked. A clever way to see why this happens is to notice that the digits in each row of $\gamma$ add up to $0$. Thus, $(1,1,1)$ is an eigenvector of $\sigma(\gamma)$  with eigenvalue $0$ no matter how we rotate the rows. Since the determinant of a matrix is equal to the product of its eigenvalues then the determinant of $\gamma$ is always zero. 
    
Using the same logic, we can see that any matrix where all its rows add up to $0$
But, as we will see, the rows of a matrix all adding up to $0$ is not a necessary condition for a matrix not to be able to be unlocked by row rotations.

Okay its time to do some maths:

**The Cauchy-Schwarz Inequality**\
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$
and
$$f(x_1)=x_1^3+\sqrt{2+x_1} \in \mathbb{Q}[x_1]$$

\begin{equation}
S=x^2+\frac{x}{y} \in \mathbb{Z}(x,y)
\end{equation}


