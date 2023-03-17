---
layout: post
title: System of Linear Equations
summary: A linear algebra review on systems of linear equations and its characteristics, with simple and advanced applications
tag: linear-algebra
---
Linear Algebra is a fascinating part of mathematics that explores linear systems of equations and the transformations they undergo. It offers a way to understand the connections between variables and make accurate predictions about how systems behave based on these connections. In this notebook, we will deep dive into the concept of system of linear equations.

* TOC
{:toc}

# System of Linear Equations
A system of linear equations (SLE) is a set of linear equations with multiple variables. These equations represent the relationships between the variables and their corresponding values in real-life situations. The equations in a SLE have the form of $$y = mx + b$$, where $$m$$ and $$b$$ are constants and $$x$$ and $$y$$ are variables. [^1]

## Validating Linear Equations

To make further sense of SLE, you need to **confirm if the linear equation follows a linear pattern**. [^1] [^3] These are the following conditions that makes a system valid:

| Conditions | Non-Example |
| --- | --- |
| The number of equations is equal to the number of unknown variables | $$a+b+c=3; a=2 $$
| The equations are linear, i.e., they are a combination of variables and constants but not higher powers or non-linear functions | $$x^2 + y^2 = 4$$ |
| The coefficients in the equations are not a function of the variables | $$x*y = 1$$ |
| The slope or y-intercept is constant in all equations | $$y = x^2 + 1$$ |

Other inuitive methods to determine if the relationship between variables follows a linear pattern:

**Graphical analysis**: Visually examine a scatter plot of the data points to see if they align in a straight line pattern. If they do, it is likely that the relationship between the variables follows a linear pattern. [^1]

```python
import matplotlib.pyplot as plt
import numpy as np

# Valid SLE
x = np.linspace(0, 10, 10)
y = 2 * x + 1
z = -x + 3

plt.scatter(x, y)
plt.scatter(x, z)
plt.plot(x, y)
plt.plot(x, z)
plt.title("Valid System of Linear Equations")
plt.show()

# Invalid SLE
x = np.linspace(0, 10, 10)
y = x**2 + 1
z = 2 * x + 1

plt.scatter(x, y)
plt.scatter(x, z)
plt.plot(x, y)
plt.plot(x, z)
plt.title("Invalid System of Linear Equations")
plt.show()
```

In the first plot, the relationship between the variables is linear because the data points form a straight line pattern. In the second plot, the relationship between the variables is not linear because the data points form a curved pattern (or can simply be described as quadratic). [^2]

**Constant rate of change**: In a linear relationship, the rate of change between the variables remains constant. This means that if you plot the values on a graph, the line should be straight. [^2]

**Proportional relationship**: In a linear relationship, the variables are proportional to each other. This means that if you double one variable, the other variable will also double.

**Equal increments**: In a linear relationship, equal increments in one variable result in equal increments in the other variable.

## Zero, Unique, and Infinite Solutions

**The nature of linear equations can only have 0, 1, or infinite solutions.**

| Solutions | Representation | Implication
| --- | --- | --- |
Zero (0) | lines are parallel | The system is overdetermined or contains contradiction |
Unique(1) | lines intersect at exactly one point| The system contains a well-defined solution | 
Infinite(∞) | lines are coincident | There is an infinite number of combinations of values for the variables that satisfies all the equations simultaneously, indicating a range of solutions.

# Simple Application: Meal Planning

An athlete is trying to create a balanced breakfast plan with a total of 245 calories, 6g of protein, and 7g of fat using the three different cereals available: Cheerios, Toast Crunch, and Rice Krispies. Each cereal has a different nutritional value, as shown in the table.

Cereal Brand | Calories | Protein | Fat
--- | --- | --- | ---
Cheerios | 120 | 4 | 2
Toast Crunch |130 | 3 | 5
Rice Krispies | 105 | 1 | 2

To create the breakfast plan, we need to determine the amount of each cereal to use (the unknown quantity). For each nutrition requirement, we can write one linear equation: 

$$\Large 120c + 130t + 105r = 245 $$

$$\Large 4c + 3t + r = 6 $$

$$\Large 2c + 5t + 2r = 7 $$

where $$c$$ represents Cheerios, $$t$$ represents Toast Crunch, and $$r$$ represents Rice Krispies. The goal is to find the values of c, t, and r that satisfy all three equations, which represent a valid solution for the breakfast plan that meets all nutritional requirements. We will solve this using a **Geometrical Interpretation**, **Scatter Plot**, and **Gaussian Elimination Method**

Here's a [video](https://www.youtube.com/watch?v=5tB7y_piK6o) to help you visualise plotting 3-variable linear equations.

## Graphical Analysis

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Define the range of values for x, y and z
x = np.linspace(0, 20, 100)
y = np.linspace(0, 20, 100)
x, y = np.meshgrid(x, y)

# Define the z values using the equations
z1 = 245 - 120 * x - 130 * y - 105 * (20 - x - y)
z2 = 6 - 4 * x - 3 * y - (20 - x - y)
z3 = 7 - 2 * x - 5 * y - 2 * (20 - x - y)

# Plot the 3D scatter and surface
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.scatter(x, y, z1)
ax.scatter(x, y, z2)
ax.scatter(x, y, z3)
ax.plot_surface(x, y, z1, color='red', alpha=0.2)
ax.plot_surface(x, y, z2, color='green', alpha=0.2)
ax.plot_surface(x, y, z3, color='blue', alpha=0.2)
plt.show()
```
This plot confirms that the system has a unique solution.

## Scatter Plot

```python
calories = np.array([120, 130, 105])
protein = np.array([4, 3, 1])
fat = np.array([2, 5, 2])
X = np.array([calories, protein, fat]).T

plt.scatter(X[:,0], X[:,1])
plt.scatter(X[:,0], X[:,2])
plt.title("Scatter Plot of Cereal Data")
plt.xlabel("Calories")
plt.ylabel("Protein/Fat")
plt.show()
```
This plot confirms that the system has a unique solution.

## Rouché-Capelli Theorem
Another way to analyze the system for compatibility is applying the **Rouché-Capelli theorem**. This theorem states that a system of linear equations with n variables has a solution if and only if the rank of its coefficient matrix A is equal to the rank of its augmented matrix. If n = rank(A), the solution is unique; otherwise there are infinitely many solutions.

$$e^{ix} = \cos{x} + i\sin{x}$$

$$ A = \begin{bmatrix} 120 & 130 & 105 \\ 4 & 3 & 1 \\ 2 & 5 & 2 \end{bmatrix} = 3 $$

$$ A|B = \begin{bmatrix} 120 & 130 & 105 \\ 4 & 3 & 1 \\ 2 & 5 & 2 \end{bmatrix} \begin{bmatrix} 245 \\ 6 \\ 7 \end{bmatrix} = 3 $$

The number of unknown quantities matches the rank of the matrix, confirming the system has a unique solution.

Finding the rank of matrix [here](https://www.youtube.com/watch?v=HZy-sFsCCxI).

## Reduced Row Echelon Form 

The Reduced Row Echelon Form (RREF) is a method for solving systems of linear equations using matrices. In this method, we transform the augmented matrix of the system into a row echelon form which is a triangular matrix where all entries below the leading 1 in each row are 0. To solve the system using RREF, we perform the following steps:

* **Write the augmented matrix** for the system of linear equations

$$\Large A\vec{x} = \vec{b}$$

$$\Large \begin{bmatrix} 120 & 130 & 105 \\ 4 & 3 & 1 \\ 2 & 5 & 2 \end{bmatrix} \begin{bmatrix} c \\ t \\ r \end{bmatrix} = \begin{bmatrix} 245 \\ 6 \\ 7 \end{bmatrix} $$

* **Perform row operations** to transform the augmented matrix into row echelon form. [You can use this solver provided by OnlineMSchool](https://onlinemschool.com/math/assistance/equation/gaus/)
* **Back-substitute the values of the variables** from bottom to top to obtain the solution.


```python
def rref(A):
    A = np.array(A, dtype=np.float64)
    m, n = A.shape
    lead = 0
    for r in range(m):
        if lead >= n:
            return A
        i = r
        while A[i, lead] == 0:
            i += 1
            if i == m:
                i = r
                lead += 1
                if lead == n:
                    return A
        A[[i, r]] = A[[r, i]]
        lv = A[r, lead]
        A[r] /= lv
        for i in range(m):
            if i != r:
                lv = A[i, lead]
                A[i] -= lv * A[r]
        lead += 1
    return A

A = [[120, 130, 105, 245], 
     [4, 3, 1, 6], 
     [2, 5, 2, 7]]

rref_A = rref(A)
```

$$\Large \begin{bmatrix} c \\ t \\ r \end{bmatrix} = \begin{bmatrix} \frac{2}{3} \\ 1 \\ \frac{1}{3} \end{bmatrix} $$

## Gaussian Elimination Method

The Gaussian Elimination Method is a process used to solve a system of linear equations (SLE) by converting the SLE into an upper triangular matrix, and then solving for the unknown variables. It works by transforming the original matrix of coefficients into an upper triangular matrix by performing row operations that eliminate the elements below the main diagonal. This can be done by multiplying a row by a non-zero constant, swapping two rows, or adding/subtracting a multiple of one row to another. The unknown variables can then be solved by back-substitution, where the values of the unknowns are found by starting from the last equation and working backwards to the first equation. [^2]

```python
def gaussian_elimination(A, b):
    n = len(b)
    # Augmenting the matrix with the identity matrix
    Ab = np.c_[A, b]
    for i in range(n):
        # Find the maximum element in the current column
        max_element = abs(Ab[i][i])
        max_row = i
        for j in range(i + 1, n):
            if abs(Ab[j][i]) > max_element:
                max_element = abs(Ab[j][i])
                max_row = j
        # Swap the current row with the row containing the maximum element
        if max_row != i:
            Ab[i], Ab[max_row] = Ab[max_row], Ab[i]
        # Perform row operations to eliminate the elements below the current pivot
        for j in range(i + 1, n):
            m = Ab[j][i] / Ab[i][i]
            for k in range(i, n + 1):
                Ab[j][k] = Ab[j][k] - m * Ab[i][k]
    # Perform backward substitution to find the solution
    x = np.zeros(n)
    for i in range(n - 1, -1, -1):
        x[i] = (Ab[i][n] - np.dot(Ab[i, i + 1:n], x[i + 1:n])) / Ab[i][i]
    return x

A = np.array([[120, 130, 105], 
              [4, 3, 1], 
              [2, 5, 2]])

b = np.array([245, 6, 7])
```
$$\Large \begin{bmatrix} c \\ t \\ r \end{bmatrix} = \begin{bmatrix} \frac{2}{3} \\ 1 \\ \frac{1}{3} \end{bmatrix} $$

## Python's Sympy

Sympy is a popular Python library for symbolic mathematics, and it can be used to solve systems of linear equations. Here's an example of how to solve a system of linear equations using Sympy:

```python
import sympy

# Define variables for the linear equations
C, T, R = sympy.symbols('C T R')

# Define the linear equations
equations = [
    120 * C + 130 * T + 105 * R - 245,
    4 * C + 3 * T + R - 6,
    2 * C + 5 * T + 2 * R - 7
]

# Use the linsolve function to find the solution to the system of linear equations
linsol = sympy.linsolve(equations, (C, T, R))

# Print the solution
print(linsol)
```
The solution is {c: 2/3, t: 1, r: 1/3}.

# Advanced Application: Supply Chain Optimization

Linear programming is a mathematical optimization technique that involves finding the best possible solution to a problem by maximizing or minimizing a linear objective function subject to constraints represented by a system of linear equations or inequalities. In other words, it's a way to solve problems that involve making the best decision given a set of limitations. This method provides a framework for businesses to find the best solution that maximizes or minimizes an objective function while taking into consideration constraints represented by linear equations or inequalities. [^5]

One real-life advanced use case of linear programming is in supply chain optimization.

Suppose a company produces two products A and B, using two raw materials X and Y. The company has limited resources such as production capacity, raw material stock and budget to produce these products. The objective is to maximize the profit by producing the products such that the constraints are satisfied. [^4] [^5]

The objective function can be represented as:

Maximize: $$Z = 40A + 50B$$

Subject to the constraints:

$$2A + 3B <= 1000$$ (Production capacity of raw material X)

$$3A + 2B <= 800$$ (Production capacity of raw material Y)

$$A <= 200$$ (Availability of raw material X)

$$B <= 150$$ (Availability of raw material Y)

$$A, B >= 0$$ (Non-Negativity constraints)

Here, the variables A and B represent the number of products A and B produced and the objective function Z represents the profit to be maximized.

## Using PuLp

This problem can be solved using linear programming with Python, using a library such as Pulp or scipy.optimize. [^6]

```python
from pulp import *

# Define the problem
prob = LpProblem("Supply Chain Optimization", LpMaximize)

# Define variables
A = LpVariable("A", lowBound=0, cat='Continuous')
B = LpVariable("B", lowBound=0, cat='Continuous')

# Define the objective function
prob += 40 * A + 50 * B

# Define the constraints
prob += 2 * A + 3 * B <= 1000
prob += 3 * A + 2 * B <= 800
prob += A <= 200
prob += B <= 150
```

# References

[^1]: The MathWorks, Inc. (2022). Systems of Linear Equations. https://www.mathworks.com/help/matlab/math/systems-of-linear-equations.html
[^2]: Karp, Dagan. (2012). Lectures of Linear Algebra. Harvey Mudd College. https://www.math.hmc.edu/~dk/math40/lecture_notes.html
[^3]: Khan Academy. (2022). Algebra Basics. https://www.khanacademy.org/math/algebra-basics
[^4]: Saci, Samir. (2022). Supply Chain Process Optimization Using Linear Programming. Towards Data Science. [https://towardsdatascience.com/](https://towardsdatascience.com/supply-chain-process-optimization-using-linear-programming-b1511800630f)
[^5]: Brilliant Org. (2022). Linear Programming. https://brilliant.org/wiki/linear-programming/
[^6]: PuLP. (2009). Optimization with PuLP. https://coin-or.github.io/pulp/