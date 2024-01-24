---
tags:
  - reviewer
course: CS2616 - Theory of Automata
period: Prelim
assessment: Prelim Exam
---

Theory of computation
 - fundamental mathematical properties of hardware / software and applications
 - Determine what can or cannot be computed, how quickly / memory and on what type of computational model
 - Areas
	 - Automata - Definitions and properties of mathematical models of computation
	 - Computability - Classification of problems by those that are solvable and those that are not solvable
	 - Complexity - Classification of problems as easy ones and hard ones

Automata theory - abstract computing devices and their capabilities
 - practice with formal definitions of computations

## Sets
 - an unordered collection of distinct objects
 - a set has the closure property under a particular operation if the result of the operation is always an element of the set

## Graphs
 - ordered pair comprising a set of V vertices and a collection of edges E
 - Edge - one of two basic units out of which graphs are constructed
	 - Each edge has two vertices which it is attached called endpoints
	 - Two vertices are adjacent if they are endpoints of the same edge
	 - Outgoing edges of V - directed edges where the vertex is the origin
	 - Incoming edges of V - directed edges where the vertex is the destination
	 - Degree = total number of edges incident to a vertex
 - Undirected graph - a graph where the edges have no orientation
	 - Maximum number of edges in an undirected graph with n vertices is `n * (n-1)/2`
	 - Simple graph - graph where multiple edges to the same vertex and loops are disallowed
 - Directed graph (digraph) - edges have orientations
	 - Edge (x, y) is different to (y, x)
	 - DAG - directed acyclic graph
		 - digraph that contains no cycles
 - Weighted graph - a value with every edge in the graph
	 - Unweighted graphs do not have any value associated with every edge. (all the edge weights are one)
	 - All graphs are assumed to be unweighted by default.
 - Complete graph - a graph where every two edges are adjacent, all edges that can exist are present
 - Connected graph - path between every pair of vertices / there are no unreachable vertices
	 - Strongly connected - every vertex of a digraph is reachable from each other.

**Path**
 - a sequence of alternating vertices and edges such that the edge connects each successive vortex
 - cycle - path that starts and ends at the same vertex
 - simple path - path with distinct vertices
 - Vertex w is reachable from u if there is a path from u to w

## Trees
 - connected graph with no cycles
 - DAG with cycles removed
 - Spanning tree - the subgraph of a graph that is a tree that includes the vertices of the graph
 - **Terms**
	 - Root - top node
	 - Child - node directly connected to another node, moving away from the root
	 - parent - converse notion of a child
	 - Siblings - node with the same parent
	 - Descendant - node reachable by repeated proceeding from parent to child
	 - Ancestor - node reachable by repeated proceeding from child to parent
	 - Leaf - a node with no children
	 - Internal node - A node with atleast one child
	 - Degree - Number of subtrees of a node
	 - Edge - Connection between one node to another
	 - Path - a sequence of nodes and edges connecting a node with a descendant
	 - Level / depth - number of nodes between the current vertex and to the root
	 - Height - The maximum level of the tree
	 - Forest - Set of disjoint trees
	 - Tree traversal - BFS and DFS
 - K-ary trees are trees whose internal nodes have at most K children

# Relations
 - Reflexive - for each element in a set A, a maps to itself
 - Symmetric -  for every pair (a, b), b maps to a
 - Transitive - for every two pairs (a, b) and (b, c), a maps to c
 - A relation is an equivalence relation if R is reflexive, symmetric and transitive
 - An equivalence relation R on A partitions A into sets called equivalence classes
 - Closures - minimal supersets of a relation such that it becomes reflexive / symmetric and transitive
	 - You add the relations that you need to satisfy the properties that you want
## Functions
 - an object that sets up an input output relationship
 - Relations but cannot be one to many
 - Domain - all possible inputs
 - Codomain - The set of all possible outputs
 - Range - the set that the domain maps to (it is different from codomain)
	 - Injective - one to one
	 - Surjective - ONTO - the codomain is equal to the range
	 - If a function is both one to one and onto, it is bijective
 - Countably finite - if there is a one to one function between the set of numbers and onto the set of counting numbers
	 - {3, 6, 9, 12, ...} is countably finite because it can be mapped to {1, 2, 3, 4...} by dividing each element into 3 

# Alphabets
 - Alphabets - A finite non empty set of symbols, denoted by Sigma
 - String - a string is a sequence of symbols of finite length, represented by w
	 - Cardinality - Length of a string `|w|`
	 - A string is called a substring of another string y if u can be found in the middle of y
		 - A string is a substring of itself
	 - A string can also be the prefix / suffix of another string
	 - An empty string is signified using epsilon
	 - String reversal - sequence of a symbols of w but in reverse order
	 - Concatenation - linking two strings in sequence
	 - n'th power - repeating w n times
 - Alphabetical ordering of an alphabet - ordering of its symbols
	 - Alphabetical ordering of strings - linear sequencing of all such strings
	 - Lexicographical ordering of strings - linear sequencing where shorter strings come first
## Languages
 - a language is a set of strings over an alphabet
 - can be listed or use set roster notation
 - Union / intersection / difference
 - Cartesian product
 - Concatenation
 - Kleene-star of an alphabet - the union of all powers of the alphabet
	 - Positive closure - Kleene-star without the empty string
 - Kleene-star of a Language - the union of all powers of L
	 - Positive closure - does not include epsilon 
	 - The compliment of a language L is the set difference between E* and L
 - Reversal of a language - set of all reversals of the strings in L
	 - `strings.map(str => str.reverse())`

# Finite automata
 - a model of computation with practical significance
 - known as finite state machines
 - one of the simplest models of computation
 - good for computers with an extremely limited amount of memory
 - basis for programs that perform spell checking / grammar checking / indexing
 - useful tools when we attempt to recognize patterns in data
 - **Examples**
	 - we use state diagrams to see what is the next action performed in reaction to an input

**Terms**
 - state diagram - can be used to represent finite automata
	 - can also be used by a state transition table
 - states - vertices
 - start state
	 - is pointed to by a special arrow from nowhere
 - accept state
	 - drawn with double circles
 - transition - a function that takes in the current state and the next symbol and outputs the next symbol
	 - are represented using directed edges labeled with the input that represents the transitions
 - accept or reject

A finite automaton is a 5-tuple where
 - Q is the a finite set of states
 - Sigma is a finite state called the alphabet
 - Delta - transition function that dictates the next state given the current state and the next input symbol
 - q0 - the state state
 - F - a subset of Q that is the accepting states

An input string is accepted by the finite state machine M if it starts at the start state and ends in an accepting state. The language recognized by the FSM, denoted by L(M), is the set of all strings that are accepted by M.

Trap / dead state - a state where there is no path to the accepting state
 - when the DFA reaches here, it dies
 - if a dead end state must exist, only 1 is needed
 - All dead-end states can be collapsed to one

## NFA
 - may have 0, 1, or more transitions on the same symbol as compared to a DFA which has exactly one
 - guesses may be required when selecting an edge to  follow
 - Same sequence of guesses may result in ending in an accepting state, a non accepting state or it may get stuck
	 - A string is accepted if a sequence of guesses ends in an accepting state
	 - It takes 1 good sequence of guesses to accept a string

The formal definition of an NFA is the same except for the transition function that maps to a set of states, containing 0 or more states, compared to a DFA whose transition function maps to exactly one state.

The language of an NFA is the set of all strings where there is atleast one path in the NFA from the start state to an accepting state

# e-NFA
 - can have transitions that go from one state to another without consuming any symbol
	 - transitions are called epsilon transitions
 - e-NFAs are obtained when NFAs are allowed to have eTransitions

The formal definition of an NFA is the same except for the transition function where epsilon is also a symbol. The language is the set of strings where there is 1 path from the start state to the accepting state

**e-closure** - the e closure of a state is the set of all states reachable from q only using e-transitions
- a state whose e-closure includes an accepting state behaves like an accepting state too

# Equivalence theorems
**Two language models are equivalent if the set of languages they accept are equal**
 - DFA is a subset of an NFA, which is a subset of an e-NFA
	 - DFAs allow exactly one transition, NFAs can have 0 - multiple, so DFAs are restricted NFAs
	 - NFAs are eNFAs without epsilon transitions
 - Every DFA is an NFA and every NFA is an eNFA (not the other way around)

## Subset construction
 - the states of DFA are subsets of the states of N of which {q0} is the start state of M
 - The accepting states of M are the subsets of Q that contain an accepting state in N
 - the transition function of M maps a subset of states (S1) and a symbol to the intersection of the set of states obtained per state in S1 when transitioned using N's transition function

## Subset construction with e elimination
 - the states of M are subsets of states Q of E
 - The start state of M is the e-closure of the start state of E
 - The accepting states of M are the subsets of Q that contain an accepting state of E
 - The transition function of M maps each subset of states paired with a symbol to a union of e-closures of states transitioned in E, from a state in the subset on the symbol.

Steps
 - find the e-closure of every state in the e-NFA
 - calculate e_closure(transition_function_e(every_state, every_character))
 - calculate the transition function of the DFA by intersecting the mappings of all elements in the current state

# Regular Expression
 - can be an elementary expression of the FF
	 - null set - empty language
	 - epsilon - a language containing the empty string
	 - a - a language denoting a set containing a
 - a composite regular expression - a combination of regular expressions
	 - (E1 + E2), the language L1 union with L2 - **union**
	 - (E1E2), the language is L1L2 - **concatenation**
	 - (E1)* , the language is L1* - kleene-star
 - A language is a regular language if a finite state machine can recognize it
	 - a language that requires memory is not a regular language
	 - such as a^n times b^n since the computer would need to remember how many a symbols were parsed
	 - A regular language can be parsed using a regular expression, and two regular expressions are equivalent if their languages are equal
		 - 01 - { 01 }
		 - 1 + e = { 1, e }
		 - (01)* = 01^n where n>= 0
		 - (0+1)* = Kleene-star of sigma
		 - 0(0 + 1)* + e = Every string that starts with 0 or epsilon
 - precedence
	 - parenthesis
	 - kleene star
	 - concatenation
	 - union
 - Examples - (a, b) is the alphabet
	 - All strings whose length is even `((a+b)(a+b))*`
	 - All strings with an odd number of a
		 - `a(aa)*`
	 - All strings that have two consecutive a's
		 - `(a+b)*aa(a+b)*`

## Converting between Regular Expressions and NFA

NFAs and regular expressions are equivalent, and have equivalent NFAs
Thompson's algorithm
 - recursively convert each part of a recursive definition into their corresponding NFAs
 - constructed NFA has one accepting state except for the empty set that has none
 - every constructed NFA has no transition back into the start state and has no transition out of the accepting state
 - Union between two regular expressions
	 - Split and connect using E-transitions, forming a diamond
 - Concatenation
	 - Chain two elementary blocks together, with the end state of one combining with the start state of RE2
 - Kleene Star
	 - Loopback rainbow thing
	 - Loop from end of elementary block back to start of elementary block
	 - Loop from beginning to the end
	 - Elementary blocks are connected to new outer points using E transitions

# Pumping Lemma
 - Every regular language can have a pumping length
 - Each such string in a regular language contains a section that can be repeated any number of times with the resulting string remaining in the language
 - To prove that a language is irregular, use proof by contradiction
	 - Say that the language is regular and that it has a pumping length p
	 - Find a string z that has a length >=p with portions u, v, and w
		 - u concat v must have a length of <= p 
		 - u and w can be epsilon but v cannot be
	 - When v is repeated, the resulting string must also be in the language for the language to be regular
 - Try to prove that the ff languages are not regular:
	 - `0^n1^n | n>=0`
	 - `w | w has an equal number of 0s and 1s`
	 - `ww|w where w is (0+1)*`
	 - `1^(n^2) | n >= 0`
	 - `0^i1^j | i > j`
		 - Assume that the language is regular and it has a pumping length p
		 - Let i = p-10 and j=p-20 such that i > j
		 - Let z = `0^(p-10)1^(p-20)` and `|z| = p-10+p-20 = 2p-30>=p`
		 - Let u = `0^(p-10)` and `v=1^10` so that `|uv| == p <= p`
		 - If we pump v with i = 2, the resulting string is `0^(p-10) * 1^20 * 1^(p-30)`
			 - is equal to `0^(p-10)1^(p-10)`, which is not in the language as i is not greater than j

# DFA Minimization
 - Equivalence Relation
	 - Two states are in the same equivalence class if for all input strings, they either both accept or both reject
 - Equivalence class - sets of states that are equivalent to each other based on the equivalent relation
 - Equivalence states
	 - States that for every string w, they have the same ending state
	 - Equivalent states are also called indistinguishable states
	 - States that are not equivalent are indistinguishable states
 - You start with two equivalence classes
	 - The class that contains accepting states
	 - The class for the rest that you break into separate subsets based on their transition function
		 - You group states whose next states match each other
			 - States that for input a and b all map into non accepting states etc.

# Properties of Regular languages
 - Regular languages are closed under union / concatenation and kleene-star
	 - Thompson's algorithm except concatenation does not merge state
	 - ![[Pasted image 20230927213928.png]]
 - Regular languages are closed under complementation
	 - Usually we can just reverse the roles of the accepting and non accepting states
 - Regular languages are closed under intersection
	 - When we intersect two languages together, the resulting language accepts strings that are accepted by both languages
	 - Proof
		 - Let K and L be regular
		 - K' and L' are also regular
		 - K' union L' is regular as per theorem 1
		 - (K' union L')' is regular
		 - Applying De Morgan's Law, K intersection L is also regular
	 - Product Construction Method
		 - The states of the intersection dfa M are ordered pairs of the states of DFAs A and B
		 - The alphabet is the intersection of the alphabets of A and B
		 - The transition function maps the elements of each ordered pair per input symbol in the alphabet. 
		 - The start state is the ordered pair of the starting state of A and B
		 - The set of accepting states contains ordered pairs, the cartesian product of the set of accepting states of A and B
 - Regular languages are closed under reversal
	 - The reverse of null is null
	 - The reverse of epsilon is epsilon
	 - The reverse of string a is string a
	 - The reverse of `E_1 + E_2` is `E_1^R + E_2^R`
	 - The reverse of `E_1 * E_2` is `E_2^R * E_1^R`
	 - The reverse of `E*` is `(E^R)*`
 - Regular languages are closed under regular language substitution
	 - We have a substitute function s that maps an input symbol into an associated language
	 - `s(abbc) = s(a)s(b)s(b)s(c)`, and s maps a, b, c into a language
	 - Example
		 - L1 = `((a+b)(a+b))*`
		 - L2 = S(a) = `a(a+b)*a`
		 - L3 = S(b) = `(a+b)*ab(a+b)*`
		 - Find `S(L1) = S(((a+b)(a+b))*)`
			 - `S(L1) = ((S(a) + S(b))(S(a) + S(b)))*`
			 - `((((a+b)*ab(a+b)*) + a(a+b)*a)(((a+b)*ab(a+b)*) + a(a+b)*a))*`
		 - The resulting language is still a regular language given that L1 and the languages that symbols are mapped to are also regular

**Decision problems**
 - answerable by yes or no
 - procedures that can answer decision problems are called decision algorithms

**Membership**
 - Whether a string is a member of the language
 - For a regular language there is always a DFA, NFA and Regex whose language is L. These can be used to test an arbitrary string for membership in L
 - Given a string w and model M
	 - w belongs to the language represented using the model M if and only if M ends in an accepting state on input w

**Emptiness**
 - L(M) is empty if no accepting state is reachable from the start state
 - Whenever the regular expression phi is not a part of the E, L is not empty

## Finiteness
 - Does a regular language include a finite number of strings
 - Delete all states that are unreachable using a graph traversal algorithm
	 - Q' and F' are the states and accepting states without unreachable states
 - Eliminate states that cannot reach any accepting state
	 - For each remaining state q in Q', use a graph traversing algorithm to see if they reach any F'
		 - If not, eliminate q and any edges around it
 - Check if there are any cycles in the remaining DFA
	 - Use a graph traversal alg from the start state and track which nodes are visited

## Equivalence
 - Checking if two regular language models model the same language
 - Three ways:
	 - First way
		 - Convert them into DFAs
		 - Minimize each DFA
		 - Check if the minimized DFAs are isomorphic
	 - 2nd way
		 - Construct the DFA M for (L1 intersection L2') union (L1' intersection L2)
		 - Get the outer join of the two language representations
			 - If the outerjoin is null set then the two language representations are equivalent
		 - Check if the resulting DFA M is empty
	 - 3rd way
		 - Convert language descriptions into DFAs
		 - Let M be the DFA whose set of states is the union of states of M1 and M2, and edges is the union of the edges of M1 and M2. Two start states
		 - Run the min algorithm of M, L1 = L2 if the start states q01 and q02 are considered equivalent states