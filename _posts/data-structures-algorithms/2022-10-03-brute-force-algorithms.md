---
layout: post
title: Brute Force Algorithms
summary: To be revised, a deep dive on brute force algorithms,
tag: data-structures-algorithms
---

**Brute Force Algorithms** solves a problem by going through all possible choices until either a solution is found or all possibilities have been exhausted. The time complexity of a brute force algorithm is often proportional to the input size.
It is used easier to implement than more optimized algorithms and could be simple enough to be bug-free. However, the disadvantages are its slow runtime when the input size is too big and mostly not applicable to real-world problems.
[^1] [^2] [^3] [^4]

- TOC
{:toc}

## Linear Search
**Linear Search** is a sequential search that operates by checking each element until the match is found or the whole list has been searched.

Cracking a 4-digit password by brute force approach would requires the ff: 1) knowing all the possible permutations with repetition 2) searching for the target password one by one.

{% highlight python %}
def product(*args, repeat=4):
    pools = [tuple(pool) for pool in args] * repeat
    result = [[]]
    for pool in pools:
        result = [x+[y] for x in result for y in pool]
    for prod in result:
        yield tuple(prod)

#https://docs.python.org/3/library/itertools.html

pin_list = list(product(range(10), repeat=4))

from random import randint

def crack_pin(pin_pass):
  attempt = 0
  for x in pin_list:
    if pin_pass == x:
      attempt += 1
      print("cracked after "+str(attempt)+" attempts")
    else:
      attempt += 1

pin_pass = (randint(0,9),randint(0,9),randint(0,9),randint(0,9)) 
print(pin_pass)
crack_pin(pin_pass)
{% endhighlight %}

Since we know our list is sorted and searches sequentially, if the password is $$(0,0,0,0)$$ then the expected time complexity is $$O(1)$$. If the password is $$(9,9,9,9)$$, then the expected time complexity is $$O(10^4)$$ which is the total size of our "pin_list".

## Bubble Sort

**Bubble Sort** is one of the easiest and brute force sorting algorithm. It operates by repeatedly swapping the adjacent elements if they are in the wrong order (swaps element on if the left is larger than the right). It is used to sort elements in either ascending or descending order. Every element is compared with every other element in bubble sort. The worst-case condition for bubble sort occurs when elements of the array are arranged in decreasing order resulting to $$O(n(n-1)/2)$$. After removing the constant, we estimate its time complexity as $$O(n^2)$$. The best case scenario is when the list is already sorted. [^2] [^3]

{% highlight python %}
def bubble_sort(list):
  count = 0
  for i in range(len(list)):
    count += 1
    for j in range(len(list) - 1):
      if list[i] != (sorted(list))[i]:
        if list[j] > list[j+1]:
          count += 1
          list[j], list[j+1] = list[j+1], list[j]
          
  print("primitive operations: ",count)

bubble_sort([10,9,8,7,6,5,4,3,2,1]) #Worst case: O(n**2-n)/2
bubble_sort([1,2,3,4,5,6,7,8,9,10]) #Best case: O(n)
{% endhighlight %}
## Selection Sort
**Selection Sort** operates by finding the minimum element from the unsorted part and swapping the minimum element with the first element of the unsorted part. It builts the array from left to right.

The time complexity remains the same for sorted, sorted backwards and duplicates in the array since  selection sort always forms a quadratic number of comparisons by iterating through the array to find the smalles element to swap. Therefore, it cannot differentiate or recognize what has been sorted or not, for example: $$[1,2,3,4,5]$$ is the same as $$[5,4,3,2,1]$$. It is also described as unstable as it cannot preserve the relative order of element with equal keys. An example of this if the array has duplicate elements: $$[1,1,1,1,1]$$. [^2] [^3] [^4]

Selection sort is preferred if writing to memory is significantly more expensive than reading.

{% highlight python %}
def selection_sort(array):
  n = len(array)
  count = 0
  for i in range(n):
    count += 1
    minimum = i
    for j in range(i+1, n):
      count += 1
      if (array[j] < array[minimum]):
        minimum = j

    temp = array[i]
    count += 1
    array[i] = array[minimum]
    count += 1
    array[minimum] = temp
    count += 1  
  return print("sorted array:", array, ", total operations:", count)

#Worst case: O(N^2) + O(N)
selection_sort([5,4,3,2,1]) #time complexity: 30
#Best case is still O(N^2) + O(N)
selection_sort([1,2,3,4,5]) #time complexity: 30
selection_sort([1,1,1,1,1]) #time complexity: 30
{% endhighlight %}

## Conclusion

Algorithm | Big O | Big Ω | Big θ | Space
--- | --- | --- | ---
Linear Search | $$O(n)$$ | $$O(1)$$ | $$O(n)$$ | O(1)
Bubble Sort | $$O(n^2)$$ |  O(N) | $$O(n^2)$$ | O(1)
Selection Sort | $$O(n^2)$$ | $$O(n^2)$$ | $$O(n^2)$$ | O(1)

[Download the code from Gist.](https://gist.github.com/kayesokua/999cdd88b6532eaa509a2837e142679d)

[^1]: Codecademy. Learn Data Structures and Algorithms with Python. [codecademy.com](https://support.microsoft.com/en-us/office/database-design-basics-eb2159cf-1e30-401a-8084-bd4f9c9ca1f5)
[^2]: Geek for Geeks. Linear Search, Bubble Sort, Selection Sort. [geekforgeeks.com](https://www.geeksforgeeks.org/)
[^3]: Harvard CS50x. (2022). [CS50’s Introduction to Computer Science](https://cs50.harvard.edu/x/2022/)
[^4]: OpenGenus IQ (2022). Time Complexity of Selection Sort. [iq.opengenus.org](https://iq.opengenus.org/)