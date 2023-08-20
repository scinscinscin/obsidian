Data - information gathered about the world
 - manipulated by operations

## ADT - abstract data type
- model of data
- components and properties
- operations performed on data
- is naturally represented by classes in Java
- stages:
	- specification
		- identification of components
		- properties and relationships
		- operations performed
		- "what" instead of how
	- representation
		- how to store
		- results in a Data Structure
			- relationships among data using primitive structures
			- design dictates space and time efficiency
			- can be made using primitive / composite data types
				- composite data types include array, string, structs and classes
		- builds on primitives
	- implementation
		- how an operation is carried out
		- each procedural description is called an **algorithm**
			- named after Musa Al-khwarezm
			- well defined procedure that process input values to solve problems
			- input - values to solve problem
			- output - results to given problem
			- properties
				- definite - each step is unambiguous
				- effective - each step is executed in a finite amount of time
				- finite - terminates after producing output
				- general - solves correctly for all problem instances
				- efficient - uses less time/space resources
			- function - algorithms that return output
			- subroutines - algorithms that do not return output but instead perform side effects
		- uses
			- declarations (variable, method declarations)
			- i/o statements
			- assignments
			- conditional statements
			- looping statements
		- recursive - if a chain of procedural calls contains the same procedure atleast twice
			- recursive definition - defines a concept recursively
			- mathematical induction - proves statements using recursion
			- recursive alg - algorithm that solves problems using recursive procedures
				- basis - direct answer to the smallest version of input
				- recursive step - solves using smaller version of itselve
					- assumes the basis is well defined
					- called inductive step in mathematical induction

## Computational complexity

 - empirical method - actual experiences on program execution
	 - many outside variables
 - theoretical method - measured using theoretical units of time / space
	 - based solely on implementation
	 - larger inputs use more time and space
	 - typically calculated on worst performance
	 - typical big O
		 - O(1) - constant
		 - O(lgn) - logarithms
			 - continually divided from previous size
		 - O(n) - operation performed on each element
		 - O(nlgn) - divided to subproblems then joined together / combined
		 - O(n^2) - fractions of all pairings of data
		 - O(n^3) - fractions of all triples of data
		 - O(2^n) - fractions of all subsets / fibonacci
		 - O(n!) - Fraction of all arrangements of the set of data
	 - typical sorts
		 - Bubble sort - start at the end then bring the lowest value to the start
			 - O(n^2) worst time
		 - Insertion sort - Incrementally grow a sub-array, finding the where to insert the new element being added to existing subarray
			 - O(n^2) worst case
		 - Merge sort - divide and conquer
			 - O(nlgn) worst case
			 - divide in half, then merge, sorting as you grow back up

Stacks
 - set of items in last in first out paradigm
 - linear arrangement of items only accessible from the top
 - item is added by pushing it to the top
 - item is removed by popping from the stack
 - sometimes referred to as the pushdown stack
 - Operations
	 - new - create a new stack
	 - clear - clear the contents
	 - isEmpty - returns true if the stack is empty / top points to no item
	 - isFull - returns true if no new items can be added to the stack
	 - push - add new item
	 - pop - remove / retrieve from the top
	 - peek - see what is at the top WITHOUT removing it

## infix to postfix

 - has an output array v
 - has an operand stack S
 - iterate through the string
	 - if operand, then add to Y
	 - else
		 - while S is not empty and the has greater precedence than the current character (which is an operator)
			 - example addition has lower precedence than multiplication
				 - therefore multiplication would be added from S to V
			 - pop from S and add it to Y
		 - push the current operator
 - add all remaining operators to Y from S
 - return Y

## Infix to prefix

 - maintain optr stack, maintain a reverse output stack
 - for n to 1
	 - add operand to output stack
	 - else transfer a lower precedence operator to output stack
 - transfer remaining operators to rev
 - return the reverse of rev

## Queues
 - first in first out data structure
 - implemented using a circular array
 - has a front and rear

## Linked list

 - data are made point to point
 - stores sequentially
 - head - points to the first node in list
 - tail - points to last node in list

## Trees

 - hierarchical data structures
 - linking in rooted trees branches out from from a root node downward to every other vertex
 - one path between every pair of vertex
 - set of all vertices V and edges on V
	 - vertex / node - object that stores data
	 - edge - connection between vertices
	 - path - sequence of vertex with edges
	- a path is simple if all edges are distinct
	- leaf - a node with no children
		- nonleaves are called internal vertices
- rooter if vertex is designated as a root
- subtree - vertices and edges are part of a larger tree
- theorems
	- a non empty tree with n-vertices has n-1 edges
	- simplest path between any 2 edges is unique
	- a full binary tree with k internal vertices has k+1 leaves
 - Forest - collection of disjoint trees
 - Relations
	 - ancestor / descendant
	 - parent / child
 - Degree - maximum degree of vertices
	 - if a deg is no more than k, then the tree is a k-ary tree
	 - 2-ary = Binary tree
		 - Complete binary tree is 2^-1 nodes where j is the depth / height
		 - almost complete - the nodes are left aligned and are all at the deepest level
 - common representations
	 -  ordered node - has pointers for each children
		 - binary tree has left and right pointers
		 - fixed number of pointers means most are not used
	 - pointer to parent
		 - useful for traversing leaves to root
		 - space eff much less than pointers
		 - does not allow identification of children
	 - children and sibling linked list
		 - each node has a pointer to the next sibling at the same parent and breadth
		 - and a children pointer to first child in the list
	 - an almost complete binary tree can be represented using an array
		 - left can be indexed using 2k
		 - right can be indexed using 2k+1
		 - parent can be indexed using floor(k/2)
 - Traversals
	 - breadth-first - traverses level by level
		 - uses a queue to know which node to visit next
		 - enqueues nodes children and runs until no more nodes left in the queue
	 - pre-order - visits current node first, before children
	 - post-order - visits children first before current node
	 - inorder - left current and right
 - Search trees
	 - uses the key of the node as the index of the data
		 - is a unique identifier

## Binary search tree

 - left child contains trees less than k
 - right child contains trees greater than k
 - search time is O(lgn)
	 - it cuts search by half with each comparison
 - BST delete operation
	 - leaf - trivial case
	 - 1 child - trivial case
	 - 2 child (node to be deleted is n)
		 - find node m with max key in the left subtree
			 - n.key = m.key
		 - assign m.left to the slot m was in parent
			 - m has no right child by definition since m is the largest value in the subtree

## Balanced search trees

 - search trees that always have the minimum height
 - prevents degeneration into a linked list
 - rotation is done in O(log_k N) where k is the degree of the tree

## AVL tree - adelson-velskii and landis

 - monitors the height of subtrees, and the height between left and right must not differ by 1
 - AVL insert
	 - do bst insert normally
	 - get the new node and store it as X
	 - find a node A from X to root such that the heights of left and right subtree of A is greater than 1
	 - B and C are now A's child and grand child on the path to X
	 - perform AVL Rotate (P, A, B, C) where P is the parent of A
		 - assign small medium and large as variables from A, B, C sorted
		 - m.parent = p
		 - if parent = null then m is now the root
		 - else assign m to problematic node's position in the parent
		 - throw m's children not in the path to the parent
		 - fix s, m, l

## heaps

 - almost complete binary trees where the key in the node is better than the children
 - max heap - the key of the current node must be larger than the keys of its descendants
 - min-heap - smaller is better
 - operations
	 - heap enqueue
		 - add item to the end of the array
		 - call heapify up on newly added value
			 - continuously swaps listed index until value is as high as it can go / performs swaps between current node and parent
	 - heap dequeue
		 - removes first item
		 - puts last item in index 0
		 - discard's last index to shrink the heap
		 - calls heapifydown starting from root
			 - starts from an index, finds between self and children which is best for the current index and continuously swaps
			 - after swapping, it calls heapifydown again
	 - heap sort
		 - find the max key, assign it to the root
		 - swap with last, heapify down
		 - largest is back in 1st, swap 2nd to the last
		 - repeat process until the heap is sorted

## Graphs

 - a set of vertices / edges
	 - vertices are adjacent if there is an edge between them
 - degree - number of vertices incident on one
	 - sum of indegree + out degree
 - subgraph - if the set of vertices and edges in Graph A are subsets of vertices and edges in Graph B
	 - graph A is isomorphic with B if nodes of A can be mapped to B
 - complete graph - all pairs of vertices are neighbors
 - sparse graph - has few edges
 - dense - has many edges
 - simple path - a path with no repeating edges
	 - cycle - first and last vertex in a path are the same
	 - two nodes are reachable if a path can be found between the two points
	 - connected graph - an undirected graph where all nodes are reachable to each other
		 - connected component - maximal subgraph of reachable components
	 - strongly connected graph - each vertex in an undirected graph is reachable to each other
 - theorems
	 -  undirected graph has n vertices, m edges, M must be n(n-1)/2 at most
	 - a tree is a connected / acyclic / undirected graph
	 - total indegrees = total out degrees
 - representations
	 - matrix - n\*n matrix showing connections . weights in the graph
	 - list
		 - n lasts containing nodes adjacent
		 - saves space for sparse graphs
		 - easer / faster to iterate
 - graph traversals
	 - spanning tree - a tree with all vertices of G
		 - minimum spanning trees
			 - the spanning tree with lowest total edge weight
			 - can be obtained using kruskal and prim's algo
				 - kruskal
					 - sort the edges by weight
					 - add one by one to mst if it does not form loops
				 - prim's algorithm
					 - track a minheap d whose index represents a single node in the graph
						 - d is the shortest distance to get to a node from a neighbor
						 - all values start as infinite as it gets lower and lower
					 - set the vertex as the root of the MST (therefore it's the first index in the minheap)
					 - while Q is not empty
						 - dequeue to a variable u
						 - add u and the parent of u to MST
						 - for every adjacent node v
							 - if it can improve the weight (ie lower than what is saved in array d)
								 - decrease key for v in the minheap to be the edge weight between u and v
								 - set u to be the parent of v
								 - set v distance to be u
				 - djikstra's algorithm
					 - same as prim but instead of tracking only edgeweight, we track total edgeweight from chosen starting vertex to v
	 - spanning forest - 1 spanning tree per connected component of G
	 - BFS - same as tree BFS but it maintains a list of visited nodes
	 - DFS - recursive w/list of visited nodes

## hashtables

 - adt using relative addressing
 - size = no of slots
 - load factor = % of storage occupied
	 - high = high space utilization
	 - low = wasted space
 - key = unique identifier that distinguishes slots
 - hashing function = used to map key to relative address
 - collision - 2 keys have the same address
	 - keys are called synonymous
	 - collisions cannot happen with a perfect hashing function which doesn't exist
 - uniform hashing - each key is likely to be hashed into a table slot
 - techniques
	 - division remainder - h(n) = n mod d
		 - as d approaches the size of the hashmap, the more uniform it is
	 - digit extraction - determine statistical distributions of the keys
	 - folding - shortens keys to relative addresses by combining values
 - collision resolution
	 - closed hashing - stored in another slot
		 - linear / quadratic folding / double hashing
			 - linear probing -> `h(key, i) = (h(key) + i mod s)`
				 - try to find the next available slot (primary clustering)
			 - double hashing -> `h(key, i) = [h1(k) + i * h2(k)] mod s`
				 - jumps around the hashmap trying to find an open space
				 - i incremented until an open space is found
	 - open hashing - hash table slots link to the synonyms (uses linked lists)
		 - separate chaining / synonym chaining
			 - hash table slots contain a head pointer to a linked list
			 - hashtable COULD degenerate to linked list when not maintained
				 - Either O(1) insertion / O(n) search 
					 - if not balancing
				 - Or O(m/2) insertion / O(m/2) search
					 - if it is sorted before hand / placed at the proper location in the linked list
			 - O(lg m) if using AVL trees instead of using linked lists
 - primary clustering - keys are stored near hash values
 - secondary clustering - keys are stored far from hash values
 - rehashing - expanding the size of the hashtable
	 - if load factor is in (0.90 > n > 0.90)
	 - existing entries are rehashed into a new hash table
		 - provides opportunity to improve hashing function
	 - brings the load factor down
	 - clears deletion markers on slots