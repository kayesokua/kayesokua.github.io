---
layout: post
title: Data Structures + Algorithms
summary: A reviewer for data structures, algorithms, growth analysis, and examples
tag: data-structures-algorithms
---
Understanding data structures and algorithms is essential for computer science and software engineering. It enables programmers to efficiently store and manipulate data, and solve complex problems through the use of optimized algorithms. By mastering these concepts, developers can write better code, improve system performance, and ultimately deliver higher quality software products.

* TOC
{:toc}

## Fundamental Concepts

A summary of fundamental concepts from the resources found below. [^1] [^2] [^3] [^4] [^5] [^6] [^7]

1. **Data Structures** are systems that we use to store, retrieve, or manipulate data. Nodes are the building blocks of a data structure and can be of two types - linear and non-linear. Linear data structures include arrays, stacks, queues, and linked lists. Non-linear data structures include trees and graphs.
2. **Algorithms** are a set of rules that guide the program to perform specific tasks such as searching, sorting, inserting, or deleting data. The characteristics of an algorithm are finiteness, definiteness, input-specified, output-specified, and language-independent.
3. **Time complexity** and **Space complexity** are two key measures used to analyze the performance of algorithms.
4. **Time complexity** measures the number of primitive operations executed by an algorithm, usually as a function of the input size.
5. **Space complexity** measures the amount of memory space required by an algorithm, including both auxiliary space and input space.
6. The efficiency of an algorithm can be analyzed at two stages: **Priori Analysis**, which is theoretical analysis done before implementation, and **Posteriori Analysis**, which is empirical analysis done after implementation. In Posteriori Analysis, the chosen algorithm is implemented using a specific programming language and executed on a target machine.
7. **Asymptotic Analysis** is a mathematical technique used to analyze the efficiency of an algorithm independent of hardware. It involves using notations such as **Big O**, **Big Theta**, and **Big Omega** to determine the performance of an algorithm.
8. **Amortized Analysis** is a technique used to analyze the average performance of an algorithm over a large dataset. It is particularly useful for algorithms that have slow performance on occasional operations but perform faster on most operations. The three main types of amortized analysis are aggregate analysis, the accounting method, and the potential method.

## Growth of Functions

Growth of functions is used to describe how time and space complexity increase as the input size grows, and it is often represented using Big O notation to describe the upper bound of the growth rate. [^1] [^3] [^4] [^9] Here's a guide to the vocabulary:

Classification | Notation | Implication
--- | ---
Constant | $$O(1)$$ | The algorithm's runtime does not depend on the input size.
Logarithmic | $$O(\log N)$$ | The algorithm's runtime grows slowly as the input size increases, making it efficient for large inputs.
Linear | $$O(N)$$ | The algorithm's runtime increases linearly as the input size increases.
Linearithmic | $$O(N\log N)$$| The algorithm's runtime grows slightly faster than linear time, but still efficient for large inputs.
Polynomial | $$O(n^k)$$ | where k>1, the algorithm's runtime grows quickly for large inputs, but is still feasible for moderate input sizes.
Quadratic | $$O(n^2)$$ | The algorithm's runtime grows quadratically as the input size increases, making it inefficient for large inputs.
Cubic | $$O(n^3)$$ | The algorithm's runtime grows cubically as the input size increases, making it even less efficient for large inputs.
Exponential | $$O(2^n)$$ | The algorithm's runtime grows exponentially as the input size increases, making it impractical for all but the smallest inputs.
Factorial | $$O(n!)$$ | The algorithm's runtime grows faster than any other complexity class, making it infeasible for even small inputs.

## Data Structures Overview

In computer science, we have two types of data structures: linear and non-linear. Data structures often have straightforward names that reflect their organization. [^1] [^10]

| Types | Linear Data Structure | Non Linear Data Structure |
| - | - | - |
| Arrangement | Elements are arranged sequentially or linearly. Items are linked before and after it. | Elements are grouped hierarchically or non-linearly |
| Implementation| They have a simple structure that allows for efficient operations. | They're challenging to put in place because of the non-linear structure. |
| Traversal | Elements are found on a single level, hence data can be retrieved in one run. | Elements are found in multi-levels, hence traversal requires many runs. |
| Memory Utilization| Inefficient for hierarchical data | More efficient than linear structures when dealing with hierarchical data
Growth of Function | Increases along with its input size and often exhibits complex behavior. | Often exhibits complex behavior as the input size increases.|
|Common Types | Arrays, Linked Lists, Queues, Stacks | Trees, Graphs|
|Applications | Mostly utilized in software development for data storage and retrieval. | Used in image processing, artificial intelligence, and other hierarchical data management applications.|

## Algorithm Types and Examples

An algorithm is a set of instructions that can be followed to solve a problem. Here's a summary of common algorithm types. [^1] [^2] [^3] [^4] [^8]

|Type|Definition|Example Application
|-|-|-|
| Sorting Algorithms | Sort data in a specified order | Bubble Sort, Insertion Sort, and Merge Sort |
| Searching Algorithms | Search for a particular item in a data structure | Linear Search, Binary Search |
| Recursion Algorithms | Solve a problem by calling itself one or more times within its code | Fibonacci sequence, Tower of Hanoi |
| Divide and Conquer Algorithms | Divides a problem into smaller sub-problems and solve them individually | QuickSort, MergeSort|
| Greedy Algorithms | Make locally optimal choices at each step with the hope of finding a global optimum solution | Knapsack Problem, Huffman Coding |
| Dynamic Programming Algorithms | Solve problems by breaking them down into smaller sub-problems, and then combining the solutions to these sub-problems | Longest Common Subsequence, 0-1 Knapsack Problem |
| Backtracking Algorithms | Generate all possible solutions to a problem and then select the best one |N-Queens Problem, Sudoku Solver |
| Brute-Force Algorithms | Solve problems by exhausting all possible solutions until one is found | Password Cracker, Traveling Salesman Problem |
| Randomized Algorithms | Use randomization to solve problems, and can be more efficient than deterministic algorithms in some cases |Randomized Quicksort, the Monte Carlo Algorithm |
| Heuristic Algorithms | Use approximations and rules of thumb to solve problems that cannot be solved exactly | Ant Colony Optimization Algorithm, the Simulated Annealing Algorithm |

## References

[^1]: Harvard University. (2022). CS50’s Introduction to Computer Science. https://cs50.harvard.edu/x/2022/
[^2]: GeeksforGeeks. (n.d.). Fundamentals of Algorithms. https://www.geeksforgeeks.org/fundamentals-of-algorithms/
[^3]: Brilliant. (n.d.). Algorithm. https://brilliant.org/wiki/algorithm/
[^4]: Khan Academy. (n.d.). Algorithms. https://www.khanacademy.org/computing/computer-science/algorithms
[^5]: Codecademy. (n.d.). Learn Data Structures and Algorithms with Python. https://www.codecademy.com/learn/learn-data-structures-and-algorithms-with-python
[^6]: Udacity. (n.d.). Learn Data Structures and Algorithms. https://www.udacity.com/course/data-structures-and-algorithms-in-python--ud513
[^7]: Thomas, J. (2022). Data Structure and Algorithms With Python: The Ultimate Guide Towards Coding. Kindle Direct Publishing.
[^8]: Radford University. (n.d.). Dynamic Programming - Memoization. https://sites.radford.edu/~nokie/classes/360/dp-memoized.html
[^9]: Humbert.(2020). "A Gentle Explanation of Logarithmic Time Complexity". https://blog.eepy.net/2020/06/15/a-gentle-explanation-of-logarithmic-time-complexity/
[^10]: Trivedi. (2022). Linear and Non-Linear Data Structure. https://www.scaler.com/topics/linear-and-non-linear-data-structures