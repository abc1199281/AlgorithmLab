
# [Middle] Shortest Path Faster Algorithm
**Chapter: 24**

## Problem Formulation:
1. input: 
	1. G=(V, E), w:E->R, 
	2. source vertix
2. output: 
	1. vector of shortest distance
	2. a single source shortest path tree
	3. whether it has negative weighted cycle reachable from source
	
## Main idea:
1.	Bassicly follow the Bellman-Ford algorithm.
2.	Use FIFO queue to store the vertex to be search
3.	Vertex shoud be inserted into queue whenever its distance is updated.

## Pseudo Code:
```
SPFA(G,w,s)
	Initialize Graph(G,s):
	que.push(k)
	while(!que.empty())
		u = q.front()
		q.pop()
		inQ[u]=false
		for(v,w:u.adj)
			if(d[v]>d[u]+w)
				d[v]=d[u]+w
				if(!inQue[v])
					q.push(v)
					inQue[v]=True
				end
			end
		end
	end
```


## Complexity:
1. Space: O(V)
2. Time: O(VE), everage O(|E|)

## Limitations:
None

## Leetcode classic problems:

1. [Network Delay Time](https://leetcode.com/problems/network-delay-time/)  

## Others modification:
None

## C++ code sample:
[Network Delay Time](https://leetcode.com/problems/network-delay-time/)  
```c++
typedef pair<int,int> pii;

class Solution{
public:
    int networkDelayTime(vector<vector<int>> & times, int n, int k)
    {
        vector<int> d(n+1, INT_MAX);
        d[0]=0; // dummy node;
        d[k]=0;
        
        vector<vector<pii>> graph(n+1);
        for(auto ele:times)
        {
            int u=ele[0];
            int v=ele[1];
            int w=ele[2];
            graph[u].push_back({v,w});
        }
        
        vector<bool> inQue(n+1, false);
        queue<int> que;
        
        que.push(k);
        inQue[k]=true;
        while(!que.empty())
        {
            int u = que.front();
            que.pop();
            inQue[u]=false;
            for(auto ele: graph[u])
            {
                int v = ele.first;
                int w = ele.second;
                if(d[v]>d[u]+w){
                    d[v]=d[u]+w;
                    if(!inQue[v]){
                        que.push(v);
                        inQue[v]=true;
                    }
                }
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
