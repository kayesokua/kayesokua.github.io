---
layout: post
title: Multivariate Calculus Review
summary: Multivariate Calculus Review
tag: calculus
---


<p><span class="tooltip"><a href="#">Multivariate Calculus</a>
<span class="right bottom"><span class="tooltip-excerpt">A type of math that helps us understand how things change and how they are related to each other when there are multiple variables involved<br>
                      </span><i></i></span></span>is the branch of mathematics that deals with the differentiation and integration of functions of multiple variables. It provides a systematic framework to address <u>how to determine the behavior of functions with multiple inputs and outputs</u>. The questions it tries to solve:</p>



1. [How does a function change as one or more of its inputs change?](# "What happens to one thing if something else changes?")
2. [What is the maximum or minimum value of a function and where does it occur?](# "What is the highest or lowest value of a situation and where does it occur?")
3. [How does the shape of a function look like, and how does it change with the inputs?](# "What does the situation look like and how does it change?")
4. [How do we calculate the area or volume under a function in multiple dimensions?](# "How do we measure the size of a situation when there are multiple parts involved?")
5. [How can we represent a function as a sum of simpler functions?](# "Can we break down a situation into simpler parts?")

Here are some of the important concepts in Multivariate Calculus:

# Partial and Total Derivatives

[Partial Derivatives](# "A measure of how much the function changes as one of its inputs changes, while holding the other inputs constant") is the rate of change of a multivariate function with respect to one variable, holding the other variables constant denoted as:

$$\frac{\partial f(x,y)}{\partial x}$$

**Example**: The tastiness of a cake can be represented by $$f(sugar, flour)$$ where sugar and flour are the amounts of each ingredient you use. Increasing the sugar results to a sweeter taste. The partial derivative of f with respect to sugar tells us how much the cake's tastiness changes with each change in the amount of sugar, while keeping the amount of flour constant. Increasing the flour results to a denser taste. By understanding how each ingredient affects the cake's tastiness, you can make adjustments to the recipe and bake a tastier cake!

**Total Derivative** is the rate of change of a multivariate function at a point, taking into account all of its variables. Unlike partial derivatives, it considers the change in all variables at the same time.

$$\frac{df(x,y)}{dx} , \frac{df(x,y)}{dy}$$


**Example**: If you change the amount of sugar and the amount of flour over time, the cake's tastiness is also changing. The total derivative of f with respect to time tells us how much the cake's tastiness is changing over time, taking into account both the changes in sugar and flour.  By knowing the total derivative, you can make decisions on how to mix the ingredients and bake the cake to achieve the optimal tastiness.

# Implicit Function Theorem
Implicit Function Theorem is a theorem that states that, under certain conditions, a implicitly defined function can be locally expressed as an explicit function of some of its variables.

# Taylor Series
Taylor Series is an expansion of a function into an infinite sum of terms, where each term is a polynomial in the variables and their derivatives at a given point.

# Vector Calculus
Vector Calculus is the study of differential and integral calculus with vectors and vector fields, including concepts such as the gradient, divergence, and curl.

# Multiple Integrals
Multiple Integrals is the integration of functions of multiple variables over regions in multiple dimensions.

# Partial differentiation
# Directional derivatives
# Calculation and geometric interpretation of vectors and matrices in multivariate calculus
## Gradient

Gradient is the vector of partial derivatives of a function, which points in the direction of maximum rate of increase of the function. It represents the direction and magnitude of the maximum rate of increase of a function. It is a vector that points in the direction of the steepest ascent of a function, and its magnitude gives the maximum rate of increase of the function in that direction. Gradient can be denoted as:

$$ ∇f = \left(\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z}\right) $$

The gradient of a function is used to answer the following question: "In which direction does the function increase the fastest, and by how much?"

**Example:** Imagine you are at the top of a hill, and you want to find the direction in which you can walk to reach the bottom of the hill as quickly as possible. The gradient of the hill in this case would represent the direction in which the hill slopes the steepest downwards. It would point in the direction that you would need to walk in order to get to the bottom of the hill in the shortest time.

```python
import numpy as np

def f(x):
    return x[0]**2 + x[1]**2

def gradient(f, x):
    return np.array([2*x[0], 2*x[1]])

x = np.array([1, 2])
grad = gradient(f, x)
print(grad)
```

## Jacobian
Jacobian Matrix is the matrix of partial derivatives of a vector-valued function, which describes the linear transformation from one space to another.

## Hessian
Hessian Matrix is a square matrix of second partial derivatives of a function, which describes the curvature of the function at a point. The significance of the second order lies in its ability to describe the curvature of a curve, the concavity of a surface, or the stability of a system. By analyzing second-order information, we can better understand the behavior of a function or system over time or space. 

Hessian matrix helps us understand how the surface changes as we move around in multiple dimensions.
# Chain rule for multivariate functions