# Quick-notes: Data structures & Algorithms

## Data-Structures

### Linked List

Like arrays, Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at a contiguous location; the elements are linked using pointers.

**Why Linked List?**
Arrays can be used to store linear data of similar types, but arrays have the following limitations.
**1)** The size of the arrays is fixed: So we must know the upper limit on the number of elements in advance. Also, generally, the allocated memory is equal to the upper limit irrespective of the usage.
**2)** Inserting a new element in an array of elements is expensive because the room has to be created for the new elements and to create room existing elements have to be shifted. Deletion is also expensive with arrays until unless some special techniques are used.

Traversing a linked list is costly. Whereas addition and deletion is easy.

**Advantages over arrays**
**1)** Dynamic size
**2)** Ease of insertion/deletion

**Drawbacks:**
**1)** Random access is not allowed. We have to access elements sequentially starting from the first node. So we cannot do binary search with linked lists efficiently with its default implementation. Read about it [here](https://www.geeksforgeeks.org/binary-search-on-singly-linked-list/).
**2)** Extra memory space for a pointer is required with each element of the list.
**3)** Not cache friendly. Since array elements are contiguous locations, there is locality of reference which is not there in case of linked lists.

**Representation:**
A linked list is represented by a pointer to the first node of the linked list. The first node is called the head. If the linked list is empty, then the value of the head is NULL.
Each node in a list consists of at least two parts:
1) data
2) Pointer (Or Reference) to the next node

### Queue

Queues are data structures that follow the **First In First Out (FIFO)** i.e. the first element that is added to the queue is the first one to be removed.

Elements are always added to the back and removed from the front. 

**Variables used**

- queue[]: Array in which queue is simulated
- arraySize: Maximum number of elements that can be stored in a queue[]
- front: Points at the index where the next deletion will be performed
- rear: Points at the index where the next insertion will be performed

**Functions supported**

Queues support the following fundamental functions:

**Enqueue**

If the queue is not full, this function adds an element to the back of the queue, else it prints “**OverFlow**”.

```java
void enqueue(int queue[], int element, int& rear, int arraySize) {
    if(rear == arraySize)            // Queue is full
            printf(“OverFlow\n”);
    else{
         queue[rear] = element;    // Add the element to the back
         rear++;
    }
}
```

**Dequeue**

If the queue is not empty, this function removes the element from the front of the queue, else it prints “**UnderFlow**”.

```java
void dequeue(int queue[], int& front, int rear) {
    if(front == rear)            // Queue is empty
        printf(“UnderFlow\n”);
    else {
        queue[front] = 0;        // Delete the front element
        front++;
    }
}
```

**Front**

This function returns the front element of the queue.

**Size**

This function returns the size of a queue or the number of elements in a queue.

**IsEmpty**

If a queue is empty, this function returns 'true', else it returns 'false'.

The standard queue data structure has the following variations:

1. Double-ended queue
2. Circular queue

**Double-ended queue**

In a standard queue, a character is inserted at the back and deleted in the front. However, in a double-ended queue, characters can be inserted and deleted from both the front and back of the queue.

**Circular queues**

A circular queue is an improvement over the standard queue structure. In a standard queue, when an element is deleted, the vacant space is not reutilized. However, in a circular queue, vacant spaces are reutilized.

While inserting elements, when you reach the end of an array and you need to insert another element, you must insert that element at the beginning (given that the first element has been deleted and the space is vacant).

### Stack

Stacks are dynamic data structures that follow the **Last In First Out (LIFO)** principle. The last item to be inserted into a stack is the first one to be deleted from it.

**Inserting and deleting elements**

Stacks have restrictions on the insertion and deletion of elements. Elements can be inserted or deleted only from one end of the stack i.e. from the top. The element at the top is called the **top** element. The operations of inserting and deleting elements are called **push()** and **pop()** respectively.

When the top element of a stack is deleted, if the stack remains non-empty, then the element just below the previous top element becomes the new top element of the stack.

**Features of stacks**

- Dynamic data structures
- Do not have a fixed size
- Do not consume a fixed amount of memory
- Size of stack changes with each push() and pop() operation. Each push() and pop() operation increases and decreases the size of the stack by 1, respectively.

### Tree

A tree is a nonlinear hierarchical data structure that consists of nodes connected by edges.

A Quick terminology walkthrough

- **Root** is the topmost `node` of the `tree`
- **Edge** is the link between two `nodes`
- **Child** is a `node` that has a `parent node`
- **Parent** is a `node` that has an `edge` to a `child node`
- **Leaf** is a `node` that does not have a `child node` in the `tree`
- **Height** is the length of the longest path to a `leaf`
- **Depth** is the length of the path to its `root`

**Why Tree datastructure?**

Other data structures such as arrays, linked list, stack, and queue are linear data structures that store data sequentially. In order to perform any operation in a linear data structure, the time complexity increases with the increase in the data size.

**Properties**

- Every tree has a special node called the root node. The root node can be used to traverse every node of the tree. It is called root because the tree originated from root only.
- If a tree has N vertices(nodes) than the number of edges is always one less than the number of nodes(vertices) i.e N-1. If it has more than N-1 edges it is called a graph not a tree.
- Every child has only a single Parent but Parent can have multiple child.

**Types of trees**

1. **General tree**

   A tree is called a general tree when there is no constraint imposed on the hierarchy of the tree. In General Tree, each node can have infinite number of children. This tree is the super-set of all other types of trees. 

2. **Binary tree**

   Binary tree is the type of tree in which each parent can have at most **two children**. 

   The children are referred to as **left** child or **right** child. This is one of the most commonly used trees. When certain constraints and properties are imposed on Binary tree it results in a number of other widely used trees like BST (Binary Search Tree), AVL tree, RBT tree etc.

   <img src="https://cdn.programiz.com/sites/tutorial2program/files/binary-tree_0.png" alt="binary-tree" style="zoom:50%;" />

   Read about types of Binary Tree [here](https://www.programiz.com/dsa/binary-tree)

3. **Binary search tree**

   Binary Search Tree (BST) is an extension of Binary tree with some added constraints. In BST, the value of the left child of a node must be smaller than or equal to the value of its parent and the value of the right child is always larger than or equal to the value of its parent. This property of Binary Search Tree makes it suitable for searching operations as at each node we can decide accurately whether the value will be in left subtree or right subtree. Therefore, it is called a Search Tree.

   

4. **AVL tree**

   AVL tree is a self-balancing binary search tree in which each node maintains extra information called a balance factor whose value is either -1, 0 or +1.

   AVL tree got its name after its inventor Georgy Adelson-Velsky and Landis.

   *Balance Factor = (Height of Left Subtree - Height of Right Subtree) or (Height of Right Subtree - Height of Left Subtree)*

   <img src="https://cdn.programiz.com/sites/tutorial2program/files/avl-tree-final-tree-1_0_2.png" alt="avl-tree" style="zoom:50%;" />

5. **Red black tree**

   Red-Black tree is a self-balancing binary search tree in which each node contains an extra bit for denoting the color of the node, either red or black.

   A red-black tree satisfies the following properties:

   1. **Red/Black Property:** Every node is colored, either red or black.
   2. **Root Property:** The root is black.
   3. **Leaf Property:** Every leaf (NIL) is black.
   4. **Red Property:** If a red node has children then, the children are always black.
   5. **Depth Property:** For each node, any simple path from this node to any of its descendant leaf has the same black-depth (the number of black nodes).

   <img src="https://cdn.programiz.com/sites/tutorial2program/files/red-black-tree_0.png" alt="red-black-tree" style="zoom:50%;" />

   Read more about Red-Black Tree [here](https://www.programiz.com/dsa/red-black-tree)

Also check [8 Useful Tree Data Structures | Towards Data Science](https://towardsdatascience.com/8-useful-tree-data-structures-worth-knowing-8532c7231e8c)

## Algorithms

### Sorting Algorithm

#### Merge Sort

Divide the input array into two halves and recursively divides the resultant array into two halves until the length of array is one(only one element present). Then sorts the array and merges it

![MergeSort](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Merge-Sort-Tutorial.png)

### Breadth First Search

There are many ways to traverse graphs. BFS is the most commonly used approach.

BFS is a traversing algorithm where you should start traversing from a selected node (source or starting node) and traverse the graph layerwise thus exploring the neighbor nodes (nodes which are directly connected to source node). You must then move towards the next-level neighbor nodes.

As the name BFS suggests, you are required to traverse the graph breadthwise as follows:

1. First move horizontally and visit all the nodes of the current layer
2. Move to the next layer

![BFS-graph](https://he-s3.s3.amazonaws.com/media/uploads/fdec3c2.jpg)

The distance between the nodes in layer 1 is comparitively lesser than the distance between the nodes in layer 2. Therefore, in BFS, you must traverse all the nodes in layer 1 before you move to the nodes in layer 2.

**Traversing child nodes**

A graph can contain cycles, which may bring you to the same node again while traversing the graph. To avoid processing of same node again, use a boolean array which marks the node after it is processed. While visiting the nodes in the layer of a graph, store them in a manner such that you can traverse the corresponding child nodes in a similar order.

In the earlier diagram, start traversing from 0 and visit its child nodes 1, 2, and 3. Store them in the order in which they are visited. This will allow you to visit the child nodes of 1 first (i.e. 4 and 5), then of 2 (i.e. 6 and 7), and then of 3 (i.e. 7) etc.

To make this process easy, use a queue to store the node and mark it as 'visited' until all its neighbours (vertices that are directly connected to it) are marked. The queue follows the First In First Out (FIFO) queuing method, and therefore, the neigbors of the node will be visited in the order in which they were inserted in the node i.e. the node that was inserted first will be visited first, and so on.

**Pseudocode**

```pseudocode
BFS (G, s)                   //Where G is the graph and s is the source node
      let Q be queue.
      Q.enqueue( s ) //Inserting s in queue until all its neighbour vertices are marked.

      mark s as visited.
      while ( Q is not empty)
           //Removing that vertex from queue,whose neighbour will be visited now
           v  =  Q.dequeue( )

          //processing all the neighbours of v  
          for all neighbours w of v in Graph G
               if w is not visited 
                        Q.enqueue( w )             //Stores w in Q to further visit its neighbour
                        mark w as visited.
```



![bfs-traversal](https://he-s3.s3.amazonaws.com/media/uploads/0dbec9e.jpg)

**Traversing process**

The traversing will start from the source node and push *s* in queue. *s* will be marked as 'visited'.

*First iteration*

- s will be popped from the queue
- Neighbors of s i.e. 1 and 2 will be traversed
- 1 and 2, which have not been traversed earlier, are traversed. They will be:
  - Pushed in the queue
  - 1 and 2 will be marked as visited

*Second iteration*

- 1 is popped from the queue
- Neighbors of 1 i.e. s and 3 are traversed
- s is ignored because it is marked as 'visited'
- 3, which has not been traversed earlier, is traversed. It is:
  - Pushed in the queue
  - Marked as visited

*Third iteration*

- 2 is popped from the queue
- Neighbors of 2 i.e. s, 3, and 4 are traversed
- 3 and s are ignored because they are marked as 'visited'
- 4, which has not been traversed earlier, is traversed. It is:
  - Pushed in the queue
  - Marked as visited

*Fourth iteration*

- 3 is popped from the queue
- Neighbors of 3 i.e. 1, 2, and 5 are traversed
- 1 and 2 are ignored because they are marked as 'visited'
- 5, which has not been traversed earlier, is traversed. It is:
  - Pushed in the queue
  - Marked as visited

*Fifth iteration*

- 4 will be popped from the queue
- Neighbors of 4 i.e. 2 is traversed
- 2 is ignored because it is already marked as 'visited'

*Sixth iteration*

- 5 is popped from the queue
- Neighbors of 5 i.e. 3 is traversed
- 3 is ignored because it is already marked as 'visited'

The queue is empty and it comes out of the loop. All the nodes have been traversed by using BFS.

### Depth First Search

The DFS algorithm is a recursive algorithm that uses the idea of backtracking. It involves exhaustive searches of all the nodes by going ahead, if possible, else by backtracking.

Here, the word backtrack means that when you are moving forward and there are no more nodes along the current path, you move backwards on the same path to find nodes to traverse. All the nodes will be visited on the current path till all the unvisited nodes have been traversed after which the next path will be selected.

This recursive nature of DFS can be implemented using stacks. The basic idea is as follows:

- Pick a starting node and push all its adjacent nodes into a stack.
- Pop a node from stack to select the next node to visit and push all its adjacent nodes into a stack.
- Repeat this process until the stack is empty. However, ensure that the nodes that are visited are marked. This will prevent you from visiting the same node more than once. If you do not mark the nodes that are visited and you visit the same node more than once, you may end up in an infinite loop.

**Pseudocode**

```pseudocode
    DFS-iterative (G, s):                                   //Where G is graph and s is source vertex
      let S be stack
      S.push( s )            //Inserting s in stack 
      mark s as visited.
      while ( S is not empty):
          //Pop a vertex from stack to visit next
          v  =  S.top( )
         S.pop( )
         //Push all the neighbours of v in stack that are not visited   
        for all neighbours w of v in Graph G:
            if w is not visited :
                     S.push( w )         
                    mark w as visited


    DFS-recursive(G, s):
        mark s as visited
        for all neighbours w of s in Graph G:
            if w is not visited:
                DFS-recursive(G, w)
```



![dfs-traversal](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg)



### BFS vs DFS

**BFS**: *Proceeds 'level by level', visiting all nodes on one level before moving to the next*.

BFS is going to use more memory depending on the branching factor, however, BFS is a complete algorithm meaning if you are using it to search for something in the lowest depth possible, BFS will give you the optimal solution. BFS space complexity is `O(b^d)` the branching factor raised to the depth (can be A LOT of memory).

**DFS**: *Follows a path from starting node to an ending node, then another path from start to end and so on, until all the nodes are visited.*

DFS on the other hand, is much better about space however it may find a suboptimal solution. Meaning, if you are just searching for a path from one vertex to another, you may find the suboptimal solution (and stop there) before you find the real shortest path. DFS space complexity is `O(|V|)`... meaning that the most memory it can take up is the longest possible path.

They have the same time complexity.

In terms of implementation, BFS is usually implemented with `Queue`, while DFS uses a `Stack`.

**How is the data structure chosen for the implementation**

Draw a small graph on a piece of paper and think about the order in which nodes are processed in each implementation. How does the order in which you encounter the nodes and the order in which you process the nodes differ between the searches?

One of them uses a stack (depth-first) and the other uses a queue (breadth-first) (for non-recursive implementations, at least).

