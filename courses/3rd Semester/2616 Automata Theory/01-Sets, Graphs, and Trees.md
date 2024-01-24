# Set

An unordered collection of distinct ideas or objects. Sets may be specified by enumerating the elements inside a pair of curly braces.

```
A = {red, yellow, blue}
```

The set that contains no elements is called the empty set or null set.

An object x is an element of a set X if x is in set X.

The number of elements in a set is its size or cardinality. The notation |S| denotes the size of set S. A set S is finite if and only if a number can be associated with |S|. The set of real numbers is an infinity set.

A set X is a subset of set Y if and only if every element of X is in set Y. A proper subset requires that they have at least one differing element, aka they are not equal. Same rules apply for super sets.

The union of two sets X and Y is formed by combining the elements of X and Y and removing duplicates to maintain distinctness between the elements. The elements in the union are exactly those that come either from X and Y.

Union is commutative and associative. The intersection of two sets X and Y is formed by selecting all the elements in common between X and Y. The elements in the intersection are exactly those that come from both X and Y.

Two sets X and Y are disjoint if they have no element in common. The set difference is the set of all elements of X that are not in Y.

The collection of all possible elements is the universal set. When integers are discussed, the universal set is `{x | x is an integer}`. The complement of a set X is the set of all elements in U but not in X. 

The Cartesian product of two sets X and Y is denoted by X x Y. It is the set of ordered pairs whose first component is an element of X and whose second component is an element of Y.

The power set of a set X is the set of all its subsets. A partition of the set X is a collection of pairwise disjoint sets whose union is X. If we have a set of all integers, the partitions could be the set of all positive integers, the set of all negative integers and the set containing 0.

A set S is closed under an operation if the result of performing a function on the elements of S is always in S. If at least  one result is not in S, then S is not closed under the function.

# Graphs

A graph is a set of vertices or nodes V, and edges or arcs E. Each edge of E links a pair of vertices V. Graphs are usually drawn with circles representing vertices and line segments representing edges ending at circles. When the pairs of vertices joined are unordered, the graph is a directed graph. Edges of a directed graph are shown using arrowed line segments going from one vertex to another. If an edge connects vertices u and v, then u and v are adjacent. If an edge connects a vertex with itself, the edge is called a self-loop. Self loops are not allowed in an undirected graph.

The degree of a vertex in an undirected graph is the number of edges incident on it. The degree of an undirected graph is the maximum degree among its vertices. The in degree of a vertex in a directed graph is the number of edges going into the vertex. The out degree is the number of edges going out from the vertex.

A path of length n from vertex u to vertex w in graph G is a sequence of vertices such that each pair of consecutive vertices in the sequence is joined by an edge of G. A vertex w is reachable from vertex u if there is a path from u to w. A path is a cycle if u=w and its length is not 0. A path or cycle is simple if the edges in the path are distinct. The path of leng5th 0 is a sequence of just one vertex. Such a path is simple and every vertex is trivially reachable from itself.

An undirected graph is connec6ted if there is atleast one path between any pair of vertices. A directed graph is strongly connected if there is atleast one path from any vertex to any other vertex.

A subgraph H of a graph G is a subset of vertices and edges of G that forms a graph. Two graphs are isomorphic if there is a 1-1 mapping of their vertices and of their edges so that the adjacencies are preserved,

# Trees

A tree is an undirected graph that is connected and has no simple cycles. A tree is a connected acyclic graph. A tree is rooted if a particular node is distinguished as the root. In a rooted tree, there is a unique simple path from the root to each ode. The length of the path from the root to a node is the level or depth of the node.

The root's level is 0. The maximum level among all nodes is the height / depth of the tree. On each of these paths, nodes nearer the root are ancestors of nodes farther from the root. These consecutive nodes on these paths have a parent-child relationship. The ones nearer the root are the parent.

All nodes have a parent except the root. Nodes with children are internal nodes, those without children are called external nodes or leaves. A rooted tree is ordered if the children of each node is ordered first, second. A k-ary tree has at most k children per node. 

Going through all the vertices and edges of a graph or a tree is called a traversal. Algorithms like breadth-first search and depth-first search are used for traversals.

# Functions and relations

A relation R from set A to set B is a subset of A x B. It is a set of ordered pairs (a, b) which can be viewed as mappings from a to b. b is called an image of a, whereas A is called the pre-image of B. The notation aRb means that a,b is a part of the relation of R. A relation R on set A is called a relation from A to A.

The relation is reflexive if for each element in set A, it is related to itself.

The relation is symmetric if aRb implies bRa for a, b in A.

R is transitive if bRc whenever aRb and bRc.

R is an equivalence relation if R is reflexive, symmetric and transitive. An equivalence relation R on A partitions A into sets called equivalence classes. The elements in each equivalence class are precisely those that are reflexively, symmetrically, and transitively related to each other. Each equivalence class may be represented by a for any a in the class. The size of any equivalence class may be finite, or infinite.

The reflexive closure, symmetric closure and transitive closure of a relation are the minimal supersets of the relation such that it becomes reflexive, symmetric and transitive respectively. 

A function f from set A to set B is a relation that maps every element of set A to exactly one element of B. The expression f(a) = b states that a is mapped uniquely to b. A function is one-to-one if each image of f has a unique pre-image. AS function f is onto if every element of B is an image under f.

A set is countably infinite if there is a one-to-one function between the set onto the set of counting numbers. The set of integer multiples of 3 is countable infinite since its elements can be rearranged to be mapped to the set of counting numbers.