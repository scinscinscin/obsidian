---
tags:
  - reviewer
course: CS2615 - Design and Analysis of Algorithms
period: Prelim
assessment: Prelim Exam
---

Problem - a statement regarding objects and structures that need to be resolved to produce answer of expectations
 - Sorting / searching / string processing / graphs / combinatorics
Problem specification
 - what are the input instances
 - what the output should be in terms of the input instance

## Algorithms 
 - used to solve problems
 - Heart of CS / idea behind computer programs
 - Automates collection / organization / processing of large amount of information
 - Is language and machine agnostic
 - Factors
	 - Correctness - Produce desired outputs on all inputs
		 - can be verified using mathematical proofs
		 - Loop invariants / Recursive functions and mathematical induction
		 - Not always checked (proofs are not emphasized)
	 - Efficiency - fast and use little memory
		 - Determines how much resources are used by a given algorithm
		 - Make quantitative assessments about the efficiency of one alg to another
		 - Do this without implementing a running version of an alg
			 - Is used with the Random Access Machine Model
				 - No parallel computations
				 - All atomic operations take O(1) time
				 - All atomic data types take O(1) space
				 - Loops and function calls are not atomic operations and depend on the size of the data and the components of a subroutine
		 - Inputs of the same size may require different steps to solve
			 - Worst case - most considered because of impact, occurs often
			 - Average case - needs info on probabilistic distribution of inputs
				 - Complicated to compute and is often as bad as the worst case
			 - Best case - minimum number of steps taken on any instance of size n
			 - Example on insertion sort
				 - Best case - when the array is already sorted O(n)
				 - Worst case - when the array is in reverse sort order O(n^2)
				 - Average case - when the array is randomly ordered, still O(n^2)
	 - Elegance - simplicity of solutions
 - Design strategies
	 - Brute force and exhaustive search
	 - Decrease and Conquer
	 - Divide and Conquer
	 - Randomized algorithms
	 - Transform and conquer
	 - Greedy
	 - Dynamic Programming
	 - Approximation

## Asymptotic Complexity
 - measures the scalability of algorithms
 - expressed in terms of the input size
 - classes algorithms in terms of efficiency
 - indicates the behavior for large enough input size
	 - focuses on large n's and ignores small n's
		 - Constant factors and lower degree terms are not significant
	 - An algorithm that is asymptotically more efficient will be the better choice for every size except for small inputs

**Big O**
 - states that a function will never run worse than a given function g(n)
 - **`lim n->inf f(n)/g(n) >= 0`**
 - `O(g(n))` = `The set of all functions f(n) where there exists values c and N over 0 such that f(n) <= c * g(n) where all values of n >= N`

**Big Omega**
 - states that a function will never run better than a given function g(n)
 - **`lim n->inf f(n)/g(n) > 0 or is infinite`**

**Theta**
 - states that a function will never run worse or better than a given function g(n)
 - It is the tightest bound that can be applied to the running time of that function
 -  **`lim n->inf f(n)/g(n) > 0`**
	 - if the limit is greater than 0, a limit can be taken since they fall under the same complexity class, and since they are the same complexity class f(n) belongs to Theta(g(n))

**Little O**
- states that a function will never run worse or be equal to a given function g(n)
-  **`lim n->inf f(n)/g(n) = 0`**
	- if the limit is equal to 0, g(n) grows faster than f(n), g(n) is of a higher complexity class, so f(n) falls under little_o(g(n))

**Little Omega**
- states that a function will never run better or be equal to a given function g(n)
-  **`lim n->inf f(n)/g(n) = inf`**
	- If the limit is equal to infinity, f(n) grows faster than g(n), g(n) is of a lower class complexity so f(n) falls under little_omega(g(n))

## Recurrence Analysis Methods
 - We need to determine the asymptotic complexity of T(n) but T(n) is expressed recursively
 - Analysis methods for recursive algorithms
	 - Extrapolation or substitution method
		 - Guess a closed for solution then prove that it is true using mathematical induction
		 - Guessing
		 - Induction
			 - Inductive hypothesis
			 - Inductive step
		 - Example: `T(n) = 2T(n-1) + 1`, where T(0) = 0
			 - **This is an example of just induction without application of complexity**
			 - Prove that `T(n) = T(2^n -1)` using induction
			 - 1. Prove the base case 
			 - 2. Inductive hypothesis that for some K>= 0, `T(n) = 2^n - 1` is true for all n<=k
			 - 3. Show that `T(k+1) = 2^(k+1) -1`
				 - `T(k+1) = 2T(k) + 1`
				 - `T(k+1) = 2 * (2^k - 1) + 1`
				 - `T(k+1) = 2^(k+1) - 1`
		 - Example: `T(n) = 3T(floor(n/4)) + n`, where T(0) = 0
			 - Prove that `T(n) = O(n)` using induction
			 - 1. Prove the base case
				 - `T(0) = 0 <= 0` - true
				 - `T(1) = 3(0) + 1 <= c` - true where c>= 1
			 - 2. inductive hypothesis that `T(n) <= c*n` where `0 <= n <= k`
			 - 3. Show that `T(k+1) <= c(k+1)`
				 - `T(k+1) = 3 * T(floor(k+1 / 4)) + k + 1`
				 - `T(k+1) <= 3 * c(floor(k+1 / 4)) + k + 1`
				 - `T(k+1) <= 3 * c(k/4 + 1/4) + k + 1`
				 - `T(k+1) <= (3c/4 + 1)k + (3c/4 + 1)`
				 - `T(k+1) <= c(k + 1)` where c>= 4
	 - Back substitution or iteration method
	 - Recursion tree method
		 - Suitable for divide and conquer and decrease and conquer type recurrences
			 - Each node represents the cost of a single subproblem
			 - Sum of the costs with each level to get level cost
			 - Sum up all the level costs to get total cost
		 - Best used to generate a good guess
		 - Can be a valid proof if recursion tree is drawn
		 - ![[Pasted image 20230914144758.png]]
	 - Master method
		 - Can be used to get the time complexity of a divide and conquer algorithm quickly
		 - The recurrence relation must be in the form of `T(n) = aT(n/b) + f(n)`
			 - We create a function called the watershed function in the form of `Theta(n^(log_a(b)))`
			 - We compare f(n) against the watershed function which can have three cases
		 - Cases
			 - `f(n)` is slower than the watershed function - running time is `Theta(n^(log_a(b)))`
			 - `f(n)` is equal to the watershed function - running time is `Theta(f(n) * lgn)`
			 - `f(n)` is faster than the watershed function - running time is `Theta(f(n))`
				 - The growth factor is dominated by `f(n)`
		 - has exceptions when we are comparing using logarithms

## Brute Force
 - the solution is solely based on the problem statement and the definition of the concepts involved
 - Force comes from using computer power
 - also called exhaustive search for combinatorial problems since we try every possibility
	 - all permutations/ combinations or subsets
	 - Permutations - the different orderings of S
		 - Generate all n! permutations of S
		 - **Incremental method** - Insert one element at a time in all possible insertion points
		 - **Johnson-Trotter's Minimal Change algorithm**
			 - Each permutation is obtained by swapping two elements int he current permutation
			 - Each element points either to the left or to the right
			 - K is mobile if it points to an adjacent smaller number
			 - Initialize with all elements pointing to the left
			 - While the last permutation has a mobile element
				 - Find the largest mobile element K
				 - Swap K with the adjacent element k points to
				 - Reverse the direction of all elements larger than K
				 - Add the new permutation to the list
	 - Combinations - the different subsets of S, with cardinalities from 0 to n
		 - Generate all 2^n subsets of S
		 - **Incremental Method**
			 - Start with the null set
			 - Create new subsets by adding an element to previously generated subsets
			 - ![[Pasted image 20230914162017.png]]
			 - There is a correspondence between bit strings and subsets
		 - **Binary Reflected Gray Code**
			 - Get the recursive output for n-1 elements
			 - Concatenate the lists of 0 prepended to the elements of the output, and 1 prepended to the reverse ordering elements of the output
			 - `const brgc = (n) => n == 1 ? ["0", "1"] : [...brgc(n-1).map(x => "0" + x), ...brgc(n-1).reverse().map(x => "1" + x)];`
 - Simplicity
	 - Is often the only general approach that often works
	 - Sometimes there is no other way to solve a problem or trying to do better is not worth it
 - Crude but often effective, but is also rarely efficient
	 - Only feasible in small instances of a problem
 - A basis to compare with more efficient strategies

**Travelling Salesman Problem**
 - find the shortest tour through a given set of n cities
	 - Must visit each city exactly once
	 - Must return from last city to first city
 - Can be modeled with a weighted complete graph where each city is a vertex and edge weights are distances between cities
 - Brute force solution
	 - Exhaustive Search
	 - Generate all permutations of n cities in a cycle
	 - Compute the tour lengths of those permutations and find the shortest among them

## Decrease and Conquer
 - Reduce problem instance to smaller instance of the same problem and extend the sub soltuion
 - Also called prune and search / increase and conquer or inductive / incremental method
 - Does not work equally on both subproblems
 - 3 types
	 - **Decrease by a constant**
		 - Exponentiation
			 - `a^n` is defined as `a^(n-1) * a`
		 - Insertion sort
		 - DFS graph search
		 - Topological sort
			 - Finds out the order that jobs must be performed in a job dependency graph
			 - Represents job dependencies using a directed graph
				 - Jobs are vertices, an edge from X to Y specifies that X must be completed before Y can be started
			 - Not solvable if the digraph has a cycle
			 - Finds a linear ordering how tasks could be performed
			 - Perform DFS on the graph starting from the nodes that contain no dependencies, and in the post order visit, add the current node to the head of a linked list. The running time is `Theta(|V| + |E|)`
		 - Generating combinations
	 - **Decrease by a constant factor (divide)**
		 - Exponentiation
			 - `a^n` is defined as `a^(floor(n/2))^2` for even n's
			 - `a^n` is defined as `a^(floor(n/2))^2 * a` for odd n's
			 - Has a running time of theta(lgn) since the number of recursions that has to occur is lgn
		 - Binary search
			 - We always remove n/2 elements in the search pool for every iteration
	 - **Variable size decrease**
		 - Euclid's algorithm for finding GCD
			 - `const gcd = (x, y) => y === 0 ? x : gcd(y, x % y);`
 - Some brute force algorithms are also decrease and conquer
	 - Sequential search / selection sort and bubble sort
 - Can be implemented top-down or bottom up

## Divide and Conquer
 - Divide the input data into two or more disjoint subsets
 - Solve the subproblems through recursion
 - Combine solutions for smaller solutions into one big solution
 - `T(n) = aT(n/b) + D(n) + C(n)`
	 - a - number of subproblems
	 - n/b - size of each subproblem
	 - D(n) - cost of each divide operation
	 - C(n) - cost of each combination operation

**Quicksort**
 - in place sorting whose average case is O(nlgn)
	 - The worst case is O(n^2) since it runs as reverse bubble sort where heavier elements sink
 - Chose a pivot element in a fixed relative location
 - Partition the elements to be sorted based on the pivot element
	 - In the element to be sorted, pick the first element p
	 - Go from opposite ends of the array and find elements that are smaller and larger than p respectively
	 - Swap their positions if the two indices are not past each other
	 - Return the index j if the two indices are past each other
 - Recursively sort smaller and larger elements

**Randomized algorithms**
 - Algorithm works well with high probability on every input
 - Algorithm may fail on every input with low probability
 - No single input causes worst-case scenario

**Closest pair divide and conquer algorithm**
 - Given P which is a set of points on a plane, find two closest points in P
 - Sort the points in P based on their x coordinates in a set called X and based on y-coordinates in a set called Y in O(nlogn) time
 - Find a vertical line that splits X and Y into two subsets each, with an equal number of elements per subset
 - XL contains the elements at the left side of the line, YL contain the elements on the left side sorted based on their y-coordinate. The same is the same with XR and YR. This is done in O(n) time
 - Find the closest pair in the subplanes
 - The closest pair is either the closest in the subplanes or one point in PL and one point in PR
	 - Find the minimum between SL and SR which is called d
	 - Create a strip P' from points in P which are at most d units from the original dividing line
	 - Create Y' which contains the points in P sorted by their y -coordinate
	 - For each p in P', find distance from p to at most 7 points until delta y exceeds d
	 - Get the minimum distance d' among all instances computed
	 - Return the pair with distance min(d, d')

## Proof that O(n lg n) is the best we can do for comparison based sorting
 - Create a binary tree whose leaves represent the swaps needed to convert an input array into a sorted array
	 - If we have 5 element array, there can be 120 swaps done to change the array into a sorted array
 - The number of leaves of a decision tree for a n-element array is n!.
	 - Then find the height for that decision tree `n! <= 2^h`, and we get `h >= lg(n!)`
	 - h is the number of comparisons we need to do to find how to sort the array
	 - We can get the lg of n! using stirling's approximation, where the dominant term is in O(n lg n)

**Sorting in Linear time**
 - if we make assumptions, we can sort in linear time
 - Bucket sort / Counting Sort / Radix sort

# Selection
 - The running time for finding the maximum and minimum in an array is in O(n) time because we only need to do 1 pass
 - ith order statistic
	 - Finding the ith smallest element in an array of N elements
	 - Is used for finding median / lower median / upper median
	 - Expected / average case is linear time
```js
function hoarePartition(A, start, end) {
  x = A[Math.floor(Math.random() * (end - start)) + start];
  // console.log({ pivot_value: x, A: A.join(", "), start, end });
  i = start;
  j = end;

  while (true) {
    while (A[j] > x) j--;

    while (A[i] < x) i++;

    if (i < j) {
      temp = A[i];
      A[i] = A[j];
      A[j] = temp;
    } else {
      return j;
    }
  }
}

const testing = [17, 12, 6, 23, 19, 8, 5, 10];
function RandomizedSelect(A, p, r, i) {
  if (p == r) return A[p];
  const q = hoarePartition(A, p, r);
  const k = q - p + 1;
  // console.log({ q, left_side: k, A: A.join(", ") });

  // console.log(q, k);
  if (i <= k) return RandomizedSelect(A, p, q, i);
  else return RandomizedSelect(A, q + 1, r, i - k);
}

for (let i = 1; i <= testing.length; i++) {
  console.log(RandomizedSelect(testing, 0, 7, i));
}
```