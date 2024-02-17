![](https://www.youtube.com/watch?v=q6UbH7G2dec)
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
	 - P(A) must always be between 0-1
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
	 - if an experiment is performed in two stages, with m ways to do the first stage, and n ways to accomplish the last stage, then there are $mn$ ways to accomplish the experiment

 - **Permutation**
	 - a permutation of a finite set A is a one to one mapping of A to itself (the order matters)
		 - Given that A is ${a, b, c}$, possible one to one mappings include the ff.
			 - ${abc, acb, bac, bca, cab, cba}$
			 - The number of unique arrangements possible is $|A|!$
			 - Since abc is three elements, the number of unique arrangements is 3! = 6
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
	   
 - **Set operations on Events**
	 - Union: Let A and B be two events, then the union of A and B is the event defined by A u B
		 - The probability of $A \cup B$ is $P(A) + P(B) - P(A \cap B)$, which is just $P(A) + P(B)$ if they are mutually exclusive events (B and A can't happen at the same time)
	 - Intersection: the intersection of A and B is the event denoted by $A \cap B$, the event e belongs to both A and B
	 - Complement: the complement of A is A bar, where the event e does NOT belong to A
		 - The probability of A bar happening is 1 - P(A)
	 - Two events are mutually exclusive if the intersection of A and B is a $\phi$, A and B can never happen at the same time
	   
 - **Independent and dependent events**
	 - Two events are independent if the occurrence of one of the events does not change the probability occurrence of the other event
		 - Doing one event doesn't change the sample space or outcome of the other event
		   
 - Conditional probability
	 - The probability that A occurs given that event B has occurred is called the conditional probability of A given B and is defined as $P(A|B) = P(A \cap B) / P(B)$
		 - The chance of A happening if B is the chance of A and B happening over the chance of B happening
	 - Need to figure out if A and B are independent events
		 - Flipping a coin and getting two heads - they are not dependent events
		 - Getting second candy from a bowl - they are dependent events since the probabilities change after the first event
	 - Two events are independent if and only if P(A|B) = P(A) or P(B|A) = P(B)
		 - the probability of P(A) occurring is not CHANGED due to P(B) occurring before it and vice versa
		   
 - Multiplication rule
	 - For any two events, A and B, the probability that both A and B occur is $P(A \cap B) = P(A) * P(\text{B given that A occurred}) = P(A) * P(B | A)$
	 - If the events A and B are independent, then the probability that both A and B occur is $P(A \cap B) = P(A) \cdot P(B)$
 - Examples
	 - P(man alive) = 0.7, P(woman alive) = 0.9, thus the chance that neither will be alive in 5 months is (0.3 * 0.1) = 0.03 or 3%
	 - 10 percent of the people are high risk, with three people randomly selected, what is the chance that one of the tree are high risk
		 - 0.1 * 0.9 * 0.9 = 0.081 or 8.1%
	 - Suppose in the previous example, 49% of the population is female, and of those, 8% are high risk. When a single person is selected at random, what is the probability that it is a high risk female?
		 - 0.49 * 0.08 = 0.0392 or 3.92%
		   
 - Total probability
	 - Let $S_1, S_2, ..., S_k$ be mutually exclusive events, the probability of any event A is
		 - $P(A) = P(A \cap S_1) + P(A \cap S_2) + \dots +P(A \cap S_k)$
		 - The chance of A happening is the sum of the chances of A happening given that it happened along side $S_1 + S_2 + \dots + S_k$
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
### Random Variables
 - quantitative variable is random if the value that it assumes corresponds to the outcome of an experiment that is chance or random event

### Discrete Random Variables 
 - finite or countable number of possible values
 - The distribution of a discrete random variable is a list of all possible values of X together with the probability that X takes that value in one trial of the experiment
 - **Single variable**
	 - Each probability P(X) must be between 0 and 1, and the sum of all probabilities is equal to 1. P(x) is also called the probability mass function.
	 - **Cumulative probability distribution: F(x)**
		 - $F(x) = P(X \le x) = \sum f(t)$ for all values of t less than or equal to x
	 - **Mean** - $\mu = E(X) = \sum xP(x)$ 
		 - Also called expected value sometimes, the average of what appears when we do the experiment n times.
		 - "When we toss the coin 3 times, the expected value to appear is 1.5"
	 - **Variance** - $\sigma^2$ = $\sum (x-\mu)^2 p(x)$
		 - The spread of the values from the mean. The higher the variance, the higher the spread of the values, less consistent.
	 - **Standard Deviation** - $\sigma = \sqrt{\sigma^2}$
		 - Also a measure of variability
 - **Discrete Joint probability distribution**
	 - f(x, y) is a joint probability distribution or probability mass function of the discrete random variables X and Y if
		 - $f(x, y) \ge 0$ and $\sum_x \sum_y f(x,y) = 1$
		 - $P(X=x, Y=y) = f(x, y)$
	 - **Cumulative probability distribution**
		 - $P[(X, Y) \in A] = \sum\sum f(x, y)$
		 - represents the area in a 2d space where the dimensions are x and y, bounded to x and y
	 - **Marginal distribution** - Pegs one variable as a constant
		 - $g(x) = \sum_y f(x, y)$
			 - Shows the probability of getting each value of x, where y doesn't matter
			 - The chance of getting x is the sum of f(x, y) for all values of y
			 - Mean of x: $\mu_x = \sum x \cdot g(x)$
		 - $h(y) = \sum_x f(x, y)$
			 - Shows the probability of getting each value of y, where x doesn't matter
			 - Mean of y: $\mu_y = \sum y \cdot g(y)$
	 - Mean of random variable: g(X, Y)
		 - $E[XY] = \sum xy \cdot f(x, y)$
	 - **Covariance of X and Y**
		 - $\sigma_{XY} = E(XY) - \mu_x\mu_y$
		 - Expected value of XY - (Average of X * Average of Y)
	 - **Conditional distribution**
		 - $f(y|x) = \frac{f(x, y)}{g(x)}$ = Chance of (x,y) over the chance of that x appearing
		 - $f(x|y) = \frac{f(x, y)}{g(y)}$ = Chance of (x,y) over the chance of that y appearing

### Continuous random variables
 - any value in some interval or intervals of real numbers
 - The probability that it assumes any value is a specific value is zero due to the continuous limit theorem (having the same bounds of integration results in zero)
 - **Single variable**
	 - the **probability density function** of a continuous random variable is defined over the set of real numbers as such:
		 - $f(x) \ge 0$ for all values of x
		 - The area under f(x) from -inf to inf is = 1
		 - $P(a < X < b) = \int^{b}_{a} f(x)dx$
	 - **Cumulative distribution function**
		 - Since it's just an area under a curve, we can take evaluate the integral between x and the lower bound of the function
		 - $F(x) = P(X\le x) = \int^{x}_{-\infty} f(t)dt$
	 - **Mean / expected variable**
		 - $E(X) = \int x \cdot f(x)dx$
	 - **Variance**
		 - $Var(X) = \sigma^2 = \int x^2 f(x)dx  - \mu^2$
 - **Continuous Joint Probability distribution**
	 - f(x, y) is a joint probability distribution of X and Y if
		 - $f(x, y) \ge 0$ for all (x, y)
		 - the volume of the function from inf to positive inf is equal to 1
	 - Cumulative mass function
		 - Is the volume of f(x, y) up to (X, Y)
		 - $P[(X, Y) \in A] = \int \int f(x, y) dxdy$
	 - Marginal distribution
		 - g(x) is a function that returns the volume of a slice of x across all values of y
		 - $$g(x) = \int^{\infty}_{-\infty} f(x, y) dy$$
		 - $$h(y) = \int^{\infty}_{-\infty} f(x, y) dx$$
	 - Mean
		 - Expected value of XY
		 - $$E[XY] = \int^{\infty}_{-\infty}\int^{\infty}_{-\infty} xy \cdot f(x, y)dxdy$$
		 - Expected value for X 
		 - $$E[X] = \int^{\infty}_{-\infty} x \cdot g(x)dx$$
		 - Expected value for Y 
		 - $$E[Y] = \int^{\infty}_{-\infty} y \cdot h(y)dy$$
	 - Covariance
		 - $\sigma_{XY} = E[XY]-E[X]E[Y]$

---
### Examples for Discrete and Continuous

1. **A fair coin is tossed three times. Let X be the number of heads that are observed.**
	 - Construct probability distribution
	 - Find the probability that at least one head is observed
	 - Construct the cumulative distribution of x
	 - Find the mean and standard deviation
	 
| x | 0 | 1 | 2 | 3 |
| ---- | ---- | ---- | ---- | ---- |
| p(x) - Probability distribution | 1/8 | 3/8 | 3/8 | 1/8 |
| F(x) - Cumulative distribution | 1/8 | 4/8 | 7/8 | 8/8 |
| $x\cdot p(x)$ | 0 | 3/8 | 6/8 | 3/8 |
| $(x-\mu)^2 p(x)$ | 0.28125 | 0.09375 | 0.09375 | 0.28125 |
The chance that at least one head is observed: $P(X \ge 1) = 1 - \frac{1}{8} = \frac{7}{8}$
Mean: $\mu = 0 + 0.375 + 0.75 + 0.375 = 1.5$
Variance: $\sigma^2 = \sum (x-\mu)^2p(x) = 0.75$
Standard Deviation: $\sigma = \sqrt{0.75} = 0.8660$


2.  **A pair of fair dice is rolled. Let X denote the sum of the number of dots on the top faces**
	 - Construct the probability distribution of X
	 - Find P(X>=9)
	 - Find the probability that X takes an even value
	 - Construct the cumulative distribution of X

| x | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| p(x) | 1/36 | 2/36 | 3/36 | 4/36 | 5/36 | 6/36 | 5/36 | 4/36 | 3/36 | 2/36 | 1/36 |
| F(x) | 1/36 | 3/36 | 6/36 | 10/36 | 15/36 | 21/36 | 26/36 | 30/36 | 33/36 | 35/36 | 36/36 |
Find $P(X\ge9) = \frac{4+3+2+1}{36} = \frac{10}{36}$
Find the probability that X is even: $\frac{1+3+5+5+3+1}{36} = \frac{1}{2}$

3. **The random variable being studied is X, the number of stock that increase in value each day**
	 - Find P(X >= 3)

| x | 0 | 1 | 2 | 3 | 4 | 5 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| p(x) - Probability distribution | ? | 0.30 | 0.20 | 0.10 | 0.05 | 0.01 |
$P(0) = 1 - (0.30 + 0.20 + 0.10 + 0.05 + 0.01) = 0.34$
$P(X\ge3) = (0.10 + 0.05 + 0.01) = 0.16$

4. **A life insurance company sells 200,000USD to an individual in a particular risk group for a premium of 195USD. Find the expected value and variance to the company if a person has 99.97% chance of surviving one year.**

From the perspective of the company, they have a 99.97% chance of gaining 195USD, but a 0.03% chance of losing 199805USD

| x | 195 | -199805 |
| ---- | ---- | ---- |
| p(x) | 0.9997 | 0.0003 |
| $(x-\mu)^2p(x)$ | 3598.92 | 11992801.08 |
Mean: $\mu = (195 * 0.9997) + (-199805 * 0.0003) = 135$
Variance: $\sigma^2 = 11996400$

5. **Two pens are selected from a box that contains 3 Blue pens, 2 red pens, and 3 green pens. Let X be the number of blue pens selected and Y is the number of red pens.**
	- Find the joint probability function, which can be generated by Combination
	- P(X, Y) where x + y <= 1
		- $\frac{3 + 9 + 6}{28} = \frac{18}{28}$
	- Marginal distribution of X and Y
		- Mean of X: $\mu_x = \frac{15 + 6}{28} = 0.75$
		- Mean of Y: $\mu_y = \frac{12+ 2}{28} = 0.5$
	- Find the expected value E(XY)
		-  $E(XY) = 6/28$
	- Conditional distribution of X given Y = 1 and use it to determine P(X=0 | Y=1)
		$$
			\begin{align}
				P(X|Y=1) &= \frac{p(X, Y=1)}{h(1)} = \frac{P(X, Y=1)}{\frac{12}{28}} \\
				P(X=0, Y=1) &= \frac{P(0, 1)}{\frac{12}{28}} = \frac{6/28}{12/28} = \frac{1}{2}
			\end{align}
		$$
		
	 - Find the covariance of x and y
		$$Cov(XY) = E(XY) - \mu_x\mu_y = \frac{6}{28} - (0.75 * 0.25) = 0.0268$$

**Probability tables for XY, X, and Y**

| X (blue pen) | 0 | 1 | 0 | 1 | 2 | 0 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Y (red pen) | 0 | 0 | 1 | 1 | 0 | 2 |
| P(X, Y) | 3/28 | 9/28 | 6/28 | 6/28 | 3/28 | 1/28 |

| X | 0 | 1 | 2 |
| ---- | ---- | ---- | ---- |
| g(x) | 10/28 | 15/28 | 3/28 |

| Y | 0 | 1 | 2 |
| ---- | ---- | ---- | ---- |
| h(y) | 15/28 | 12/28 | 1/28 |

6. The error in the reaction temperature is a continuous random variable X having the PDF of $f(x) = \frac{x^2}{3}$ between $-1<x<2$
	 - Verify that f(x) is a density function
		 - We can integrate the function between the range where it is defined, and it must equal 1
			$$
			\int^2_{-1} \frac{x^2}{3} = \frac{x^3}{9} \Biggm\lvert^2_{-1} = \frac{8 + 1}{9} = 1
			$$
	 - Find P(0 < X <= 1)
		 - Integrate the function between the ranges of 0 and 1
			$$			
				\int^1_0 \frac{x^2}{3} = \frac{x^3}{9} \Biggm\lvert^1_0 = \frac{1}{9}
			$$
	 - Find the cumulative distribution function
		 - The function is defined between -1 and 2, thus the lower bound for integration is -1 while the upper bound is x, taken from F(x)
		$$
			F(x) = \int_{-1}^{x} \frac{t^2}{3} dt = \frac{t^3}{9} \Biggm\lvert^x_{-1} = \frac{x^3 +1}{9}
		$$
	- Find the mean and standard deviation of X
		$$
			\mu_x = \int^{2}_{-1} \frac{x^3}{3}dx = \frac{x^4}{12} \Biggm\lvert ^{2}_{-1} = \frac{16 - 1}{12} = \frac{5}{4}
		$$
		$$
			\begin{align}
				\sigma^{2} &= \int^{2}_{-1} \frac{x^4}{3} - \mu^2 = (\frac{x^5}{15} \Biggm\lvert^{2}_{-1}) - \frac{25}{16} = \frac{33}{15} - \frac{25}{16} = 0.6375 \\
				\sigma &= \sqrt{0.6375} = 0.7984
			\end{align}
		$$
---

# Types of Probability Distribution

### Discrete probability distributions

 - **Bernoulli Distribution**
	 - **Asks the probability of an experiment only happening 1 time in n trials**
	 - Is a special case of binomial distribution where the experiment is only performed one time
	 - Bernoulli variable - a random variable with two possible values
		 - Bernoulli distribution - the distribution of Bernoulli variable
		 - Bernoulli trial - any experiment with a binary outcome
	 - if p is the probability of success, then q = 1-p is the probability for failure
		 - it goes that P(x) is q for failure(x=0), and p for success(x=1)

---

 - **Binomial distribution**
	 - **Asks the probability of x happening in n trials**
	 - the experiment is performed a fixed number times, each repetition is called a trial
		 - trials are independent, the outcome of one trial will not affect the outcome of other trials
		 - each trial has two mutually exclusive outcomes, and the probability of success is fixed for each experiment
	 - the number of successes of independent Bernoulli trials
	 - $P(x) = nCr(n, x) \cdot (p)^x \cdot (1-p)^{n-x}$
		 - where x is the number of successes
		 - where n is the total number of trials
		 - where p is the chance for success
	 - Mean: $\mu = np$
	 - Standard deviation: $\sigma = \sqrt{npq}$
	 - Variance: $\sigma^2={npq}$

 In a random sample of 20 households, what is the probability that exactly 5 match, when the chance for a match is 18.3%
- $P(x) = nCr(20, x) \cdot (0.183)^x \cdot (0.817)^{20-x}$
- $P(5) = nCr(20, 5) \cdot (0.183)^5 \cdot (0.817)^{15} = 0.1535$
In a random sample of 20 households, what is the probability that less than 4 match?
- $P(0) + P(1) + P(2) + P(3) = 0.4885$
In a random sample of 20 households, what is the probability that atleast 4 match?
- $1-(P(0) + P(1) + P(2) + P(3)) = 1-0.4885 = 0.5115$

18.3% of households have 3 or more cars. In a random sample of 400 households, determine the mean and stan.dev. of households with 3 or more cars?
 - $\mu = 400 * 0.183 = 73.2$
 - $\sigma = \sqrt{400 * 0.183 * 0.817} = 7.7333$

 20% of subscribers receive a promotion. A group of 10 are selected for the service. What is the probability that atleast 4 of them get a promotion?
 - $P(x) = nCr(10, x) * 0.20^{x} * 0.80^{10-x}$
 - $P(x \ge 4) = 1-P(x \le 4) = 1-(P(0) + P(1) + P(2) + P(3)) = 0.1209$

An exciting computer game is released. Sixty percent of players complete all the levels. Thirty percent of them will then buy an advanced version of the game. Among 15 users, what is the expected number of people who will buy the advanced version? What is the probability that at least two people will buy it?
 - The probability of buying the advanced version is 0.60 * 0.30 = 0.18
 - $P(x) = 15Cx \cdot 0.18^x \cdot 0.82^{15-x}$

 - What is the probability that at least two people will buy it?
 - $P(x\ge 2) = 1-(P(0) + P(1)) = 0.7813$

 - What is the expected number of people who will buy the advanced version?
 - $\mu = 15 * 0.18 = 2.7$

---

 - **Multinomial distribution**
	 - there are more than 2 possible outcomes
		 - You are given the number of times each outcome occurs, and the chance that that outcome occurs
			 - the sum of the number of times each outcome occurs is equal to the number of experiments performed
			 - the sum of all the chances of each outcome occurring is equal to 1
		 $$
			 P(X) = \frac{n! \cdot p_1^{X_1} \cdot p_2^{X_2} \cdot p_3^{X_3} \dots  p_k^{X_k}}{X_1! \cdot X_2! \cdot X_3! \dots X_k!} \text{ where } X_1+X_2+ \cdots + X_k = n \text{ and } p_1 + p_2 + \cdots + p_k = 1 
		 $$
 
 A small airport coffee shop manager found that the probabilities a customer buys 0, 1, 2, or 3 cups of coffee are 0.3, 0.5, 0.15, and 0.05, respectively. If 8 customers enter the shop, find the probability that 2 will purchase something other than coffee, 4 will purchase 1 cup of coffee, 1 will purchase 2 cups, and 1 will purchase 3 cups.

$$
	P(x_1, x_2, x_3, x_4) = \frac{8!
		 \cdot 0.3^{x_1} \cdot 0.5^{x_2} \cdot 0.15^{x_3} \cdot 0.05^{x_4}
	}{x_1! x_2!x_3!x_4!}
$$
$$
P(x_1=2, x_2=4, x_3=1, x_4=1) = 0.0354
$$

In a large city, 50 % of the people choose a movie, 30 % choose dinner and a play, and 20 % choose shopping as a leisure activity. If a sample of 5 people is randomly selected, find the probability that 3
are planning to go to a movie, 1 to a play, and 1 to a shopping mall.

$$
	P(x_1, x_2, x_3)=\frac{5! * 0.5^{x_1} * 0.30^{x_2} * 0.20^{x_3}}{x_1!x_2!x_3!}
$$
$$
	P(3, 1, 1) = 0.15
$$

---
 - **Hypergeometric solution**
	 - Given a population with two types of objects, with $a$ objects of type A and $b$ objects of type B, P(X) is the probability of selecting X items of A and $n-X$ items of B without replacement
	 - 15 cats and 5 dogs are in a bag, what is probability of getting 3 cats and 2 dogs when selecting 5 items
	 - $$P(x) = \frac{_aC_x \cdot _bC_{n-x}}{_{a+b}C_n}$$
	 - Mean: $\mu = \frac{nk}{a+b}$
	 - Variance: $$\sigma^2 = \frac{N - n}{N - 1} \cdot n \cdot \frac{k}{n}\left(1-\frac{k}{N}\right)$$

Ten people apply for a job as assistant manager of a restaurant. Five have completed college and five have not. If the manager selects 3 applicants at random, find the probability that all 3 are college graduates.

$$
	P(x) = \frac{nCr(5, x)\cdot nCr(5, 3-x)}{nCr(10, 3)}
$$
$$
P(3) = 0.0833
$$

A recent study found that 2 out of every 10 houses in a neighborhood have no insurance. If 5 houses are selected from 10 houses, find the probability that exactly 1 will be uninsured.

$$
	P(x) = \frac{nCr(2, x)*nCr(8, 5-x)}{nCr(10, 5)}
$$
$$
P(1) = 0.5556
$$
---
 - **Geometric Distribution**
	 - Describes the number of Bernoulli Trials needed to be formed in order to get the first success
		 - A special case of the negative binomial distribution where k = 1
	 - P(x) is the chance that the 1st success occurs on the $x^{th}$ trial
		 - $P(x) = (1-p)^{x-1}p$
			 - p is the probability of success
		 - The chance that success occurs in the first try is p
		 - The chance that success occurs on the 2nd try is $(1-p) * p$
		 - It keeps multiplying the success of failure per try that is supposed to be a failure
	 - Mean: $E(x) = \frac{1}{p}$
	 - Variance: $Var(x) = \sigma^2 = \frac{1-p}{p^2}$

 -  **Negative binomial distributions**
	 - Describes the probability of the xth trial resulting in the kth success
	 - $$P(x, k) = nCr(x-1, k-1)(1-p)^{x-k}p^k$$
	 - Where k is the number of success, x is the number of trials, p is the probability of success
	 - $$E(x) = \mu = \frac{k}{p}$$
	 - Variance: $$\sigma^2 = Var(X) = \frac{k(1-p)}{p^2}$$

An oil company conducts a geological study that indicates that an exploratory oil well should have a 20% chance of striking oil.
$$
	P(x, k) = nCr(x-1, k-1)(1-0.20)^{x-k}0.20^{k}
$$
a. What is the probability that the first strike comes on the third well drilled?
	$P(x=3, k=1) = 0.128$
b. What is the probability that the third strike comes on the seventh well drilled?
	$P(x=7, k=3) = 0.0492$
c. What is the mean and variance of wells that must drilled if the oil company wants to set up three producing wells?
	$\mu = 3/0.20 = 15$ and $\sigma^2 = 3(1-0.20) / (0.20)^2 = 60$
	

In a recent production, 5% of certain electronic components are defective. We need to find 12 non-defective components for our 12 new computers. Components are tested until 12 non-defective ones are found. What is the probability that more than 15 components will have to be tested?

Find the chance that the 15th computer will have the 12th non defective units, the chance for being non-defective is p=0.95
$P(x) = nCr(x-1, 11) \cdot (1-0.95)^{x-12} \cdot 0.95^{12}$
$P(x\ge15) = 1-(P\left(12\right)+P\left(13\right)\ +\ P\left(14\right)+P\left(15\right)) = 0.0055$


You are surveying people exiting from a polling booth and asking them if they voted independent. The probability (p) that a person voted independent is 20%. What is the probability that 15 people
must be asked before you can find 5 people who voted independent? Determine its mean and variance
$$
	P(x, k) = nCr(x-1, k-1)(1-0.20)^{x-k}0.20^{k}
$$
a.) What is the probability that 15 people must be asked before you can find 5 people?
	$P(15, 5) = 0.0343$
b.) Determine its mean and variance?
	Mean: $\mu = 5/0.20 = 25$
	Variance: $\sigma^2 = 5(1-0.20)/0.20^2  = 100$
	
For a certain manufacturing process, it is known that, on the average, 1 in every 100 items is defective. What is the probability that the fifth item inspected is the first defective item found?

$P(x) = (1-0.01)^{x-1}0.01$
$P(5) = 0.0096$

---
 -  **Poisson distribution**
	 - Properties of a possion process
		 - The probability of two or more successes in any sufficiently small subinterval is 0
		 - The probability of success is the same for any two intervals of equal length
		 - The number of successes in any interval is independent of the number of successes in any other interval provided the intervals are not overlapping
	 - The PDF of a Possion process is the following: 
		 $$
			 P(X=x)=\frac{(\lambda t)^x \cdot e^{-\lambda t}}{x!}
		 $$
		 - where lambda is the average number of occurrences of the event in some interval of length 1
	 - The mean and variance are both lambda
	 - Poisson can be used to approximate binomial probabilities provided the number of trials is over 100
	 - The number of independent trials of the optimal experiment should be large and the probability of success should be small

The average number of patients visited UST Hospital is 15. The hospital can only accommodate at most 20 patients per hour. What is the probability that in a given hour, patients are ask to wait for
another hour since all the doctors are occupied?

$$P(x) = \frac{15^x \cdot e^{-15}}{x!}$$
$$P(20) = \frac{15^{20} \cdot e^{-15}}{20!} = 0.0418$$


During a laboratory experiment, the average number of radioactive particles passing through a counter in 1 millisecond is 4. What is the probability that 6 particles enter the counter in a given millisecond? Find its mean and variance.
$$P(x) = \frac{4^{x} \cdot e^{-4}}{x!}$$
$$P(6) = 0.1042$$


97% of electronic messages are transmitted with no error. What is the chance that out of 200 messages, at least 195 will be transmitted correctly

Rewrite as 3% are transmitted with error, find the chance that the number of broken messages is 0 to 4 out of 200
$$
P(x) = \frac{6^x \cdot e^{-6}}{x!}
$$
Find the sum of $P(0) + P(1) + P(2) + P(3) + P(4) = 0.2850$

If approximately 2% of the people in a room of 200 people are left-handed, find the probability that exactly 5 people there are left-handed.

$$
P(x) = \frac{(0.02 * 200)^x \cdot e^{-(0.02 * 200)}}{x!} = \frac{4^{x} \cdot e^{-4}}{x!}
$$
$$
	P(5) = 0.1563
$$

---
### Continuous Distribution

- **Continuous uniform distribution**
	 - Characterized by a density function that is flat, the probability is uniform in a closed interval.
	 - $f(x) = \frac{1}{B-A}$ when x is between A and B, else it is 0
	 - Mean: $\mu=\frac{A+B}{2}$
	 - Variance: $\sigma^2 = \frac{(B-A)^2}{12}$

Suppose that a large conference room at a certain company can be reserved for no more than 4 hours. Both long and short conferences occur quite often. Suppose that the length X of a conference has a uniform distribution on the interval 0 to 4.
Give the PDF: $f(x) = 1/4$
Probability that any given conference lasts atleast 3 hours: $f(x\ge3) = 1/4$
 - evaluate the integral of 1/4 between 3 and 4
Mean: $\mu = 0 + 4 / 2 = 2$
Variance: $\sigma^2 = (4-0)^2/12 = 4/3$

---

 - **Normal Distribution**
	 - Properties
		 - Bell shaped - symmetric family
		 - Mean = median = mode
		 - The total area under the curve is equal to one
		 - Has long tapering tails, which extend indefinitely in either direction, corresponding to the infinite range of x values in the distribution
	 - Controlled by Mean and standard deviation, representing location and spread.
		 - Approximately half fall above and below mean
		 - 68% fall within 1 standard deviations of mean
		 - 95% fall within 2 standard deviations of mean
	 - Mean: $\mu = \text{expectation, location parameter}$
	 - Standard Deviation: $\sigma = \text{standev, the scale parameter}$
	 - The probability distribution function:
		 $$
			 f(x) = \frac{1}{\sigma\sqrt{2\pi}}exp{\frac{-(x-\mu)^2}{2\sigma^2}}
		 $$
 - **Standard Normal Distribution**
	 - Normal distribution where the mean is 0 and the standard deviation is 1
	 - There's an unlimited number of normal distributions
		 - $z = \frac{X-\mu}{\sigma}$ - the range is between 0, 1

![[9340559_orig.webp]]
![[8573955-1.webp]]

$P(z > 1.20) = 1-z(1.20) = 1-0.8849 = 0.1151$
$P(0 < z < 1.20) = z(1.20) - z(0) = 0.3849$
$P(-1.30 \le z \le -1.10) = z(-1.10) - z(-1.30) = 0.1357 - 0.0968 = 0.0389$

Given a normal distribution with mean equal to 200 and standard deviation of 10. Find the following:
$z(x)=(x-200)/10$
 - the area below 210 - find z(210) = 1
	 - 0.8413
 - area between 182 and 208
	 - find the area within z(182) = -1.8 and z(210) = 1
	 - 0.8413 - 0.0359 = 0.8054
 - the x value that has 80% of the area below it
	 - z=0.85
	 - x = (z * 10) + 200 = 208.5
 - the two values of x containing the middle 75% of area.
	 - 1.15 and -1.15
	 - x=188.5 to 211.5

The mean scores in a Biostat exam was 72.8 with a standard deviation of 17.45. If it can be assumed that the scores are normally distributed
$z(x) = (x-72.8)/17.45$

what proportion of the students got 80 and above?
$1-z(80) = 1 - 0.6628 = 0.3372$

if 110 students took the exam, how many got 80 and above?
$110 * 0.3372 = 37.092$

what is the probability that a student will have a score between 45 and 75?
$z(75)-z(45) = 0.5517 - 0.0559 = 0.4958$

if the department is interested in inputting a special class for the upper 15%, what should be the score of the student?
z=1.04
$x = 1.04 * 17.45 + 72.8 ~= 91$ 

---

 - **Gamma and Exponential Distribution**
	 - plays an important role in queuing theory and reliability problems
		 - models time, waiting time, arrivals 
	 - Derives its name from the well known gamma function studied in many areas of mathematics
		 - Gamma function:
			 - is an approximation of the factorial that can be used to extend it into non integer numbers
			   $$
			   \Gamma(\alpha) = \int^{\infty}_{0}x^{\alpha-1}e^{x}dx
			   $$
 - Gamma distribution - the continuous random variable X has a gamma distribution with parameters a and b
	   $$
	   f(x, \alpha, \beta) = \frac{1}{\beta^{\alpha}\Gamma(a)}x^{\alpha-1}e^{-\frac{x}{\beta}}
	   $$
	 - Mean: $\mu = \alpha\beta$, Variance: $\sigma^{2}=\alpha\beta^2$

 - Exponential distribution is a special case of the gamma distribution where $\alpha =1$
	   $$
	   f(x) = \frac{1}{\beta}e^{-\frac{x}{\beta}}
	   $$
	 - Mean: $\mu = \beta$, Variance: $\sigma^{2}=\beta^2$

Jobs are sent to a printer at an average rate of 3 jobs per hour.
	$$
	   f(x) = \frac{1}{20}e^{-\frac{x}{20}}
	   $$
(a) What is the expected time between jobs?
Mean: 20 minutes

(b) What is the probability that the next job is sent within 5 minutes?
$$
\int^{5}_{0} \frac{1}{20}e^{-\frac{x}{20}} dx
$$


---

 - **Chi squared distribution**
	 - Obtained by using the gamma distribution where alpha = v/2 and beta = 2 where v is a positive integer, only uses v as a single parameter
	 - basically a special case of Gamma where v is the degrees of freedom
	 - Has vital role in statistical inference
		   $$
		   f(x) = \frac{1}{2^{\frac{v}{2}}\Gamma(\frac{v}{2})}x^{\frac{v}{2}-1}e^{-\frac{x}{2}}
		   $$
	 - Mean: $\mu = \beta = v$ and Variance: $\sigma^2 = 2\beta = 2v$

---

 - **Beta distribution**
	 - a distribution of distribution, models probabilities
		 - a uniform distribution, with alpha = 1 and beta = 1
	 - Beta function: 
		$$
			B(\alpha, \beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha + \beta)}
		$$
	- Beta distribution:
		$$
			f(x) = \frac{1}{B(\alpha, \beta)}\cdot x^{\alpha-1}\cdot(1-x)^{b-1}
		$$
		- The uniform distribution on (0, 1) is a beta distribution with parameters alpha = 1 and b = 1
	- Mean: $\mu = \frac{\alpha}{\alpha + \beta}$
	- Variance 
		$$
		\sigma^2 = \frac{\alpha \beta}{(\alpha + \beta)^2 (\alpha + \beta + 1)}
		$$

---

- **Lognormal distribution**
	- happens if the random variable Y = ln(x) has a normal distribution with its mean and standard deviation
		$$
			f(x; \mu, \sigma) = \frac{1}{\sqrt{2\pi}\sigma x}\cdot e^{-\frac{1}{2\sigma^2}}[ln(x)-\mu]^2
		$$
	 - Mean: $\mu = e^{\mu + \frac{\sigma^2}{2}}$
	 - Variance: $\sigma^2 = e^{2\mu + \sigma^2}(e^{\sigma^2} - 1)$

---

 - **Weibull Distribution**
	 - f(x) is given as
		 $$
			 f(x) = \alpha\beta x^{\beta - 1}e^{-\alpha x^{\beta}}
		 $$
	- Mean: 
		$$
		\mu = \alpha^{\frac{1}{\beta}}\Gamma \left(1 + \frac{1}{\beta}\right)
		$$
	- Variance: 
		$$
		\sigma^{2} = \alpha^{\frac{-2}{\beta}}\left(\Gamma \left(1 + \frac{2}{\beta}\right) - \left[\Gamma \left(1 + \frac{2}{\beta}\right)\right]^{2}\right)
		$$
	- Cumulative distribution function: $F(x) = 1-e^{-\alpha x^{\beta}}$

