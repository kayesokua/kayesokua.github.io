---
layout: post
title: Asymtotic Analysis
summary: A notebook on Asymptotic Analysis for analyzing algorithm performance based on input size growth. Covers Big O, Big Theta, and Big Omega notations and various time complexities, from constant to logarithmic.
tag: data-structures-algorithms
---

**Asymptotic Analysis** is a method of analyzing algorithms that focuses on their performance characteristics as the input size grows towards infinity. It provides a way to define the boundaries of an algorithm's runtime performance based on its time and space complexity. This method is independent of the hardware used to execute the algorithm. [^1] [^2] [^3] [^4] [^5]

| Notation | Definition | Implication |
| - | - | - |
| Big $$O$$ | Upper bound of the algorithm or the worst-case scenario | It's like the slowest traffic you might encounter on your commute, but it won't get any worse than that! |
| Big Theta(Θ) | Tight bound or the average-case scenario | It's like the typical amount of time it takes you to get ready in the morning, once you've been doing it long enough to have a routine. |
| Big Omega(Ω) | Lower bound of the algorithm or the best-case scenario | It's like the fastest you might be able to get to work if there's no traffic. |

By understanding the Big O, Big Theta, and Big Omega notations, you can compare different algorithms and make informed decisions about which one to use in different situations based on their trade-offs.

* TOC
{:toc}

## Calculating Time Complexity

Since we are extracting truth independent of its hardware, we will not rely on  python's built-in function of `timeit`. We will count its primitive operation and assume 1 unit of time: 1 operation. In this section, we will deep dive into algorithms with different run times.

### Constant Complexity

```python
def constant_algorithm(items):
    return items[0] * items[-1]
constant_algorithm([1,2]) 
constant_algorithm([1,2,3,4,5,6,7,8,9,10])
```

The function `constant_algorithm performs` the same operation of multiplying the first and last item of the input list, regardless of the size of the input. This means that the time it takes to run the function does not depend on the size of the input and therefore has a constant time complexity of $$O(1)$$.

### Linear Complexity

Linear time means that the time it takes to complete the function increases linearly with the size of the input. In other words, if the size of the input doubles, the time it takes to complete the function will also double.

```python
def linear_algorithm(items):
    for item in items:
        print(item)

linear_algorithm([0,1,2,3,4])
```

In this case, the for-loop will iterate $$N$$ times, so if $$N$$ is 5, the loop will iterate 5 times. Therefore, the function `linear_algorithm` has a linear time complexity of $$O(N)$$.

### Quadratic, Quartic Complexity

```python
strings = ["butter","milk","fish","nuts"]
compound_words = []

def quadratic_algorithm(strings):
    for string in strings:
        for string2 in strings:
            print(string, ' ' ,string2)
quadratic_algorithm(strings)
```

In this function `quadratic_algorithm`, for each word in the input list of words, another loop iterates through the same input list of words. This means that the number of iterations of the inner loop increases with the size of the input, leading to an overall time complexity that grows exponentially with the input size. Therefore, this function runs on quadratic time, $$O(N^2)$$.

*Degree 0 is called constant, degree 1 is linear, degree 2 is quadratic, degree 3 is cubic, degree 4 is quartic, degree 5 is quintic, etc..*

```python
strings = ["butter","milk","fish","nuts"]
compound_words = []

def quartic_algorithm(strings):
    for string in strings: 
        for string2 in strings: 
            new_word = string+string2
            compound_words.append(new_word)

quartic_algorithm(strings)
```

The function `quartic_algorithm` has two nested for-loops, which means for each string in the list, it will create a new word by combining it with each of the other strings. This results in a total of $$N^2$$ operations, which is why it has a quartic time complexity of $$O(N^{2(2)})$$.

### Logarithmic Complexity

Logarithmic time complexity means that the time it takes to complete the function increases logarithmically with the size of the input.

```python
def binary_search(array, left, right, target):
    if right >= left:
        #middle = (left + right)/ 2 will result to bug
        middle = left + (right - left) // 2

        if array[middle] == target:
            return middle

        elif array[middle] > target:
            return binary_search(array, left, middle-1, target)
        else:
            return binary_search(array, middle + 1, right, target)

    else:
        return "not found"
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32]
 
binary_search(array, 0, len(array)-1, 8) #returns index 7
```

The code snippet is a recursive binary search (ofcourse, only works for sorted numerical array), which is a classic example of *divide and conquer algorithm*. The function `binary_search` runs on logarithmic time complexity because it uses the binary search algorithm which halves the search space at every step until the target is found. Therefore, as the input size doubles, the number of steps to search for the target only increases by 1. This makes the function very efficient for large inputs, with a time complexity of $$O(log N)$$.

### Linearithmic Complexity

```python
def merge(left, right):
  left_index, right_index = 0, 0
  result = []

  while left_index < len(left) and right_index < len(right):
    if left[left_index] < right[right_index]:
      result.append(left[left_index])
      left_index += 1
    else:
      result.append(right[right_index])
      right_index += 1

  result += left[left_index:]
  result += right[right_index:]
  return result

def merge_sort(array):
  if len(array) <= 1:
    return array

  half = len(array) // 2
  left = merge_sort(array[:half])
  right = merge_sort(array[half:])

  return merge(left, right)

```

A *merge sort* function works by first dividing the array into halves which takes $$O(log N)$$ or logarithmic time, and then merges while checking each element to determine its order which takes $$O(log N)$$ or linear time. Here's a visual way of estimating its primitive operations:

![Image](/assets/images/merge-sort.png)

Combining these two complexities can be denoted as $$O(N(log N))$$ and therefore, the entire operation can be described having linearithmic complexity.

### Polynomial Complexity

A polynomial time complexity function is one where the time it takes to solve a problem increases polynomially with the size of the input.

```python
def find_word_in_text(word, text):
    n = len(text)
    m = len(word)
    for i in range(n - m + 1):
        if text[i:i+m] == word:
            return i
    return -1
```

The function find_word_in_text has a time complexity of $$O(n * m)$$, where n is the length of the text and m is the length of the word. This is because in the worst case scenario, we may need to compare every character of the word with every character of the text. Since the number of comparisons is polynomially related to the length of the input, the function is said to have polynomial time complexity.

### Exponential Complexity

```python
def fibonacci_r(n):
  if n <= 1:
    return n
  return fibonacci_r(n-1) + fibonacci_r(n-2)
```

The time complexity of the recursive fibonacci function known to be $$O(2^n)$$. Here's a visual way of estimating its primitive operations:

```python
i
0                        n
1            (n-1)                 (n-2)
2        (n-2)    (n-3)      (n-3)     (n-4)
3   (n-3)(n-4) (n-4)(n-5) (n-4)(n-5) (n-5)(n-6)
```

The time complexity of the `fibonacci_r` function is exponential, with a worst-case time complexity of $$O(2^n)$$, where n is the input value. This is because the function recursively computes the fibonacci sequence, with each recursive call branching out into two more calls, resulting in an exponential growth of the number of function calls. Since the number of function calls is exponentially related to the input size, the function is said to have exponential time complexity.

### Factorial Complexity

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```

The `factorial` function has a time complexity of $$O(n!)$$, where n is the input value. This is because the function recursively computes the factorial by performing n multiplications at each step, resulting in n! total multiplications for the entire computation. As the input size increases, the number of multiplications grows exponentially, resulting in a factorial time complexity.

### Summary

Classification | Time | Implication
--- | ---
Constant | $$O(1)$$ | The algorithm is very clever! Only requires 1 operation regardless of the input size
Logarithmic | $$O(log N)$$ | The runtime grows logarithmically (or in division). The bigger the input, the smaller proportion of the actual input your program has to go through!
Linear | $$O(N)$$ | Runtime grows *directly* in proportion to input size. The increase in time will be proportional to the increase in input size.
Linearithmic | $$O(N log N)$$| The runtime grows faster than linear but slower than polynomial, and is often seen in algorithms that use divide and conquer strategies. It could be "the worst of the best"
Polynomial | $$O(n^c)$$ | The runtime grows quickly but not as quickly as exponential or factorial, making it feasible to process moderately-sized inputs.
Quadratic | $$O(n^2)$$ | The runtime grows faster than polynomial and is often seen in algorithms that use nested loops.
Cubic | $$O(n^3)$$ | The runtime grows faster than quadratic and is often seen in algorithms that use three nested loops.
Exponential | $$O(c^n)$$ | The runtime grows very quickly and becomes impractical to use for even moderately-sized inputs.
Factorial | $$O(n!)$$ | The runtime grows so quickly that it becomes unusable for all but the smallest inputs.

## Space Complexity

Space complexity is the amount of memory required by an algorithm to solve a problem, including both the space needed to store the input data and any additional space required during execution. It is a complementary concept to time complexity and can also impact the efficiency of an algorithm. By analyzing the space complexity of an algorithm, we can identify potential memory usage issues and optimize the algorithm to use memory more efficiently. [^6] [^7]

**Linear space complexity**: This function stores an array of size n, resulting in linear space complexity.

```python
def linear_space(n):
    arr = [0] * n
    return arr
```

**Constant space complexity**: This function uses a fixed amount of memory, regardless of the input size, resulting in constant space complexity.

```python
def constant_space():
    a = 1
    b = 2
    c = 3
    return a + b + c
```

**Logarithmic space complexity**: This function stores only a logarithmic amount of data by dividing the input in half at each step, resulting in logarithmic space complexity.

```python
def logarithmic_space(n):
    if n == 0:
        return 1
    else:
        return logarithmic_space(n // 2)
```

**Linearithmic space complexity**: This function uses a divide-and-conquer approach and stores an amount of data that grows faster than logarithmic but slower than polynomial, resulting in linearithmic space complexity.

```python
def linearithmic_space(n):
    if n <= 1:
        return n
    else:
        left = linearithmic_space(n // 2)
        right = linearithmic_space(n // 2)
        return left + right
```

**Exponential space complexity**: This function stores an exponential amount of data due to recursive calls that result in multiple copies of data being stored in memory, resulting in exponential space complexity.

```python
def exponential_space(n):
    if n <= 1:
        return n
    else:
        return exponential_space(n-1) + exponential_space(n-2)
```

## Time and Space Trade-Offs

Time and space complexity trade-offs are crucial in computer science, where optimizing for one often means sacrificing the other. Balancing the two is necessary to create efficient and scalable software systems, which can be achieved by using efficient algorithms and data structures, reducing redundant computation, and utilizing hardware acceleration. In web development, high time or space complexity can impact website performance, while in machine learning, they can impact training and inference times. Strategies to address these trade-offs include optimizing code for performance, selecting the right algorithms and models, and using hardware acceleration. Understanding time and space complexity trade-offs is essential for building efficient and scalable applications.

[^1]: Malik.(2022). "Big O Notation and Algorithm Analysis with Python Examples". Stack Abuse. https://stackabuse.com/big-o-notation-and-algorithm-analysis-with-python-examples/
[^2]: Codecademy. (n.d.). Why Asymtotic Notation. https://www.codecademy.com/article/cspath-why-asymptotic-notation
[^3]: Khan Academy. (2022), "Asymptotic notation". https://www.khanacademy.org/computing/computer-science/algorithms
[^4]: Brilliant. (n.d.). Big O Notation. https://brilliant.org/wiki/big-o-notation/
[^5]: Nilsson. (2022). "How to analyze time complexity: Count your steps". yourbasic.org. https://yourbasic.org/algorithms/time-complexity-explained
[^6]: GeekforGeeks. (2022). Space Complexity. https://www.geeksforgeeks.org/g-fact-86/
[^7]: Brilliant. (n.d.). Space complexity. Brilliant. https://brilliant.org/wiki/space-complexity/.