# [Middle] Bellman-Ford Algorithm
**Chapter: 24.1**

## When to use?
1. Single source shortest path with # of iterations constrain

## Problem Formulation:
1. input: 
	1. G=(V, E), w:E->R, 
	2. source vertix
2. output: 
	1. vector of shortest distance
	2. a single source shortest path tree
	3. whether it has negative weighted cycle reachable from source

## Limitations:
1.	If all the weight are positive, please use Dijkstra's algorithm.
3.	It can be optimized by shortest path faster algorithm (SPFA) where worst case is the same as O(VE) but in aversage is O(|E|).

## Main idea:
1.	Shortest path cannot contain cycle-->shortest path is simple path
2. |V| vertices-->|V|-1 relaxations can achieve shortest path (somehow DP)
3. If |v| relaxation still updates value,
	-> there is negative weighted cycle reachable from source in graph
	-> return false

## Complexity:
1. Space: O(V)
2. Time: O(VE)
	
## Pseudo Code:
```
Bellman_Ford_Algorithm(G,w,s)
	Initialize Graph(G,s):
	for i = 1 to |G.V|-1:
		for each edge (u,v) in G.E:
			relax(u,v,w)
	for each edge(u,v) in G.E:
		if v.d>u.d+w(u,v):
			return False;
	return True
```

## Leetcode classic problems:

1. [787. Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)  

## Others modification:
None

## C++ code sample:

[787. Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)  

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

[743. Network Delay Time](https://leetcode.com/problems/network-delay-time/)  
```c++
// Bellman Ford: TLE, need to use Dijkstra or SPFA
class Solution {    
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k)
    {
        vector<int> d(n+1,INT_MAX);
        d[0]=0; //dummy node.
        d[k]=0;
        
        for(int i = 1;i<=n-1;i++)
        {
            for(auto ele: times)
            {
                // relax
                int u = ele[0];
                int v = ele[1];
                int w = ele[2];
                
                if (d[u]!=INT_MAX && d[v]>d[u]+w)
                    d[v]=d[u]+w;
            }
        }
        
        int max_ele = 0;
        for(auto ele: d)
        {
            max_ele=max(max_ele,ele);
        }
        return max_ele==INT_MAX? -1: max_ele;  
    }
};
```
