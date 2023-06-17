# Topics

## Data Structures

## 8 Common Data Structures every Programmer must know

## Why you should learn Big-O and stop hacking your way through algorithms

## Data Structure

What type of data gets stored in a data structure ?

a number of data items grouped together is called compound data that need to be stored in a data structure.

There is no one data structure to rule them all.

The way we sort data Structures is how efficient they are in adding,retrieving(getting) , sorting or searching is by employing O(n)

### Types of Data Structures

1. Linked list : A linked list is a sequential structure that consists of a sequence of items in linear order which are linked to each other.

#### **Linked list terms**

- Elements in a linked list are known as nodes.
- Each node contains a key and a pointer to its successor node, known as next.
- The attribute named head points to the first element of the linked list.
- The last element of the linked list is known as the tail.

        Head                            Tail
        (12)    ->      (8)     ->      (7)
        node| pointer |node| pointer |  node

#### **Types of linked list**

- Singly linked list — Traversal of items can be done in the forward direction only.
- Doubly linked list — Traversal of items can be done in both forward and backward directions. Nodes consist of an additional pointer known as prev, pointing to the previous node.
- Circular linked lists — Linked lists where the prev pointer of the head points to the tail and the next pointer of the tail points to the head.

#### **Linked list operations**

- Search: Find the first element with the key k in the given linked list by a simple linear search and returns a pointer to this element
- Insert: Insert a key to the linked list. An insertion can be done in 3 different ways; insert at the beginning of the list, insert at the end of the list and insert in the middle of the list.
- Delete: Removes an element x from a given linked list. You cannot delete a node by a single step. A deletion can be done in 3 different ways; delete from the beginning of the list, delete from the end of the list and delete from the middle of the list.

#### **Applications of linked lists**

- Used for symbol table management in compiler design.
- Used in switching between programs using Alt + Tab (implemented using Circular Linked List).

Pro to linked list :

its really good at adding or deleting new items.

Con to linked list :

its bad at retrieving or searching because every node is only aware of the node next to it.

2. Array : An array is a structure of fixed-size, which can hold items of the same data type.rrays are indexed, meaning that random access is possible.

#### **Array operations**

- Traverse: Go through the elements and print them.
- Search: Search for an element in the array. You can search the element by its value or its index
- Update: Update the value of an existing element at a given index
- Inserting elements to an array and deleting elements from an array cannot be done straight away as arrays are fixed in size.

#### **Applications of arrays**

- Used as the building blocks to build other data structures such as array lists, heaps, hash tables, vectors and matrices.
- Used for different sorting algorithms such as insertion sort, quick sort, bubble sort and merge sort.

Pro:

as a result of the array being a continous value we can retrieve items very efficiently

Con:

since array needs to be contiunous we might need to move the array to a different spot in the memory as we are adding. which takes away from its efficency

3. Hash table : A Hash Table is a data structure that stores values which have keys associated with each of them. Furthermore, it supports lookup efficiently if we know the key associated with the value.

#### **Hash Function**

A special function named as the hash function (h) is used to overcome the problem in direct addressing.

In direct accessing, a value with key k is stored in the slot k. Using the hash function, we calculate the index of the table (slot) to which each value goes. The value calculated using the hash function for a given key is called the hash value which indicates the index of the table to which the value is mapped.

#### _h(k) = k % m_

h: Hash function

k: Key of which the hash value should be determined

m: Size of the hash table (number of slots available). A prime value that is not close to an exact power of 2 is a good choice for m.

#### **Applications of hash tables**

- Used to implement database indexes.

- Used to implement associative arrays.

- Used to implement the “set” data structure.

Pro:

good at adding, removing, retrieving

cons: a collision might occur where two keys might hash to the same memory location.(doesnt affect workflow but needs to be mentined)

4. stack and queue: very similar, stack is last in first out. queue is first in first out

#### **Stack operations**

- Push: Insert an element on to the top of the stack.
- Pop: Delete the topmost element and return it.
- Peek: Return the top element of the stack without deleting it.
- isEmpty: Check if the stack is empty.
- isFull: Check if the stack is full.

#### **Applications of stacks**

- Used for expression evaluation (e.g.: shunting-yard algorithm for parsing and evaluating mathematical expressions).
- Used to implement function calls in recursion programming.

#### **Applications of queues**

- Used to manage threads in multithreading.
- Used to implement queuing systems (e.g.: priority queues).

Pros : efficient add and remove

Cons : limited use cases

#### **Queue operations**

- Enqueue: Insert an element to the end of the queue.
- Dequeue: Delete the element from the beginning of the queue.

4. Graphs and Trees : graph is similar to linked list istead of the pointer its called edges and edges can have weights or numbers assigned to them

Directed Graphs
A graph G is said to be a directed graph if all its edges have a direction indicating what is the start vertex and what is the end vertex.

Undirected Graphs
A graph G is said to be an undirected graph if all its edges have no direction. It can go in both ways between the two vertices.

#### **Applications of graphs**

- Used to represent social media networks. Each user is a vertex, and when users connect they create an edge.
- Used to represent web pages and links by search engines. Web pages on the internet are linked to each other by hyperlinks. Each page is a vertex and the hyperlink between two pages is an edge. Used for Page Ranking in Google.
- Used to represent locations and routes in GPS. Locations are vertices and the routes connecting locations are edges. Used to calculate the shortest route between two locations.

a special graph is called a tree when the data is expanding in one direction (can use parent and children naming to signal the order of the tree)

there is a special tree called binary search tree its bound by specific rules but it allows for really efficient searching

#### **binary search tree rules**

1. each can have a maximum of 2 children (0-2)

2. left child must be less than parent

3. right child must be more than the parent

an unbalanced BST(binary search tree) can lose efficency really quickly

#### **binary search tree attributes**

1. key: The value stored in the node.
2. left: The pointer to the left child.
3. right: The pointer to the right child.
4. p: The pointer to the parent node.

#### **Applications of trees**

- Binary Trees: Used to implement expression parsers and expression solvers.
- Binary Search Tree: used in many search applications where data are constantly entering and leaving.
- Heaps: used by JVM (Java Virtual Machine) to store Java objects.
- Treaps: used in wireless networking.

5. Heaps

A Heap is a special case of a binary tree where the parent nodes are compared to their children with their values and are arranged accordingly.

#### **types of Heaps**

- Min Heap — the key of the parent is less than or equal to those of its children. This is called the min-heap property. The root will contain the minimum value of the heap.
- Max Heap — the key of the parent is greater than or equal to those of its children. This is called the max-heap property. The root will contain the maximum value of the heap

#### **Applications of heaps**

- Used in heapsort algorithm.
- Used to implement priority queues as the priority values can be ordered according to the heap property where the heap can be implemented using an array.
Queue functions can be implemented using heaps within O(log n) time.
- Used to find the kᵗʰ smallest (or largest) value in a given array.

### Big O

Both take the worst case.

Time complexity

how much time is required to run the function. base case is O(1) but when using a loopit becomes O(n) if the loop has a condition like (i=array.Length/2) the time complexity becomes O(n/2)

Space complexity

how much space is required to run the function. base case is O(1) but when using a loop to insert data it becomes O(n)

### Discussion Questions

What is 1 of the more important things you should consider when deciding which data structure is best suited to solve a particular problem?

depending on my requirements for the data structure, if i require fast inserting i use structures that have good data insertion times

How can we ensure that we’ll avoid an infinite recursive call stack?

by introducing a base case to stop the function once a certain criteria is met
