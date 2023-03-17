---
layout: post
title: Vector Spaces
summary: A linear algebra review on vector spaces, axioms, spans and subspaces
tag: linear-algebra
---

Vectors are elements in a vector space represented as $$v \in V $$. Two operations can be performed on these elements: **vector addition** and **scalar multiplication**. To establish the existence of vectors, we need to define the properties of a vector space. The conditions were already outlined by Italian mathematician Giuseppe Peano in 1888, and now it's important to understand each axiom. [^4] [^7]

# Vector Space Axioms

You'll find different rephrased versions of the axioms on the internet. This notebook uses [lecture notes from University of Puget Sound mathematics professor, Beezer](http://linear.ups.edu/html/section-VS.html). [^2]

Given that $$u,v,w$$ are arbitary numbers in $$V$$ and $$\alpha,\beta$$ are real numbers in $$\mathbb{R}$$:


Axiom | Notation | In Context
--- | --- | ---
Additive Closure | If $$u,v \in V$$, then $$u+v \in V$$ | For every $$u,v$$ in $$V$$, one can have additive closure means that the sum of these 2 vectors are  also an element of $$V$$
Scalar Closure | If $$\alpha \in \mathbb{R}$$ and $$u \in V$$, then $$\alpha{u} \in V$$ | Since $$\alpha$$ in $$\mathbb{R}$$ is a real number, one can have a scalar multiplication that is denoted as $$\alpha{u} \in V$$
Commutativity | If $$u,v \in V$$, then $$ u+v \in V $$ | For every $$u,v$$ in $$V$$, we have commutativity of vector addition which can be written as $$u+v=v+u$$
Additive Associativity | If $$u,v,w \in V$$, then $$ u+(v+w)=(u+v)+w $$ | For every $$u,v$$ in $$V$$, we have associativity of vector addition which can be written as $$ u+(v+w)=(u+v)+w$$
Zero Vector | $$u+0=u$$ exists in every $$u \in V$$ | For every $$u$$ in $$V$$, there exists a $$0$$, called **zero vector**, therefore one can have an identity element of vector addition.
Additive Inverses | $$-u+(u)=0$$ exists in every $$u \in V$$ | For every $$u$$ in $$V$$, there exists a $$-u$$, called **additive inverse of** $$u$$, therefore one can have an inverse elements of vector addition.
Scalar Multiplication Associativity | If $$\alpha,\beta \in \mathbb{R}$$ and $$u \in V$$, then $$\alpha(\beta{u}) = \alpha\beta{u}$$ | Since that $$\alpha , \beta$$ in $$\mathbb{R}$$ are a real number, for every $$u$$ in $$V$$, one can have compatibility of scalar multiplication with field multiplication
Distributivity across Vector Addition | If $$\alpha,\beta \in \mathbb{R}$$ and $$u,v \in V$$, then $$\alpha(u+v) = \alpha{u} + \alpha{v}$$ | Since that $$\alpha$$ in $$\mathbb{R}$$ is a real number, for every $$u,v \in V$$, one can have distributivity of scalar multiplication with respect to vector addition written as $$\alpha(u+v) = \alpha{u} + \alpha{v}$$
Distributivity across Scalar Addition | If $$\alpha,\beta \in \mathbb{R}$$ and $$u \in V$$, then $$(\alpha+\beta)u = \alpha{u} + \beta{u}$$ | Since that $$\alpha, \beta$$ in $$\mathbb{R}$$ are real numbers, for every $$u \in V$$, one can have distributivity of scalar multiplication with respect to field addition
Scalar Identity  | $$1(u)=u$$ exists in every $$u \in V$$ | For every $$u$$ in $$V$$, there exists a $$1$$, called <b>multiplicative identity</b>, therefore one can have an identity element of scalar multiplication

## Example: Euclidean Space 

A Eucledian space is a vector space with any dimension and is based on coordinates.$$\mathbb{R}^1$$ represents a real number line, $$\mathbb{R}^2$$ represents a cartesian plane, and $$\mathbb{R}^3$$ is a 3D space, $$\mathbb{R}^n$$ represents a n-dimensional space. If we have the set { $$(x,2x)$$: $$x$$ is a real number }, how do we prove in detail that it is indeed a vector space?

Given that set, we can assume $$ (x_{1},2x_{1}),(x_{2},2x_{2})$$ ... $$(x_{n},2x_{n}) \in \mathbb{R}^2 $$ and $$\alpha, \beta $$ ... $$\in \mathbb{R}$$

Axiom | Proof
Additive Closure | If $$x_{1} = 1, x_{2} = 3 $$ then $$({x_{1}},2{x_{1}}),({x_{2}},2{x_{2}})$$ is $$(1,2),(3,6)$$. The sum will be $$(4,8)$$ which will be found in $$ \in \mathbb{R}^2 $$
Scalar Closure | Since $$\alpha$$ is a real number, one can have a scalar multiplication that is denoted as $$\alpha({x_{1}},2{x_{1}}) \in \mathbb{R}^2$$
Commutativity | $$({x_{1}},2{x_{1}}) + ({x_{2}},2{x_{2}}) = ({x_{2}},2{x_{2}}) + ({x_{1}},2{x_{1}})$$
Additive Associativity|$$\color{blue}(({x_{1}},2{x_{1}}) + ({x_{2}},2{x_{2}})\color{blue})$$ + $$({x_{3}},2{x_{3}})$$ = $$({x_{1}},2{x_{1}})$$ + $$\color{blue}(({x_{2}},2{x_{2}}) + ({x_{3}},2{x_{3}})\color{blue})$$
Zero Vector| If $$x = 0$$ then $$(x,2x) = (0,2(0))$$, therefore the solution is $$(0,0)$$
Additive Inverses|$$(x,2x) + (-x,2(-x)) = (x,2x) + (-x,-2x)) = 0 $$
Scalar Multiplication Associativity|$$\alpha((x\beta,2x\beta))) = \beta((x\alpha,2x\alpha)) = ((x\alpha\beta,2x\alpha\beta)) $$
Distributivity across Vector Addition|$$\alpha(({x_{1}},2{x_{1}})+({x_{2}},2{x_{2}})) = \alpha({x_{1}},2{x_{1}}) + \alpha({x_{2}},2{x_{2}})$
Distributivity across Scalar Addition|$$(\alpha+\beta)({x_{1}},2{x_{1}}) = \alpha({x_{1}},2{x_{1}}) + \beta({x_{1}},2{x_{1}})$$
Scalar Identity|$$1(x,2x) = (1({x}),1(2x)) = (x,2x) $$|

With this, we can conclude that the set $$(x,2x)$$ is indeed a vector space. [^3]

## Example and Non-example: Polynomial Sets

A polynomial is a mathematical expression of one or more algebraic terms each of which consists of a constant multiplied by one or more variables raised to a nonnegative integral power such as $$a + bx + cx^2$$ [^5]. When does a polynomial set becomes a vector space and not?

The set of all polynomials of degree exactly 3 is not a vector space. Why is that?

We first write the function of the form as $$ P_3 = \{\alpha_3 x^3 + \alpha_2 x^2 + \alpha_1 x + \alpha_0\} $$


Axiom | Proof
--- | ---
Additive Closure | It cannot be closed under addition. For example, if n = 4, $$x^2+x^4$$ and  $$−x^4$$ are both 4th degree polynomials however their sum is not. 
Zero Vector | If $$x = 0$$ then $$(x,2x) = (0,2(0))$$, therefore the solution is $$(0,0)$$

Why is $$P_n$$, a polynomnial with a degree set $$n$$, coefficients from $$\mathbb{R}$$, a vector space?

We write the polynomial of degree $$n$$ as the function of the form: $$ P(x) = \alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n $$ and where $$\alpha, \beta$$ are the coefficients from $$\mathbb{R}$$
    
We write the polynomial of degree $n$ as the function of the form: $$ P(x) = \alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n $$ and where $$\alpha, \beta$$ are the coefficients from $$\mathbb{R}$$

Axiom | Proof
Additive Closure | If $$x = 1 $$ then $$({x_{1}},2{x_{1}}),({x_{2}},2{x_{2}})$$ is $$(1,2),(3,6)$$. The sum will be $(4,8)$ which will be found in $$ \in \mathbb{R}^2 $$
Scalar Closure | Since $$\alpha$$ is a real number, one can have a scalar multiplication that is denoted as $$\alpha({x_{1}},2{x_{1}}) \in \mathbb{R}^2$$
Commutativity | $$({x_{1}},2{x_{1}}) + ({x_{2}},2{x_{2}}) = ({x_{2}},2{x_{2}}) + ({x_{1}},2{x_{1}})$$
Additive Associativity| $$\color{blue}(({x_{1}},2{x_{1}}) + ({x_{2}},2{x_{2}})\color{blue})$$ + $$({x_{3}},2{x_{3}})$$ = $$({x_{1}},2{x_{1}})$$ + $$\color{blue}(({x_{2}},2{x_{2}}) + ({x_{3}},2{x_{3}})\color{blue})$$
Zero Vector| If $$x = 0$$ then $$(x,2x) = (0,2(0))$$, therefore the solution is $$(0,0)$$
Additive Inverses | $$(x,2x) + (-x,2(-x)) = (x,2x) + (-x,-2x)) = 0 $$
Scalar Multiplication Associativity| $$\alpha((x\beta,2x\beta))) = \beta((x\alpha,2x\alpha)) = ((x\alpha\beta,2x\alpha\beta)) $$
Distributivity across Vector Addition| $$\alpha(({x_{1}},2{x_{1}})+({x_{2}},2{x_{2}})) = \alpha({x_{1}},2{x_{1}}) + \alpha({x_{2}},2{x_{2}})$$
Distributivity across Scalar Addition|$$(\alpha+\beta)({x_{1}},2{x_{1}}) = \alpha({x_{1}},2{x_{1}}) + \beta({x_{1}},2{x_{1}})$$
Scalar Identity| $$1(x,2x) = (1({x}),1(2x)) = (x,2x) $$

The equation below satisfies the vector addition [^2]

$$(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n) + (\beta_0 + \beta_1x + \beta_2x^2 + · · · + \beta_{n}x^n)$$
= $$(\alpha_0 + \beta_0) + (\alpha_1 + \beta_1)x + (\alpha_2 + \beta_2)x^2 + (\alpha_n + \beta_n)x^n$$

$$(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n) + (0 + 0 + 0 ... + 0)$$
= $$(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n)$$

The equation below satisfies the scalar multiplication

$$0(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n) = 0(\alpha_0) + 0(\alpha_1x) + 0(\alpha_2x^2) + · · · + 0(\alpha_{n}x^n) = 0$$

$$ 1(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n) = 1(\alpha_0) + 1(\alpha_1x) + 1(\alpha_2x^2) + · · · + 1(\alpha_{n}x^n)$$

$$ 2(\alpha_0 + \alpha_1x + \alpha_2x^2 + · · · + \alpha_{n}x^n) = 2(\alpha_0) + 2(\alpha_1x) + 2(\alpha_2x^2) + · · · + 2(\alpha_{n}x^n)$$

The equation below satisfies the scalar multiplication:

$$2(\alpha_0 + \alpha_1x + \alpha_2x^2 + ... + \alpha_{n}x^n) = 2(\alpha_0) + 2(\alpha_1x) + 2(\alpha_2x^2) + · · · + 2(\alpha_{n}x^n)$$

$$ 1(\alpha_0 + \alpha_1x + \alpha_2x^2 + ... + \alpha_{n}x^n) = 1(\alpha_0) + 1(\alpha_1x) + 1(\alpha_2x^2) + · · · + 1(\alpha_{n}x^n)$$

# Real World Application

Vector spaces have numerous real-world applications, including:

1. **Vector-Based Graphics in Computer Graphics**: In computer graphics, vector spaces are used to represent images and shapes as vectors for manipulation and rendering. For example, a 2D image can be represented as a set of vectors in a 2D vector space, where each vector corresponds to a point in the image. These vectors can be transformed and manipulated using linear transformations, such as translation, rotation, and scaling, to create new images. This representation is particularly useful in computer graphics because it allows images to be transformed and manipulated with precise control, while maintaining their geometric properties. Additionally, vector representations can be efficiently processed by computer graphics hardware, making them a key tool in the creation and rendering of computer graphics. [^9] [^10]

2. **Vector Space Model** (VSM) is a mathematical model used in information retrieval and NLP that represents documents and query terms as vectors in a high-dimensional space. The magnitude of each dimension reflects the term frequency in the document or query and the direction reflects the term weight, which represents its importance. VSM calculates similarity between documents and queries by measuring the angle between the document and query vectors, where smaller angles indicate greater similarity and higher relevance. VSM uses the theory of vector spaces to represent and compare documents and queries, making it a useful tool in information retrieval and NLP. [^1] [^8]

3. **Others**:
* Economics: Modeling supply and demand using vectors
* Robotics: Representing position and orientation of robots using vectors
* Engineering: Solving systems of linear equations using vector spaces
* Navigation: Calculating the shortest path between two points using vector spaces.

The significance of learning the theory and axioms of vector spaces lies in the ability to make logical deductions, prove theorems, and establish relationships that hold true for any example of a vector in a vector space.

# Subspaces and Span

* **Span** refers to the set of all possible linear combinations of a set of vectors. It represents the set of all possible vectors that can be created from the original set of vectors.

* **Basis** is a set of vectors that are used as the building blocks to create any vector in the span. They are unique, linearly independent, and can be used to define any vector in the span. Think of it like an "alphabet" of vectors, from which you can create any other vector. By using the basis vectors, we can represent any vector in the span as a linear combination of the basis vectors.

# Linear Independence
# Basis and Dimension
# Dot Products and Inner Products
# Least Squares

# Application: Coding Theory
# Application: Graph Theory I

# References

[^1]: Vector Space Model (2020). [Wikipedia](https://en.wikipedia.org/wiki/Vector_space_model)
[^2]: Beezer, Rober. (2012). A First Course in Linear Algebra. University of Puget Sound. [www.linear.ups.edu](http://linear.ups.edu/html/section-VS.html)
[^3]: Math Exchange (2011). Prove in full detail that the set is a vector space. https://math.stackexchange.com/questions/49733/prove-in-full-detail-that-the-set-is-a-vector-space/49735
[^4]: Davis. (2007) University of California. https://www.math.ucdavis.edu/~anne/WQ2007/mat67-Le-Vector_Spaces.pdf
[^5]: Khan Academy (2020). Vectors and Spaces. https://www.khanacademy.org/math/linear-algebra/vectors-and-spaces
[^6]: Brilliant.(2022). Vector Spaces. https://brilliant.org/wiki/vector-space/
[^7]: Britannica. (2023). Vector Spaces. https://www.britannica.com/science/vector-space
[^8]: Venkat N. Gudivada, C.R. Rao. (2018). Computational Analysis and Understanding of Natural Languages: Principles, Methods and Applications. Chapter 11. https://www.sciencedirect.com/science/article/abs/pii/S0169716118300245
[^9]: Wikipedia. (2023). Vector graphics. https://en.wikipedia.org/wiki/Vector_graphics
[^10]: Lutkevich, Ben. (2021). Vector Graphics. TechTarget. https://www.techtarget.com/whatis/definition/vector-graphics