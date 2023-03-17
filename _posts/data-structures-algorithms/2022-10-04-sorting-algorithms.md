---
layout: post
title: Comparison vs. Non-Comparison Sorts
summary: To be revised
tag: data-structures-algorithms
---

**Sorting algorithms** operates by arranging elements of a list into an "order" - usually numerically, lexicographically, ascending or descending. Sorting is used to optimize the efficiency of other algorithms and for canonicalizing data (the process of converting data that has more than one possible representation). [^1] [^2] 

- TOC
{:toc}

## Comparison-Based Sorting
A comparison sort algorithm sorts items by comparing values between each other. The best time complexity is O(n*log(n)) which can be proved mathematically. Here are the basic comparison-based sorting algorithms:
* [Bubble Sort](/brute-force-algorithms#bubble-sort)
* [Selection Sort](/brute-force-algorithms#selection-sort),
* [Merge Sort](/recursive-vs-iterative)
* [Quick Sort](/recursive-algorithms#quick-sort) which was already discussed in the previous notes.

## Quicksort
Quicksort is a divide-and-conquer algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. For this reason, it is sometimes called partition-exchange sort.

### Heap Sort
**Heapsort** is an algorithm that sorts arrays by inserting the data into a heap data structure and then repeatedly extracting the root of the heap. Heapsort is a particularly time-efficient algorithm due to its O(n log n) time complexity in every case.

### Insertion Sort

## Non-Comparison Sort
A non-comparison sort algorithm uses the internal character of the values to be sorted.

### Pigeonhole Sort
### Radix Sort

{% highlight python %}
def count_sort(array, place):
    size = len(array)
    output = [0] * size
    count = [0] * 10

    for i in range(0, size):
        index = array[i] // place
        count[index % 10] += 1

    for i in range(1, 10):
        count[i] += count[i - 1]
      
    i = size - 1
    while i >= 0:
        index = array[i] // place
        output[count[index % 10] - 1] = array[i]
        count[index % 10] -= 1
        i -= 1

    for i in range(0, size):
        array[i] = output[i]
      
def radix_sort(array):
  max_element = max(array)

  place = 1
  while max_element // place > 0:
    count_sort(array, place)
    place *= 10
  
  print(array)

radix_sort([1,2,3,4,5])
radix_sort([5,4,3,2,1])
{% endhighlight %}

## Conclusion


Algorithm | Big O | Big Ω | Big θ | Space | Stable
--- | --- | --- | --- | ---
Bubble Sort | O(n<sup>2</sup>) |  O(n) |  O(n<sup>2</sup> | O(1) | True
Selection Sort |  O(n<sup>2</sup>) |  O(n<sup>2</sup>) |   O(n<sup>2</sup>) | O(1) | False
Quick Sort | O(n<sup>2</sup>) | O(n log n) |   O(n log n) | O(log n) | False
Merge Sort | O(n log n) | O(n log n) |  O(n log n) | O(n) | True
Heap Sort | O(n log n) | O(n log n) |  O(n log n) | O(1) | False
Tree Sort | O(n log n) | O(n log n) |  O(n log n) | O(n) | True
Shell Sort | O(n log n | O(n<sup>3/2</sup>) |  O(n<sup>4/3</sup>) | O(1) | False
Cocktail Sort | O(n<sup>2</sup>) | O(n<sup>2</sup>) |  O(n) | O(1) | True
Pigeonhole Sort | O(n+2<sup>k</sup>) | N/A |  O(n+2<sup>k</sup>) | O(2<sup>k</sup>) | True
Radix Sort | --- | --- | --- | ---


[^1]: Sorting algorithm. (2022). Wikipedia. https://en.wikipedia.org/wiki/Sorting_algorithm
[^2]: Non-Comparison Based Sorting. (2022). OpenGenus IQ. [iq.opengenus.org](https://iq.opengenus.org/non-comparison-based-sorting/)
[^3]: Sorting Algorithms. (2022) Geek for Geeks. [geeksforgeeks.org](https://www.geeksforgeeks.org/sorting-algorithms/)
[^4]: Learn Data Structures and Algorithms with Python. (2022). Codecademy. https://www.codecademy.com/learn/learn-data-structures-and-algorithms-with-python

