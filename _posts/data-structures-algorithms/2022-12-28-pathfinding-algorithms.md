---
layout: post
title: Pathfinding Algorithms
summary: Pathfinding or pathing is the plotting, by a computer application, of the shortest route between two points. It is a more practical variant on solving mazes
tag: data-structures-algorithms
---

* TOC
{:toc}

Pathfinding or pathing is the plotting, by a computer application, of the shortest route between two points. It is a more practical variant on solving mazes

# Breadth-First Search
**Breadth-First Search** is a graph traversal algorithm that explores all the vertices at the current depth level before moving on to the next level.

✅ Complete: It visits all nodes in the graph, so it's guaranteed to find the solution if it exists.

✅ Optimal: BFS always finds the shortest path from the starting node to the goal node.

❌ High space complexity: requires a queue data structure to store nodes, which can use up a lot of memory for large graphs

# Depth-First Search
**DFS** is a graph traversal algorithm that explores as far as possible along each branch before backtracking.

✅ Space efficiency: DFS uses a stack data structure, which is more memory efficient than a queue.
Suitable for infinite graphs: DFS can handle infinite graphs, as it will only explore nodes that are reachable from the starting node.
Cons of DFS:

❌ Non-optimal: DFS does not guarantee that the path it finds is the shortest path.

❌ Incomplete: DFS may not visit all nodes if the graph contains cycles, making it impossible to find the solution.

# Dijkstra's Algorithm
Dijkstra's Algorithm is a graph search algorithm that finds the shortest path from a source node to all other nodes in a weighted graph.

✅ Guaranteed to find the shortest path in a graph with non-negative edge weights.

✅ The algorithm is simple to implement and understand.

✅ Can be easily modified to find paths from multiple sources.

❌ Has a time complexity of $$O(E + VlogV)$$, which can be slow for large graphs.

❌ Not efficient for graphs with negative edge weights.

❌ Not suitable for real-time systems where quick response is required, as it has to process all nodes before finding the shortest path.


# A* Algorithm
A heuristic search algorithm that finds the shortest path from a source node to a target node in a weighted graph.

# Bellman-Ford Algorithm
 A single-source shortest path algorithm that can handle negative edge weights.

# Floyd-Warshall Algorithm
An all-pairs shortest path algorithm that finds the shortest distances between all pairs of vertices in a weighted graph.

# Bidirectional Search
An optimization technique for graph search algorithms that involves searching from both the source and target nodes simultaneously.

# Greedy best-first search
A graph search algorithm that selects the next node to visit based on the estimated distance to the target node.
