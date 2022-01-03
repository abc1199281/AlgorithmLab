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

## Complexity:
1. Space: O(V)
2. Time: 
    1.  O(# of sub-problems x # of choices)


## Pseudo Code:
```
Comming soon
```

## Leetcode classic problems:
Comming soon

## C++ code sample:
Comming soon

## Others:
None