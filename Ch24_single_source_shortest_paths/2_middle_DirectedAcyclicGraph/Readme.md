# [Middle] Directed Acyclic Graph
**Chapter: 24.2**

## When to use?
1. Single source shortest path in directed acyclic graph

## Problem Formulation:
1. input: 
	1. G=(V, E), w:E->R, 
	2. source vertix
2. output: 
	1. vector of shortest distance
	2. a single source shortest path tree
	
## Limitations:
1.  must be acyclic.

## Main idea:
1. Based on topological sort, we can relax each vertex just once.
2. Works with negative weight because there is no cycle, shortest path is guaranteed.

## Pseudo Code:
```
DAG_Algorithm(G,w,s)
	Topological Sort(G)                 <--O(V+E)
    Initialize Graph(G,s):              <--O(V)
	
    for each vertex u in topological sorted order:
        for each vertex v in G.adj[u]    <- each edge of a vertex
			relax(u,v,w)
	// O(V+E) in amortized analysis
```

## Complexity:
1. Space: O(V)
2. Time: O(V+E)

## Leetcode classic problems:
1. Comming Soon

## C++ code sample:
1. Comming soon

## Others:
None
