---
layout: post
title: Pattern Search Algorithms
summary: To be revised, a deep dive on Pattern Search Algorithms
tag: data-structures-algorithms
---

- TOC
{:toc}

## Naive Pattern Search

**Naive Pattern Search** requires two components: 1) a full text and 2) a pattern to search for. For each iteration of the text, naive pattern search iterates over the entire pattern. If the length of the pattern happens to be the length of the text, then the run-time performance can approach O(n^2). If the pattern turns out to be the same as the text, the best case run-time would approach O(n). [^1] [^3]

Backtracking is the algorithmic feature that can cause naive pattern search to compare each character of the text with the entirety of the pattern. The length of a given pattern may change how long a specific instance of the algorithm takes to execute, but it does not cause the near-quadratic growth in the algorithm’s run-time.

{% highlight python %}
def naive_search(pattern, text):
  for index in range(len(text)):
    match_count = 0
    for char in range(len(pattern)):
      if pattern[char] == text[index + char]:
        match_count += 1
      else:
        break
        
      if match_count == len(pattern):
        print("Pattern was found at index ", index)
naive_search("ABCDABD", "ABC ABCDAB ABCDABCDABDE")
{% endhighlight %}

## Knuth–Morris–Pratt Algorithm
**Knuth–Morris–Pratt Algorithm** was the first-ever string matching algorithm that ran in linear time. Most of the naive string matching algorithms run in O(nm) time, while the KMP algorithm runs in O(m + n) time where n is the length of the string, and m is the length of the pattern. [^2]

{% highlight python %}
def kmp_search(pat, txt):
    M = len(pat)
    N = len(txt)

    lps = [0]*len(pat)
    j = 0 
    compute_lps(pat, M, lps)
 
    i = 0
    while i < N:
        if pat[j] == txt[i]:
            i += 1
            j += 1
 
        if j == M:
            print ("Found pattern at index", str(i-j))
            j = lps[j-1]
          
        elif i < N and pat[j] != txt[i]:
            if j != 0:
                j = lps[j-1]
            else:
                i += 1
 
def compute_lps(pat, M, lps):
    len = 0 
    lps[0] 
    i = 1

    while i < M:
        if pat[i]== pat[len]:
            len += 1
            lps[i] = len
            i += 1
        else:
            if len != 0:
                len = lps[len-1]
            else:
                lps[i] = 0
                i += 1
kmp_search("ABCDABD", "ABC ABCDAB ABCDABCDABDE")
{% endhighlight %}

## Rabin-Karp Algorithm
Rabin-Karp Algorithm is a string-pattern search algorithm that uses hashing to find an exact match of a pattern string in a text. [^4]

{% highlight python %}
def rk_search(pattern, text, prime):
  M = len(pattern)
  N = len(text)
  i = 0
  j = 0
  pattern_hv = 0  
  text_hv = 0 
  h = 1
 
  for i in range(M-1):
    h = (h*input_alphabet) % prime

  for i in range(M):
    pattern_hv = (input_alphabet*pattern_hv + ord(pattern[i])) % prime
    text_hv = (input_alphabet*text_hv + ord(text[i])) % prime
      
  for i in range(N-M+1):
    if pattern_hv == text_hv:
      for j in range(M):
        if text[i+j] != pattern[j]:
          break
        else:
          j += 1
                  
      if j == M:
        print("Pattern found at index " + str(i))
 
    if i < N-M:
      text_hv = (input_alphabet*(text_hv-ord(text[i])*h) + ord(text[i+M])) % prime
      if text_hv < 0:
        text_hv = text_hv+prime

rk_search("ABCDABD", "ABC ABCDAB ABCDABCDABDE",101)
{% endhighlight %}

## Conclusion

Algorithm | Big O | Big Ω | Big θ | Space
--- | --- | --- | --- | ---
Naive Search | O(n<sup>2</sup>) | O(nk) | O(n<sup>2</sup>) | O(1)
KMP Search | O(n+k) |  O(n) |  O(n) | O(1)
RK Search | O(mn)+O(m) |  O(n) |  O(mn)+O(m) | O(1)


[^1]: Learn Data Structures and Algorithms. (2022). Codecademy. https://www.codecademy.com/learn learn-data-structures-and-algorithms-with-python
[^2]: Knuth–Morris–Pratt algorithm. (2022, October 18). In Wikipedia. https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm
[^3]: Naive Algorithm for Pattern Searching. (2022). GeekforGeeks. https://www.geeksforgeeks.org/naive-algorithm-for-pattern-searching/
[^4]: Rabin–Karp algorithm. (2022, September 20). In Wikipedia. https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm