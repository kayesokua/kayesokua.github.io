---
layout: post
title: Distance Algorithms
summary: Distance algorithm refers to mathematical functions used to determine the similarity or difference between two data points, usually represented as vectors. Here, I have gathered common distance algorithms that are used in machine learning, data mining, and image processing for tasks such as clustering, classification, and pattern recognition.
tag: data-structures-algorithms
---

Distance algorithm refers to mathematical functions used to determine the similarity or difference between two data points, usually represented as vectors. Here, I have gathered common distance algorithms that are used in machine learning, data mining, and image processing for tasks such as clustering, classification, and pattern recognition.

* TOC
{:toc}

# Euclidean Distance: How far is point A to B?
**Euclidean distance**, or also known as Pythagorean Distance, finds the straight-line distance between two points in a multidimensional space. [^1] [^2]

On an elementary level, we use this algorithm to find the distance between two points in a 2D plane.


```python
# Algorithm behind scipy.spatial import distance.euclidean
def euclidean_distance(pt1, pt2):
  distance = 0
  for i in range(len(pt1)):
    distance += (pt1[i] - pt2[i]) ** 2
  return distance ** 0.5
```

The Euclidean distance can also calculate the distance between the end effector and the origin. [^4]

```python
import numpy as np

def euclidean_distance(point1, point2):
  return np.linalg.norm(point1 - point2)

def end_effector(joints, d_link, theta):
  x = np.array([0, d_link[0]])
  y = np.array([0, 0])
  for i in range(1, len(joints)):
    x += d_link[i] * np.array([np.cos(theta[i]), np.sin(theta[i])])
    y += d_link[i] * np.array([-np.sin(theta[i]), np.cos(theta[i])])
  return np.array([x[-1], y[-1]])

#4DOF Robotic Arm
joints = [0, 0, 0, 0]
#the link lengths
d_link = [0, 1, 1, 1]
#joint angles
theta = [0, np.pi/2, np.pi/2, np.pi/2]
ee = end_effector(joints, d_link, theta)
print("End effector: ", ee)
print("Euclidean distance to origin: ", euclidean_distance(np.array([0, 0]), ee))
```

On a more advanced level,  here a simple example of path planning using Euclidean distance in Python. This calculates the Euclidean distance between two points and uses it to determine the path between a start point and a goal point while avoiding obstacles. The path is represented as a list of points. [^3]

```python
import numpy as np

def euclidean_distance(start, goal):
    return np.sqrt(np.sum((goal - start)**2))

def path_planning(start, goal, obstacles):
    # Initialize the path with start and goal points
    path = [start, goal]
    # Check if the line connecting start and goal intersects with any obstacle
    for obstacle in obstacles:
        # Calculate the minimum distance between the line and the obstacle
        min_distance = np.min([euclidean_distance(start, obstacle), euclidean_distance(goal, obstacle)])
        # If the minimum distance is less than the threshold, add the closest point on the line to the path
        if min_distance < threshold:
            closest_point = np.argmin([euclidean_distance(start, obstacle), euclidean_distance(goal, obstacle)])
            path.insert(-1, closest_point)
    return path

start = np.array([0, 0])
goal = np.array([10, 10])
obstacles = [np.array([5, 5]), np.array([6, 5]), np.array([6, 6])]
threshold = 1
path = path_planning(start, goal, obstacles)
print(path)
```

# Manhattan distance: Number of Blocks from point A to B?

**Manhattan distance**, also known as L1 distance or Taxicab Geometry, is a measure of the absolute differences between two points in a multi-dimensional space. It is the sum of the absolute differences of the coordinates of the two points. For easy illustration, think of a checkboard and ask "how many grid-based moves that results to a checkmate?". [^2] [^6]

```python
def manhattan_distance(pt1, pt2):
  distance = 0
  for i in range(len(pt1)):
    distance += abs(pt1[i] - pt2[i])
  return distance
print(manhattan_distance([1, 2], [4, 0]))
print(manhattan_distance([5, 4, 3], [1, 7, 9]))

#Using Scipy
from scipy.spatial import distance
print(distance.cityblock([1,2],[4,0]))
```

The Manhattan distance can be used to calculate the minimum number of moves a queen can make in a chess game from one square to another. The queen can move in any direction (horizontally, vertically, or diagonally), and the Manhattan distance is the sum of the absolute differences of the horizontal and vertical component of the move. Here's an example application of "the Queen's Gambit", a chess opening move where a player offers to sacrifice a pawn to gain an advantage in position. 

```python
def manhattan_distance(x1, y1, x2, y2):
  return abs(x1 - x2) + abs(y1 - y2)

# example of queen's gambit move
x1, y1 = 3, 3 # initial position
x2, y2 = 7, 7 # final position

distance = manhattan_distance(x1, y1, x2, y2)
print("The queen's gambit move from {} to {} has a Manhattan distance of {}".format((x1, y1), (x2, y2), distance))
```

# Hamming distance: Are the dimensions exactly equal?

**Hamming distance** is a simple measure of difference between two strings of equal length. It calculates the number of positions in which the corresponding symbols are different in two strings. It is mainly used to detect errors in data transmission or storage.

For example, Hamming distance can be used in DNA sequence analysis to compare two DNA sequences and find similarities and differences between them.

```python
def hamming_distance(seq1, seq2):
    distance = 0
    for i in range(len(seq1)):
        if seq1[i] != seq2[i]:
            distance += 1
    return distance

dna1 = "AGCTACG"
dna2 = "AGCTATG"
print(hamming_distance(dna1, dna2)) # Output: 1
```

# Levenshtein distance: Difference between Sequence 1 and 2?
Levenshtein distance is a string metric that measures the difference between two strings by counting the minimum number of edits (insertions, deletions or substitutions) needed to transform one string into another. In spelling correction algorithms, Levenshtein distance can be used to identify close approximations of correct spelling. [^7]

```python
def levenshtein(str1, str2):
    if len(str1) == 0:
        return len(str2)
    if len(str2) == 0:
        return len(s1)
    if str1[-1] == str2[-1]:
        cost = 0
    else:
        cost = 1
    return min([levenshtein(str1[:-1], str2) + 1,
                levenshtein(str1, str2[:-1]) + 1,
                levenshtein(str1[:-1], str2[:-1]) + cost])
```

However, the disadvantages of this algorithm is that it can be computationally expensive for large strings and not suitable for comparing sets. [^7]

Advanced application of Levenshtein distance can also be found in bioinformatics. Itcan be used to compare DNA or protein sequences and measure the evolutionary distance between species. [^7]

# Cosine Similarity: How similar is Vector A and B?
**Cosine similarity** is a measure of similarity between two non-zero vectors of an inner product space that measures the cosine of the angle between them. In simple terms, cosine similarity compares the direction (or orientation) of two vectors rather than their magnitude. A common use case of cosine similarity is to recommend items to users based on their preferences. For example, given a user's past behavior represented as a vector, we can recommend items that have the highest cosine similarity with that vector. [^8] [^9]

```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.metrics.pairwise import cosine_similarity

def plagiarism_checker(text1, text2):
    vectorizer = CountVectorizer().fit_transform([text1, text2])
    similarity = cosine_similarity(vectorizer[0], vectorizer[1])
    return similarity[0][0]

text1 = "This is a sample text"
text2 = "This is another sample text"

similarity = plagiarism_checker(text1, text2)
print("Cosine similarity:", similarity)
```

The output will be a similarity score between 0 and 1, with 1 indicating that the text is identical.

# Jaccard Similarity: How similar is Set A and B?
Jaccard similarity (Jaccard index) measures the similarity between two sets of data as the size of their intersection divided by the size of their union. Example use cases of this algorithm can be found in text mining, finding similar customers based on purchase history, or recommendation systems. [^10] [^11]

To use Jaccard similarity, you would first need to create a binary representation of each customer's purchase history which is illustrated below.
```python
# Create a set of all items in the catalog
catalog = set(["item1", "item2", "item3", "item4", ...])

# Create a dictionary to store the binary representation of each customer's purchase history
customer_vectors = {}

# Example data for customer purchase history
customer1_purchases = ["item1", "item2", "item3"]
customer2_purchases = ["item2", "item3", "item4"]

# Create the binary representation for each customer
for customer, purchases in [(1, customer1_purchases), (2, customer2_purchases)]:
    vector = [1 if item in purchases else 0 for item in catalog]
    customer_vectors[customer] = vector

# Example output:
# customer_vectors = {1: [1, 1, 1, 0], 2: [0, 1, 1, 1]}
```
Then calculate the Jaccard similarity score between each pair of customer vectors, which can be done by dividing the number of items that both customers have purchased (the set intersection) by the number of items that at least one of the customers has purchased (the set union). The result will be a value between 0 and 1, with 1 indicating that the customers have purchased exactly the same items. [^10] [^11]

```python
def jaccard_similarity(set1, set2):
    intersection = set1.intersection(set2)
    union = set1.union(set2)
    return len(intersection) / len(union)

similarity = jaccard_similarity(customer_vectors[1], customer_vectors[2])
```
If the Jaccard similarity score is high, it indicates that the customers have a similar set of purchased items.

# References

[^1]: Wikipedia. Euclidean Distance. https://en.wikipedia.org/wiki/Euclidean_distance
[^2]: Codecademy (2022). Distance Formulas. https://www.codecademy.com/courses/machine-learning/lessons/distance-formula
[^3]: Russell, S., & Norvig, P. (2010). Artificial Intelligence: A Modern Approach (3rd ed.). Prentice Hall.
[^4]: Sodemann, Angela. (2017). Introduction to Robotics and Unboxing the Kit. [Youtube](https://www.youtube.com/watch?v=pLXoDRctwRg&list=PLT_0lwItn0sDBE98BsbaZezflB96ws12b)
[^5]: Simplify Chess. The Queen's Gambit. [simplifychess.com](https://simplifychess.com/queens-gambit/#:~:text=Queen's%20Gambit%20Accepted-,Overview,centre%20with%20his%20King%20pawn.)
[^6]: Wikipedia. Taxicab Geometry. https://en.wikipedia.org/wiki/Taxicab_geometry
[^7]: Levenshtein, V. I. (1965). Binary codes capable of correcting deletions, insertions, and reversals. Soviet Physics Doklady, 10, 707–710.
[^8]: Codecademy. Natural Language Processing: Word Embeddings. [codecademy.com/learn/dscp-natural-language-processing](https://www.codecademy.com/learn/dscp-natural-language-processing/modules/dscp-word-embeddings/cheatsheet)
[^9]: Scikit Learning (2007-2023). Cosine Similarity. https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html
[^10]: Karabiber, Fatih. (2023). Jaccard Similarity. LearnDataSci. https://www.learndatasci.com/glossary/jaccard-similarity
[^11]:Jaccard, P. (1901). Étude comparative de la distribution florale dans une portion des Alpes et des Jura. Bulletin de la Société Vaudoise des Sciences Naturelles, 37, 547-579.