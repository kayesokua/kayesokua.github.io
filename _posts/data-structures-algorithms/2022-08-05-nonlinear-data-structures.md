---
layout: post
title:  Nonlinear Data Structures
summary: A reviwer on nonlinear data structures, nodes and graphs, its properties and applications
tag: data-structures-algorithms
---

A **non-linear data structure** is a type of data structure that stores elements in a hierarchal fashion. This feature utilizes memory better than linear structures because it does not require memory allocation in advance. Even when the input size increases, the time complexity remains the same. However, the implementation of a non-linear data structure is more complex. [^1] [^2] [^3] [^4] [^5] [^6] [^7]

There are two types of non-linear data structures: *trees* and *graphs*.

{% gist 060b23979a86ac5306daca6a5aad86bc %}

- TOC
{:toc}

## Node and Trees

Nodes are the basic unit of data structures and are often arranged in a tree structure. A tree is a collection of nodes that are connected through edges, with the topmost node called the root node. Trees are useful for representing hierarchical data structures, such as file systems and organizational charts. [^4] [^5]

![Image](/assets/images/tree-data-structure.png)

1. **Root node** is the highest node (or topmost) of the tree
2. **Child node** is a node extending from another node
3. **Sibling nodes** are nodes connected to the same parent node
4. **Parent node** is the parent of the current node.
5. **Internal node** is a node with at least one child
6. **Leaf node** is a node with no children.

![Image](/assets/images/non-tree-examples.png)

## Binary Tree

A binary tree is a nonlinear data structure where each node has at most two child nodes.

1. **Properties**: It follows the general tree structure, and each node can have at most two children - a left child and a right child.
2. **Time and Space Complexity:** Binary trees have a time complexity of O(log n) for searching and inserting nodes, and O(n) for worst-case scenarios. The space complexity is also O(n) due to the allocation of nodes in memory.
3. **Applications**: search and sorting algorithms; File systems; Huffman coding

## Binary Search Tree

A Binary Search Tree is a non-linear data structure used for efficient searching and sorting of elements. [^6] [^7]

1. **Properties**: It follows the general binary tree structure, and each node can have at most two children - a left child and a right child. Then a special rule, the left child of a node contains only elements lesser than the node, and the right child contains only elements greater than the node.
2. **Time and Space Complexity:** The time complexity for operations such as search, insertion, and deletion in a Binary Search Tree is O(log n), which is efficient for large datasets. The space complexity is O(n), where n is the number of elements in the tree.
3. **Applications**: Databases, file systems, and compilers for efficient searching and sorting of data

![Image](/assets/images/binary-search-tree.png)

## Adelson-Velskii-Landis Tree

Adelson-Velskii-Landis (AVL) Tree is a self-balancing binary search tree. [^6] [^8] [^9]

1. **Properties**: The properties of an AVL tree are that it is a binary search tree with the additional constraint that the heights of the left and right subtrees of every node differ by at most one.
2. **Time and Space Complexity**: Time complexity of an AVL tree is O(log n) for both search and insertion operations. Space complexity is O(n) for n elements.
3. **Applications**: Fast searching and insertion operations in databases, compilers, implementation of the C++ STL map and set classes

![Image](/assets/images/avl-tree.png)

## Red Black Tree

Red-Black Tree is a self-balancing binary search tree with guarantees on worst-case performance.

1. **Properties**: The properties of a red-black tree are that each node is either red or black, the root and leaves (null nodes) are black, red nodes have black parents, and every path from the root to a leaf contains the same number of black nodes.
2. **Time and Space Complexity**: Red-black tree operations (search, insertion, and deletion) have worst-case time complexity of O(log n). Space complexity is O(n).
3. **Applications**: Red-black trees are used in many software libraries and operating systems, including the Linux kernel and the C++ STL.

## Splay Trees

Splay Tree is a self-adjusting binary search tree with good amortized performance. [^4]

1. **Properties**: Splay trees are binary search trees with the additional property that recently accessed nodes are moved to the root. This way, frequently accessed nodes are kept near the root, improving the overall performance of the tree.
2. **Time and Space Complexity**: The amortized time complexity of a splay tree operation is O(log n). Space complexity is O(n).
3. **Applications**: Splay trees are used in many applications where frequently accessed nodes need to be kept in memory, such as caches and garbage collectors.

![Image](/assets/images/splay-tree.png)

## B-Trees

B-Tree is a self-balancing tree data structure that can handle large amounts of data.

1. **Properties**:  B-Trees are multi-way search trees where each node contains multiple keys and pointers to child nodes. The keys are stored in sorted order, and the tree is kept balanced by adjusting the number of keys in each node.
2. **Time and Space Complexity**: The time complexity of operations on a B-Tree is O(log n) in the worst case. Space complexity is O(n).
3. **Applications**: B-Trees are commonly used in databases and file systems to store large amounts of data efficiently.

![Image](https://cdn.programiz.com/sites/tutorial2program/files/b-tree.png)

## Treaps

Treap is a randomized data structure that combines properties of binary search trees and heaps.

1. **Properties**:  Treaps are binary search trees where each node has an associated priority value. The tree is kept balanced by adjusting the priorities of nodes randomly.
2. **Time and Space Complexity**: The expected time complexity of a treap operation is O(log n). Space complexity is O(n).
3. **Applications**: Treaps are used in many applications where a combination of ordering and randomness is desired, such as in network protocols and computer games.

![Image](https://i.stack.imgur.com/jYjuf.png)

Image from https://livebook.manning.com/book/algorithms-and-data-structures-in-action/chapter-3/

## Fenwick tree

Fenwick Tree (also known as Binary Indexed Tree) is a data structure for efficient calculation of prefix sums. [^9]

1. **Properties**: Fenwick trees are arrays where each element contains the sum of a range of values in the original array. The tree is constructed in a way that allows efficient updates and queries of prefix sums.
2. **Time and Space Complexity**: The time complexity of Fenwick tree operations is O(log n). Space complexity is O(n).
3. **Applications**: Fenwick trees are used in many applications where prefix sums need to be calculated efficiently, such as in range query problems and dynamic programming.

![Image](https://i.stack.imgur.com/QcUPG.png)

Image from Brilliant [^9]

## K-Dimensional Tree

K-Dimensional Tree is a space partitioning data structure for organizing points in a k-dimensional space.

1. **Properties**: K-D Trees are binary search trees where each node is a point in a k-dimensional space. The left and right subtrees of a node are also k-dimensional spaces. It allows efficient range searches and nearest neighbor searches.
2. **Time and Space Complexity**: Searching and insertion operations take O(log n) time in average case but can take O(n) in worst case. Space complexity is O(n).
3. **Applications**: K-D Trees are widely used in computational geometry, computer graphics, machine learning, and geographic information systems. [^12]

![Image](/assets/images/kdtree.png)

## Prefix Tree

Prefix Tree (Trie) is a tree-based data structure used for efficient retrieval of keys in a dataset.

1. **Properties**: A prefix tree consists of a set of nodes, where each node represents a prefix of a key stored in the tree. The root node represents an empty string, and the branches of the tree represent the characters of the keys. Each node in the tree may have multiple children, and the keys are stored in the leaf nodes.
2. **Time and Space Complexity**: The time complexity for inserting, searching, and deleting keys in a prefix tree is O(m), where m is the length of the key. The space complexity of a prefix tree is O(nm), where n is the number of keys and m is the average length of the keys.
3. **Applications**: Prefix trees are often used in applications that require fast string matching, such as spell checkers, search engines, and DNA sequence analysis.

![Image](/assets/images/prefix-tree.png)

## Max and Min Heap Trees

Max and Min Heap Trees are binary trees used to efficiently retrieve the maximum or minimum element in a set of data.

1. **Properties**: In a max heap, each parent node is greater than or equal to its children, while in a min heap, each parent node is less than or equal to its children. The root of the heap contains either the maximum or minimum element in the heap.
2. **Time and Space Complexity**: The time complexity for finding the maximum or minimum element in a heap is O(1), while the time complexity for inserting or deleting an element is O(log n). The space complexity of a heap is O(n).
3. **Applications**: Heap trees are commonly used in priority queues, which are used to manage tasks based on their importance or urgency. They are also used in sorting algorithms, such as heapsort.

![Image](/assets/images/heap-tree.png)

https://docs.python.org/3/library/heapq.html

## Graphs, and Types

Graphs are structures that consist of vertices and edges that connect them. Unlike trees, the relationship between the vertices in a graph is not limited to a parent-child relationship. Graphs are used in many areas such as social networks, knowledge representation, and flight networks. A popular representation of a graph is an adjacency matrix, which can be represented as a two-dimensional array. $$O(V+E)$$ is a common way to represent the time or space complexity of graph algorithms, indicating that the time/space required by the algorithm grows linearly with the number of edges and vertices in the graph. [^13]

![Image](https://miro.medium.com/max/1400/1*IBtDZq0_4yWpXt0mhda0jw.png)

This example below is a directed graph.

```python
   graph = {'A': ['B', 'C'],
             'B': ['C', 'D'],
             'C': ['D'],
             'D': ['C'],
             'E': ['F'],
             'F': ['C']}

def find_path(graph, start, end, path=[]):
        path = path + [start]
        if start == end:
            return path
        if not graph.has_key(start):
            return None
        for node in graph[start]:
            if node not in path:
                newpath = find_path(graph, node, end, path)
                if newpath: return newpath
        return None

```

## Types of Graphs

1. Undirected Graphs:
    - Properties: Edges are undirected and there are no self-loops.
    - Time and Space Complexity: O(V+E) for traversal and O(V^2) for the adjacency matrix.
    - Applications: Social network analysis, route finding, game AI.
2. Directed Graphs (Digraphs):
    - Properties: Edges are directed and there are no self-loops.
    - Time and Space Complexity: O(V+E) for traversal and O(V^2) for the adjacency matrix.
    - Applications: Internet links, website navigation, data flow analysis.
3. Weighted Graphs:
    - Properties: Edges have weights or costs associated with them.
    - Time and Space Complexity: O(E*log V) for Dijkstra's algorithm and O(V^3) for the Floyd-Warshall algorithm.
    - Applications: Shortest path algorithms, traffic routing, flight scheduling.
4. Bipartite Graphs:
    - Properties: Vertices can be divided into two disjoint sets such that every edge connects a vertex in one set to a vertex in the other set.
    - Time and Space Complexity: O(V+E) for traversal and O(V^2) for the adjacency matrix.
    - Applications: Resource allocation, matching algorithms, electronic circuit design.
5. Cyclic Graphs:
    - Properties: Contains at least one cycle.
    - Time and Space Complexity: O(V+E) for traversal and O(V^2) for the adjacency matrix.
    - Applications: Data dependency analysis, deadlock detection, software validation.

## Resources

[^1]: Thomas, J. (2022). *Data Structure and Algorithms With Python: The Ultimate Guide Towards Coding*. Amazon KDP.
[^2]: Tech Differences. (2022). *Difference Between Linear and Non-linear Data Structure*. [techdifferences.com](https://techdifferences.com/difference-between-linear-and-non-linear-data-structure.html)
[^3]: Grow with Google. (2022). *Intro to Data Structures and Algorithms*. [udacity.com](https://www.udacity.com/course/data-structures-and-algorithms-in-python--ud513)
[^4]: Wikipedia. (2022). *Node (Computer Science)*. Wikimedia Foundation. [wikipedia.org](https://en.wikipedia.org/wiki/Node_(computer_science))
[^5]: Wikipedia. (2022). *Tree Data Structure*. Wikimedia Foundation. [wikipedia.org](https://en.wikipedia.org/wiki/Tree_(data_structure))
[^6]: Mallawaarachchi. (2020). *8 Useful Tree Data Structures Worth Knowing*. Medium. [towardsdatascience.com](https://towardsdatascience.com/8-useful-tree-data-structures-worth-knowing-8532c7231e8c)
[^7]: GeekforGeeks. (2022). *Binary Search Tree Data Structure*. [geeksforgeeks.org](https://www.geeksforgeeks.org/binary-search-tree-data-structure/)
[^8]: Wikipedia. (2022). *AVL Tree*. Wikimedia Foundation. [wikipedia.org](https://en.wikipedia.org/wiki/AVL_tree)
[^9]: Mallawaarachchi, Vijini. (2020). Self Balancing Binary Search Trees. https://towardsdatascience.com/self-balancing-binary-search-trees-101-fc4f51199e1d
[^13]:Geek for Geeks. (2022). *Graph Data Structure and Algorithms.* https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/
<!--
[^8]: Baeldung.(2022). *Red-Black Trees*. [baeldung.com](https://www.baeldung.com/cs/red-black-trees)
[^9]: Brilliant Org. (2022). *Fenwick Tree*. [brilliant.org](https://brilliant.org/wiki/fenwick-tree/)
[^10]: Codecademy. (2022). *Learn Advanced Algorithms and Data Structures* [codecademy.com](https://www.codecademy.com/learn/learn-advanced-algorithms-and-data-structures/modules/advanced-trees)
[^11]: Python Software Foundation. (2019). *Python Patterns - Implementing Graphs*. [python.org](https://www.python.org/doc/essays/graphs/)
[^12]: Wikipedia. (2022). *K-D Tree*. https://en.wikipedia.org/wiki/K-d_tree

[^14]: Wikipedia. (2022). *Graphs*. https://en.wikipedia.org/wiki/Graph_(discrete_mathematics) -->
