---
layout: post
title: DFS vs. BFS Tree Traversal
summary: To be revised
tag: data-structures-algorithms
---

**Depth-First Search** starts at the root and explores as far as possible along each branch before backtracking. This implies checking all children first.

While **Breadth-first search** is an algorithm for traversing or searching tree data structure. It starts at the tree root and explores the neighbor nodes first, before moving to the next level neighbors.

* The pre-order traversal will visit nodes in Parent-LeftChild-RightChild order.
* The in-order traversal will visit nodes in LeftChild-Parent-RightChild order. In this way, the tree is traversed in an ascending order of keys.
* The post-order traversal will visit nodes in LeftChild-RightChild-Parent order.

## Depth-First Search

Pre-order Traversal
In-order Traversal
Post-order Traversal

### Pre-Order Traversals
1. Checks off a node as you see it before you traverse any further in a tree
2. Traverse down until we reach the leaf
3. Check the leaf and go back to the parent
4. Traverse to the right child

### In-Order DFS
Checks the node in order from left to right

* **Post-Order DFS** starts from the root but only starts checking from the leaf, moves back to the parent but only checks the sibling node, then moves back to the parent to check it off. Sk

Post order: D, F, E, B, C, A

visits all the children first and return.



## Comparison
