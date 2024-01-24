problem
 - statement regarding objects and structures that need to be solved to produce answers
 - problem spec
	 - what are the input instances
	 - what the output should be in terms of the input instance

worst case running time
 - upper bound on the running time for any input
 - guarantees that the algorithm will never take any longer
 - occurs fairly often
	 - search for absent information may not be present which takes the worst case

average case
 - roughly as bad as the worst case
 - can be found using probabilistic analysis
 - may not be apparent what constitutes an average input for a problem

rate of growth
 - we only consider the leading term of a formula since lower order terms are relatively insignificant for a large value of n
 - ignore leading term's constant coefficient since constant factors are less significant than the rate of growth in determining efficiency for large inputs
 - we are studying the asymptotic efficiency of algorithms
	 - how the running time increases with the size of the input in the limit

recurrence
- used for describing algorithms that call themselves
- overall running time of a problem of size n in terms of running times of the same algorithms with smaller inputs

big O notation
 - an upper bound in the asymptotic behavior of a function
 - a function grows no faster than a certain rate, based on the highest order term
 - if a function grows no faster than n^3, we can say that it's O(n^3)
	 - you can also say that n^3 grows no faster than O(n^4)
	 - O(N^3) - a set of functions whose running times fall under n^3
 - when taking the limit, the result must be >= 0
	 - when the limit is equal to zero - the function has a lower degree than g(n)
 - set of functions whose degrees are less than or equal to g(n)

omega notation
 - lower bound of the asymptotic behavior of a function
 - a function grows at least as fast as a certain rate
 - 7n^3 + 100n^2 - 20n + 5
	 - Omega(n^3), also n^2 and n because these running times are lower than the equation itself
 - it will never run slower than this Omega running time
 - **runs the same limit test but result must be > 0 or infinity**
	 - when infinity - the degree of the function is larger than the degree of the running time
 - set of functions whose degrees are greater than or equal to g(n)

theta notation
 - describes that a function grows precisely at a certain rate, based on the highest order term
 - characterizes the rate of growth of a function to within a constant factor from above and to within a constant factor for below
 - if a function is both O(n) and Omega(n) then a function is theta(n)
	 - exactly the degree of O(g(n)) / is the intersection between the omega and big o notation
 - **when taking the limit, the result must be >0**
	 - when the limit is greater than 0, it's an equal degree
 - set of functions that have an equal degree

little o
 - **when taking the limit, it's just equal to 0**
 - loose upper bound
 - big O just without exact degree of O(g(n))
	 - set difference of big O and theta
 - set of functions whose degrees are less than g(n)

little omega
 - n^3 is little omega of little_omega(n^2)
 - **when taking the limit, the result must be infinity**
 - set of functions whose degrees are greater than g(n)

![[Pasted image 20230818082735.png]]