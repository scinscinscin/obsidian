### Probability
 - how often something occurs, A probability provides a quantitative description of the chances or likelihoods associated with various outcomes
 - RelativeFrequency = F / n,
	 - F - how often something occurred
	 - n - the number of samples registered
 - Theoretical probability = Na / Ns = number of accepting states / number of elements in sample space
	 - Getting a head in 3 coin tosses
		 - Sample space = {HHH, HHT, HTH, HTT, THH, THT, TTH, TTT}
		 - States where you get a head = {HHH, HHT, HTH, HTT, THH, THT, TTH}
		 - Probability = 7/8
 - Experimental probability = frequency / n
	 - After flipping a coin 100 times, you get 57 heads and 43 tails, thus the chance of getting a head is 57%
 - Properties of probabilities
	 - P(A) must never be between 0-1
		 - If an event can never occur, P(A)=0
		 - if it always occurs, then P(A)=1
	 - The sum of all probabilities of all simple events in S = 1
 - It provides a bridge between descriptive and inferential statistics
	 - Probabilistic: Given that we know the proportion of people with Covid-19 in Manila, we can find the probability that the first patient tested is negative with the virus.
	 - Statistic: Given that we don't know the proportion of the patients, but would like to estimate it, observe a random number of patient's records per city in MM, and find the estimate proportion of the population with Covid-19
 - Applications
	 - modeling of text / web data
	 - speech recognition, robotics
	 - network traffic and system reliability modelling
		 - what is the expected lifetime of a computer composed from many components
		 - how is the computer's cache memory designed and managed to maximize the speed of the ram
		 - find the probability of the packet being received correctly when being transmitted over an unreliable link
	 - analysis of algorithms and graphs
	 - machine learning, data mining, cryptography
	 - image and signal processing
### Experiments
 - Experiment - the process by which an observation is obtained
 - Event - the outcome of an experiment, denoted by a capital letter
	 - a collection of one or more simple events
		 - simple event - if the event has only 1 possible outcome
 - Sample space - the set of all possible outcomes of an experiment
 - Examples of experiment / event / sample space
	 - Rolling a dice / getting a 5 / 1-6
	 - Coin toss / getting a head / {head and tails}
### Combinatorics
 - A field of mathematics concerned with problems of selection / arrangement and operation within a finite / discrete system
 - determine the number of possible configurations of a given type
 - **Fundamental counting principle**
	 - if an experiment is performed in two stages, with m ways to do the first stage, and n ways to accomplish the last stage, then there are mn ways to accomplish the experiment
 - **Permutation** - a permutation of a finite set A is a one to one mapping of A to itself
	 - Given that A is {a, b, c}, possible one to one mappings include {a, b, c}, {b, c, a}.
		 - {abc, acb, bac, bca, cab, cba}
	 - Rearrangements of a given set - the order matters
	 - The number of unique arrangements possible is $|A|!$
	 - Examples
		 - Arranging 4 people - 4! = 24
	 - **Circular permutation** - the total number of a permutations of a set A of n elements when these elements are in a circular manner is (n-1)!
	 - **Taking r things at a time**
		 - The number of ways you can arrange n distinct objects, taking them r at a time
		 - $nPr = \frac{n!}{(n-r)!}$
	 - **Permutation of N distinct objects**
		 - The total number of permutations of a set with non distinct items
			 - `N = n! / (n_1! * n_2!)` where n_1 and n_2 are the number of each item respectively
		 - A set of bulbs with 3 red bulbs, 2 blue bulbs and 4 green bulbs
			 - $\frac{9!}{3! * 2! * 4!}$
 - **Combination**
	 - the number of distinct combinations of n distinct objects that can be formed, taking them r at a time is $nCr = \frac{n!}{r!(n-r)!}$
	 - creating a 3 person committee from 5 people = 5C3
 - Set operations on Events
	 - Union: Let A and B be two events, then the union of A and B is the event defined by A u B
		 - The probability of A U B is P(A) + P(B) - P(A n B), which is just P(A) + P(B) if they are mutually exclusive events
	 - Intersection: the intersection of A and B is the event denoted by A n B, the event e belongs to both A and B
	 - Complement: the complement of A is A bar, where the event e does NOT belong to A
		 - The probability of A bar happening is 1 - P(A)
	 - Two events are mutually exclusive if the intersection of A and B is a nullset, A and B can never happen at the same time
 - Independent and dependent events
	 - Two events are independent if the occurrence of one of the events does not change the probability occurrence of the other event
		 - Doing one event doesn't change the sample space or outcome of the other event
 - Conditional probability
	 - The probability that A occurs given that event B has occurred is called the conditional probability of A given B and is defined as $P(A|B) = P(A n B) / P(B)$
	 - Need to figure out if A and B are independent events
		 - Flipping a coin and getting two heads - they are not dependent events
		 - Getting second candy from a bowl - they are dependent events since the probabilities change after the first event
	 - Two events are independent if and only if P(A|B) = P(A) or P(B|A) = P(B)
		 - the probability of P(A) occurring is not CHANGED due to P(B) occurring before it and vice versa
 - Multiplication rule
	 - For any two events, A and B, the probability that both A and B occur is $P(A n B) = P(A) * P(\text{B given that A occurred}) = P(A) * P(B | A)$
	 - If the events A and B are independent, then the probability that both A and B occur is $P(A n B) = P(A) \cdot P(B)$
 - Examples
	 - P(man alive) = 0.7, P(woman alive) = 0.9, thus the chance that neither will be alive in 5 months is (0.3 * 0.1) = 0.03 or 3%
	 - 10 percent of the people are high risk, with three people randomly selected, what is the chance that one of the tree are high risk
		 - 0.1 * 0.9 * 0.9 = 0.081 or 8.1%
	 - Suppose in the previous example, 49% of the population is female, and of those, 8% are high risk. When a single person is selected at random, what is the probability that it is a high risk female?
		 - 0.49 * 0.08 = 0.0392 or 3.92%
 - Total probability
	 - Let S_1, S_2, ..., S_k be mutually exclusive events, the probability of any event A is
		 - $P(A) = P(A n S_1) + P(A n S_2) + \dots +P(A n S_k)$
		 - The chance of A happening is the sum of the chances of A happening given that it happened along side S_1 + S_2 + S_k
 - Bayes Rule
	 - $$P(S_i | A) = \frac{P(S_i)P(A|S_i)}{\sum P(S_i)P(A | S_i)} \text{for all i}$$
	 - The chance of S_i happening if A happens is the (chance of A happening if S_i happened times S_i happening) over the (total chance of A happening if S_i happened times S_I happening)
	 - The numerator is just one addend of the denominator
 - Example:
	 - Example 1:
		 - 49% of the population is female, of those 8% are high risk
		 - 51% of the population is male, of those 12% are high risk. 
		 - A single person is selected at random and found to be high risk, find the probability that it is a male
		 - $$P(M | H) = \frac{P(M) * P (H | M)}{P(F) * P (H | F) + P(M) * P(H  |M)}$$
			 - The denominator represents the probability of picking a high risk patient using the principle of total probability
			 - The numerator represents the probability of picking a high risk male patient
			 - 0.6095
	 - Example 2
		 - P(Infected) = 0.001 > Given
		 - P(Positive test | infected person) = 0.99 > Given
		 - P(Negative test | infected person) = 0.01
		 - P(Positive | uninfected person) = 0.02
		 - P(Negative | uninfected person) = 0.98
		 - If someone tested positive, what's the chance they have the disease?
		 - P(Infected | Positive) 
			 - = (P(Infected) * P(Positive | Infected)) / ((P(Uninfected) * P(Positive | Uninfected)) + (P(Infected) * P(Positive | Infected)))
			 - (0.001 * 0.99) / (0.999 * 0.02) + (0.001 * 0.99) = 0.0472