**Finite state machine** - a model of computation with theoretical and practical significance. they are used in neural networks, sequential logic diagrams, software engineering and for modelling many other processes.

# Deterministic Finite Automata

Composed of the FF
 - Q - a finite set of states
 - Sigma -  an alphabet that describes the operations that the automata can perform
 - fn - the transition function for each state and input symbol that determines the next state
 - q0  - the initial state
 - F - the set of accepting and final states

When a state is not accepting, it is in a rejecting state. The names assigned to states are arbitrary as long as they are distinct form each other. Naming states is important in order to refer to those states. Some or all state names may be omitted if there is no need to refer them individually.

A transition diagram is essentially a graph. The states are the nodes and the transitions are the edges. One state is designated as the start state. Some states are identified as accepting states. Edges are labeled by input symbols. Finally there must be **exactly one edge** from each state for each input symbol.

When there are few states and transitions, a diagram is often used to give a pictorial view of the DSA. But as the number of states and transitions increases, the diagram may become more difficult to draw or visualize. In this case, a properly labeled transition table is preferred instead of a diagram.

The rows are labeled by the states from Q, and the columns are labeled by the symbols from the alphabet. The arrows on state q0 identifies that it is the start state. The asterisks indicate that it is an accepting state.

The transition function may be extended to handle an input string instead of just a single symbol. Just apply the equal function on the leftmost symbol and to the next state recursively apply the function to the remainder of the string until no more symbols remain.

When input strings cause a DFA to end in one of the accepting states of the DFA, they are said to be in the language of the DFA. The language of a DFA is the set of all strings over sigma that from q0 is taken to an accepting state after consuming all the symbols in the string. If the DFA is named M, we refer to the language as L(M). 

When stating the language of a DFA, it must be exactly described. Every string in the language of the DFA must be included by the description, and strings not included in the language should be excluded by the description. When the language is small and finite, they can be enumerated, but for infinitely large languages, they might not suffice.

A dead-end state of a DFA is a state from which there is no path to any accepting state. When a DFA reaches a dead-end state, processing of the DFA dies. DFA diagrams do not need to show dead-end states and edges going into and out of them. Whenever edges are not shown in a DFA diagram, they are implied to lead into dead-end states which are not shown.

**Applications**
 - Compiler design. Tokens are defined by rules
	 - Hex numbers in the C language are written with prefix 0x or 0X followed by one or more hexadecimal digits. The DFA for C hexadecimal characters should end in an accepting state when and only when the sequence of characters complies with these rules.

# Non-deterministic finite automata

We can extend the definition of DFAs by allowing an single input character to lead into 2 differing states from the same state. By doing so, we can reduce the complexity of some DFAs. In NFAs, a string is accepted if a sequence of guesses ends in an accepting state. It just takes one good sequence of guesses to accept a string. 

NFA transition maps into a set of states which may contain 0, 1 , or more states. If this set is empty then the NFA is stuck. If it has more than one state, it behaves like an NFA and goes into that state. If it has more than one state, a choice or guess can be made to go to any one of those states.

The language of an NFA is the set of all strings for which there is at least one path in the NFA from the start and accepting state, as the symbols of each string are read from left to right. If the NFA is named N, we refer to the language of N as L(N).

NFAs are useful if we have to take historical context into account, as guesses can be made based on the historical context, not just the current input that is being processed.

# e-NFA

Transitions that go from one state to another without consuming any symbol are called e-transitions or e-moves. These transitions are not allowed in DFAs or NFAs according to their definitions. In those, a move can only be made by consuming the next input symbol and traversing an edge labeled y this symbol from the current state into the next state.

The language of an e-NFA is the set of all strings for which there is at least one path in the e-NFA from the start state to an accepting state, as the symbols of each string are read from left to right.

Whenever there is an e-transition, the e-NFA can sponty go from its source state to the next state.

# Equivalence Theorems

These new types of transitions facilitate the convenient modelling of some languages to create smaller or easier to understand automata. However these transitions do not allow the acceptance of languages that more restricted models cannot accept. These finite state machines have the same computing power in terms of what languages they can and cannot accept. The languages one model could accept, the other two could accept.  Two models are equivalent if the set of languages they can accept are equal.

**All NFAs have equivalent DFAs**

When an NFA is processing an input, the NFA could take multiple alternative path. For each prefix of an input, consider determining all the states the NFA could be in from among all alternative paths. We can use the subset construction method to determine the equivalent DFA

 - the states of M are subsets of the states of N where they share the same starting state
 - the accepting states of M are those subsets of Q that contain an accepting state of N
 - the transition function of M maps each subset of states paired with a symbol to the set containing those states where a state in the subset can go in N on the symbol.
	 - Each state of M remembers all the possible states that N could be in after a prefix of the input is processed. The DFA can be viewed as simulating all possible paths of the NFA at the same time as each symbol is read.