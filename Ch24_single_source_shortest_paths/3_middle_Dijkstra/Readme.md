# [Middle] Dijkastra
**Chapter: 24.3**

## When to use?
1. Single source shortest path with no negative weight.

## Problem Formulation:
1. input: 
	1. G=(V, E), w:E->R, 
	2. source vertix
2. output: 
	1. vector of shortest distance
	2. a single source shortest path tree
	
## Limitations:
1. All the weights are not negative.
2. If this graph is directed acyclic, consider using DAG algorithm O(E+V).

## Main idea:
1. Using gready approach. Each step selects the "min current distance" from currently reachable vertices.
    - In pseudo code, it seems to be implemented in set data structure
    - However, it is impelmented similar to BFS (queue), but requires the ability to selects the "min current distance".    
    
2. Use heap to achieve the min weight selection, use visited vector to distinguish set.
    - Please be familiar with the pair and comparator using priority_heap.
    - Please note the usage of visited vector.

## Complexity:
1. Space: O(V)
2. Time: 
    1. Use Binary heap: O[(|V|+|E|)logV]
    2. Use Fibonacci heap: O(E+VlogV)

## Pseudo Code:
```
Dijkstra_Algorithm(G,w,s)
    S = empty set
    Q = G.V
    while(!Q.empty){
        u = extract-min(Q)
        S = union{S,u}
        for each vertex v in G.Adj[u]:
            RELAX(u,v,w)
    }   
```

``` v2
Dijkstra_Algorithm(G,w,s)
	Initialize Graph(G,s):
	initialize heap, visited
	heap.push({0,s})
	
	while(!heap.empty())
	    w, u = heap.top()
	    heap.pop()
	    if visited[u]: continue
	    for([v,w]: G.adj[u])
	        if(d[v]>d[u]+w)
	            d[v]=d[u]+w
	            heap.push({d[v],v})
        visited[u]=true
```

## Leetcode classic problems:
1. [743. Network Delay Time](https://leetcode.com/problems/network-delay-time/)  

## C++ code sample:
[743. Network Delay Time](https://leetcode.com/problems/network-delay-time/)  

```c++
typedef pair<int,int> pii;
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<int> d(n+1,INT_MAX);
        d[0]=0; //dummy node.
        d[k]=0;
        vector<bool> visited(n+1, false);
        vector<vector<pii>> graph(n+1);
        for(auto ele: times)
        {
            graph[ele[0]].push_back({ele[1],ele[2]});
        }
        priority_queue<pii, vector<pii>, greater<pii>> que;
        que.push({0,k});
        
        while(!que.empty())
        {
            auto [cost,u] = que.top();
            que.pop();
            if(visited[u]) continue;
            for(auto ele: graph[u])
            {
                int v = ele.first;
                int w = ele.second;
                if(d[v]>d[u]+w){
                    d[v]=d[u]+w;
                    que.push({d[v],v});                    
                }
            }
            visited[u]=true;
        }
        int min_time = 0;
        for(auto ele: d)
            if (min_time<ele)
                min_time=ele;
        return min_time==INT_MAX? -1: min_time;        
    }    
};
```


## Others:
None