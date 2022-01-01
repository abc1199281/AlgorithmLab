# [Middle] Breadth First Search
**Chapter: 22.2**

## When to use?
1. Traversing all vertex in a graph
2. Finding the shortest path between two vertices where **all edges have equal and positive weights**.

## Problem Formulation:
1. input: 
	1. G=(V, E) 
	2. source vertix
2. output: 
	1. vector of shortest distance
	2. a single source shortest path tree
	
## Limitations:
1.  **all edges have equal and positive weights**.

## Main idea:
1.	Shortest path cannot contain cycle-->shortest path is simple path
2. |V| vertices-->|V|-1 relaxations can achieve shortest path (somehow DP)
3. If |v| relaxation still updates value,
	-> there is negative weighted cycle reachable from source in graph
	-> return false

## Complexity:
1. Space: O(V)
2. Time: O(V+E), we need toe check each vertex & edge.

## Pseudo Code:
```
Breadth_First_Search(G,s)
	
    for each vertex u in G.V-{s}{
        u.color=white
        u.d = inf
        u.pi = null
    }
    s.color = gray
    s.d = 0
    s.pi = null
    
    que = empty_set
    que.push(s)
    while(!que.empty()){
        u = que.front();
        u.color = gray;
        for each v in G.adj[u]{
            if v.color == white{
                v.color = gray
                v.d = u.d+1
                v.pi = u
            }
        }
    }    
```

## Leetcode classic problems:
1. comming soon

## C++ code sample:

[Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)  

```c++
typedef pair<int,int> pii; // useful data structure for weighted graph.
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        // Because of its k constrain, conventional Bellman Ford is chosen.
        // There is no need of path, vector predecessor is ignored.

        // Initialize graph 
        // distance vector
        vector<int> d(n, INT_MAX);        
        d[src]=0;
        vector<int> d_cur(n, INT_MAX);
        
        // cost_graph
        vector<vector<pii>> graph(n+1);
        for(auto edge: flights)
        {
            int u=edge[0];
            int v=edge[1];
            int w=edge[2];
            graph[u].push_back({v,w});
        }
        
        for(int i = 0;i<k+1;i++)
        {         
            d_cur = d;
            for(int j = 0;j<n;j++) // for each reachable vertex
            {
                for(auto edge: graph[j]) // for each adj.
                {                    
                    int v=edge.first;
                    int w=edge.second;
                    // note the comparison, we need to array to compare.
                    if(d_cur[j]!=INT_MAX && d[v]>d_cur[j]+w) 
                        d[v]=d_cur[j]+w;
                }
            }            
        }
        return d[dst]==INT_MAX?-1:d[dst];
    }
};
```

## Others:
N.A.
