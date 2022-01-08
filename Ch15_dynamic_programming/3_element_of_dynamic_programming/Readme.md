# [Middle] Element of Dynamic Programming & SOP
**Chapter: 15.3**

## Problem Formulation:
1. Problem can be solved by sub-problems with overlapping
2. Usually types: 
	1. Optimization

## Limitations:
1.	If Gready algorithm is possible, greedy should be faster.

## Main idea (SOP):
1. Charactering the Optimal substructure 
    1. Define the sub-problems, choices
    2. Define the state (thinking in Graph)
    3. Dimension: number of variables to define the state.
2. Define the value of an optimal substructure 
    1. Determine the relationship of the tables
3. Compute the value of an optimal substructure (button up)
	1. Built the tabulation sequence for loop
4. Construct the optimal solution from computed information.
	1. Obtains the inforamtion

## Detail of Main Idea
1. Charactering Optimal substructures
	1. Proof: 
		1. Make a choice, given the first choice, what's the subproblems?
		2. Use "cut-and-paste" to prove: opt solution of sub-problem is a part of opt solution in original problem.
	2. Aspects:
		1. How many sub-problems? -->The space of subproblems should be as simple as possible.
		2. How many choices?
        
## The framework (from leetcode)
1. a function or data structure that will contain/compute the answer to the problem for given any state. (Tabulation/memoization)
2. a currence relation to transition between states. (This is the most difficult part in DP problem.)
3. Base cases

## The common things that requires a state variable
1. An index along some input. (e.g., end index of an array, for this state, we've optimized the problem at the index.)
2. Start idx and end idx. (e.g., Matrix Multiplication chains)
3. Explicit numerical constraints given in the problem. (e.g., you're allowed to complete K transactions.)
4. Variables that describes statues in a given state. (e.g., current holding k keys.)
5. Some sort of data like a tuple or bitmask used to indicate things being 'visited' or 'used'.




## Complexity:
1. Space: O(V)
2. Time: 
    1.  O(# of sub-problems x # of choices)


## Pseudo Code:
```
Comming soon
```

## Leetcode classic problems:
#### One dimension
1. [70. (Easy)Climping Stair](https://leetcode.com/problems/climbing-stairs/)
2. [198. House Robber](https://leetcode.com/problems/house-robber/)
3. [746 Min cost climbing stair](https://leetcode.com/problems/min-cost-climbing-stairs/)
4. [1137. (Easy) N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)
5. [740. Delete and Earn](https://leetcode.com/problems/delete-and-earn/)


## C++ code sample:
Comming soon

## Others:
None