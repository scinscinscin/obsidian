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
	
 - Agent types
	 - table lookup agents
		 - maintains an array of previous perceptions, initialized to empty array by default
		 - has a huge table of rules deciding the action to perform based on the current state AND previous states
			 - takes a long time to build even with learning because the past data is also taken into consideration
		 - has no autonomy since all actions are determined from the predetermined rules
	 - simple reflex agents
		 - looks at current percepts but ignores past percepts
			 - the output is derived solely from the current environment of the agent
			 - is simple but has a limited intelligence only
		 - does not work in partially observable environments since it doesn't have memory
	 - model based reflex agents
		 - Model - a representation of how things work and the effect of own actions
			 - State depends on the perception history
			 - transitional model - knowledge of how the world works
				 - turning the steering wheel turns the car
				 - the camera is wet when it is raining
			 - sensor model - how the state of the world is reflected on the percepts
				 - droplets appear in the camera when it is wet
		 - Model based agent - uses a model, previous state, last action and current percept to estimate new current state and make a best guess for its next action using some rules
	 - goal based reflex agents
		 - considers the goal in deciding what to do next
			 - goals are solely binary representations between happy and unhappy states
		 - can combine knowledge about the goal with the model in considering what action to do next
		 - involves consideration in the future - what will happen if i do this action, and will it make me happy.
		 - the knowledge that supports its decisions is represented explicitly and can be redefined
	 - utility based planning agents
		 - considers satisfaction in different states via a utility function to reach possibly conflicting goals
			 - since goals are a binary state, a more general measure should allow for a comparison of different world states acdg. to its utility to the agent
		 - utility function - internalization of the performance measure
		 - not all utility based agents are model-based, a model-free agent can learn what action is best in a situation without ever learning exactly how that action changes the environment
	 - learning agents
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

**Problem solving agents**
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

**Search algorithms**
 - take a search problem as input and returns a solution, or an indication of failure
 - each node in the search tree corresponds to a state in the state space and the edges in the tree correspond to actions
	 - the root of the tree is the initial state of the problem
 - Difference between state-space graph and search tree
	 - Graph - possibly infinite set of states in the world, and the actions that allow transitions from one state to another
	 - search tree - describes paths between these states, reaching towards the goal
		 - the tree may have multiple paths to any given state, but each node in the tree has a unique path path back to the root
 - We expand nodes by considering the available actions for that state, and using the result function to see where those actions lead
	 - We generate a new node for each of the resulting state
	 - The essence of search is figuring out which child node to expand next, the **frontier** is any node that has not been explored
 - **Best first search**
	 - A general approach where we choose a node with minimum value of some eval function.
	 - Each child node is only added to the frontier if it has not been reached before, or is re-added if it is now being reached with a path that has a lower path cost than any previous path
	 - Can be customized to different specific algorithms by changing the evaluation function of the alg
 - graph search - if the search algorithm checks for redundant paths
	 - remembers all previously reached states, allowing to detect redundant paths and keep only the best path to each state
 - tree-like search - if it does not check the graph
 - **Characteristics of problem solving performance**
	 - completeness - is it guaranteed to find a solution when there is one and ca correctly report failure when there is not?
		 - a search algorithm must be systematic in the way that it explores an infinite search space to make sure it can reach any state that is connected to the initial state
		 - in a search state with no solution, a sound algorithm needs to keep search forever
	 - cost optimality- does it find a solution with the lowest path cost of all solutions
	 - time complexity - how long it takes to find a solution
		 - can be measured in the number of states and actions considered
	 - space complexity - how much memory is needed to perform the search

# Uninformed search
 - Location of goal states are unknown, but it can test if it is at the goal
	 - early goal test - test if the node is the goal as soon as it is generated
	 - late goal test - test if the node is the goal when it's visited
 - Search formulation
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
 - Environment assumptions
	 - fully observable, discrete, deterministic, known, static, sequential, single agent
	 - Toy examples are usually well defined, not realistic and are useful for comparing algorithms, while real world example are complex, with usually no standard description
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
 - An uninformed search strategy uses only the information available in the problem definition
 - **Breadth first search** - expand the shallowest unexpanded node
	 - can be implemented using Best first search where the eval function is the depth of the node, the number of actions it takes to reach the node
		 - or also by using a first in first out queue
	 - Is complete - will always find a solution if it exists
	 - Time and Space - $O(b^{d+1})$
		 - it keeps every node in memory
	 - Optimal - is optimal if the cost per step is 1
 - **Depth-first search** - Expand deepest unexpanded node
	 - Can be implemented as a call to Best First Search where the eval function is the negative of the depth but is usually implemented as a tree like search that doesn't keep track of reached states
	 - Properties
		 - Not complete - fails in infinite depth-spaces and spaces with loops
			 - Can be modified to avoid repeated states along path, complete in finite spaces
		 - Time - $O(b^m)$ - only terrible if the maximum depth of the tree is worse than the depth of the least-cost solution
			 - if solutions are dense, may be much faster than breadth-first search
		 - Space - $O(bm)$ - uses linear space
		 - Is not optimal
	 - For problems where tree search is feasible, depth first search has smaller needs for memory since a reached table isn't needed and the frontier is very small
	 - Has an even more optimized variant called backtracking search
		 - only one successor is generated at a time rather than all successors, and it is generated by modifying the current state rather than allocating memory to a brand new state
 - **Depth limited search** - depth first search with depth limit of l, nodes at depth l have no successors
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
	 - Is optimal if the step cost is 1
	 - Number of nodes generated in a depth limited search to depth d with a branching factor of b can be computed by $N_{DLS} = b^0 + b^1 + b^2 + b^3 + \cdots + b^d$
	 - Number of nodes generated in an iterative deepening search to depth d with a branching factor b can be computed by $N_{IDS} = (d+1)b^0 + db^1 + (d-1)b^2 + (d-2)b^3 + \cdots + b^d$
 - **Uniform cost search** - like branch and bound algorithmic technique, but bounds are exact costs
	 - while breadth-first search spreads out in waves of uniform depth, uniform-cost spreads out in waves of uniform path cost
		 - the valuation function is the cost of the path from the root to the current node - djikstra's algorithm
		 - Expand the unexpanded node that has the least total path cost - the cost from root to current node
		 - Fringe is a priority queue ordered by path cost
		 - First goal is least-cost solution
	 - Complete - if the step cost >= epsilon
	 - Time - number of nodes with g <= cost of optimal solution
	 - Space - number of nodes with g <= cost of optimal solution
		 - Space and time can be exponential because large subtrees with inexpensive steps may be explored before useful paths with costly steps
		 - Equivalent to breadth-first if step costs all equal, otherwise, there is a complexity related to cost of optimal solution
		 - Djikstra's is a uniform cost search, but minimum cost to all nodes are computed
	 - Optimal - yes - nodes are expanded in increasing order of total path cost
### Bidirectional Search
 - simultaneously searches forward from the initial state and backwards from the goal state, hoping that the two searches will meet since $b^{\frac{d}{2}} + b^{\frac{d}{2}} \leq b^{4}$
 - need to keep track of two frontiers and two tables of reached states, and be able to reason backwards (need to be able to go up a parent in the successor function)
# Informed search
 - Location of goal states are known by using a heuristic function
	 - can find solutions more efficiently than an uninformed strategy
	 - h(n) - estimated cost of the cheapest path from the state at node n to a goal state
	 - Similar to uniform cost search, but UCS uses an exact function, instead of something that estimates desirability
	 - Implementation - order the nodes in fringe in decreasing order of desirability
 - Greedy best first search - a form of best - first search that expands first the node with the lowest h(n) value
	 - the desirability of the node is directly tied to how close it is from the goal (if it is near to the goal then it must be desirable)
	 - complete in finite state spaces, but not in infinite spaces
		 - can get stuck in loops or what seems close but is actually inaccurate due to heuristics
	 - worst case time and space complexity is: $O(|V|)$ but can be reduced in certain problems to $O(bm)$ with a good heuristic function
 - A* search
	 - solves the problem with greedy search by avoiding expanding paths that are already expensive
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
	 - Types of heuristics
		 - Admissible Heuristics
			 - h(n) is admissible if for every node n, $h(n) \leq h^*(n)$ where $h^*(n)$ is the true cost to reach the goal state from n
			 - it never overestimates the cost to reach the goal, being optimistic
			 - if h(n) is admissible, then A* using TreeSearch is optimal
		 - Consistent heuristics
			 - h(n) is consistent if for every node n, every successor n' of n generated by any action a, $h(n) \leq c(n, a, n') + h(n')$
				 - follows the triangle inequality, going directly from A to B is faster than A through C then B
			 - Every consistent heuristic is admissible but not vice versa
			 - the output of the heuristic is non decreasing along a path and is admissible
			 - if h(n) is admissible and consistent, then GraphSearch is optimal
 - 