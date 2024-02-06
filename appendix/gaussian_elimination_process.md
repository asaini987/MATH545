# Gaussian Elimination

 a matrix $A$ and vector $b$ we assemble its augmented matrix
and proceed through the following sequence, until the final augmented
matrix is upper triangular.

$$
    \begin{amatrix}{1}
        A & b
    \end{amatrix} \mapsto
    \begin{amatrix}{1}
        A^{(1)} & b^{(1)}
    \end{amatrix} \mapsto
    \begin{amatrix}{1}
        A^{(2)} & b^{(2)}
    \end{amatrix} \mapsto
    \dots \mapsto
    \begin{amatrix}{1}
        A^{(n-1)} & b^{(n-1)}
    \end{amatrix}
$$

where $A^{(n-1)} = U$ is upper triangular. In more detail, at
each step of this process we eliminate the elements in column
$i$ below the diagonal.

1. The process begins with the matrix

$$
    \begin{amatrix}{1}
        A & b
    \end{amatrix} =
    \begin{amatrix}{4}
        a_{11} & a_{12} & \dots & a_{1n} & b_1 \\
        a_{21} & a_{22} & \dots & a_{2n} & b_2 \\
        \vdots & \vdots & \ddots & \vdots & \vdots \\
        a_{n1} & a_{n2} & \dots & a_{nn} & b_n \\
    \end{amatrix}
$$

We then eliminate the elements in the first column below
the main diagonal by:
    1. Subtracting $\ifrac{a_{21}}{a_{11}}$ times the first row from the second row. In other words,

    $$
        R_2 \mapsto R_2 - \frac{a_{21}}{a_{11}}R_1.
    $$

    2. Subtracting $\ifrac{a_{31}}{a_{11}}$ times the first row from the second row. In other words,

    $$
        R_3 \mapsto R_3 - \frac{a_{31}}{a_{11}}R_1.
    $$

    3. And so on until ...
    4. Subtracting $\ifrac{a_{n1}}{a_{11}}$ times the first row from the second row. In other words,

    $$
        R_n \mapsto R_n - \frac{a_{n1}}{a_{11}}R_1.
    $$

This results in the new augmented matrix

$$
    \begin{amatrix}{1}
        A^{(1)} & b^{(1)}
    \end{amatrix} =
    \begin{amatrix}{4}
        a_{11} & a_{12} & \dots & a_{1n} & b_1 \\
        0 & a_{22}^{(1)} & \dots & a_{2n}^{(1)} & b_2^{(1)} \\
        \vdots & \vdots & \ddots & \vdots & \vdots \\
        0 & a_{n2}^{(1)} & \dots & a_{nn}^{(1)} & b_n^{(1)} \\
    \end{amatrix}
$$

2. Next consider the $(n-1)\times n$ sub-matrix found by ignoring the first row and column of the matrix above. Then repeat the process of eliminating the first column of this sub-matrix.
This gives us

$$
    \begin{amatrix}{1}
        A^{(2)} & b^{(2)}
    \end{amatrix} =
    \begin{amatrix}{5}
        a_{11}  & a_{12}        & \dots         & \dots     & a_{1n}        & b_1 \\
        0       & a_{22}^{(1)}  & a_{23}^{(1)}  & \dots     & a_{2n}^{(1)}  & b_2^{(1)} \\
        0       & 0             & a_{33}^{(2)}  & \dots     & a_{3n}^{(2)}  & b_3^{(2)} \\
        \vdots  & \vdots        & \vdots        & \ddots    & \vdots        & \vdots \\
        0       & 0             & a_{n3}^{(2)}  & \dots     & a_{nn}^{(2)}  & b_n^{(2)} \\
    \end{amatrix}
$$

2. Repeat the previous steps until ...
3. We repeat this process $(n-1)$-times until we find

$$
    \begin{amatrix}{1}
        A^{(n-1)} & b^{(n-1)}
    \end{amatrix} =
    \begin{amatrix}{5}
        a_{11}  & a_{12}        & \dots         & \dots     & a_{1n}            & b_1 \\
        0       & a_{22}^{(1)}  & a_{23}^{(1)}  & \dots     & a_{2n}^{(1)}      & b_2^{(1)} \\
        0       & 0             & a_{33}^{(2)}  & \dots     & a_{3n}^{(2)}      & b_3^{(2)} \\
        \vdots  & \vdots        & \vdots        & \ddots    & \vdots            & \vdots \\
        0       & 0             & 0             & \dots     & a_{nn}^{(n-1)}    & b_n^{(n-1)} \\
    \end{amatrix}
$$

What is the cost of Gaussian Elimination? The matrix
$\begin{amatrix}{1} A & b \end{amatrix}$ has size $n \times ( n + 1 )$.
The first step is the  most expensive. We need to eliminate $n-1$
non-zero elements, via $n-1$ row operations. That's a total of

$$
    2(n-1)(n+1),
$$

floating point operations. When we are dealing with row $i$ then there
are $k = n - i + 1$ unknowns left, thus we require

$$
    2(k-1)(k+1) = 2(k^2 - 1)
$$

floating point operations. For the total cost we add up the costs
for each individual step of Gaussian elimination to find

$$
\begin{aligned}
    2\sum_{k=1}^n \lb k^2 - 1\rb &= 2\sum_{k=1}^n k^2 - 2\sum_{k=1}^n 1
        = \frac{1}{3} n(n+1)(2n+1) - 2n \\
        % = \frac{1}{3} n (2n^2 + 3n + 1)
        &= \frac{2}{3}n^3 + n^2 - \frac{5}{3} n.
\end{aligned}
$$

