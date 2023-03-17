---
layout: post
title: Scalars, Vectors, Matrices, Tensors
summary: A linear algebra review on fundamental mathematical objects and its properties - scalars, vectors, matrices and tensors
tag: linear-algebra
---

Scalars, vectors, matrices, and tensors are fundamental mathematical objects used in linear algebra to represent and manipulate data in a concise and organized manner. In order to extract meaningful results, we need to have a solid understanding of its properties, representations and operations. [^1]

* TOC
{:toc}

# Scalar Properties and Operations
**Scalars** are single-value entities that can be are used to represent a magnitude or size of a quantity, but not its direction. Common applications include measuring length, area, or volume. Scalars can be used to manipulate the magnitude of another scalar, vectors, matrices and tensors.

## Algebraic Properties of Scalars

| Properties | Notation |
| --- | --- |
| Commutative properties of addition and multiplication | $$a + b = b + a$$ or $$a * b = b * a$$ |
| Associative properties of addition and multiplication | $$(a + b) + c =  a+ (b + c)$$ or $$(ab)c = a(bc)$$ |
| Distributive property | $$ a * (b + c) = a * b + a * c $$ |
| Additive identity | $$a + 0 = a$$ |
| Additive inverse | $$a + (-a) = 0$$ |
| Multiplicative identity | $$a * 1 = a$$ |
| Multiplicative inverse | For each scalar a (except 0) - $$\frac{1}{a}$$ and $$\frac{1}{a} * a = 1 $$|


## Examples

```python
# Scalar addition
scalar = 5
vector = [1, 2, 3]
result = [scalar + x for x in vector]
print(result) # Output: [6, 7, 8]

# Scalar multiplication
scalar = 2
vector = [1, 2, 3]
result = [scalar * x for x in vector]
print(result) # Output: [2, 4, 6]

# Scalar division
scalar = 2
vector = [2, 4, 6]
result = [x / scalar for x in vector]
print(result) # Output: [1.0, 2.0, 3.0]
```

# Vector Properties and Operations
**Vectors** are arrays of numbers (or list), typically represented as a column or a row, that can be used to represent points and direction in space. Vectors are mathematical objects that have magnitude and direction. They are often used to represent physical quantities such as force, velocity, or displacement.

| Algebraic Properties | Notation |
| --- | --- |
| Commutativity | If $$\vec{a}$$ and $$\vec{b}$$ are vectors, then $$\vec{a} + \vec{b} = \vec{b} + \vec{a} $$ |
| Associativity  | $$(\vec{a} + \vec{b}) + \vec{c} = \vec{a} + (\vec{b} + \vec{c})$$|
| Distributivity| If $$\vec{a}$$ is a vector and $$k$$ is a scalar, then $$k (\vec{a} + \vec{b}) = k\vec{a} + k\vec{b}$$|
| Additive identity| There exists a $$0$$ vector, then $$\vec{a} + 0 = 0 + \vec{a} = \vec{a}$$|
| Additive inverse| For every vector a, there exists another vector -a such that a + (-a) = (-a) + a = 0.|
| Scalar multiplication| If a is a vector and k is a scalar, then ka is a vector that points in the same direction as a but has magnitude k times greater |
| Multiplicative identity| $$1\vec{a} = \vec{a}(1) = \vec{a}$$ |
| Multiplicative inverse | For non-zero vectors, there exists a reciprocal scalar k such that $$k\vec{a} = 1 $$, where k = 1/a |

## Eigenvalues and Eigenvectors
An eigenvalue is a scalar that represents the stretching factor of a linear transformation, while an eigenvector is a non-zero vector that is only stretched (but not rotated) by a linear transformation.

## Orthogonality and Orthonormality

Orthogonality: Two vectors are orthogonal if they are perpendicular to each other, meaning they form a 90-degree angle. This property is used in many areas including signal processing, where signals can be orthogonally decomposed into their components to simplify analysis.

Orthonormality: Orthonormal vectors are orthogonal vectors with a magnitude of 1. They are commonly used in numerical analysis and are the basis for many methods, such as the Fourier Transform and PCA (Principal Component Analysis) in data science.

Example: Orthogonality in computer graphics is used to represent 3D objects in a 2D image in a way that preserves their angles and proportions, making the objects appear as three-dimensional even though they are actually represented in 2D.

# Matrix Properties and Operations

**Matrices** are arrays of numbers that have both row and column dimensions, and are commonly used to represent linear transformations and systems of linear equations. They also have mathematical operations such as addition, scalar multiplication, and matrix multiplication that allow us to perform complex transformations and analysis.


## Determinant
Determinant: The determinant of a matrix is a scalar value that represents the magnitude of a linear transformation, and is used to determine the invertibility of a matrix.

## Inverse matrix
The inverse of a matrix is a special matrix that, when multiplied with the original matrix, results in the identity matrix. If a matrix has an inverse, it is considered to be invertible.

## Rank
The rank of a matrix is the number of linearly independent rows (or columns) in the matrix, and is used to determine the dimension of the subspace spanned by the columns (or rows) of the matrix.

## Null space
The null space of a matrix is the set of all vectors that are mapped to the zero vector under a linear transformation represented by the matrix.
## Inverses and Systems of Equations
## Four Fundamental Subspaces
## Adjacency Matrices
# Matrix Properties and Operations

# Tensors Properties and Operations

Tensors are multi-dimensional arrays of numbers that can be used to represent higher order relationships and data in a compact form. They are used in areas such as machine learning, computer vision, and physics to perform complex data manipulation and analysis.

# References

[^1]: Brilliant Org (2023). Linear Algebra. https://brilliant.org/courses/linear-algebra/.
