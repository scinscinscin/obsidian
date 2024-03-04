### Different Ways of thinking
 - **Thinking Humanly**
	 - recognizes the brain as an information processing machine
		 - requires scientific theories about how the brain works
	 - we need to understand how humans think
		 - we need to think about our own thoughts - introspection
		 - predict and test behavior of human subjects
		 - image the brain, examine neurological data
	 - cognitive science and neuroscience
 - **Acting humanly**
	 - Turing test - Interrogator asks questions, a computer and human give written answers
		 - The AI passes if interrogator cannot tell if responses are from computer or person at least 30% of the time
		 - allows physical objects to be passed into the computer
		 - Capabilities required: NLP, Reasoning, Computer Vision, Knowledge Representation, Machine Learning, Robotics
		 - Criticism - intelligent agents exists that do not imitate humans
			 - We should stop imitating the brain and focus instead on the output since computers work differently, Internally, ChatGPT thinks and acts somewhat different from humans
 - **Thinking rationally**
	 - Idealized way of thinking, using logic and arguments that yield correct conclusions when given correct premises
	 - describe the problem in formal notation then use deduction procedures to solve it
		 - aristotle, philosophers and mathematicians have attempted to formalize the rules of logical thought
		 - But there is a computational complexity of finding solutions
		 - It's hard to describe problems and knowledge in logical notation
		 - Some behavior are not controlled by facts
		 - Have difficulty with certain facts
 - **Acting rationally**
	 - Rational behaviour - do the right thing
		 - do what is expected to maximize goal achievement given the available information and resources
		 - see more below
	 - Knowledge is not just for showing that you have a lot of knowledge, but also for generating effective behaviour
	 - Actions don't involve thinking - blinking reflex and reactions to heat
	 - Rational agents - an entity that acts rationally
		 - Learn a function, given a history of percepts, determine the correct action
		 - Perfect rationality is not feasible in complex environment due to computational limitations, so design the best program for a given set of machine resources

### AI
 - Difference between AI and ML
	 - **Artificial Intelligence**
		 - developing models and algorithms for rational agents that map received percepts from the environment into actions
		 - maximize the attainment of given or hidden goals inspite of uncertainty
		 - Applications
			 - Game playing, machine learning, data mining, speech recognition, computer vision, web agents
			 - Medical diagnosis, fraud detection, genome analysis, object identification, space shuttle scheduling, information retrieval
	 - **Machine Learning**
		 - A popular branch of AI that through experience and analysis, figures out what it needs to do to perform well
		 - **AI is a superset of Machine Learning which is a superset of Deep Learning**
 - Connections of AI with other fields
	 - Philosophy - logic, methods of reasoning, mind vs matter, foundations of learning and knowledge
	 - Mathematics - logic, probability, optimization
	 - Economics - utility, decision theory
	 - Neuroscience - biological basis of intelligence
	 - Linguistics - grammar, language acquisition, knowledge representation
	 - Control theory - design systems that use a controller to achieve a near optimal behaviour
	 - Comp Eng - build fast computers to carry out intelligence
	 - Computer Science - computability, tractability
 - History of AI
	 - 1943 - McCulloch & Pitts - Boolean circuit model of a brain
	 - 1950 - Turing's "Computing machinery and intelligence"
		 - turing test, machine learning, genetic algorithm and reinforcement learning
	 - 1952 - 69 - Machines doing some things
		 - 1956 Dartmouth meeting - McCarthy called meeting, coined the term AI
		 - Invented LISP, time sharing, advice taker
		 - Newell & Simon's Logic theorist program
		 - Newell & Simon's General Problem Solver applied to puzzles
		 - Robinson's resolution method that is complete for logical reasoning
		 - Minsky's neural net, anti-logic
		 - Rosenblatt's perceptrons
		 - Samuel's checkers programs
	 - 1966 - 73 - AI's difficulties
		 - Computational complexity, resolution method, GA
		 - NLP translation issues
		 - Neural network research almost disappears, perceptron issue with XOR
	 - 1969-86 - Early knowledge-based expert systems
		 - AI becomes an industry - many commercial projects
		 - AI winter - many companies fail to deliver AI promises
	- 1986 - Neural networks begin to popularity
		- backpropogation algorithm is reinvented
			- originally invented in 1969 by Bryson and Ho
		- connectionist approach to AI vs symbolic and logicist approaches
		- probabilistic reasoning, HMMs and Bayesian networks
	- 2001 - Big data
		- internet and cloud computing gave to the rise of large data sets
		- bots in the internet, data mining
	- 2011 - Deep Learning
		- Computer Vision, NLP, and robotics
		- Software packages to easily construct and run large models
- State of the Art
	- 1991 - Gulf War: United states uses AI logistics planning and scheduling program that involved up to 50k vehicles, cargo, and people
	- 1996 - Proved a mathematical conjecture unsolved for decades
	- 1997 - Deep Blue beats Garry Kasparov
	- 2004 - Nasa's autonomous planning program controlled the scheduling of operations for a spacecraft
	- 2010 - Google - Toyota driving autonomously 98% of the time from Pittsburgh to San Diego
	- 2011 - IBM watson wins in Jeopardy over 2 human champions
	- 2016 - 17 - AlphaGo beats Lee Sidol and #1 Ke Jie in Go
	- 2018 - Cloud computing infrastructure more powerful and affordable to process vast and complex information
		- Information: Search engines, spam filtering, auto-help desks
		- NLP: Speech recognition and language translation
		- Vision: OCR, Face Detection, object detection
	- Automatic restaurants - Foodom Robotic Restaurant Tech
		- All food is made and delivered to customers' tables by an automated robotic system
	- 2020 - New Normal
		- Chatbots: LivePerson, Watson, Siri, ChatGPT
		- Education: Online Learning and MOOCs, ChatGPT
		- Art - DallE2
			- Generates images and videos given a description, like Photos or artistic
			- can vary, fill, extend objects, relates objects & actions
		- Lawyer and accounting assistants for research
	- OpenAI
		- Sam Altman - CEO, Elon Musk, Greg Brockman (President and Chairman), Ilya Suskever (Chief Scientist)
		- Investors: Microsoft, Matthew Brown Companies
		- AI Techniques: RL, NLP, Vision, Robotics
		- ChatGPT
			- Competes against Google Search and Bard
			- 1M users in the first 5 days
			- trained with data up to September 2021
			- When prompted properly
				- can converse, summarize, elaborate, outline, plan
				- write letters, resumes, have humor, translate, change tone
				- do math, code, create, and answer tests
	- Future
		- AI and ML research is growing exponentially
			- From internet age to knowledge age
			- AI is not perfect but improvements can be gained on specialized domains and hardware
		- Need to think about ethical concerns

# Intelligent Agents
 - **Agents** - perceives its environment through sensors and acts upon that environment through actuators
	 - Examples of agents
		 - Human agent
			 - Sensors - eyes, ears, nose, skin
			 - Actuator - hands, legs, mouth
		 - Robotic Agent
			 - Sensors - cameras, sonars, radars
			 - Actuators: grippers, manipulators, motors, etc.
		 - Software agent
			 - Sensors - keystrokes, file contents, network packets
			 - Actuators: screen display, writing files, send packets
			 - Not all software agents are mechanical
	 - Agent function -  maps from percept histories to actions
	 - Agent program - runs on an architecture with actuators and sensors to produce f
	 - Agent - the sum of the program and its underlying architecture
		 - Vacuum-cleaner
			 - Percepts: `[location {A, B}, contents {clean, dirty}]`
			 - Actions: Left, Right, Suck, NoOp
			 - A finite state machine can be used to determine the next action based on the current percept state
	 - **Rational agents**
		 - strives to do the right thing by selecting actions that maximize its performance measure
			 - Performance measure - an evaluation of any sequence of environment states based on a criterion for success of an agent's behaviour
				 - Ex: number of dirt cleaned, board position, amount of noise generated
		 - based on what it can perceive, built in knowledge, and the actions that it can perform
			 - rationality != omniscience, since they can only act on information that they know presently, aspire for expected instead of actual perfection
			 - gather information to improve action choices (exploration)
		 - the solution to given Task Environments
	 -  An agent is autonomous if its behaviour is determined by its own experience, it can adapt and improve from its previous plan

### Defining task environments
 - **Problem specification (PEAS)** - Performance Measure, Environment, Actuators, Sensors
	 - must be designed before designing rational agents
	 - Agent: automated taxi driver
		 - Performance measure - Safe / fast / legal / comfortable trip while maximizing profits
		 - Environment - roads, other traffic, pedestrians, customers, weather
		 - Actuators - steering wheel, accelerator, brake, signal horn
		 - Sensors - Sonar, speedometer, GPS, odometer, engine, sensors, keyboard
	 - the sensors gather input, while actuators enacts the decided output, and the performance measure is the goal of the process as the agent interacts with its environment
	
 - **Environment types**
	 - Fully observable - an agent's sensors give it access to the complete state of the environment at each point in time
		 - partially observable - not all of the state can be seen by the sensors
	 - Deterministic - the next state of the environment is completely determined by its current state and action executed by the agent
		 - Strategic - deterministic except for the actions of other agents
			- before you do your next action, things can change because of other agents
		 - Non deterministic - uncertainty, no probabilities, performance requires success in all possible outcomes
			 - two or more, at least once
		 - Stochastic - with uncertainty, like non-deterministic, but assigns possibilities to futures that might happen
	 - Episodic vs sequential - the agents experience is divided into episodes
		 - each episode consists of the agent perceiving and then performing a single action, turn based
		 - Sequential - the next episode is independent of actions on previous episodes
	 - Static vs dynamic - the environment is unchanged while an agent is deliberating
		 - Semidynamic - the environment does not change with time but the performance score of the agent does
	 - Discrete vs continuous - a finitely countable number of possible percepts and actions
	 - Single agent vs multiagent- an agent operating by itself in an environment
	 - Known vs unknown - if the rules of the environment, percepts and actions are known
	
 - Environment representation
	 - expressive power
		 - atomic - blackbox, states are indivisible with no internal structure
			 - they have one feature used as a key
		 - factored - each state is a set of attribute-value pairs
			 - two different factored states can share some attributes; making it easier to figure out how to turn one state into another
		 - structured - the states show relationship among its attributes
			 - More expressive representations are more concise / more powerful, they show a more complex reasoning and learning needed
	 - mapping locations between concepts and memory location
		 - localist representation - one to one mapping between concepts and memory
		 - distributed representation - a representation of a concept is spread over many memory locations
			 - more robust against noise and information loss
	
### Agent types
 - **Table Lookup Agents**
	 - maintains an array of previous perceptions, initialized to empty array by default
	 - has a huge table of rules deciding the action to perform based on the current state AND previous states
		 - takes a long time to build even with learning because the past data is also taken into consideration
	 - has no autonomy since all actions are determined from the predetermined rules
 - **Simple Reflex Agents**
	 - is literally just a DFA
	 - looks at current percepts but ignores past percepts
		 - the output is derived solely from the current environment of the agent
		 - is simple but has a limited intelligence only
	 - does not work in partially observable environments since it doesn't have memory
 - **Model based reflex agents**
	 - Model - a representation of how things work and the effect of own actions
		 - State depends on the perception history
		 - transitional model - knowledge of how the world works
			 - turning the steering wheel turns the car
			 - the camera is wet when it is raining
		 - sensor model - how the state of the world is reflected on the percepts
			 - droplets appear in the camera when it is wet
	 - Model based agent - uses a model, previous state, last action and current percept to estimate new current state and make a best guess for its next action using some rules
 - **Goal based reflex agents**
	 - considers the goal in deciding what to do next
		 - goals are solely binary representations between happy and unhappy states
	 - can combine knowledge about the goal with the model in considering what action to do next
	 - involves consideration in the future - what will happen if i do this action, and will it make me happy.
	 - the knowledge that supports its decisions is represented explicitly and can be redefined
 - **Utility based learning agents**
	 - considers satisfaction in different states via a utility function to reach possibly conflicting goals
		 - since goals are a binary state, a more general measure should allow for a comparison of different world states acdg. to its utility to the agent
	 - utility function - internalization of the performance measure
	 - not all utility based agents are model-based, a model-free agent can learn what action is best in a situation without ever learning exactly how that action changes the environment
 - **Learning agents**
	 - learning allows the agent to operate in initially unknown environments and to become more competent than its initial knowledge might allow
	 - Critic - gives feedback values on the percepts, based on a standard
		 - tells learning element how well the agent is doing with respect to a fixed standard
		 - conceptually outside the agent
	 - Problem generator - suggests things to try out, tells the agent to try things it does not know about
	 - learning element - responsible for making improvements
		 - uses feedback from the critic on how the agent is doing and determines how the performance element should be modified
		 - can make changes to any knowledge components incorporated in the previous agents
			 - Example: Improving the model component of a model based agent so they conform better with reality
	 - performance element - responsible for selecting external actions
		 - takes in percepts and decides on actions

### Problem solving agents
 - goal formulation - goals organize behaviour by limiting the objectives and hence the actions to be considered
 - problem formulation - the agent devises a description of the states and actions necessary to reach the goal
	 - abstraction - the process of removing detail from a representation, a good problem formulation has the right level of abstraction
		 - abstraction is valid if we can elaborate any abstract solution into a solution n the more detailed world, and is useful if carrying out each of the actions in the solution is easier than the original problem
 - search - the agent simulates the sequences of actions in its model, searching until it finds one that reaches the goal - called the solution
	 - it might have to simulate multiple sequences, but it will eventually find a solution, or that a solution is not possible
	 - a search problem is composed of the following:
		 - state space - a set of possible states that the environment can be in
			 - can be represented by a graph in which vertices are states and the directed edges are actions
		 - initial state - the state that the agent starts in
		 - a set of one or more goal states
		 - list of actions available to the agent
		 - transition model - describes what each action does
			 - `Result(s, a)` returns the state that results from doing `a` in state `s`
		 - action cost function - gives the numeric cost of applying action a in state s to reach `Result(s, a)`.
			 - A problem solving agent should use a cost function that reflects its own performance measure. Example: a routing agent should use the length of the road as a cost function
		 - path - a sequence of actions
			 - action costs are additive, the total cost of a path is the sum of the individual action costs, an optimal solution has the lowest path among all solutions
		 - solution - a path from the initial state to a goal state
 - execution - the agent can now execute the actions in the solution
	 - in a deterministic environment - the solution to any problem is a fixed sequence of actions, and can be executed while ignoring its percepts
		 - referred to as an open loop system
	 - if the model is incorrect or the environment is non deterministic, the agent would be safer using a closed-loop approach
	 - in a partially observable environment, a solution would be a branching strategy that recommends different actions depending on what percepts arrives

### Search algorithms
 - take a search problem as input and returns a solution, or an indication of failure
 - each node in the search tree corresponds to a path in the state space and the edges in the tree correspond to actions
	 - Each node has the state, previous node, action taken from previous node, depth, and total path cost.
 - Difference between state-space graph and search tree
	 - Graph - possibly infinite set of states in the world, and the actions that allow transitions from one state to another
	 - search tree - describes paths between these states, reaching towards the goal
		 - the tree may have multiple paths to any given state, but each node in the tree has a unique path back to the root
		 - Each node in the search tree corresponds to a path from the root to a node in the state-space graph
 - We expand nodes by considering the available actions for that state, and using the result function to see where those actions lead
	 - We generate a new node for each of the resulting state
	 - The essence of search is figuring out which child node to expand next
		 - the **frontier** is any node that has not been explored
 - **Best first search**
	 - A general approach where we choose a node with minimum value of some eval function.
	 - Each child node is only added to the frontier if it has not been reached before, or is re-added if it is now being reached with a path that has a lower path cost than any previous path
	 - Can be customized to different specific algorithms by changing the evaluation function of the alg
	 - graph search - if the search algorithm checks for redundant paths
		 - remembers all previously reached states by keeping track of them, allowing to detect redundant paths and keep only the best path to each state
		 - means that nodes previously explored are not re-added back into the frontier
	 - tree-like search - if it does not check the graph
 - **Characteristics of problem solving performance**
	 - completeness - is it guaranteed to find a solution when there is one and can correctly report failure when there is not?
		 - a search algorithm must be systematic in the way that it explores an infinite search space to make sure it can reach any state that is connected to the initial state
		 - in a search state with no solution, a sound algorithm needs to keep search forever
	 - cost optimality- does it find a solution with the lowest path cost of all solutions
	 - time complexity - how long it takes to find a solution
		 - can be measured in the number of states and actions considered
	 - space complexity - how much memory is needed to perform the search

### Search Strategies
 - is defined by picking the order of node expansion
 - Strategies are evaluated based on the following dimensions
	 - completeness - does it always find a solution if one exists
	 - time complexity - number of nodes generated
	 - space complexity - maximum number of nodes in memory
		 - time and space complexity are measured in terms of:
			 - b - maximum branching factor of the search tree
			 - d - depth of the least-cost solution
			 - m - maximum depth of the state space tree
	 - optimality - does it always find a least-cost solution
	 - use of knowledge - uninformed vs informed search
# Uninformed search
 - **Location of goal states are unknown, but it can test if it is at the goal**
	 - early goal test - test if the node is the goal as soon as it is generated
	 - late goal test - test if the node is the goal when it's visited
 - Only uses the information available in the problem description
 - **Search formulation**
```pseudocode
actionSequence = [];
state; // current world state
goal; // a goal that is initially null
problem; // a formulation of the problem

function SimpleProblemSolvingAgent(percept): action{
	// actionSequence is computed once if not present
	// then the head is popped everytime this function is called afterwards
	if(actionSequence is empty) then
		goal <- FormulateGoal(state);
		problem <- FormulateProblem(state, goal)
		seq <- Search(problem)

	// pop and return the top action
	action <- First(seq);
	seq <- Rest(seq);
	
	return action
}
```
 - **Environment assumptions**
	 - fully observable, discrete, deterministic, known, static, sequential, single agent
	 - Toy examples are usually well defined, not realistic and are useful for comparing algorithms, while real world example are complex, with usually no standard description
 - **Breadth first search** - expand the shallowest unexpanded node
	 - can be implemented using Best first search where the eval function is the depth of the node, the number of actions it takes to reach the node, or also by using a first in first out queue
	 - Is a general version of Uniform Cost search where all the steps equal to 1
	 - Properties
		 - Is complete - will always find a solution if it exists
		 - Time and Space - $O(b^{d+1})$ - since BFS keeps every node in memory
		 - Optimal - is optimal if the cost per step is 1 (see Uniform Cost Search)
			 - It will find the solution that is closest to the root
 - **Depth first search** - Expand deepest unexpanded node
	 - Can be implemented as a call to Best First Search where the eval function is the negative of the depth but is usually implemented using a stack
	 - Properties
		 - Not complete - fails in infinite depth-spaces and spaces with loops
			 - Can be modified to avoid repeated states along path, complete in finite spaces
		 - Time - $O(b^m)$ - only terrible if the maximum depth of the tree is worse than the depth of the least-cost solution
			 - if solutions are dense, may be much faster than breadth-first search
		 - Space - $O(bm)$ - uses linear space since it only has to keep track of the path of the current node it is on
		 - NOT Optimal
			 - it will return the first solution that it sees, which might be deeper than the most optimal solution
	 - For problems where tree search is feasible, depth first search has smaller needs for memory since a reached table isn't needed and the frontier is very small
	 - Has an even more optimized variant called backtracking search for limited environments
		 - only one successor is generated at a time rather than all successors, and it is generated by modifying the current state rather than allocating memory to a brand new state
 - **Depth limited search**
	 - depth first search with depth limit of l, nodes at depth l have no successors
	 - keeps DFS from wandering down an infinite path
 ```pseudocode
	 function DepthLimitedSearch(problem, limit){
		 return RecursiveDLS(<initial state of problem>, problem, limit)
	 }

	function RecursiveDLS(node, problem, limit){
		boolean cutoffReached = false;
		if node is the solution then return node as solution
		else if node is at the limit then return cutoff
		else for each successor of the node do{
			result = RecursiveDLS(successor, problem, limit)
			if(result = cutoff) then cutoffReached = true
			else result is not failure then return result
		}	

		if(cutoffReached == true) return cutoff;
		else return failure;
	}
```
 - **Iterative deepening search** - runs DLS with increasing depth limits
	 - Is complete
	 - Time - $O(b^d)$
	 - Space - $O(bd)$
	 - Is optimal if the step cost is 1, the first solution it finds is the closest to the starting state
	 - Number of nodes generated in a depth limited search to depth d with a branching factor of b can be computed by $N_{DLS} = b^0 + b^1 + b^2 + b^3 + \cdots + b^d$
	 - Number of nodes generated in an iterative deepening search to depth d with a branching factor b can be computed by $N_{IDS} = (d+1)b^0 + db^1 + (d-1)b^2 + (d-2)b^3 + \cdots + b^d$
 - **Uniform cost search** - like branch and bound algorithmic technique, but bounds are exact costs
	 - while breadth-first search spreads out in waves of uniform depth, uniform-cost spreads out in waves of uniform path cost
		 - the evaluation function is the cost of the path from the root to the current node - djikstra's algorithm
		 - Expand the unexpanded node that has the least total path cost - the cost from root to current node
		 - Fringe is a priority queue ordered by path cost
		 - First goal is least-cost solution
	 - Complete - if the step cost >= epsilon
		 - is not complete if the path cost becomes smaller and smaller - will continue to search deeper and deeper instead of searching paths with the soln
	 - Time - number of nodes with g <= cost of optimal solution
	 - Space - number of nodes with g <= cost of optimal solution
		 - Space and time can be exponential because large subtrees with inexpensive steps may be explored before useful paths with costly steps
		 - Djikstra's is a uniform cost search, but in Djikstra the minimum cost to all nodes are computed
	 - Optimal - yes - nodes are expanded in increasing order of total path cost
### Bidirectional Search
 - simultaneously searches forward from the initial state and backwards from the goal state, hoping that the two searches will meet since $b^{\frac{d}{2}} + b^{\frac{d}{2}} \leq b^{4}$
 - need to keep track of two frontiers and two tables of reached states, and be able to reason backwards (need to be able to go up a parent in the successor function)
# Informed search
 - In informed search, the location of goal states are known by using a heuristic function
	 - can find solutions more efficiently than an uninformed strategy using heuristics
	 - $h(n)$ - estimated cost of the cheapest path from the state at node n to a goal state
	 - Similar to uniform cost search, but UCS uses an exact function, instead of something that estimates desirability
	 - Implementation - order the nodes in fringe in decreasing order of desirability
 - **Greedy best first search** 
	 - a form of best-first search that expands first the node with the lowest h(n) value
	 - the desirability of the node is directly tied to how close it is from the goal (if it is near to the goal then it must be desirable)
	 - complete in finite state spaces, but not in infinite spaces
		 - can get stuck in loops or what seems close but is actually inaccurate due to heuristics
	 - time and space complexity is: $O(b^m)$ (as worst as depth first search) 
		 - can be reduced in certain problems to $O(bd)$ with a good heuristic function
 - **A* search**
	 - solves the problem with greedy search by avoiding expanding paths that are already expensive
	 - A combination of UCS and Greedy Best First Search
	 - Function: $f(n) = g(n) + h(n)$
		 - where g is the function for the path cost from the initial state to node n
		 - where h is the estimated cost of the shortest path from n to a goal state
		 - thus f is the estimated cost of the best path that continues from n to a goal
	 - is similar to branch and bound in that the true value cannot be better than the estimate
	 - Properties
		 - Is complete
		 - Optimal: depends on the type of search and heuristic function
			 - Tree search - if the heuristic function is admissible
			 - Graph search - if heuristic function is admissible and consistent
				 - if the heuristic function is inconsistent, a node in the state space tree may be rediscovered by multiple paths with lowering path costs, and be readded into the frontier
				 - consistent h(n) ensures that we discover optimal goals before suboptimal goals
		 - Time complexity
			 - Expands all nodes in increasing order until it reaches C*
### Heuristics 
 - creating heuristics is easier by simplifying the rules of the game (deriving from a relaxed version of the problem)
	 - For example: in 8 puzzle, instead of sliding the pieces, it could be the number of squares that are not in the proper location, or the Manhattan distance for each square
 - Dominance - if h1 and h2 are both admissible heuristics, and h2(n) >= h1(n), then h2 dominates h1
	 - a better heuristic is one that is closer to the actual value since then you would have to expand less nodes
 - Combining heuristics
	 - picking one from multiple heuristics
	 - h(n) = get the max across all heuristic functions (is costly if you have a lot of heuristics)
 - **Types of heuristics**
	 - Admissible Heuristics
		 - h(n) is admissible if for every node n, $h(n) \leq h^*(n)$ where $h^*(n)$ is the true cost to reach the goal state from n
		 - it never overestimates the cost to reach the goal, being optimistic
		 - if h(n) is admissible, then A* using TreeSearch is optimal since it will never overlook the cheapest most optimal solution.
	 - Consistent heuristics
		 - h(n) is consistent if for every node n, every successor n' of n generated by any action a, $h(n) \leq c(n, a, n') + h(n')$
			 - follows the triangle inequality, going directly from A to B is faster than A through C then B
		 - Every consistent heuristic is admissible but not vice versa
		 - the output of the heuristic is non decreasing along a path and is admissible
		 - if h(n) is admissible and consistent, then GraphSearch is optimal since the same nodes would never get added to the frontier, the direct route to the Goal node is always more optimal than the path with other nodes.

# Local search
 - For optimization, goal finding and constraint satisfaction problems
	 - has no prescribed start state, can start from anywhere
	 - path to optimal solution or goal is irrelevant, and it only cares about the final answer
		 - "in a set of complete configurations, find the MOST optimal"'
	 - an iterative improvement algorithm that finds better and better solutions incrementally, tracking a single state and trying to improv it
 - we want to maximize an objective function gives the quality of a possible solution
	 - known as the **performance measure**
	 - find the x and y that maximizes / minimizes the function of z
 - state space = a set of complete configurations
	 - complete - a set of complete configurations, basically a domain of solutions that are unoptimal
		 - 8 queens: the state space is all the boards with 8 queens placed (64C8)
		 - Travelling Salesman problem - all possible tours
	 - consistent - does not violate any constraints
 - **Hill climbing search**
	 - Also known as gradient ascent / descent
	 - can only see what's 1 action away - the local neighborhood
		 - once it reached a local maximum, it stops searching since there is no better neighbor to move to
			 - is not globally optimal, can get stuck in local optima, depending on the initial state 
				 - is not complete
	```pseudocode
	function HillClimbing(problem){
		// create the initial state of the problem
		current = Node(GenerateInitialState(problem))
		
		/**
			from the given state, other neighbors have values (h)
			8 queens: the h is the number of pairwise attacking queens if a 
				queen from the same column is moved to that location
			TSP: the h is the overall tour length if a pair of paths is switched,
				so A->C and B->D will switch to A->D and B->C
			HillClimbing picks the next state with the lowest or highest h value, 
				which is the "best" neighbor
		*/
		
		while(true){
			neighbors = current.generateNeighbors();
			maxNeighbor = max(neighbors);
			if(maxNeighbor.value > current.value) current = maxNeighbor;
		}
	}
	```
	 - has no memory of the past (except in some variants)
	 - Variants
		 - Choose first better successor (First choice hill climbing)
			 - select the first random neighbor with a better value, good for many neighbors
		 - Randomly choose among better successors (Stochastic hill climbing)
			 - Randomly select from uphill moves, possibly weighted by gradient
			 - For example, moving from a node with value 5 to 7, (7-5)/5 calculates the chance to go into that direction, the smaller the improvement, the less likely it will be chosen
		 - Random restart hill climbing
			 - when stuck, try from another random state
 - **Making HCS better**
	 - Sideways moves - Allows moves to neighbors that have the same value as the current node (sideways, not up or down)
		 - Is able to handle shoulders or plateaus so the AI can possibly find better solutions ahead
		 - **Tabu Search** - keep a small list of recently visited states, and forbid returning to those states
			 - Allows worsening moves if no better / equal solutions are found
		 - Is able to reduce the chance of 8 queens getting stuck from 86% to 6% of the time
			 - 3 to 4 steps to find solution or get stuck
			 - If 100 consecutive sideways movement is allowed, 8 queens only gets stuck 6% of the time, but much more steps are needed to find the solution
	 - Simulated Annealing
		 - Inspired by tempering of glass, at the beginning, the temperature rapidly decreases, but eventually it starts to level off at a certain temperature
		 - Escapes local maxima by allowing bad moves but gradually decrease their frequency
			 - Steeper downhill moves have less chance to be taken than less steep downhill moves
			 - Controlled by annealing schedule, dictates how much downhill moves are tolerated
				 - They are more tolerated at the beginning of the search than later
		 ```pseudocode
		 function SimulatedAnnealing(problem, schedule){
			 // schedule is a table that takes in the number of moves passed, and returns a probability of whether to accept bad moves or not, decreasing as the number of moves passed increases
			 
			 current = makeNode(initialState(problem));
			 currentTime = 0;
			 
			 while(true){
				 T = schedule[currentTime++];
				 if(T == 0) return current;
				 
				 next = random(current->generateSuccessor());
				 delta = next.value - current.value
				 if(delta > 0) current = next;
				 // we accept next as the curernt state even if it's worse based on a e^(delta/T) probability
				 else if(random(e^(delta / T))) current = next;
			 }
		 }
		```
		- Formula is given by $P=e^{\frac{\delta E}{T}}$ where T is the temperature and Delta E is the change in value from next.value to current.value
		- If the annealing is slow enough, then it will find a globally optimum state with probability approaching one, but is impractically long
			- The more downhill steps needed to escape a local optimum, the less likely to make all of them in a row
	- **Local Beam Search**
		- How it works
			- Start with K randomly generated states
				- K is known as the beam width
			- Iterate all of their successors
			- If one of the successors are a goal, then return it
			- Else pool all of their successors together and pick the k best ones.
			- repeat
		- It is not the same as running k greedy searches in parallel since in this, you are pooling the best, so some bad starting states could be completely dominated and removed by better starting states.
			- Open list only keeps the best K nodes
		- **Stochastic Beam Search**
			- Many times, all k states end up in the same local hill, this can be solved by choosing k successors randomly, but biased towards good ones.
			- Similar to natural selection
		- Properties
			- Is not complete - since it's by chance, it may not find a solution
			- Is not optimal - it may return a goal state, but it doesn't know if it's the most optimal
			- Heuristic - yes
			- Time - km
				- May search the entire state space tree
			- Space - kb 
				- Only stores the next 1st level of successors for K beams.
	- **Genetic Algorithms**
		- An adaption procedure based on the mechanics of natural genetics and natural selection
		- Optimization and Evolution
			- Optimization - survival of the fittest
				- Picking the best from the batch 
			- Evolution - Recombination
				- From the best, merging them together to hopefully make a better version
		- Representation
			- Gene - A single bit or subsequence in string that represents a single attribute
			- Chromosome - a string that represents each attempt state a GA makes towards a solution
				- a sequence of traits that can be interpreted as a possible solution
				- typically represented by a series of binary digits (genes)
			- A genetic algorithm maintains a collection or population of chromosomes, and each chromosome represents a different guess at the solution
		- GA procedure
			- Initialize a generation of random guesses
			- Evaluate each chromosome in the generation using a fitness function
			- Apply GA operation between the best of the current population to make the next generation
			- Finish when solution is reached or number of generations has reached an allowable maximum
		- Operations
			- Selection or reproduction
				- Select individuals x according to their fitness function f(x)
					- fitness function shouldn't just be a single trait, but a combination of many traits
				- Fittest individuals survive and possibly mate for next generation
				- We can run the children through a fitness function to determine its value, then the percentage that it gets chosen for the next generation is its value / the sum of the values of the children
					- Children can be chosen twice for the next generation
						- 1st child can be the parent with 2nd child and 3rd child
			- Crossover
				- Select two parents, and select a point in their chromosomes where they will swap
				- Cut and splice pieces of one parent to those of the other, creating a child where the left side of chromosomes is from A and right side of chromosomes is from B
			- Mutation
				- With small probability, randomly alter 1 bit
				- An insurance against lost bits
				- Pushes the GA out of local minima, since if all the children are similar almost nothing happens.
		- Similar to
			- Simulated Annealing
				- Diverse population at the beginning
				- large steps at the beginning when using crossover
				- Hopes to converge with small steps later to a solution
			- Stochastic Beam Search
				- Combines uphill tendency using many states
				- Randomly selects next generation of states
	- Non deterministic actions
		- The actions that you perform don't always do the same things, sometimes they do A, sometimes they do B
			- Requires percepts to narrow down states that agent could be in
		- Do not need a sequence of actions since next state is not guaranteed
			- We need a contingency plan on what to do based percepts and goal
				- so use decision trees instead of sequences
				- If this happens, this is what we do next, else this
		- AND-OR search trees
			- OR nodes - selection at discretion of agent
			- AND nodes- possible states based on percepts about environment
				- you have to analyze all nodes under an AND node
			- OR and AND nodes alternate in AND-OR trees
			- Solution - a subtree with a goal in each leaf, an action in each OR node, and every branch in AND nodes
			- When you perform an action from the current node, you can either go to an OR node or an AND node, an OR node directly goes to the next node, meaning there's no variability in the action, an AND node, it can either go to one node from a selection of multiple NODES

# Adversarial Search
**Games**
 - Games are a hallmark of intelligence and are easy to formalize
	 - They can be a good model of real world competitive activities
 - Types of game environments
	 - Deterministic vs Stochastic - does the game have a element of randomness to them
	 - Fully observable / partially observable - do you know all the information about the game
	 - PI and deterministic
		 - Chess / Checkers / Go / Tic Tac Toe / Tower of Hanoi
	 - II and deterministic
		 - Battleships
	 - PI and stochastic
		 - Backgammon / Monopoly
	 - II and stochastic
		 - Scrabble / Poker / Bridge
 - Two player zero sum games
	 - Player takes turns, and they have opposite goals (are adversarial)
		 - If one wins, the other loses
	 - Each game outcome or terminal state has a utility for each player
		 - A win is +1 point, a loss is a -1 point or 0
	 - The sum of both player's utilities is 0
		 - Sometimes the sum is a non-zero constant, if no points are lost on losing
 - Games vs Single agent search
	 - We don't know how the opponent will act
		 - The solution can't be determined from the start since the opponent may act in different ways, it's not a fixed sequence of actions but a policy that maps from state to best move in that state
	 - Efficiency is critical in playing well
		 - Time to make a move is limited, the branching factor, depth and number of configurations are huge so you need to terminate searching eventually
			 - In chess, branching factor is around 35 and depth is around 100, resulting in 10^154 nodes having to be searched
			 - This rules out searching until the very end of the game
 - Representation of a Game tree - 2player, deterministic
	 - You start with the root node (it's your turn)
		 - You make a move
		 - The children of the root node are the game states with all the possible moves that you could do
		 - For each of the children, their children are any of the moves your opponent could make from that game state
		 - It's similar to AND-OR trees where turns that are YOUR choice are OR nodes, and choices that your opponents make are AND choices.
	 - Nodes in the game tree are game states
	 - Edges are moves for each player
	 - Utility = favorability for max
	 - The search tree is very large for more complex games like chess
- Representation of general games
	- More than two players - the utilities have non zero sums
	- Utilities are now tuples
	- Each player maximizes their own utility at each node
	- Utilities get propagated from children to parents

### Minimax
 - perfect play for deterministic games
 - Maximizes your payoff when opponent minimizes your payoff
	 - "If my opponent is the best, what moves should I play such that I avoid reaching the states where I lose"
 - **The decision algorithm**
	 - MiniMax-Decision - returns the action of the children of the current state that has the utility of MAX-VALUE
	 - MAX-VALUE - from the current state, what's the max(MIN-VALUE) of the child states
		 - What's the best choice you can make knowing that your opponent is optimal, and will choose the move that MINIMIZES your chance to win
	 - MIN-VALUE - from the current state, what's the min(MAX-VALUE) of the child states
		 - this represents your opponent's choice since they want to minimize your utility, they select the minimum of the MAX-VALUE of child states, since you are MAX-VALUE
 - Properites
	 - Complete - yes
	 - Optimal
		 - It's optimal against an optimal opponent (Minimax is optimal to itself)
		 - If the opponent is non-optimal, it's possible to do better
		 - A different strategy might work better for a sub-optimal opponent, but that strategy will be worse against an optimal opponent
	 - Time complexity - $O(b^m)$
	 - Space complexity - $O(bm)$
		 - It uses depth-first search so it only needs to keep track of current state and its parent tree.
### Alpha beta pruning
 - Improving minimax by not having to expand all the nodes in the game tree
 - Similar to branch and bound, where you don't search nodes whose f(n) is already worse than the solution you currently have
 - Pruning - portions of the search tree are ignored
	 - doesn't affect action choice against minimax
	 - amount of pruning depends on move ordering
		 - should check with best moves so that more lower value branches can be pruned
		 - With perfect ordering, the time to find the best move is reduced from $O(b^m)$ to $O(b^{\frac{m}{2}})$
 - alpha - the value of the best choice for the MAX player found so far at any choice point above n
 - beta - value of the best choice for the MIN player found so far at any choice point above n
 - ![[Pasted image 20240207123953.png]]
	 - The 2nd layer takes the minimum value from all the children
	 - The 1st layer takes the max from all children
	 - The children of the middle tree is not expanded, because the min value of the left tree is 3
		 - There's no point in finding lower values for the middle tree because the player will already go down the left tree
		 - The middle tree can only get worse from 2, but the left is already fully expanded with the min value being 3

# Constraint Satisfaction Problems
 - has variables, domains, constraints
	 - variables - things to fill out
	 - domains - possible values for variables
	 - constraints - dictates what values variables can or cannot be
 - has a factored state (attribute value pairs) - defined by attribute variables X_i with values from Domain D_i
 - goal test is checking if each constraint specifying allowing combinations of values for subset values is satisfied
 - a solution is an assignment of values to attributes that satisfies all constraints
	 - consistent - an assignment does not violate any constraint
	 - complete - every variable is assigned a value
	 - designed solutions are complete and consistent assignments of variables
 - allows for general purpose algorithms with more power than standard search algorithms
 - Varieties of CSP variables
	 - Discrete variables
		 - finite domains
			 - has n variables with a domain size d, resulting in O(d^n) complete assignments
			 - Boolean CSPs, is NP complete
		 - infinite domains
			 - integers / strings
			 - needs a constraint language
	 - continous variables
		 - linear constraints solvable in polynomial time by linear programming
		 - solved in operations research
	 - constraints
		 - unary - involves a single variables
		 - binary - involves pairs of variables
			 - can be represented using a constraint graph
		 - higher order - involves 3 or more variables
			 - cryptoarithmetic column constraints

**Constraint graphs**
 - binary CSP - each constraint relates two variables
 - constraint graph - nodes are variables, arcs are constants
	 - a structured representation
	 - represents which variables are constrained against or to other variables

### CSP Naive Search
 - DFS
	 - one variable per node from bottom left
	 - uses a successor function - any coloring of next uncolored region
	 - only performs consistency checking with complete assignments, resulting in very slow search
 - Incremental search
	 - states - assignment made so far (usually incomplete)
	 - initial state - the empty assignment
	 - successor function: assign a value to an unassigned variable that does not conflict with current assignments, and backtrack if there are no legal assignments
	 - goal test
		 - check if the current assignment is complete
 - backtracking search
	 - problem is commutative if the order of applying a set of actions does not matter
	 - CSPs are commutative, the assignment is important but not the path to it
	 - basic uninformed incremental search algorithm for CSPs
		 - DFS with one variable per level and checks constraints as assignments are added
		 - checks consistency on each assignment of a value to a variable
		 - can be improved by general purpose methods
			 - Ordering
				 - which variable should be assigned next? (MRV and DH)
				 - in what order should its values be tried (LCV)
			 - inference
				 - can we detect inevitable failure early (FC, AC)
					 - forward checking
						 - when a variable is assigned a value, restrict the domains of the other unassigned variables because of this assignment and the constraints
						 - check unassigned neighbor and remove any variables that are now in conflict because of the current assignment 
						 - only propagates constraints on the neighbor, not detecting potential conflicts
						 - does not provide early checking for all conflicts
					 - arc consistency
						 - does constraint propagation by repeatedly enforcing constraints
						 - makes each arc consistent
							 - X->Y is consistent if and only if for every value x of X, there is a some allowed Y
							 - removes options that make it so the other node has no other possible values

**Improving CPSs**
 - minimum remaining values
	 - choose first the most constrained variable (fewest possible legal assignments)
		 - is based on the domain
	 - is a fail first heuristic - prunes the search tree and results in early failure detection
 - degree heuristic
	 - choose first the variable involved in most number of constraints with other unassigned values
		 - is based on the constraints
	 - used as a tie breaker for MRV
	 - reduces the branching factor of neighbors
 - least constrained value
	 - choose first the value that rules out the fewest values in the remaining variables
	 - performed once an unassigned variable has been selected for assignment
	 - Value selection is fail-last heuristic
	 - what value removes the least number of assignments for other variables
 - Choose a variable for assignment using MRV and DH as a tie breaker, then use LCV to choose a value to assign to the selected variable
	 - pick the unassigned variable that has the fewest possible legal assignments
		 - if tie, then pick the unassigned variable with the most number of constraints
	 - then use LCV to choose a value to assign to the selected variable
