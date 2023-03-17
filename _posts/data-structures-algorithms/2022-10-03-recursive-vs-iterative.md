---
layout: post
title: Recursive vs. Iterative Algorithms
summary: To be revised
tag: data-structures-algorithms
---

Both **recursion** and **iteration** are programming structures that carry out a sequence of instructions repeatedly.

The **recursive method** is a technique that makes a function call itself and has two fundamental aspects called the base case and recursive step. For example, you are a character queuing at a bubble tea shop. The operation can be defined as if the person before you moves forward, you can assume there is one less customer at the front as you move one step closer to the counter. Once there is no more person before you, you can assume you are at the front and now able to order. The **base case** refers to the smallest instance of the problem, which could be "Is it my turn to order?" in this scenario, while the **recursive step** refers to the specific instructions you repeated. If there were ten customers before you, then you would repeat the step "move one step closer" ten times before you can make an order. [^1] [^2] [^3] [^7]

The **iterative method** is a technique that repeats specific instructions until the control condition becomes true or false. For example, you are programming the "sugar caramelization" process. If the statement "sugar turned golden brown" becomes true, the heating system must automatically switch off. [^1] [^2] [^3] [^7]

Basis | Recursion | Interation
-|-|-
Format | It's always applied to a *function* which makes the code shorter and easier to comprehend. | More code will be written since an interation could include some *initialization*, *condition*, *for* and *while* statement loops, *update* operations
Termination | When the function converges to the base condition, the recursion stops. If the maximum recursion depth is exceeded (eg. Python's limit is 1000), the code terminates on an error. | The iteration statement is repeatedly executed until the control condition becomes true or false. 
Non-Termination | If it does not have a way to meet the base condition, theoretically it leads to infinite recursion. | If the control condition stays the opposite, it leads to infinite iteration. Infinite loop uses CPU cycles repeatedly so the program doesn't crash.
Memory | Each recursive call requires a memory on the stack. | It does not uses stack.
Speed | Slow in execution. | Fast in execution.


- TOC
{:toc}

## Recursive vs. Iterative Binary Search

**Binary Search** repeatedly divides the search interval in half until the target value is found. Using the recursive method, this algorithm will need follow a divide-and-conquer approach. The base case would be if *high* or the length of the array is bigger than 0 which tells us the program if there is still something to divide. The recursive step would be if the target element is found in the middle. If the target element is in the middle, this terminates the search. If the target element is smaller than the middle element, search the left side of the array. If the target element is larger, then search the right side. The recursive step is called until the base condition is met. [^3]

{% highlight python %}
#recursive approach
def binary_search_r(array, low, high, target):
  if high >= low:
    middle = low + (high - low) // 2  
    if array[middle] == target:
      return middle
    elif array[middle] > target:
      return binary_search_r(array, low, middle-1, target)
    else:
      return binary_search_r(array, middle + 1, high, target)
  else:
    return "not found"

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32]
print(binary_search_r(array, 0, len(array)-1, 29)) #28
print(binary_search_r(array, 0, len(array)-1, 33)) #not found
{% endhighlight %}

Using the iterative method, the control statement would be "the length of the array minus 0 is above 1". While this statement remains true, keep checking if the target element matches the middle. If the target element is smaller than the middle element, search the left. If the target element is bigger than the middle element, search the right. [^3]

{% highlight python %}
#iterative approach
def binary_search_i(array, low, high, target):
  while high - low > 1:
    middle = (high + low) // 2
    if array[middle] < target:
      low = middle + 1
    else:
      high = middle
 
  if array[low] == target:
    return low
  elif array[high] == target:
    return high
  else:
    return "not found"
  
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32]
print(binary_search_i(array, 0, len(array)-1, 29)) #28
print(binary_search_i(array, 0, len(array)-1, 33)) #not found
{% endhighlight %}

Both recurisve and iterative binary search have the time complexity of $$O(log n)$$. However, the recurisve binary search will require an auxiliary space of $$O(log n)$$ due to memory stacking while the iterative binary search only needs $$O(1)$$. [^3]

## Recursive vs. Iterative Factorial

**Factorial** of a number is the product of all positive integers equal to $$n$$, so it is denoted as $$n! = 1 * 2 * 3 * ... * n$$. [^2] [^5]

{% highlight python %}
def factorial_r(x):
    if x == 0: #base case
        return 1
    return x * factorial_r(x-1) #recursive step
{% endhighlight %}

{% highlight python %}
def factorial_i(x):
    result = 1
    while x > 1: #interation
        result = result * x
        x -= 1
    return result
{% endhighlight %}

Both recursive and iterative factorial algorithms have the time complexity of $$O(n)$$. However, when the value of x increases as as if the x = 500, the algorithm will result to *"RecursionError: maximum recursion depth exceeded in comparison"*. The auxillary space required by *factorial_r* is $$O(n)$$ while *factorial_i* only requires $$O(1)$$. [^2]

## Recursive vs. Iterative Fibonacci

**Fibonacci Sequences** forms a sequence in which each number is the sum of the two preceding ones. The first ten fibonacci numbers are 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55. [^2] [^6]

A recursive approach to fibonacci function would require a time complexity of $$O(2^n)$$.

{% highlight python %}
def fibonacci_r(n):
  if n <= 1:
    return n
  return fibonacci_r(n-1) + fibonacci_r(n-2)
{% endhighlight %}

Here's a more visual way of counting the primitive operations.

<pre>
0                        n
1            (n-1)       +         (n-2)
2        (n-2) +  (n-3)  +   (n-3)  +  (n-4)
3   (n-3)(n-4)+(n-4)(n-5)+(n-4)(n-5)+(n-5)(n-6)
</pre>


{% highlight python %}
def fibonacci_i(n):
    a, b = 0, 1
    for i in range(0, n):
        a, b = b, a + b
    return a
{% endhighlight %}

A iterative approach would require to initialize variables a and b to state the first two fibonacci numbers and the control statement only runs from the range of 2 to n. Therefore, the time complexity of an interative fibonacci function is $$O(n)$$, which makes it clearly more efficient than the recursive approach.  [^2]

## Recursive vs. Iterative Merge Sort

**Merge Sort** conceptually works by first dividing the unsorted list into $$n$$ sublists, each containing one element, and then repeatedly merging sublists to produce new sorted sublists until there is only one sublist remaining, which is the sorted list. [^9] [^10]

A recursive merge sort would require a top-down approach. The function recursively splits the list into sublists until sublist size is 1, then merges those sublists to produce a sorted list. [^9] The code snippet is taken from a response in Stack Exchange. [^8]

{% highlight python %}
def top_down_merge(left, right):
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

def top_down_merge_sort(array):
  if len(array) <= 1:
    return array
    
  half = len(array) // 2
  left = top_down_merge_sort(array[:half])
  right = top_down_merge_sort(array[half:])

  return top_down_merge(left, right)

array = [1995,1998,1999,1991,2000, 1993,1996,1992,1994,1997]
new_array = top_down_merge_sort(array)

{% endhighlight %}

The time complexity of a recursive merge sort is $$O(n log n)$$. Here's a visual way of counting the primitive operations:

![Image](/assets/images/merge-sort.png)

The bottom-up iterative merge sort merges every successive pair of elements into sorted runs of length two. Then merge these into more sorted runs of length four. Then merge those into sorted runs of length eight, and so on. [^10]

{% highlight python %}
def merge(array, left, middle, right):
  n1 = middle - left + 1
  n2 = right - middle
  left_array = [0] * n1
  right_array = [0] * n2
  for left_index in range(0, n1):
    left_array[left_index] = array[left + left_index]
  for left_index in range(0, n2):
    right_array[left_index] = array[middle + left_index + 1]
  
  left_index, right_index, new_index = 0, 0, left
  while left_index < n1 and right_index < n2:
    if left_array[left_index] <= right_array[right_index]:
      array[new_index] = left_array[left_index]
      left_index += 1
    else:
      array[new_index] = right_array[right_index]
      right_index += 1
    new_index += 1
 
  while left_index < n1:
    array[new_index] = left_array[left_index]
    left_index += 1
    new_index += 1
 
  while right_index < n2:
    array[new_index] = right_array[right_index]
    right_index += 1
    new_index += 1
    
def merge_sort_i(array):
    width = 1   
    n = len(array)                             
    while (width < n):
        left=0;
        while (left < n):
            right = min(left+(width*2-1), n-1)        
            middle = min(left+width-1,n-1)          
            merge(array, left, middle, right)
            left += width*2
        width *= 2
    return array
{% endhighlight %}

The time complexity of a recursive merge sort is $$O(n log n)$$. Here's a visual way of counting the primitive operations:

![Image](/assets/images/merge-sort-iterative.png)

## Conclusion
Interation is the act of repeating a process while recursion is act of repeating smaller process of the same problem. Recursion in practice is easier to implement however speed execution is slower and memory requirements are higher compared to iteration.

[^1]: Codecademy. (2022). *Recursion with Python*. [www.codecademy.com](https://www.codecademy.com/courses/learn-data-structures-and-algorithms-with-python/lessons/recursion-python)
[^2]: GeekForGeeks. (2022). *Difference between Recursion and Iteration*. [www.geekforgeeks.org](https://www.geeksforgeeks.org/difference-between-recursion-and-iteration)
[^3]: GeekForGeeks. (2022). *Binary Search*. [www.geekforgeeks.org](https://www.geeksforgeeks.org/binary-search/)
[^4]: TechDifferences. (2022). *Difference Between Recursion and Iteration* [www.techdifferences.com](https://techdifferences.com/difference-between-recursion-and-iteration-2.html)
[^5]: Wikipedia. (2022). *Factorial*. [wikipedia.org](https://en.wikipedia.org/wiki/Factorial)
[^6]: Wikipedia. (2022). *Fibonacci Number*. [wikipedia.org](https://en.wikipedia.org/wiki/Fibonacci_number)
[^7]: Interview Kick Start. (2022). *Difference between Recursion and Iteration*. [wikipedia.org](https://www.interviewkickstart.com/learn/difference-between-recursion-and-iteration)
[^8]: Stack Exchage. (2022). Recursive Merge Sort in Python. [codereview.stackexchange.com](https://codereview.stackexchange.com/questions/154135/recursive-merge-sort-in-python)
[^9]: Wikipedia. (2022). *Merge Sort*. [wikipedia.org](https://en.wikipedia.org/wiki/Merge_sort)
[^10]: LevelUp Coding by Git Conneted. (2022). *Merge Sort — Top Down and Bottom Up for Arrays and Linked Lists*. [levelup.gitconnected.com](https://levelup.gitconnected.com/sorting-algorithms-merge-sort-top-down-bottom-up-for-arrays-linked-lists-2426dcc39611)




