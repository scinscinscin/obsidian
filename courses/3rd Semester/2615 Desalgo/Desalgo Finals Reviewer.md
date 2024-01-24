---
tags:
  - reviewer
course: CS2615 - Design and Analysis of Algorithms
period: Finals
assessment: Final Exam
---

![](https://www.youtube.com/watch?v=ATd59_wqSJA)
# Transform and conquer
 - Modify the problem instance to something easier to work with
 - Conquer - work back to original problem 
 - Strengths
	 - Take advantage of powerful data structures
	 - Effective in complexity theory
 - Disadvantages
	 - requires ingenuity (especially in reduction)
### Variations
 
 - instance simplification - transform to a simpler or more convenient instance of the same problem
	 - Pre-sorting - many questions about a list are easier to answer if the list is sorted
		 - sorting a list takes O(nlgn) time
 - Representation change - Transform to a different representation of the same instance
	 - Horner's rule
		 - Convert a formula to a new one by successively taking x as a common factor in the remaining polynomials of diminishing degrees
		 - Create a variable called val whose starting value is the coefficient of the highest degree
		 - Iterate over remaining coefficients by `val = val(x) + coefficient`
		 - ``const horner = (coeffs, x) => coeffs.slice(0, -1).reverse().reduce((acc, curr) => acc * x + curr, coeffs[coeffs.length - 1])``
		 - Runs in O(n) time
	 - binary exponentiation
		 - Create a variable called val whose starting value is the base
		 - For every bit in the exponent starting from the 2nd highest bit, `val = val * val * (current bit == 1 ? base : 1)`
		 - ``const binaryExponentiation = (base, exp) => exp.toString(2).split("").slice(1).reduce((val, curr) => val * val * (curr == 1 ? base : 1), base)``
		 - Runs in O(lgn)
	 - Heap and heapsort
		 - Transforms an array into a heap
		 - Used to implement priority queues
			 - A multiset of items with orderable priorities with the following operations
				 - Find the item with highest priority
				 - Delete an item with the highest priority
				 - Add a new item to the multiset
	 - Balanced search trees
 - Problem reduction - Transform to an instance of a different problem for which you know an efficient algorithm
	 - Computing LCM
		 - lowest integer that both numbers divide perfectly
		 - ``lcm(m, n) = mn / gcd(m,n)``
	 - Computing paths in a graph
	 - Reduction to optimization problems
	 - Reduction to graph problems
		 - Algorithms available after reduction to a graph problem
			 - BFS and DFS
		 - State-spaces graphs - Vertices represent states and edges represent valid transition between states
			 - River crossing puzzle - all must cross river, however you need to do it in a specific order otherwise things eat each other, Can be represented using states and transitions

# Greedy Algorithms
 - Greedy method - general algorithm design paradigm
	 - Configurations - different choices / collections / values to find
	 - Objective function - a score assigned to configurations that we want to max / minimize
 - Greedy choice property - a globally optimal solution can always be found by a series of local improvements from a starting configuration
 - Greedy algorithm - always makes the choice that looks the best at the moment
	 - a sequence of locally optimal solutions will lead to a globally optimal solution
	 - Tend to be easier to code than other techniques

**Making Change**
 - break an amount using a set of coin amounts and minimize the number of coins returned
 - Greedy - always return the highest value coin you can
	 - Only works no value over the highest denomination can be minimized by omitting the highest value coin
	 - Ex: 0.32p, 0.08p, 0.01p is solvable using this solution
	 - Ex: 0.30p, 0.20p, 0.05p, 0.01p is not solvable using this solution
 - Runs in O(n)

**Fractional knapsack problem**
 - Given a set of problems with each item i having a value and weight, choose items with maximum total benefit but with least weight
 - Maximize Summa(benefit / weight), such that the sum of the weights is <= W
 - Keep taking the item with the highest benefit to weight ratio
 - Runs in O(nlgn)

**Task Scheduling**
 - a set of tasks with a start and finish time
 - perform all tasks using a minimum number of machines
 - Consider n tasks by their start tie and schedule on an available machine
	 - while T is not empty
		 - remove task i with smallest s
		 - if there is an available machine, use it
		 - else increase the number of machines and allocate the task to that machine
	 - return the number of machines used
 - Runs in O(nlgn) time, sorting using a minheap based on the start time

**Text compression**
 - files can often be compressed - represented using fewer bytes than standard representation
 - Fixed length encoding - some characters are more common than others, more common characters should have a shorter representation
 - Huffman encoding - Uses shorter codes for more frequent symbols - no code is a prefix of another code
 - How to do it
	 - Construct a binary tree from the bottom up
	 - Create a node for each character with frequency counts
	 - Create two lowest count roots and merge them
		 - Count for new parent is the sum of the children's roots
	 - The code forr each character is determined by the path from the root to the corresponding leaf
		 - Right = 1, left = 0, symbols on leaves only, no code is a prefix of another
	 - Huffman tree for: ``{ m: 5, a: 11, h: 2, b: 3, ' ': 6, n: 2, g: 4 }`` ![[Pasted image 20231015030822.png]]

**Minimum spanning tree**
 - *tbh you can import ung 2605 notes here*
 - Spanning tree - subgraph tree that connects all nodes
 - Weight of a tree - sum of edge weights
 - Minimum spanning tree - one that connects all nodes with the least total weight
 - Kruskal's algorithm - select a minimum weight edge that does not form a cycle
	 - Uses a minheap to sort the edges (ascending edge weight order)
	 - Grows the MST by adding a least weighted cycle that will not cause a cycle
	 - Cycles can be detected by keeping track of sets of connected components
	 - **Running Time**: $O(|E|lg|E| + |E|lg^*|V|)$
 - Prim's algorithm - start from an an arbitrary node, choose the minimum edge weight from N to V-N
	 - Uses minheap to keep track the minimum edge weight adjacent to each nodes
	 - Greedy using the partition property
	 - Grow MST from a vertex by adding a least weighted edge joining a vertex in MST to another vertex not in MST
	 - **Running Time:** $O(|V|lg|V|+|E|lg|V)$

**Shortest paths**
 - Given a weighted directed graph
	 - find the shortest path from vertex u to vertex v
	 - the shortest paths from vertex u to all other vertices in V
	 - shortest path from each vertex in V to a vertex u
	 - shortest paths from each vertex to every other vertex
 - How to do it:
	 - Grows a shortest paths tree from a vertex by adding the nearest node from the tree
	 - Iteratively improves paths to non SPT vertices from newly added nodes to the SPT
	 - maintain two arrays and a queue, one array represents distances of a node from the start node, another array maintains the parents of each node
	 - we enqueue all nodes with the distance value of infinity, set the starting vertex to have a distance of 0
	 - while the queue is not empty, dequeue it from the queue, for each adjacent vertex, if the current distance of the adjacent is greater than the current distance of the current node + edge weight, set the current node as the parent and decrease the queue
 - It adds vertices in increasing path lengths

**Disjoint set operations**
 - a collection of non empty sets that partitions U
 - Each set is identified by a fixed member of the set, called its representative
 - Operations
	 - `MAKE-SET(x)` - Make a new set with only X
		 - x is the set's representative
		 - assume that X is not already in another set
	 - `UNION(x, y)` - combine two sets containing x and y into one new set, a representative is selected for the new set
	 - `FIND-SET(x)` - return the representative of the set containing x
 - Linked list implementation
	 - Each set is a linked-list, with head and tail points
	 - Each node contains value, next node ptr and back to representative pointer
	 - Make-set costs O(1) - create a single element list
	 - Find-set costs O(1) - return back to representative pointer
	 - Union costs O(lg n)

# Dynamic Programming
**Optimization substructure** - exists when a solution to a problem is recursively defined in terms of optimal solutions to subproblems
**Memoization** - solutions to subproblems are remembered
**Dynamic programming**
 - applicable to optimization problems when a solution to a problem has an optimal substructure and becomes efficient using memoization
 - the subproblems overlap
	 - two similar problems can contain subproblems in common, and two subproblems contain a common sub-sub-problem, thus remembering solutions allow for fast computations
 - **Difference from divide and conquer**
	 - A divide and conquer algorithm might solve the same subproblems multiple times since they are solved independently
 - **How to do it**
	 - Recursively break the original problem to smaller subproblems
		 - Characterize the optimal solution to contain optimal solution so subproblems
	 - Iteratively solve subproblems bottom up, starting with the base cases
		 - Remember solutions to subproblems
		 - Combine solutions to solve bigger problems

**0/1 Knapsack Problem**
 - How to pack the knapsack of max weight W to achieve maximum total value of packed items?
 $$
B[i, w] =
\begin{cases}
0  & \text{if $i=0$ or $w=0$} \\
\begin{cases}
B[i-1, w],  & \text{if $w_i > w$} \\
max(B[i-1, w], B[i-1, w-w_i]+b_i) & \text{if $w_i \le w$}
\end{cases}
\end{cases}
$$
 - The solution uses a two-dimensional array, called B, to keep track of the maximum benefit of including each item per weight.
	 - Each column represents an item and each row represents a weight.
	 - This array is constructed iteratively from the lower weights to the higher weights, where the lower weights are guaranteed to be optimal, hence adhering to the optimization substructure
 - Calculating higher weights is done as following
	- Check if the item can be added with the remaining weight. 
		- Say max_weight is 20, the current row is 15 and the current item weights 9. The item cannot be added (since 24 > 20, thus `w_i` > w), so current item is copied from the previous column in the same weight row.
		- if the item can be added, it needs to be checked if the benefit of adding the item is higher than not adding it.
			- We compare `B[i-1, w]` with `B[i-1, w-w_i] + b_i` where `w_i` is the weight of the current item, and `b_i` is the benefit of the current item, and then take the one that yields higher benefit.
			- `B[i-1, w]` represents the max optimal benefit of not adding the item
			- `B[i-1, w-w_i]` represents the max optimal benefit of items 1 to i-1 with a max_weight of `w-w_i`. We subtract from the weight since the current item is **not** being accounted for.
				- Ex: If we have a bag of 5 items, we're calculating the optimal solution for a bag of 4 items with a reduced weight (by taking item 5 out of the equation).
- Running time
	- The problem is solved by calculating all of the entries of a 2d array with `|n| + 1` items and `W + 1` rows. Thus the running time is `O(n * W)`
		- Can run poorly when the weight is high, therefore scaling needs to be performed (converting weights to tons, might reduce the accuracy of the algorithm),

**Bellman-Ford Shortest Paths Algorithm**
 - Single-source Shortest Path problem
	 - Find the minimum weight path from a given source to every other vertex
 - Optimal substructure - the shortest path consists of shortest subpaths
 - Properties
	 - Shortest path satisfies the triangle inequality where a direct route between point a to c is always less than the route from a to b to c
	 - The graph must not have negative weight cycle, since it will not have a solution. (you can keep going to negative infinity)
 - **Why Dijkstra's doesn't work for digraphs with negative weights**
	 - Dijkstra's adds to the shortest path tree by the smallest total path length (using a min priority queue)
	 - If it allowed negative edge weights, it might find a better distance for a node that's already in the shortest paths tree
 - **Bellman Ford**
	 - Solution
		 - We maintain a 2d array that signifies the cheapest length to every node from the start node, with a max amount of edges
			 - Each additional row is an additional edge for traversal
			 - Each column represents a node, with the starting node as the first node.
		 - For every row
			 - For each node
				 - For each adjacent_node of node
					 - Calculate edge_weight + shortest path for node in previous row and compare if it is smaller than the shortest path for adjacent_node in previous row.
	 - Running time - `|n| * |n| * |n| = O(n^3)`
		 - Number of columns - `|n|`
		 - Number of rows - `|n|`
			 - The worst case of the algorithm for a graph with n nodes is when the graph is a linked list, where the shortest path tree will have n edges.
		 - Number of adjacent nodes
			 - The worst case is when the graph is completely connected, where each node is adjacent to each other, each node has `|n|` neighbors

**Matrix Chain Multiplication**
 - Determining the best order to multiply matrices to minimize the number of multiplication operations
 - Solution
	 - Utilizes a square matrix that contains minimal multiplication operations for each matrix multiplication
		 - The top right element is the minimal for all matrices
		 - Top left leans to the first n elements
		 - Bottom right leans to the last n elements
		 - The diagonal of the array is all 0s, representing individual matrices
			 - (individual matrices contain no multiplication operations)
		 - The bottom left half of the matrix is all null
	 - Starting from the diagonal of the matrix, the next upper-right diagonal is computed which represents more matrices being multiplied
		 - Center diagonal - 1 Matrix (A, B, C, D)
			 - Next diagonal - 2 Matrices (AB, BC, CD)
			 - Is done until the final diagonal of the matrix, the upper right corner (ABCD).
	 - Each entry is calculated by trying all possible combination of factors, which lie on the same row and column.
		 - Example: `ABCD` is being calculated
			 - `ABC`, `AB` and `A` all lie on the same row
			 - `D`, `CD` and `BCD` all lie on the same column
		 - Each entry is calculated using 
			 - `p = a.value + b.value + a.rows * a.columns * b.rows`
			 - then the minimum is taken
 - Running time - `O(n^3)`
# Iterative Improvements
 - an algorithm design technique for solving optimization problems
	 - start with a feasible solution
	 - repeat until no improvement can be found
		 - change current solution to a new feasible solution with a better value of the objective function
	 - return the last feasible solution as "optimal"
		 - is sometimes the locally optimal solution, not globally optimal
		 - Greedy and DP algorithms are subset of iterative improvement algorithms which are guaranteed to provide globally optimal solutions based on the Greedy Choice property and Optimal substructure principles
 - Difficulties
	 - Finding the initial feasible solution
		 - Use a trivial solution
		 - Use an approximate or arbitrary solution
	 - Determining changes that can be made to improve the current solution
		 - Efficiently check fi the current soln is locally optimal
		 - Determine how to find a better one to replace current soln
	 - Can get trapped in a local extrema instead of progressing to global extrema

**Bellman Ford (Iterative Improvements)**
 - runs like Djikstra by maintaining an array containing distances from the start node to each vertex.
 - runs like Kruskal by iterating through each edge (multiple times)
 - an array D is maintained that list distances from the start node to each vertex
	 - `d[s]` is set as 0 since s is the start node
 - for k between 1 to |V| - 1
	 - for all edges between (u, v) in set E
		 - if `d[v] > d[u] + weight(u, v)`
			 - relax that edge by setting the parent of v to be u
			 - sometimes u is infinite
 - The running time is O(VE)

**Flow networks**
 - A weighted digraph with non negative integer edge weights where the weight of an edge e is called the capacity c(e) of e
 - Two vertices, s and t, called the source and sink respectively such that s has no incoming edges and t has no outgoing edges.

**Flow**
 - A flow for a network N is an assignment of integer values f(e) to each edge
	 - Capacity rule - the flow going through a pipe cannot be more than its capacity
	 - Conversation rule - A cut has the same total flow between its left and right
 - The value of a flow f, denoted by |f| is the total flow from the source, which is the same as the total flow into the sink.

**Maximum flow problem**
 - A flow is a maximum flow if its value is the largest of all flows for N
 - Given a flow network N - find a flow with maximum flow value for N
 - Cut - creates 2 disjoint sets V_s and V_t of vertices such s belongs to V_s and t belongs to V_t
	 - Forward edge - the origin is in V_s and destination of the edge is in V_t
	 - backward edge - the origin is in V_t and the destination of the edge is in V_s
	 - The capacity c(x) of cut x - total capacity of forward edges
	 - The flow f(x) of a cut x - the total flow of forward edges minus the total flow of backward edges.
 - Max-flow Min-cut theorem
	 - The flow value is less than the capacity of any cut 
	 - The maximum flow of a network is equal to the minimum capacity of any cut
		 - The edges affected by the cut serve as the bottleneck of the flow network
 - Augmenting path
	 - Consider a flow in a network N - A flow is a path in the graph that does not take into account the direction of the arrows, it treats the graph like an undirected graph
	 - Let pi be a path from s to t
		 - Let e be an edge from u to v in the direction of pi (going from the source to sink)
		 - Residual capacity of a forward edge - Capacity of that edge - flow of that edge
		 - Residual capacity of a backward edge - The flow of that edge
		 - The residual capacity of the path pi is the minimum between the residual capacities of all edges
	 - A path pi between s to t is an augmenting path if its residual capacity is greater than 0
	 - The flow along this path can be increased by its residual capacity

## Ford Fulkerson's Algorithm
 - Let f(e) = 0 for each edge e
 - pi = use DFS to find an augmenting path
	 - an edge is traversed provided the residual capacity of that path is greater than 0
 - While there is an augmenting path pi
	 - Compute the residual capacity of path pi
	 - Augment the flow along the edges of pi by the computed residual capacity
 - The worst case of Ford-Fulkerson is `O(|f*| (n+m) )`

## Maximum Bipartite Matching
 - Determine the maximum number of edges that can be paired in a bipartite graph
	 - A bipartite graph is a graph where all edges connect vertices from disjoint sets U and V, such that there are no odd length cycles.
 - Transform the problem into a Maximum flow problem by creating a source and sink connected to all nodes in U and V respectively. Also turn edge from U to V into a directed edge.
 - Solve the problem using the Ford Fulkerson Algorithm, the maximum flow is equal to the maximum number of pairings M

# Geometric and String algorithms
**Jarvis March**
 - Uses a gift wrapping approach
 - finding the convex hull of n points
```
// Find the bottommost point
i = bottom_point; // takes n time as you just iterate through each point
do{
	for each point p_j not i
		compute angle from p_i to p_j
		find point p_k with the min angle from p_i
	output(p_k, i); // p_k to i is a line in convex hull 
}while(i != bottom_point)

// OPT 2
// Find the bottom most point
i = bottom_point; // takes n time as you just iterate through each point
do{
	p_k = // start with a random point p_k
	p_j = // start with a random point p_j

	// p_j is if there are only two remaining points
	while p_j is not null:
		if p_j is to the right of p_k
			// p_j is a better p_k candidate
			rule_out(p_k); // remove p_k from current pool so its not considered
			p_k = p_j;
		else p_j is to the left of p_k
			rule_out(p_j); // remove p_j from current pool so its not considered
		
		p_j = // find another random point p_j, returns NULL if there are no remaining points

	output(p_i, p_k); // p_k to p_i is a line in the convex hull
}while(i != bottom_point)
```
 - The algorithm begins with a search for the lowest point and repeatedly selects the next extreme
	 - Running time `O(nh)` where n is the number of nodes and h is the number of edges of the convex hull
		 - It's output sensitive as the running depends on the output size.

## String searching
 - pattern - a string of m characters to search for
 - text - a string of n characters to search in for
 - String searching problem - find a pattern P in text T
	 - w is a prefix of x, if x can be decomposed into wy for some y
	 - w is a suffix  of x, if x can be decomposed into yw for some y
 - Shifts
	 - P occurs with shift s in T if they match up
		 - P can occur in T with different shifts
		 - An occurrence can begin within another one (ie: the end of the pattern is the same as the beginning)
 - **Brute force string searching**
	 - align pattern with beginning of text
	 - moving from left to right, compare each character until all characters to be matched are found or a mismatch is detected
		 - if a mismatch is found, realign pattern to one position to the right
 - Space for time tradeoffs
	 - Two transform and conquer approaches that trade space-for-time algorithms
	 - prestructuring - preprocesses the input to make accessing its elements easier
		 - hashing and indexing schemes
		 - a representation change
	 - input enhancement - preprocesses the input to store some info to be used later in solving the problem
		 - does a pass of the data to find out some information about it
		 - counting sorts
		 - string searching algorithm
 
 **Horspool's algorithm**
 - preprocesses the pattern to generate a shift table
	 - Shift table - says how much to shift the pattern when a mismatch occurs
 - always makes a shift based on the text's character c aligned with the last character in the pattern
	 - the amount to shift is based on the shift table's entry for C
	 - the following formula is used to calculate the shift for every character `s(c)`
$$
s(c) =
\begin{cases}
m  & \text{if c is not within the first m-1 characters} \\
m - n & \text{where n is the position of the rightmost position of c}
\end{cases}
$$
 - Pseudocode for generating the shift table
```pseudocode
// Runs in O(m + |sigma|), |sigma| is the size of the alphabet
ShiftTable(pattern, alphabet)
	for each letter in alphabet
		s[alphabet] = pattern.length

	// the pattern uses base 0 indexing.
	for i <- 0 to pattern.length - 2 // don't include the last character
		s[pattern[i]] = m - 1 - i
		
	return s
```
 - Pseudocode for Horsepool's algorithm
```pseudocode
Horsepool(pattern[0..m-1], text,[0..n-1])
	s = ShiftTable(pattern, alphabet);
	i = m - 1; // the location ot the rightmost character of the pattern along the text

	// if i >= m that means the pattern is not within the text
	while i < m
		k = 0; // number of matched characters

		// scan the pattern against the string from right to left
		while k < m and text[i - k] == pattern[m - 1 - k]
			// matched a character, move k to the left
			k++;

		if k == m return i - m + 1; // found the pattern
		else i += s[T[i]]; // didn't find the pattern, shift
		
	return -1;
```
 - best case: `O(m+|sigma|) + O(n/m)`
	 - occurs when the pattern is moved m characters at a time on a string containing n chars
 - worst case: `O(m+|sigma|) + O(nm)`
	 - occurs when the pattern is moved 1 character at a time, and fails scanning at the left most character
	 - `BBBBBBCBB` with a pattern of `CBB`
		 - Shift table: `B=1, C=2`

# Backtracking + Branch and Bound
## Backtracking
 - Used by problems requiring a selection of sequence of elements from a set
 - Sequence must satisfy some constraint (**Brute force difficulty**)
 - Is used by problems where the number of sequences grows exponential to the size of the problem
 - The solution traverses the state space using a depth first search with pruning
	 - constructs solutions and evaluates partial solutions organizer into a state-space-tree
	 - Builds the state-space tree using DFS
		 - if a partial solution is viable, it continues building the solution
			 - If a solution is not viable / non promising, it prunes the subtree rooted at this node ad backtracks
		 - It outputs the solutions that have the desired property
 - Efficiency
	 - significantly better than an exhaustive search of the tree for an average problem
	 - Worst case - as bad as brute force of exhaustive search over the entire search space
```pseudocode
CheckAndExtend(X[1..i])
	if the input is the solution, return the input
	else for every next viable step, try and check if they are solutions
		X[i + 1] <- next step
		return CheckAndExtend(X[1..i+1])
```
**N queens problem**
 - Place N queens on the board so that no queens are in danger
 - Brute force / expensive way
	 - Generate a tree that builds all possible layout
	 - Backtracking prunes entire subtrees that cannot be a solution
		 - Once a node is generated, check if queens see each other, if they see each other, do not proceed further
		 - Backtrack up the tree to search for other possible solutions

**Hamiltonian Cycle**
 - Goes through all the nodes in a graph
 - Start at a node, expand unvisited nodes until you reach the starting node
 - When you hit a dead-end (from the current node, there are no other unvisited nodes), go back up the tree until you can visit an unvisited node from the current node

**Subset sum**
 - Given a set of integers S, find a subset with a given sum X
	 - Example: `S=[3, 5, 6, 7] and X=15`
 - Steps
	 - Start with the root node at 0
	 - Each row in the binary tree represents an element being added or not
		 - Assign an item to each level in the tree
		 - Going left means adding the item, going right is not adding the item
	 - Binary tree in array form `[0, 3, 0, 8, 3, 5, 0]`
	 - Root
		 - 3 - we took 3
			 - 8 - we took 5
			 - 3 - we didn't take 5
		 - 0 - we didn't take 3
			 - 5 - we took 5
			 - 0 - we didn't take 5
## Branch and Bound
 - Similar to backtracking in that a state space tree is used
 - Used for optimization problems
	 - feasible - solution satisfies problem constraint
	 - optimal - best feasible solution based on an objective function
 - Uses breadth-first search variation with pruning instead of depth-first search with backtracking
 - Computes a bound at each node of state-space-tree
	 - Best value of the objective function for the subtree rooted at the node ("it will never be better than this")
 - prunes nodes whose bounds are worse than the best solution seen so far
	 - Why would you expand a tree that will always lead to a worse value than the current best solution?
 - expands the node with the best bound
	 - uses a priority queue with a breadth first search
	 - **best-first branch-and-bound strategy.**
```pseudocode
BranchAndBound(){
	root = create root
	queue = new Queue();
	queue.enqueue(root);

	while(root.isEmpty() == false){
		node = queue.dequeue();
		
		determine the children of the node and compute their bounds
		if(node.isLeaf()) prune
		else if( the node's children are infeasible ) prune 
		else if( value of child node's bound is no better than the best ) prune
	
		else add the children of the node to the priority queue
	}
}
```
 - Efficiency of branch and bround
	 - Faster than backtracking as it prunes solutions no better than current solution
	 - Investigates most promising subtrees (greedy?)
	 - Worst case scenario - visits every node in the tree

**Assignment Problem**
 - There are n people who need to be assigned to execute n jobs, with 1 job per person
 - Find the assignment with the minimum total cost
	 - Select an element in each row so that all elements are in different columns
	 - Total the sum of the selected elements, the smallest is the solution
 - Lower bounds
	 - The lower bound of the node represents the cheapest possible sum if that tree is expanded, though the lower bound may not be the solution
	 - The lower bound is used to determine which solutions are expanded first with the use of a min priorityqueue
 - Improving lower bounds
	 - Lower bound = cost of assignment + sum of smallest elements in each of the unassigned rows and columns
 - Root
	 - the lower bound of the solution will NEVER be better than the min cost for each job
	 - From the root, see the lower bounds for adding each of the 4 items and add them to a priority queue
	 - Continually dequeue the cheapest from the priority queue until a solution is found

**TSP**
 - Given a weighted digraph, find the cheapest cycle possible across all nodes
 - Initial bound - sum of the minimum edge weight from each vertex
 - Improving the bound
	 - Cost of each node
		 - Cost of edges selected currently + Sum of minimum edge weights from vertices that don't have an outgoing edge selected.

**Knapsack**
 - Given n items with b benefits and w weights, find the most valuable set of items that fit into the knapsack
 - Solution
	 - Sort value to weight ratios in descending order
	 - Each row in the search-space tree represents an item being added or not into the set
		 - Left branch of a node includes ith item and right branch excludes it
		 - The upper bound of a node is the sum of the values of the current items + (remaining capacity * value to weight ratio of the next item)
			 - We take upper bound since we want to maximize the value of the items in the knapsack

# NP-Completeness Overview
**Optimization vs Decision Problems**
 - Optimization - find an optimal solution satisfying 0 or more constraints
 - Decision - Answerable by Yes or no
	 - is easier than optimization problems because an algorithm for an optimization problem can be used to solve the corresponding decision problem
		 - "Does a path exist from U to V" can be solved using an optimized path finding algorithm (Djikstra)
	 - If a decision problem is hard, then the optimization problem is also hard

 **Reduction**
 - A reduction from A to B shows that B is atleast as hard as A ( A<= B)
	 - The difficulty of B is equal or greater than A, proven if you can solve A with an algorithm that solves B
 - We can reduce squaring to multiplication, which shows that multiplication is atleast as hard as squaring
 - **Polynomial time reduction**
	 - a reduction that can be performed by some polynomial time algorithm
	 - Every instance a of A is transformed to an instance beta of B
		 - The answer for a is YES iff. the answer for beta is YES in B

**Complexity classes**
 - P - problems solved in polynomial time
	 - Tractable problems, (easily managed) problems
		 - Problems that are efficiently solvable (can be solved in polynomial time)
		 - solvable by a deterministic Turing machine in Polynomial time
	 - Prove that a problem belongs to P or does not belong to P
	 - **Problems in P**
		 - Shortest Path - solved by Djikstra, Bellman-Ford, Floyd-Warshall
			 - Total worst case is O(n^3)
		 - Graph Connectivity - solved by Tarjan's SCC?
			 - Worst case is O(V+E)?
		 - Minimum Spanning tree - solved by Kruskal's and Prim's algorithms
	 - **Problems NOT in P**
		 - Halting problem - is in NP-hard, see below
 - NP - problems verifiable but not solvable in polynomial time 
	 - Problems that are decidable in a finite number of operations
		 - Solvable by a Non-deterministic Turing machine in Polynomial time
		 - Guess a solution non-deterministically then verify if it is indeed a solution in P time.
		 - Creates a tree of solutions since it's non-deterministic
			 - Each path to a leaf is a verification of a certificate
			 - NTM time is height of the comp tree, the max steps over all certificates
			 - A solution in a DTM is a path to a leaf in an NTM, thus P is a subset of NP
	 - Every problem P is in NP since if you can solve them in polynomial time, you can verify them in polynomial time (Decision is easier than optimization)
	 - There are some NP problems not solvable in polynomial time but are verifiable in polynomial time
		 - Ex: Finding two prime factors of a big number is hard, but you can verify the solution easily
	 - **Examples**
		 - Hamiltonian Cycle / Travelling Salesperson / Satisfiability
		 - Clique
			 - Does a graph G(V,E) contain a strongly connected subgraph C with k nodes?
			 - Verify C is a subset of V of size k - are all nodes in C connected in G
			 - Check that this verification runs in polynomial time
	 - **Relative Hardness**
		 - Clique is as hard as satisfiability, `satisfiability <= clique`
		 - If Satisfiability is NP, then Clique is NP
		 - If Satisfiability is undecidable, then Clique is undecidable
		 - If Clique is P, then Satisfiability must be in P
 - NP-Hard
	 - Every NP problem is polynomially reducible to them
		 - They are at least as hard as the hardest problem in NP
		 - They may not even be decidable (disjoint from NP-complete)
	 - The halting problem (a decision problem) is NP-hard because it's a decision problem, but it's not in NP-complete or NP
		 - The halting problem is not decidable in a finite number of operations, (it goes for infinity), thus it's not in NP or NP-complete
 - NP-Complete
	 - Are in NP and are in NP-hard
	 - Travelling salesman problem and Subset sum problem
		 - is in NP-hard AND is verifiable in polynomial time, eg, visiting through the path and adding the contents of the subset
	 - It's important to find if a problem is NP-complete so we don't waste time trying to find a polynomial / efficient solution for that problem
		 - Instead we can focus on writing an approximation / special case algorithm or a systemic solution with greedy / DP / backtracking techniques
	 - **How to prove a problem is NPC**
		 - Prove A is in NP
		 - Reduce a known NP-hard problem H to A
			 - All NP problems reduce to H, H reduces to A, thus all NP problems reduce to A to show that A is NP-hard.

**P = NP or P is a proper subset of NP**
 - A solution can be used for verification
	 - Solving is at least as hard as (but can be more time consuming) verifying the soln.
 - If we can verify in polynomial time, can be solve in polynomial time?
	 - Is P = NP?
 - Are all NPC problems solvable in polynomial time?
	 - Finding a Polynomial time solution for atleast one NPC problem means that P=NP, and all NPC problems are solvable in polynomial time (due to relative hardness)
	 - As the number of NPC problems grows, and having no polynomial time solution for any of them continues, P!=NP looks likely
### Examples of Algorithms that are NPC

**Circuit-Satisfiability problem**
 - is there an assignment of truth values to the variable gates that causes the circuit to output true
 - BF solution:
	 - For each possible assignment of values, check until they generate a 1
	 - If the number of inputs is k, then there are a total of 2^k possible assignments
	 - BF runs in 2^k which is not polynomial
 - is proven to be NP-Compleete
	 - No polynomial time soln is found, and likely there is none
	 - **Cook's theorem**
		 - AKA Cook-Levin Theorem or Boolean-SAT
		 - C-SAT is NP-Complete
			 - Among the first problems to be proven to be NPC
				 - Established the very first NP-complete problem through which all other problems were proved to be NP-complete
			 - Every problem in NP reduces to C-SAT in polynomial time
		 - transitively reduced to other problems to show they are also NP-hard.
	 - can be verified in polynomial time (is NP)
		 - Given a certificate C for instance A
			 - This certificate is an assignment of boolean values to the variable gates of A
	 - Verify the problem is NP-Hard
		 - Encode the input a (the circuit) for an arbitrary problem X in NP
			 - Every input can be encoded in binary
			 - Graphs can be represented by an adjacency list or matrix
		 - Every NP problem X has a P-time verification algorithm

**Satisfiability**
 - Given a set of variables X, and a set of clauses where each clause is a disjunction of logical variables, is there a truth assignment the variables that satisfies all the clauses
 - **Special cases**
	 - Circuit-SAT: only has one clause (a circuit which can be encoded in a single clause)
	 - 3-SAT: SAT but each clause has at most 3 variables

**Graph NP-C problems**
 - **Hamiltonian Path** - Does there exist a Hamiltonian path in G?
	 - Visits each node exactly once
 - **HAM-Cycle** - Does there exist a Hamiltonian Cycle in G?
	 - Visits each node exactly once and returns to starting node
 - **Travelling Salesperson Problem**
	 - Is there a tour of n cities with the total distance travelled being at most K?
		 - Uses a weighted graph
	 - A certificate is a sequence of vertices
		 - Check whether each vertex of G appears once
		 - Sums up the weights and checks if it is at most K
	 - NP-hard
		 - Assume that HAM-CYCLE is NP-hard
		 - Reduction
			 - From an input for HAM-CYCLE graph G, construct in polynomial time a TSP instance G' that adds weight to the edges 
				 - Assign edge weight 1 if the edge exists in G
				 - Assign edge weight 2 if the edge doesn't exist
			 - Analysis
				 - If G has a ham cycle h, then h is a tour in the G' with at most |V|
				 - If G' has a tour h' of at most |V| then each edge in h' has a value of 1, meaning the edge belongs in E
				 - Check that the transformation can be done in polynomial time
 - **Independent set** - Is there an independent set of nodes C in a graph (V, E) such that no nodes in C are connected by edges in E?
 - **Clique** - Does there exist a clique of size K in a graph G?
 - **Vertex cover** - Does there exist a set of nodes C of at most size K such that for every edge between u and v, atleast one of u and v are in C.
	 - Can you reach all edges directly with a set of nodes C of at most size K?

**Other NP-Complete problems**
 - **Subset sum** - given a set of positive integers, is there a subset Q of the set such that the elements of Q add up to a value S
 - **Partition Problem**
	 - given a set of positive integers, can you create two disjoint subsets such that the sum of the elements of the two subsets are equal?
