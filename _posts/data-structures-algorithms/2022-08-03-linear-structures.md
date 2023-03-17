---
layout: post
title: Linear Data Structures
summary: An overview of linear data structures such as arrays, linked lists, stacks, queues, and hash tables
tag: data-structures-algorithms
---

**Linear Data Structure** are basically list-based collections. [^1] It arranges data elements in a sequential manner just as how computer memory operates, which makes the implementation relatively easier. It is also important to learn how to talk about data structures abstractly and how it is actually implemented using a particular programming language.

- TOC
{:toc}

## Arrays and Types

Arrays are a data structure that store elements with an index or key assigned to them. They are known for their mutability, which allows elements to be added, removed or modified after creation. The characteristics of arrays, such as whether they contain *homogeneous* or *heterogeneous* data types and whether their memory allocation is *static* or *dynamic*, depend on how the programming language was constructed. For example, Python arrays are homogeneous and dynamic, while JavaScript arrays are heterogeneous and dynamic. [^1] [^2]

There are three types of arrays: **Indexed arrays**, which access data through an integer index and include vectors, single rows, and single columns. **Multidimensional arrays**, which have one or more dimensions and include matrices, tensors, and 3D arrays. **Associative arrays**, which store data in key-value pairs and include hash tables and dictionaries.

| Language | Implementation |
| - | - |
| Python | `arr = [item1, item2, ...]`, `arr = list()` |
| JavaScript |`var arr = [item1, item2, ...]`, `var arr = new Array(item1, item2, ...);` |
| C++ | `type arr[length] = {item1, item2, ...};` `vector<type> arr = {item1, item2, ...};` |
| Java | `String[] myStrings = {"apple", "banana", "cherry"};`|

## Linked Lists and Types

**Linked Lists** are a data structure that use links or pointers to connect its elements, rather than indices or keys. They are more efficient than arrays for adding and deleting elements. Common types include Singly(unidirectional), Doubly (bidirectional), and Circular linked lists (circular queue), which can be used for implementing queues, dequeues, and stacks. Applications include image galleries, browser pages, and music players. [^1] [^3]

**Python** implements a linked list by creating a Node class that contains a data attribute and a next attribute which points to the next node in the list, and a LinkedList class which uses the Node class to create and maintain a linked list.

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node
```

**JavaScript**: Linked lists can be implemented using objects or classes to define nodes and create the linked structure.

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
  }

  append(data) {
    const new_node = new Node(data);
    if (this.head === null) {
      this.head = new_node;
      return;
    }
    let last_node = this.head;
    while (last_node.next) {
      last_node = last_node.next;
    }
    last_node.next = new_node;
  }
}
```

**C++**: Linked lists can be implemented using pointers to define nodes and create the linked structure.

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class LinkedList {
public:
    Node* head;
    LinkedList() {
        head = NULL;
    }
    void append(int data) {
        Node* new_node = new Node();
        new_node->data = data;
        new_node->next = NULL;
        if (head == NULL) {
            head = new_node;
            return;
        }
        Node* last_node = head;
        while (last_node->next != NULL) {
            last_node = last_node->next;
        }
        last_node->next = new_node;
    }
};
```

**Java**: Linked lists are implemented using the LinkedList class, which is included in the Java Collections Framework.

```java
public class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {
    Node head;

    public void append(int data) {
        Node new_node = new Node(data);
        if (head == null) {
            head = new_node;
            return;
        }
        Node last_node = head;
        while (last_node.next != null) {
            last_node = last_node.next;
        }
        last_node.next = new_node;
    }
}
```

## Stack

A **stack** is a data structure that follows the last-in-first-out policy, implemented using arrays or linked lists. Elements are added to the top of the stack using push() and removed from the top using pop(). Stacks are useful for revision history, undo mechanisms, string reversals, and backtracking. [^1] [^4]

![Image, "Examples of Stack Data Structure"](/assets/images/linear-data-structures-stack.png)

**Python**: Stacks can be implemented using lists, which are dynamic arrays. The append() and pop() methods are used to add and remove elements, respectively.

```python
stack = []  # Create an empty list to serve as the stack

# Add an element to the top of the stack using the append() method
stack.append(3)
stack.append(7)
stack.append(1)

# Remove the top element of the stack using the pop() method
top_element = stack.pop()
```

**JavaScript**: Stacks can be implemented using arrays, which are similar to Python lists. The push() and pop() methods are used to add and remove elements, respectively.

```javascript
let stack = [];  // Create an empty array to serve as the stack

// Add an element to the top of the stack using the push() method
stack.push(3);
stack.push(7);
stack.push(1);

// Remove the top element of the stack using the pop() method
let topElement = stack.pop();
```

**C++**: Stacks can be implemented using arrays or linked lists, with the push() and pop() methods used to add and remove elements, respectively. In C++, the Standard Template Library provides a built-in stack class.

```cpp
#include <stack>  // Include the stack library

std::stack<int> stack;  // Create an empty stack of integers

// Add an element to the top of the stack using the push() method
stack.push(3);
stack.push(7);
stack.push(1);

// Remove the top element of the stack using the pop() method
int top_element = stack.top();
stack.pop();
```

**Java**: Stacks can be implemented using the Stack class, which is part of the Java Collections Framework. The push() and pop() methods are used to add and remove elements, respectively. Alternatively, a linked list can be used to implement a stack in Java.

```java
import java.util.Stack;  // Import the Stack class

Stack<Integer> stack = new Stack<>();  // Create an empty stack of integers

// Add an element to the top of the stack using the push() method
stack.push(3);
stack.push(7);
stack.push(1);

// Remove the top element of the stack using the pop() method
int topElement = stack.pop();
```

## Queue

A **queues** is a data structure that follows the first-in-first-out policy and can be implemented using arrays or linked lists. The head refers to the oldest element, the tail to the newest element, and peek means to access the head element. Enqueue adds an element to the end of the queue, while dequeue removes the oldest element. Queuing systems are useful for informing clients and workers about events or queue demand in real-time, such as in airport departures or bank waiting screens. [^1] [^5]

**Python**: Queues can be implemented using the deque class from the collections module. deque is an abbreviation for "double-ended queue", which can be used to implement both stacks and queues.

```python
from collections import deque
queue = deque()
queue.append(1) # enqueue
queue.popleft() # dequeue
```

**JavaScript**: Queues can be implemented using arrays. The `push` method can be used to enqueue elements into the array, and the `shift` method can be used to dequeue the first element from the array

```javascript
let queue = [];
queue.push(1); // enqueue
queue.shift(); // dequeue
```

**C++**: Queue data structure is part of the programming language's standard library.

```cpp
#include <queue>

std::queue<int> q;
q.push(1); // enqueue
q.pop(); // dequeue
```

**Java**: linked lists is used to implement queues.

```java
import java.util.LinkedList;

Queue<Integer> q = new LinkedList<>();
q.offer(1); // enqueue
q.poll(); // dequeue
```


## Hash Tables

A hash data structure is a collection of key-value pairs that uses a hash function to map keys to array indices. A hash function takes a key and returns an index in the array. [Implementing a hashtable from scratch](https://coderbook.com/@marcus/how-to-create-a-hash-table-from-scratch-in-python/) is complex because collisions can occur, where multiple keys hash to the same index, requiring a collision resolution strategy. Hash tables are efficient because they support constant time search, insert, and delete operations. Raymond Hettinger’s "[Python Hash Tables](https://thepythoncorner.com/posts/2020-08-21-hash-tables-understanding-dictionaries/)" explains Python's dictionary implementation, which uses hash tables and an open addressing collision resolution method. [^1] [^6] [^7]

**Python**: Hash table is implemented as a built-in data type called dictionary

```python
my_dict = {"key1": "value1", "key2": "value2"} # Creating a dictionary
my_dict["key1"] # Accessing a value by key
my_dict["key3"] = "value3" # Adding a new key-value pair
del my_dict["key2"] # Deleting a key-value pair
```

**JavaScript**: Hash table is implemented using objects.

```javascript
let myObj = {key1: "value1", key2: "value2"}; // Creating an object
myObj.key1; // Accessing a value by key
myObj.key3 = "value3"; // Adding a new key-value pair
delete myObj.key2; // Deleting a key-value pair
```

**C++**: Hash table is implemented using STL(standard library) unordered_map.

```cpp
unordered_map<string, int> my_map = { {"key1", 1}, {"key2", 2} };
my_map["key1"];
my_map["key3"] = 3;
my_map.erase("key2");
```

**Java**: Hash table is implemented using HashMap.

```java
HashMap<String, Integer> my_map = new HashMap<String, Integer>(); // Creating a HashMap
my_map.put("key1", 1);
my_map.put("key2", 2);
my_map.get("key1"); // Accessing a value by key
my_map.put("key3", 3); // Adding a new key-value pair
my_map.remove("key2"); // Deleting a key-value pair
```

## Time and Space Complexity

From the table, we can observe the time and space complexity of the linear data structures, which can help in choosing the appropriate data structure for specific tasks. Majority of the operations run on constant run time while space complexity is the same size of the input.  If you're working with a small dataset, a space complexity of O(n) might not be a problem. However, if you're working with a large dataset, a space complexity of O(n) might not be efficient and you may need to consider alternative data structures with lower space complexity.

| Data Structure | Access | Search | Insertion | Deletion | Space Complexity |
| - | - | - | - | - | - |
| Arrays|O(1)|O(n)|O(n)|O(n)|O(n) |
| Linked Lists|O(n)|O(n)|O(1)|O(1)|O(n) |
| Stack|O(n)|O(n)|O(1)|O(1)|O(n) |
| Queue|O(n)|O(n)|O(1)|O(1)|O(n) |
| Hash Tables|N/A|O(1)|O(1)|O(1)|O(n) |

In terms of web development, linear data structures such as arrays, linked lists, stacks, and queues are commonly used to store and manipulate data.Arrays offer fast access to elements, but have higher time complexity for search, insertion, and deletion compared to other data structures. Linked lists offer constant time insertion and deletion, but have slower access times. Stacks and queues are specialized data structures that offer efficient insertion and deletion operations based on the order of the data. Hash tables offer constant time access, insertion, and deletion, but at the cost of higher space complexity due to the need for additional memory for hash function and collision resolution. In web development, linear data structures are often used for tasks such as storing and retrieving user input, managing session data, and optimizing web page loading times. [^8]

## References

[^1]: Udacity. (2022). List-based Collections. https://learn.udacity.com/courses/ud513
[^2]: GeeksforGeeks. (n.d.). Differences and Applications of List, Tuple, Set and Dictionary in Python. https://www.geeksforgeeks.org/differences-and-applications-of-list-tuple-set-and-dictionary-in-python/
[^3]: GeeksforGeeks. (n.d.). Python List vs Array vs Tuple. https://www.geeksforgeeks.org/python-list-vs-array-vs-tuple/
[^4]: Wikipedia. (n.d.). Stack (Abstract Data Type). https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
[^5]: Wikipedia. (n.d.). Queue (Abstract Data Type). https://en.wikipedia.org/wiki/Queue_(abstract_data_type/)
[^6]: Marcus. (n.d.). How to Create a Hash Table from Scratch in Python. Coderbook. https://coderbook.com/@marcus/how-to-create-a-hash-table-from-scratch-in-python/
[^7]: The Python Corner. (2020, August 21). Hash Tables: Understanding Dictionaries. https://thepythoncorner.com/posts/2020-08-21-hash-tables-understanding-dictionaries/
[^8]: Big O Cheat Sheet.(n.d.). (https://www.bigocheatsheet.com/)