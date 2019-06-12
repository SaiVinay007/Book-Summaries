# Chapter 2
## Linear Algebra

#### 2.1 Scalars, Vectors, Matrices and Tensors

Scalar : Its a single number $\in R$ 
Vector : An array of numbers $\in R^n$
Matrix : A 2D array of numbers $\in R^{m \times n}$
Tensor : An array of numbers arranged on a regular grid with a *variable* number of axes is known as a tensor (array with more than 2 axes).
$C_{i,j} = A_{i,j} + b_j $ here b is added to each row of A, this implicit copying of b to many locations is called *broadcasting*

#### 2.2 Multiplying Matrices and Vectors

The matrix product is represented as,
$$C = AB$$
$$C_{i,j} = \sum_
k
A_{i,k}B_{k,j}$$
* We can think of the matrix product C = AB as computing $C_{i,j}$ as the dot product between row i of A and column j of B.

The element-wise product is called Hadamard product and denoted by $A \circ B$ 
* For matrices of different dimensions ($m \times n$ and $p \times q$, where $m \neq p$  or  $n \neq q$) the Hadamard product is undefined.


#### 2.3 Identity and Inverse Matrices


#### 2.4 Linear Dependence and Span

The span of a set of vectors is the set of all points obtainable by linear combination of the original vectors.
A set of vectors is linearly independent if no vector in the set is a linear combination of the other vectors.

#### 2.5 Norms

In machine learning, we usually measure the size of vectors using a function called a norm.
Intutively, the norm of a vector x measures the distance from the origin to the point x.

the $L_p$ norm is,
$$\left\Vert\left (\bf x_{\rm n}\rm\right) \right\Vert = \Big( \sum_i \vert x_i \vert^p \Big)^\frac{1}{p} $$

#### 2.6 Special Kinds of Matrices and Vectors

#### 2.7 Eigendecomposition 

#### 2.8 Singular Value Decomposition

#### 2.9 The Moore-Penrose Pseudoinverse

#### 2.10 The Trace Operator

#### 2.11 The Determinant

#### 2.12 Example: Principal Components Analysis



