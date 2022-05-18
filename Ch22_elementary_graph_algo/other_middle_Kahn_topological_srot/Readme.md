# [Middle] Topological sort (DFS)
**Chapter: 22.4**

## Problem Formulation:
1. input: 
	1. G=(V, E), directed acyclic graph (DAG)
	
2. output: 
	1. vertices with topological order
    2. bool: whether it is cyclic graph.
	
## Limitations:
1. **for a cyclic graph, there is no topological sorting at all**.
2. Ther is one alternative: Kahn's algorithm.
	
## Main idea:
1. DFS and then reverse the visited list.
2. If a vertex is marked as todo but visited again-->cycle.

## Pseudo Code:
```
Topological_Sort(G)
    call DFS to compute finishing time v.f for each vertex v.
    as each vertex is finished, insert it onto the front of a linked list.
    return the linked list.
```

## Complexity:
1. Space: O(V)
2. Time: O(V+E)

## Limitations:
1. Recurvise version suffers from the limited system stack-->Kahn's algorithm may be an alternative.

## Leetcode classic problems:
1. [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)  

## Others modification:
1. Please be aware the iterative version is much tricker to implement due to the need of labeling the status.

## C++ code sample:
[210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)  
```c++
//DFS, recursion version
class Solution{
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        int N = numCourses;
        vector<vector<int>> out_graph(N);
        for(auto ele: prerequisites){
            out_graph[ele[1]].push_back(ele[0]);
        }
        vector<int> rtn;
        vector<bool> visited(N,false);
        vector<bool> todo(N,false); // Important, this can help determine there is a cycle.
        
        for(int i = 0;i<N;i++)
        {
            if(!visited[i] && !acyclic(out_graph, todo, visited, i, rtn)){
                return vector<int>();
            }            
        }
        
        reverse(rtn.begin(), rtn.end());
        return rtn;        
    }
    
    bool acyclic(vector<vector<int>>&out_graph, vector<bool>&todo, vector<bool>& visited, int node, vector<int>&rtn ){
        if(todo[node]){ // found a cycle.
            return false;
        }
        
        if(visited[node]){
            return true;
        }
        todo[node]=true;
        visited[node]=true;
        for(int ele: out_graph[node]){
            if(!acyclic(out_graph, todo , visited, ele, rtn)){
                return false;
            }
        }
        rtn.push_back(node);
        todo[node]=false;        // Important, set back to false.
        return true;
    }
};
```
