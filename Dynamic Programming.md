
#### What is Dynamic Programming? 
Dynamic programming is a design technique, like an incremental approach, divide and conquer, etc. Typically applied to optimization problems.
	Many possible solutions, each solution has a value, we wish to find a solution with the optimal value. A set of choices must be made to get an optimal solution. There may be several solutions that achieves the optimal value. 
	**End Goal** find an optimal solution.
So lets approach this as follows 
1. Characterize the structure of the optimal solution
2. Recursively define the value of an optimal solution
3. Compute the value of an optimal solution in a bottom-up fashion
4. Construct an optimal solution from computer information( not always necessary)

Computer the number of ways to select k items out of n items( no substitution, order does not matter)

#### Solving Problems 
So how could we begin solving a problem using dynamic programming?
Lets start with finding the optimal substructure.
	The parenthesizing of the 'prefix' $A_{i...k}$ must be an optimal parenthesizing
	An optimal solution to an instance of the matrix chain multiplication contains within it optimal solutions to subproblems. 
now find a recursive solution. 
	Determine the minimum cost of parenthesizing 
		$A_{i...j} = A_i  A_{i+1} ... A_j for 1 \leq i \leq j \leq n$ 
		let m$[i,j]$ = the minimum number of multiplications needed to compute $A_{i...j}$ 
		- full problem $(A_{1...n}): m[1,n]$ 
		- recursive definition
			If $i = j:  A_{i...i} = A_i => m[i,i] =0$ for $i= 1,2,...,n$ ( no scalar multiplication are necessary)
### Longest Common Subsequence 
Given two sequences $x[1....m]$ and $y[1...n]$ find the longest subsequence( there could be more then one) common to both of them.

so we could just brute force this, check every subsequence of x with y. But when we analyze this we can see that there will be $x^m$ subsequences in x same with y. to check if it matches in y we would need to check every element in y so the worst case running time would be $O(n2^m)$ which is incredibly slow. 

##### How do we make this better?
What if we found the length of the longest subsequence, and then extend the algorithm to then find the LCS( Longest Common Subsequences)

Now when we are doing this we can do it recursively, but when we do it recursively we end up solving some sub problems twice which can detrimentally effect the run time of the algorithm so how do we avoid that? well we can just use a look up table, if we solve a problem, lets store it in the table, and then check the table before we solve the next problem.


