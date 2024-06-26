# Subspaces

```{div} bigidea
Subspaces of $\mathbb{R}^n$ include lines, planes and hyperplanes through the origin. A basis of a subspace is a linearly independent set of spanning vectors. The Rank-Nullity Theorem describes the dimensions of the nullspace and range of a matrix.
```

```{image} /img/02_01_01.png
:width: 100%
:align: center
```

## Subspaces

```{div} definition
A subset $U \subseteq \mathbb{R}^n$ is a **subspace** if:

1. $U$ contains the zero vector $\boldsymbol{0}$
2. $\boldsymbol{u}_1 + \boldsymbol{u}_2 \in U$ for all $\boldsymbol{u}_1,\boldsymbol{u}_2 \in U$
3. $c \boldsymbol{u} \in U$ for all $c \in \mathbb{R},\boldsymbol{u} \in U$

Condition 2 is called **closed under addition**. Condition 3 is called **closed under scalar multiplication**. Condition 3 with $c=0$ implies Condition 1.
```

```{div} example
<p>

* The zero subspace $\{ \boldsymbol{0} \}$ and the entire space $\mathbb{R}^n$ are both subspaces of $\mathbb{R}^n$.
* Subspaces of $\mathbb{R}^2$ include any line through the origin.
* Subspaces of $\mathbb{R}^3$ include any line or plane through the origin.
* In general, subspaces of $\mathbb{R}^n$ are hyperplanes of any dimension through the origin.

</p>
```

```{div} example
Consider the set

$$
U = \left\{ \begin{bmatrix} x \\ y \end{bmatrix} : y \geq 0 \right\}
$$

Then $U$ contains the zero vector

$$
\boldsymbol{0} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \in U
$$

and $U$ is closed under addition since

$$
\boldsymbol{u}_1 + \boldsymbol{u}_2 = \begin{bmatrix} x_1 \\ y_1 \end{bmatrix} + \begin{bmatrix} x_2 \\ y_2 \end{bmatrix} = \begin{bmatrix} x_1 + x_2 \\ y_1 + y_2 \end{bmatrix} \in U
$$

because $y_1 + y_2 \geq 0$ since $y_1 \geq 0$ and $y_2 \geq 0$. However $U$ is not closed under scalar multiplication because

$$
(-1) \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \begin{bmatrix} -1 \\ -1 \end{bmatrix} \not\in U
$$

Therefore $U$ is not a subspace of $\mathbb{R}^2$.
```

## Linear Independence and Span

```{div} definition
A **linear combination** of vectors $\boldsymbol{u}_1,\dots,\boldsymbol{u}_m \in \mathbb{R}^n$ is a vector

$$
c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m
$$

where $c_1,\dots,c_m \in \mathbb{R}$. The **span** of vectors $\boldsymbol{u}_1,\dots,\boldsymbol{u}_m \in \mathbb{R}^n$ is the set of all linear combinations

$$
\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \} = \{ c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m \in \mathbb{R}^n : c_1,\dots,c_m \in \mathbb{R} \}
$$
```

```{div} theorem
Let $\boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \in \mathbb{R}^n$. Then $\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ is a subspace of $\mathbb{R}^n$.
```

```{div} example
The span of a single nonzero vector $\boldsymbol{u}$ is a line with direction $\boldsymbol{u}$. The span of two nonzero vectors $\boldsymbol{u}$ and $\boldsymbol{v}$ is a plane as long as $\boldsymbol{u}$ and $\boldsymbol{v}$ are not colinear.
```

```{div} definition
A set of vectors $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \} \subset \mathbb{R}^n$ forms a **linearly independent** set if the vectors satisfy the property:

$$
c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m = \boldsymbol{0} \hspace{5mm} \text{if and only if} \hspace{5mm} c_1 = \cdots = c_m = 0
$$

In other words, $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is a linearly independent set if no vector in the set can be expressed as a linear combination of the others.
```

```{div} note
How do we know if a set of vectors $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is linearly independent? Create a matrix where the columns are the given vectors

$$
A = \begin{bmatrix} & & \\ \boldsymbol{u_1} & \cdots & \boldsymbol{u_m} \\ & & \end{bmatrix}
$$

Then $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is a linearly independent set if and only if the linear system $A \boldsymbol{x} = \boldsymbol{0}$ has only the trivial solution $\boldsymbol{x} = \boldsymbol{0}$.
```

## Basis and Dimension

```{div} definition
Let $U \subseteq \mathbb{R}^n$ be a subspace. A set of vectors $\{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ forms a **basis** of $U$ if:

1. $\{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ is a linearly independent set
2. $\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \} = U$

The **dimension** of $U$ is the number $m$ of vectors in a basis.
```

## Nullspace and Range

```{div} definition
The **nullspace** of a $m \times n$ matrix $A$ is

$$
N(A) = \{ \boldsymbol{x} \in \mathbb{R}^n : A\boldsymbol{x} = \boldsymbol{0} \}
$$
```

```{div} theorem
Let $A$ be a $m \times n$ matrix. The nullspace $N(A)$ is a subspace of $\mathbb{R}^n$.
```

```{div} theorem
Let $A$ be a $m \times n$ matrix and let $A = LU$ be the LU decomposition (if it exists). Then $N(A) = N(U)$.
```

```{div} definition
The **range** of a $m \times n$ matrix $A$ is:

$$
R(A) = \{ A \boldsymbol{x} : \boldsymbol{x} \in \mathbb{R}^n \}
$$

The range of $A$ is also called **image** or **column space** of $A$.
```

```{div} note
Matrix multiplication can be written as

$$
A \boldsymbol{x} = \begin{bmatrix} & & \\ \boldsymbol{a}_1 & \cdots & \boldsymbol{a}_n \\ & & \end{bmatrix} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = x_1 \boldsymbol{a}_1 + \cdots + x_n \boldsymbol{a}_n
$$

Therefore the range of $A$ is the equal to the span of the columns

$$
R(A) = \mathrm{span} \{ \boldsymbol{a}_1 , \dots, \boldsymbol{a}_n \}
$$

and that's why $R(A)$ is sometimes called the column space.
```

```{div} theorem
Let $A$ be a $m \times n$ matrix. The range $R(A)$ is a subspace of $\mathbb{R}^m$.
```

```{div} theorem
Let $A$ be an $m \times n$ matrix. Then

$$
\dim (R(A)) = \mathrm{rank}(A)
$$

---

*Proof*. The rank of $A$ is the number of nonzero rows in the row echelon form of $A$. The dimension of $R(A)$ is the number of linearly independent columns in $A$ which is also equal to the number of nonzero rows in $A$.
```

```{div} theorem
Let $A = LU$ be the LU decomposition of $A$ (if it exists) and let $r = \mathrm{rank}(A)$. Then

$$
R(A) = \mathrm{span} \{ \boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r \}
$$

where $\boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r$ are the first $r$ columns of $L$. In particular, $\boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r$ is a basis of $R(A)$.

---

*Proof*. If $\mathrm{rank}(A) = r$ then only the first $r$ entries of the vector $U \boldsymbol{x}$ are nonzero

$$
U \boldsymbol{x} = \begin{bmatrix} * & * & \cdots & * \\ 0 & \ddots & \ddots & \vdots \\ \vdots & \ddots & * & * \\ 0 & \cdots & 0 & 0 \end{bmatrix} \boldsymbol{x} = \begin{bmatrix} * \\ \vdots \\ * \\ 0 \end{bmatrix}
$$

Therefore

$$
LU \boldsymbol{x} = \begin{bmatrix} & & \\ \boldsymbol{\ell}_1 & \cdots & \boldsymbol{\ell}_n \\ & & \end{bmatrix} \begin{bmatrix} * \\ \vdots \\ * \\ 0 \end{bmatrix} = (*) \boldsymbol{\ell}_1 + \cdots + (*) \boldsymbol{\ell}_r
$$
```

## Rank-Nullity Theorem

```{div} theorem
Let $A$ be an $m \times n$ matrix. Then

$$
\dim(R(A)) + \dim(N(A)) = n
$$

---

*Proof*. The dimension of $N(A)$ is equal to the number of columns of the row echelon form of $A$ *without* a leading nonzero entry, and $\mathrm{rank}(A) = \dim(R(A))$ is equal to the number of columns of the row echelon form of $A$ *with* a leading nonzero entry, and there are $n$ total columns.
```

## Exercises

````{div} exercise
Determine whether or not the set

$$
U = \left\{ \begin{bmatrix} a \\ b \\ c \end{bmatrix} : abc = 0 \right\}
$$

is a subspace of $\mathbb{R}^3$.

```{dropdown} Solution
$U$ is not a subspace because it is not closed under vector addition.
```

````



````{div} exercise
Are the vectors below linearly independent?

$$
A = \begin{bmatrix} 
5 & 2 & 4 \\
-2 & -3 & 5 \\ 
4 & 5 & -7
\end{bmatrix}
$$

```{dropdown} Solution
The RREF of A is 
$$
\begin{bmatrix}
1 & 0 & 2 \\
0 & 1 & -3 \\
0 & 0 & 0
$$ 
This means we have two pivots, thus the vectors are not linearly independent. Equivalently, $Ax = 0$ has a non-trivial solution and hence the vectors are not linearly independent.
```

````

````{div} exercise
Determine the nullity of the given matrix below by appealing to the rank-nullity theorem. Avoid computations.

$$
\begin{pmatrix}
2 & -3 \\
0 & 0 \\
-4 & 6 \\
22 & -33
\end{pmatrix}
$$

```{dropdown} Solution
Row 3 and 4 are multiples of Row 1. Then, the dimension of the column space is 1. By the rank-nullity theorem, $\dim (N(A)) = n - \dim (R(A)) = 2 - 1 = 1$
```

````

````{div} exercise
Determine whether $\mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 \} = \mathrm{span} \{ \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ where

$$
\boldsymbol{u}_1 = \left[ \begin{array}{r} 2 \\ -3 \\ 1 \\ -1 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_2 = \left[ \begin{array}{r} -5 \\ 1 \\ 2 \\ -2 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_3 = \left[ \begin{array}{r} -1 \\ -5 \\ 4 \\ -4 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_4 = \left[ \begin{array}{r} 3 \\ -11 \\ 6 \\ -10 \end{array} \right]
$$

```{dropdown} Solution
$\mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 \} \ne \mathrm{span} \{ \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ since $\boldsymbol{u}_1,\boldsymbol{u}_2,\boldsymbol{u}_4$ are linearly independent.
```

````

````{div} exercise
Let $U = \mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 , \boldsymbol{u}_3 , \boldsymbol{u}_4 \} \subseteq \mathbb{R}^4$ where

$$
\boldsymbol{u}_1 = \left[ \begin{array}{r} 2 \\ 4 \\ 4 \\ 2 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_2 = \left[ \begin{array}{r} 3 \\ 5 \\ 3 \\ 1 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_3 = \left[ \begin{array}{r} 3 \\ 3 \\ -1 \\ -11 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_4 = \left[ \begin{array}{r} 0 \\ 3 \\ 11 \\ -2 \end{array} \right]
$$       

* Find a basis and the dimension of $U$.
* Is $\{ \boldsymbol{u}_1 , \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ a basis of $U$? Explain.

```{dropdown} Solution
Putting the vectors that span U into a matrix A and row reducing that gets us: \\
$$
\begin{bmatrix}
1 & 0 & 0 & 7.5 \\
0 & 1 & 0 & -6 \\
0 & 0 & 1 & 1 \\
0 & 0 & 0 & 0
$$ \\
We see that this 4x4 matrix only has 3 columns as pivot columns, so we can omit $u_{4}$ from the basis.
$\dim(U) = 3$ and $\{ \boldsymbol{u}_1 , \boldsymbol{u}_2 , \boldsymbol{u}_3 \}$ form a basis of $U$.
```

````

````{div} exercise
Let $A = LU$ be the LU decomposition of $A$. Determine whether the statement is **True** or **False**.

* $N(A) = N(U)$
* $\dim (N(A)) = \dim (N(U))$
* $R(A) = R(U)$
* $\dim (R(A)) = \dim (R(U))$

```{dropdown} Solution
* True
* True. Since from the previous question we have that $N(A) = N(U)$, this means that the
two spaces have the same basis and in particular the same number of vectors in their basis and hence their dimensions agree.
* False
* True. By definition, we have that $\dim (R(A)) = \text{rank}(A) = \text{rank}(U) = $\dim (R(U))$.
```

````