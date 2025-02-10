---
layout: page
title: Rotating matrices
description: Does an invertible matrix stay invertible if you rotate its rows?
img: assets/img/bipartite4.png
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

This project is designed to give an introduction to [this write-up](/assets/pdf/Unlocking_Matrices.pdf), which is based on the final chapter of my [masters dissertation](/assets/pdf/PM.pdf).

A slightly random but fun question we can ask is: given a matrix, when can we rotate its rows to make it invertible? We will say that a matrix can be unlocked if there is a way we can rotate its rows so that it becomes invertible.

For example, the matrix  $$ \pi = \begin{pmatrix} 3 & -1 & -4 \\ 1 & 5 & -9 \\ 2 & -6 & 5 \end{pmatrix}$$ is not currently invertible since $$\det(\pi)=0$$. However, if we rotate the 3rd row to the left by one step, we get the matrix  
$$\begin{pmatrix}
        3 & -1 & -4 \\
        1 & 5 & -9 \\
        -6 & 5 & 2
    \end{pmatrix}$$, which has determinant $$-27$$ and thus is invertible. So $$\pi$$ can indeed be unlocked.
    
Now let's look at another example. Take $$\gamma =
    \begin{pmatrix} 
    2 & -7 & 5 \\ 
    -3 & -8 & 11 \\
    2 & 0 & -2
    \end{pmatrix}$$. 
    

Now, however hard you try, you will never be able to rotate the rows of $$\gamma$$ such that its determinant is non-zero and thus $$\gamma$$ can never be unlocked. A clever way to see why this happens is to notice that the digits in each row of $$\gamma$$ add up to $$0$$. Thus, $$(1,1,1)$$ is an eigenvector of $$\gamma$$  with eigenvalue 0 no matter how we rotate the rows. Since the determinant of a matrix is equal to the product of its eigenvalues then the determinant of $$\gamma$$ is always zero. 
    
Using the same logic, we can see that any matrix where all its rows add up to 0 can never be unlocked. We might conjecture that if the rows of a matrix do not all add up to 0, then it can be unlocked. However, if we take
$$\begin{pmatrix}
1 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 
\end{pmatrix}$$
we see that two of the rows will always be the same no matter how we rotate them so the determinant will always be zero since the rows are not linearly independent. 

Can we even give an exact condition on when a matrix can be unlocked?

It turns out that the answer is yes - we just need the help of a little bit of graph theory.

